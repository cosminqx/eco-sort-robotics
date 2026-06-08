# Software Setup

## Scope
This document covers the software environments that support the current prototype and the next planned integration stages. The repository is organized around a distributed control path rather than a single monolithic application.

## Current Software Areas
- Arduino firmware for the Uno R3 actuator layer
- Arduino firmware for the UNO WiFi Rev2 sensor and state layer
- Python communication bridge on the laptop
- Future computer vision and AI tooling for later perception work
- Optional dashboard and analytics components for monitoring and diagnostics

## Environment Strategy
- Keep embedded firmware and host software separate
- Use small, versioned interfaces between components
- Avoid adding dependencies that are not tied to a documented requirement
- Validate each layer independently before connecting them into a larger workflow

## Suggested Development Setup
- Arduino IDE or a compatible Arduino toolchain for firmware work
- Python 3.x environment for the laptop bridge and future computer vision work
- PySerial for serial routing between the two boards
- Serial monitor or terminal access for debugging message flow
- Documentation and logging workflow for experiment notes

## Step-by-Step Implementation Guide

### Step 1: Wiring and Safety Checks
- Verify the Uno R3, UNO WiFi Rev2, and Braccio connections independently before linking them through Python
- Confirm that both boards are stable on their own power and USB connections
- Keep the emergency stop path available during all bench tests
- Check that grounds, sensor wires, and servo connections are not shared incorrectly

### Step 2: Serial Communication From WiFi Rev2 to Laptop
- Load the WiFi Rev2 firmware first and confirm it can send newline-delimited sensor messages
- Open the laptop serial port for the Rev2 at a fixed baud rate
- Verify that messages are readable before adding any routing logic

Note: the current preferred board-to-board communication path is WiFi Rev2 -> Python bridge -> Uno R3. Direct board-to-board links are intentionally avoided to preserve modularity and fault isolation.

### Step 3: Python Bridge Script
- Open one serial connection to the WiFi Rev2 and one to the Uno R3
- Parse messages into key/value fields instead of relying on free-form text
- Forward only structured command messages to the Uno R3
- Log malformed lines and protocol errors rather than silently ignoring them

### Step 4: Commands From Python to Uno R3
- Start with STOP, START, and HOME before adding motion commands
- Confirm that the Uno R3 accepts and acknowledges commands one at a time
- Keep motion execution deterministic and conservative while the Braccio poses are being validated

### Step 5: Basic State Machine on WiFi Rev2
- Use the Rev2 to manage SAFE and RUNNING states
- Read the ultrasonic sensor and emit sensor packets regularly
- If the Rev2 determines a stop condition, send a STOP command through Python instead of driving servos directly

### Step 6: Full Pipeline Test
- Trigger a sensor event on the Rev2
- Confirm the Python bridge receives the message and forwards the intended command
- Confirm the Uno R3 executes the safe motion or stop behavior
- Record the result in the engineering journal before expanding the protocol

## Reference Snippets

### A) Arduino UNO WiFi Rev2: Sensor Reading and Message Output
```arduino
const int TRIG_PIN = 7;
const int ECHO_PIN = 6;
const int BUTTON_PIN = 2;
const int LED_RUN_PIN = 4;
const int LED_SAFE_PIN = 5;
const int OBSTACLE_THRESHOLD_CM = 20;

enum SystemState {
	SAFE,
	RUNNING
};

SystemState systemState = SAFE;
bool lastButtonState = HIGH;
unsigned long lastReportMs = 0;

long readDistanceCm() {
	digitalWrite(TRIG_PIN, LOW);
	delayMicroseconds(2);
	digitalWrite(TRIG_PIN, HIGH);
	delayMicroseconds(10);
	digitalWrite(TRIG_PIN, LOW);

	unsigned long duration = pulseIn(ECHO_PIN, HIGH, 30000);
	if (duration == 0) {
		return -1;
	}

	return duration / 58;
}

void setState(SystemState nextState) {
	systemState = nextState;
	digitalWrite(LED_RUN_PIN, systemState == RUNNING ? HIGH : LOW);
	digitalWrite(LED_SAFE_PIN, systemState == SAFE ? HIGH : LOW);
}

void sendSensorPacket(long distanceCm) {
	bool objectDetected = distanceCm > 0 && distanceCm <= OBSTACLE_THRESHOLD_CM;

	Serial.print("SENSOR|node=wifi_rev2|state=");
	Serial.print(systemState == RUNNING ? "RUNNING" : "SAFE");
	Serial.print("|distance_cm=");
	Serial.print(distanceCm);
	Serial.print("|object_detected=");
	Serial.println(objectDetected ? 1 : 0);
}

void sendCommand(const char *action, const char *reason) {
	Serial.print("CMD|source=wifi_rev2|action=");
	Serial.print(action);
	if (reason != NULL && reason[0] != '\0') {
		Serial.print("|reason=");
		Serial.print(reason);
	}
	Serial.println();
}

void setup() {
	pinMode(TRIG_PIN, OUTPUT);
	pinMode(ECHO_PIN, INPUT);
	pinMode(BUTTON_PIN, INPUT_PULLUP);
	pinMode(LED_RUN_PIN, OUTPUT);
	pinMode(LED_SAFE_PIN, OUTPUT);

	Serial.begin(115200);
	setState(SAFE);
}

void loop() {
	bool buttonState = digitalRead(BUTTON_PIN);
	if (lastButtonState == HIGH && buttonState == LOW) {
		setState(systemState == SAFE ? RUNNING : SAFE);
		if (systemState == SAFE) {
			sendCommand("STOP", "manual_toggle");
		} else {
			sendCommand("START", "manual_toggle");
		}
		delay(200);
	}
	lastButtonState = buttonState;

	long distanceCm = readDistanceCm();
	bool objectDetected = distanceCm > 0 && distanceCm <= OBSTACLE_THRESHOLD_CM;

	if (systemState == RUNNING && objectDetected) {
		sendCommand("STOP", "obstacle");
		setState(SAFE);
	}

	if (millis() - lastReportMs >= 250) {
		sendSensorPacket(distanceCm);
		lastReportMs = millis();
	}
}
```

