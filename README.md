# Smart Automotive Airbag System

## 📌 Short Description

The **Smart Automotive Safety & Airbag Simulation System** is a safe educational embedded-systems prototype developed using the **STM32F103C8T6 Blue Pill**.

The system demonstrates the basic concept of an automotive safety controller using the sequence:

> **SENSE → DECIDE → ACT**

A **5 kg load cell with an HX711 amplifier** is used to detect whether a passenger is present. An **MPU6050 accelerometer/gyroscope** monitors acceleration and detects simulated impact conditions using experimentally configurable thresholds.

When an impact condition is detected, the STM32 evaluates the passenger-presence condition and activates a **safe visual airbag deployment mechanism using an SG90 servo motor**.

A **16×2 I²C LCD** displays system status, an active buzzer provides an audible warning, and red/green LEDs indicate system states. A push button is provided to reset the system after a simulated deployment.

A small **5 V DC fan** may be used only to create a visual fabric-movement effect during demonstration. It is **not an airbag inflator**.

> ⚠️ **Educational Safety Notice:**  
> This project is an educational simulation only. It is not a real automotive airbag controller and must not be used in a real vehicle or connected to an actual airbag system. The servo and lightweight fabric mechanism are intended only to demonstrate the visual concept of airbag deployment.

---

# 1. Problem Statement

Automotive safety systems must rapidly detect abnormal vehicle conditions and respond appropriately. Real automotive airbag systems are highly specialized safety-critical systems involving dedicated sensors, validated algorithms, redundant electronics, and controlled deployment mechanisms.

For educational purposes, it is useful to develop a low-cost prototype that demonstrates the fundamental embedded-system concept without using pyrotechnic devices or real airbags.

The problem addressed by this project is:

> **How can a microcontroller-based system sense passenger presence and simulated impact conditions, make a safety decision, and activate a safe visual response using commonly available embedded-system components?**

The proposed solution uses an STM32 microcontroller together with load-cell sensing, inertial sensing, display, indicators, and a servo-controlled mechanical mechanism.

---

# 2. Objectives

The main objectives are:

- Develop an STM32-based automotive safety simulation.
- Detect passenger presence using a load cell and HX711 amplifier.
- Measure acceleration using an MPU6050.
- Detect simulated impact conditions using configurable thresholds.
- Implement a simple finite-state machine.
- Demonstrate the SENSE → DECIDE → ACT architecture.
- Control an SG90 servo using PWM.
- Display system status using a 16×2 I²C LCD.
- Provide audible warning using a buzzer.
- Provide visual status indication using red and green LEDs.
- Implement a manual reset mechanism.
- Develop a modular Embedded C firmware architecture.
- Demonstrate hardware-software integration.

---

# 3. Features

- STM32F103C8T6-based control system
- MPU6050 accelerometer/gyroscope interface
- HX711 load-cell interface
- Passenger-presence detection
- Configurable passenger threshold
- Configurable impact threshold
- 16×2 I²C LCD
- SG90 servo-based visual deployment
- Active buzzer
- Red and green LED indicators
- Push-button reset
- PWM-based servo control
- I²C sensor communication
- GPIO-based peripheral control
- Optional UART debugging
- Finite-state-machine control
- Safe educational mechanical demonstration

---

# 4. System Architecture

```text
                    ┌─────────────────────┐
                    │       Passenger     │
                    │       / Load        │
                    └──────────┬──────────┘
                               │
                               ▼
                        ┌─────────────┐
                        │  Load Cell  │
                        └──────┬──────┘
                               │
                               ▼
                         ┌──────────┐
                         │  HX711   │
                         └────┬─────┘
                              │
                              │
                              ▼
                    ┌────────────────────┐
                    │                    │
                    │      STM32         │
                    │     F103C8T6        │
                    │                    │
                    │  Decision Logic    │
                    │       + FSM        │
                    └───────┬────────────┘
                            │
              ┌─────────────┼──────────────┐
              │             │              │
              ▼             ▼              ▼
         ┌─────────┐   ┌─────────┐   ┌────────────┐
         │ MPU6050 │   │  LCD    │   │ Indicators │
         │         │   │ 16×2    │   │ LED/Buzzer │
         └─────────┘   └─────────┘   └────────────┘
                            │
                            │
                            ▼
                     ┌────────────┐
                     │ SG90 Servo │
                     └─────┬──────┘
                           │
                           ▼
                  Safe Visual Deployment
                        Mechanism

                       5 V DC Fan
                           │
                           ▼
                  Fabric Movement Effect
