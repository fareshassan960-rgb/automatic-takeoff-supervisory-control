# Automatic Takeoff Supervisory Control System

## Project Overview

This project presents the modeling and implementation of an **Automatic Takeoff (ATO) supervisory control system** for a fixed-wing aircraft using MATLAB and Simulink.

The system was developed as a high-level decision-making layer that manages takeoff-related actuator commands while monitoring aircraft states, system failures, and abort conditions. It connects the cockpit and aircraft flight-dynamics model through a centralized supervisory controller.

The project focuses on supervisory logic rather than low-level aircraft dynamics alone. The controller receives aircraft-state information and fault signals, evaluates the current takeoff condition, and generates coordinated commands for the main aircraft actuators.

## Project Objectives

- Develop a supervisory controller for automatic takeoff
- Coordinate aircraft actuator commands during the takeoff sequence
- Monitor engine, tyre, and abort-related fault signals
- Generate safe actuator commands under normal and faulted conditions
- Connect the supervisory controller with a flight-dynamics model
- Provide a clear transition between normal takeoff and abort behavior
- Evaluate the interaction between the cockpit, controller, and aircraft model in Simulink

## System Architecture

The Simulink model contains three main elements:

1. **Cockpit subsystem**  
   Provides the aircraft data bus and pilot-related inputs.

2. **ATO supervisory controller**  
   Processes aircraft states, heading information, runway-condition inputs, fault signals, and abort conditions.

3. **Aircraft flight-dynamics model**  
   Receives the actuator commands and returns the aircraft response to the simulation.

The controller generates the following outputs:

- Left throttle command
- Right throttle command
- Flap command
- Elevator command
- Nose-wheel steering command
- Rudder command
- Brake command
- Landing-gear command

## Fault Monitoring

The fault-management subsystem includes logic for:

- Automatic takeoff abort
- Left-engine failure
- Right-engine failure
- Left-main-tyre failure
- Right-main-tyre failure
- Nose-tyre failure

Each fault input is converted to a Boolean signal and combined into an error bus. The ATO controller uses this error bus to determine whether the takeoff should continue or whether a safe abort response is required.

## Supervisory-Control Logic

The supervisory block receives:

- Abort conditions
- Aircraft-speed information
- Aircraft attitude
- Rate-of-climb data
- Pitch angle
- Heading data
- Runway-related information
- Fault signals

Based on these inputs, the controller determines the required actuator commands for the current phase of takeoff.

The logic is intended to maintain coordinated control during the takeoff run and initial climb while preserving the ability to stop the aircraft safely when a critical failure is detected.

## Main Outcomes

- Implemented fault-tolerant takeoff supervisory logic
- Generated coordinated actuator commands for the aircraft model
- Produced safe abort behavior during simulated engine and tyre failures
- Connected supervisory control with the cockpit and aircraft flight-dynamics model
- Demonstrated real-time signal exchange through the aircraft data bus
- Verified the response of throttle, flap, elevator, rudder, brake, wheel-steering, and landing-gear commands

## Project Images

### Complete Simulink Architecture

![Complete automatic takeoff Simulink model](images/ato_complete_simulink_model.png)

### Internal ATO Supervisory Logic

![Internal ATO supervisory logic](images/ato_supervisor_internal_logic.png)

### Fault-Input and Error-Bus Logic

![Fault-input and error-bus logic](images/ato_fault_input_logic.png)

## Software Used

- MATLAB
- Simulink
- Supervisory decision logic
- Aircraft flight-dynamics simulation environment

## Engineering Applications

The same supervisory-control structure can support later work in:

- Automatic takeoff and landing
- Flight-envelope protection
- Fault detection and isolation
- Rejected-takeoff logic
- Autopilot mode management
- Aircraft health monitoring
- Pilot-assistance systems
- Hardware-in-the-loop testing

## Current Project Status

The current model demonstrates the integration of takeoff supervisory logic, actuator-command generation, and fault-response behavior within a Simulink-based aircraft simulation.

Further work may include:

- More detailed takeoff-state sequencing
- Runway-length and decision-speed logic
- Wind and crosswind disturbance cases
- Sensor-noise and actuator-delay modeling
- Additional failure combinations
- Hardware-in-the-loop implementation
- Formal verification of supervisory states and transitions

## Suggested Repository Structure

```text
automatic-takeoff-supervisory-control/
├── README.md
├── images/
│   ├── ato_complete_simulink_model.png
│   ├── ato_supervisor_internal_logic.png
│   └── ato_fault_input_logic.png
├── model/
│   └── publishable Simulink files
└── results/
    └── selected response plots and test cases
```

Only model files, libraries, aircraft data, and images that are permitted for public release should be uploaded.

## Author

**Fares Hassan**  
Aerospace Engineering Graduate  
Institute of Space Technology, Islamabad

LinkedIn:  
https://www.linkedin.com/in/fares-hassan-177728273/