### B) Python Bridge: Read From Rev2 and Forward to Uno R3
```python
import serial
import time

WIFI_PORT = "/dev/cu.usbmodem-WIFI"
UNO_PORT = "/dev/cu.usbmodem-R3"
BAUD_RATE = 115200


def parse_message(line: str) -> dict[str, str]:
    fields: dict[str, str] = {}
    parts = line.strip().split("|")

    if parts:
        fields["type"] = parts[0]

    for part in parts[1:]:
        if "=" in part:
            key, value = part.split("=", 1)
            fields[key] = value

    return fields


def forward_command(uno: serial.Serial, message: dict[str, str]) -> None:
    action = message.get("action")
    if not action:
        return

    payload = ["CMD", f"action={action}"]
    if message.get("reason"):
        payload.append(f"reason={message['reason']}")
    if message.get("seq"):
        payload.append(f"seq={message['seq']}")

    uno.write(("|".join(payload) + "\n").encode("utf-8"))


with serial.Serial(WIFI_PORT, BAUD_RATE, timeout=1) as wifi, serial.Serial(UNO_PORT, BAUD_RATE, timeout=1) as uno:
    time.sleep(2)

    while True:
        raw_line = wifi.readline().decode("utf-8", errors="ignore").strip()
        if not raw_line:
            continue

        message = parse_message(raw_line)
        if message.get("type") == "CMD":
            forward_command(uno, message)
        elif message.get("type") == "SENSOR":
            print(raw_line)
        elif message.get("type") == "ERR":
            print(f"WiFi Rev2 error: {raw_line}")
```

### C) Arduino Uno R3: Receive Commands and Control Braccio Safely
```arduino
#include <Braccio.h>

const int STOP_BUTTON_PIN = 2;
const int LED_RUN_PIN = 4;
const int LED_SAFE_PIN = 5;
const int BUZZER_PIN = 6;

bool robotRunning = false;

String readAction(const String &line) {
	int actionIndex = line.indexOf("action=");
	if (actionIndex < 0) {
		return "";
	}

	int endIndex = line.indexOf('|', actionIndex);
	if (endIndex < 0) {
		return line.substring(actionIndex + 7);
	}

	return line.substring(actionIndex + 7, endIndex);
}

void setSafeState() {
	robotRunning = false;
	digitalWrite(LED_RUN_PIN, LOW);
	digitalWrite(LED_SAFE_PIN, HIGH);
	tone(BUZZER_PIN, 220, 80);
}

void setRunningState() {
	robotRunning = true;
	digitalWrite(LED_RUN_PIN, HIGH);
	digitalWrite(LED_SAFE_PIN, LOW);
}

void goHome() {
	Braccio.ServoMovement(20, 90, 90, 90, 90, 90, 10);
}

void movePick() {
	Braccio.ServoMovement(20, 90, 55, 70, 70, 10, 10);
}

void movePlace() {
	Braccio.ServoMovement(20, 20, 80, 90, 90, 90, 10);
}

void executeAction(const String &action) {
	if (action == "STOP") {
		setSafeState();
		goHome();
		Serial.println("ACK|action=STOP|status=OK");
		return;
	}

	if (action == "START") {
		setRunningState();
		goHome();
		Serial.println("ACK|action=START|status=OK");
		return;
	}

	if (!robotRunning && action != "HOME") {
		Serial.println("ERR|code=SAFE_LOCK|message=Robot is stopped");
		return;
	}

	if (action == "HOME") {
		goHome();
		Serial.println("ACK|action=HOME|status=OK");
		return;
	}

	if (action == "MOVE_PICK") {
		movePick();
		Serial.println("ACK|action=MOVE_PICK|status=OK");
		return;
	}

	if (action == "MOVE_PLACE") {
		movePlace();
		Serial.println("ACK|action=MOVE_PLACE|status=OK");
		return;
	}

	Serial.println("ERR|code=UNKNOWN_ACTION|message=Unrecognized command");
}

void setup() {
	pinMode(STOP_BUTTON_PIN, INPUT_PULLUP);
	pinMode(LED_RUN_PIN, OUTPUT);
	pinMode(LED_SAFE_PIN, OUTPUT);
	pinMode(BUZZER_PIN, OUTPUT);

	Serial.begin(115200);
	setSafeState();
}

void loop() {
	if (digitalRead(STOP_BUTTON_PIN) == LOW) {
		setSafeState();
		goHome();
		Serial.println("ACK|action=STOP|status=HARD_OVERRIDE");
		delay(250);
	}

	if (Serial.available() > 0) {
		String line = Serial.readStringUntil('\n');
		line.trim();
		String action = readAction(line);
		if (action.length() > 0) {
			executeAction(action);
		}
	}
}
```

## Current Setup Checklist
- [x] Repository structure and documentation hierarchy defined
- [x] Early Arduino control and safety documentation established
- [ ] Firmware development environment standardized
- [ ] Python environment documented for bridge work
- [ ] Serial communication protocol finalized in code
- [ ] End-to-end integration test recorded in the journal

## Future Setup Notes
- The UNO WiFi Rev2 should remain the sensor and logic node rather than a motor controller
- The Uno R3 should remain the deterministic actuator node rather than a sensor hub
- The dashboard should be added only after the data path and control path are stable
