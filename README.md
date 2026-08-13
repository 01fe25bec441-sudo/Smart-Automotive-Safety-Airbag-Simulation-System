# 🚗 Smart-Automotive-Airbag-System

An STM32-based embedded system that demonstrates crash detection, passenger detection, decision-making, and safe airbag deployment simulation.

##  Overview

Real automotive airbag systems use complex and safety-critical hardware that cannot be safely tested in an academic environment.

This project develops a low-cost and reusable automotive safety simulation platform using an STM32F103C8 microcontroller. The system detects simulated impacts using an MPU6050, detects passenger presence using a load cell and HX711, and demonstrates the safety response through a servo-operated airbag compartment along with visual and audible alerts.

> **Note:** This is an educational simulation and does not replicate or replace a real automotive airbag system.

---

##  Objectives

- Detect simulated impacts using the MPU6050.
- Detect passenger presence using a load cell.
- Process sensor data using the STM32F103C8.
- Implement threshold-based crash detection.
- Demonstrate airbag deployment using an SG90 servo.
- Display system status using a 16×2 I²C LCD.
- Provide visual and audible alerts.
- Create a safe, reusable and low-cost automotive safety demonstration platform.

---

##  System Concept

The system follows a simple:

**SENSE → DECIDE → ACT**

### SENSE
- MPU6050 → Impact detection
- Load Cell + HX711 → Passenger detection

### DECIDE
- STM32F103C8 processes sensor data.
- Threshold-based logic determines the system state.

### ACT
- SG90 Servo → Opens airbag simulation compartment
- Buzzer → Warning alert
- Red LED → Crash indication
- LCD → System status
- DC Fan → Visual fabric movement effect

---

## 🧩 Hardware Components

| Component | Purpose |
|---|---|
| STM32F103C8 | Main microcontroller |
| MPU6050 | Accelerometer/Gyroscope for impact sensing |
| Load Cell | Passenger/occupant detection |
| HX711 | Load-cell signal interface |
| SG90 Servo | Airbag compartment mechanism |
| 16×2 I²C LCD | Status display |
| Active Buzzer | Audible alert |
| Red LED | Crash indication |
| Green LED | Normal status |
| Push Button | System reset |
| 5V DC Fan | Visual fabric movement effect |

---

## Communication & Control

| Interface | Component |
|---|---|
| I²C | MPU6050 |
| I²C | 16×2 LCD |
| GPIO | Buzzer |
| GPIO | LEDs |
| GPIO | Reset Button |
| PWM | SG90 Servo |
| GPIO | HX711 |

---

##  Working Principle

### 1. System Initialization

The STM32 initializes the sensors and peripherals.

### 2. Passenger Detection

The load cell measures the load applied to the model seat.

If the measured load exceeds the configured threshold:

`Passenger Present = YES`

### 3. Impact Detection

The MPU6050 continuously measures acceleration.

If the measured acceleration exceeds the configured threshold:

`Impact Detected = YES`

### 4. Decision Making

The STM32 evaluates the sensor conditions.

```text
Passenger Present
        +
Impact Detected
        ↓
Safety Response
