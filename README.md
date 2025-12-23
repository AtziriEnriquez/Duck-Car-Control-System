# Closed-Loop Motor Control System (Duck Car)

## Overview
This project implements a closed-loop feedback controller to regulate the position of a DC-motor-driven cart. The system was designed, simulated, built, and experimentally tuned to meet real-world constraints on settling time, overshoot, robustness, and actuator limits.

The focus of this project is not only control design in simulation, but **debugging the gap between theory and physical hardware**.

---

## System Architecture
- DC motor modeled as a first-order system
- Position obtained by integrating motor velocity
- Position-to-voltage distance sensor
- Power amplifier with voltage saturation limits
- Feedback controller implemented in hardware

<img width="868" height="485" alt="blockdiagram" src="https://github.com/user-attachments/assets/6ca8e33c-08b8-4907-8ac0-c11fe0f09737" />

---

## Modeling and Simulation
- Identified motor parameters from experimental step-response data
- Linearized the sensor model around an operating point
- Combined motor, integrator, and sensor into an open-loop plant
- Analyzed uncompensated system stability, damping, and margins using MATLAB

---

## Controller Design
- Designed a PD compensator using root locus and frequency-domain methods
- Selected performance targets for settling time, overshoot, bandwidth, and robustness
- Verified predicted performance in MATLAB prior to hardware implementation

<img width="1198" height="942" alt="PDcontroller" src="https://github.com/user-attachments/assets/0fd0ed4f-406d-4843-a0b0-7ce920cad8e1" />

---

## Hardware-in-the-Loop Debugging
Initial controller designs that performed well in simulation did not behave as expected on the physical system due to unmodeled effects such as static friction, sensor noise, and actuator saturation.

To address this:
- Controller gain was increased to overcome friction and improve responsiveness
- High-frequency roll-off was added to suppress derivative noise amplification
- Oscilloscope measurements were used to validate control effort and disturbance rejection

---

## Experimental Results
- Settling time: ~2.4 s  
- Zero steady-state error to step input  
- Bandwidth increased from ~2.9 to ~4.8 rad/s  
- Control voltage remained within ±12 V amplifier limits  

These results demonstrate a deliberate tradeoff between overshoot and real-world responsiveness.

---

## Tools & Technologies
- MATLAB / Control System Toolbox
- Oscilloscope-based debugging
- Analog control circuitry
- Experimental system identification
