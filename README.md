

Smart Predictive Maintenance System

Team TJ TITANS | WireWizards Hackathon 2026 | Problem Statement ECW260006: Predictive Maintenance for Rotating Machines

A low-cost IoT unit mounted on a motor that tracks vibration and temperature and warns before the machine fails. An ESP32 does the analysis on the device, so it also works offline.

Team
Name	Role
Ashwin K	Team Leader
Kumaravel T	Member
Arunkumar P	Member
Magesh R	Member

Faculty Mentor: Mr. Thiyagarajan N | Team ID: EC026

Problem

Rotating machines such as motors, fans and pumps often run until they fail. This causes downtime, repair cost and safety risk.

Solution
MPU6050 measures vibration and LM35D measures temperature.
ESP32 compares the readings with thresholds and decides Normal, Warning or Critical.
Green, yellow and red LEDs show the status on the machine; readings are also printed to the Serial Monitor.
Faults detected

Imbalance, shaft misalignment, bearing wear / looseness (vibration) and overheating (temperature).

Hardware (current prototype)
Component	Purpose
ESP32 DevKit	Main controller
MPU6050	Vibration (I2C)
LM35D	Temperature (analog)
Green / yellow / red LEDs + 220 ohm resistors	Status indication
5V power supply (to ESP32 VIN)	Powers the whole unit
Breadboard, jumper wires	Prototype build

Full pin connections and wiring diagram: hardware/pinout.md or docs/Pinout.pdf

Quick pinout
Part	ESP32 pin
MPU6050 SDA / SCL	GPIO 21 / GPIO 22
LM35D output	GPIO 34
Green LED	GPIO 25
Yellow LED	GPIO 26
Red LED	GPIO 27
5V supply (+) / (-)	VIN / GND
Alert logic
State	Condition	LED
NORMAL	Below warning limits	Green
WARNING	Temp >= 40 C or vibration >= 1.5 m/s^2	Yellow
CRITICAL	Temp >= 50 C or vibration >= 3.0 m/s^2	Red
SENSOR ERROR	MPU6050 not found or LM35D out of range	Red

Limits should be calibrated on the test rig against a healthy baseline.

Getting started
Install the Arduino IDE and the ESP32 board package.
In Library Manager install Adafruit MPU6050 and Adafruit Unified Sensor.
Wire the parts as in hardware/pinout.md.
Open firmware/predictive_maintenance/predictive_maintenance.ino, select your ESP32 board and upload.
Open the Serial Monitor at 115200 baud to see temperature, vibration and status.
Prototype

Breadboard prototype

Team working on the project

Project structure
firmware/predictive_maintenance/   ESP32 sketch (MPU6050 + LM35D + LEDs)
hardware/                          pinout and wiring notes
docs/                              presentation and images
Roadmap
 MPU6050 vibration + LM35D temperature with LED status
 Motor current sensing (ACS712)
 OLED display
 RMS and FFT fault-frequency analysis
 Z-score anomaly check against a healthy baseline
 Wi-Fi + MQTT/HTTP, Blynk/ThingSpeak dashboard
 TinyML upgrade
License

MIT. See LICENSE.
