# LED-POV-Clock-Arduino
Persistence of Vision Clock project built using Arduino Nano for Creovate 2K25.



# LED POV Clock: Arduino Implementation for Creovate 2K25

**Summary:** This project is a Persistence of Vision (POV) clock built on the Arduino Nano platform. It was successfully designed and exhibited at the Creovate 2K25 tech fest.

---

## I. Technical Design and Components

This project relies on precise timing and synchronization to create the illusion of a floating display (Persistence of Vision).

### Key Components:
* **Microcontroller:** Arduino Nano (The control unit for timing and logic).
* **Display:** 16-LED strip (The actual display elements).
* **Synchronization:** Hall Effect Sensor (Crucial component for detecting the rotation starting point).
* **Mechanicals:** DC Motor and Power Supply.

### Core Mechanism: Synchronization
The primary function of the **Hall Effect Sensor** is to act as a zero-reference point. Every time the sensor detects the magnet passing, the rotation cycle resets, ensuring the time display starts in the same position on every rotation.

---

## II. Control Logic and Implementation

The C++ sketch (`POV_Clock_Sketch.ino`) focuses on high-speed execution to maintain a stable POV effect.

### Key Logic Challenges:
1.  **Precise Timing:** Managing the `delayMicroseconds()` value (line 151) is critical. This value must be finely tuned to match the motor speed, dictating how long each vertical column of LEDs is displayed.
2.  **Timekeeping:** The code uses `millis()` and interrupt detection to track time (seconds, minutes, hours), ensuring accurate time updates even during high-speed display operations.

### Function Overview:
* `loop()`: Contains the core synchronization logic, waiting for the Hall sensor to go LOW to start the drawing cycle (`while(val == LOW)`).
* `drawMinutesHand()`, `drawHoursHand()`, etc.: Functions that turn on specific LEDs to create the time hands and markers.

---

## III. Challenges and Problem Solving

| Challenge Faced | Technical Solution/Approach |
| :--- | :--- |
| **Flickering/Jitter** | Debugged the Hall Effect sensor readings to ensure a clean, reliable signal before starting the drawing cycle. |
| **Display Shift** | Required fine-tuning the `delayMicroseconds()` value to perfectly align the display hands at different motor speeds. |
| **Resource Management** | Utilized a separate power source for the LEDs/Motor to prevent the Arduino from browning out during peak current draw. |

---

## IV. Project Media and Code

Will upload later

**Source Code:** The complete C++ sketch is available in the file `POV_Clock_Sketch.ino`.
