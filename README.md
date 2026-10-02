# Centralized Robotic Systems

Centralized Robotic Systems is a personal engineering project that explores how multiple robotic devices can be monitored and controlled through a unified, browser-based interface.

The project is being developed incrementally. Each phase introduces a new robotic device or system capability while building toward centralized coordination across devices with different hardware, functions, and levels of complexity.

## Project Status

| Phase | Device or Capability | Status |
|---|---|---|
| Phase 1 | Embedded robotic vehicle | Complete |
| Phase 2 | Motion-controlled robotic arm | Concept development |
| Future | Unified multi-device interface | Planned |

At present, the repository contains the completed Phase 1 robotic vehicle. Multi-device coordination has not been implemented yet.

## Phase 1: Embedded Robotic Vehicle Control System

Phase 1 demonstrates end-to-end remote control and two-way data communication between a browser interface and physical robotic hardware.

The vehicle has three primary functions:

1. Controllable multicolor lighting.
2. Forward, reverse, left, and right movement.
3. Distance scanning across a 180-degree field of view.

A browser-based interface accessible from devices on the same local network sends commands to the vehicle and displays returned sensor data.

### System Architecture

The system is divided into three primary layers:

- **Browser interface:** Provides lighting, movement, and scanning controls and displays scan results.
- **Raspberry Pi backend:** Hosts the Python/Flask service, processes HTTP requests, manages system state, and communicates with the Arduino through USB serial.
- **Arduino firmware:** Performs low-level control of the motors, servo, ultrasonic sensor, and lighting hardware.

This separation keeps the microcontroller firmware focused on hardware control while assigning interface and coordination functions to the Raspberry Pi.

### Communication Flow

```text
Browser Interface
       |
     HTTP
       |
Raspberry Pi 5
Python / Flask
       |
   USB Serial
       |
 Arduino Uno
       |
Motors, Servo, Ultrasonic Sensor, and Lighting
