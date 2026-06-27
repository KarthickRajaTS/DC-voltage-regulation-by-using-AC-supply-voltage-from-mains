# DC-voltage-regulation-by-using-AC-supply-voltage-from-mains
Conversion of Domestic AC Mains to a Regulated 12 V DC Supply for Consumer Electronics Applications
Conversion of Domestic AC Mains to a Regulated 12 V DC Supply for Consumer Electronics Applications

Project Overview

This project demonstrates the complete design and simulation of an AC-DC power supply capable of converting domestic mains voltage into a regulated 12 V DC output suitable for powering consumer electronic devices.

## Circuit Diagram
![Circuit](images/circuit.png)


The design combines traditional transformer-based isolation and rectification with a DC-DC boost conversion stage to achieve a stable output voltage under varying load conditions.

The entire system was designed and verified using LTSpice, with emphasis on component selection, power conversion principles, voltage regulation, ripple reduction, and practical non-ideal effects.

---

Design Objectives

- Convert domestic AC mains supply to regulated DC output.
- Provide electrical isolation between mains and load.
- Step down mains voltage to a safer low-voltage level.
- Rectify AC voltage into DC.
- Reduce ripple using capacitor filtering.
- Regulate output voltage using a switching converter.
- Deliver a stable 12 V output suitable for consumer electronics applications.

---

Target Specifications

Parameter| Value
Input Voltage| 247 V AC RMS
Input Frequency| 50 Hz
Output Voltage| 12 V DC
Output Current| 1.5 A
Output Power| 18 W
Simulation Platform| LTSpice

---

System Architecture

The power supply is divided into two major stages:

Stage 1: AC-DC Rectification and Voltage Step-Down

This stage converts the high-voltage AC mains into an unregulated low-voltage DC source.

Components:

- Mains Isolation Transformer
- Step-Down Transformer
- Bridge Rectifier
- Filter Capacitor

Functions:

- Provides galvanic isolation from the mains.
- Reduces mains voltage to a lower AC voltage.
- Converts AC voltage to pulsating DC.
- Smooths the rectified waveform to produce DC suitable for the next stage.

---

Stage 2: DC-DC Boost Converter

This stage regulates the filtered DC voltage and produces the final output voltage.

Components:

- Input Filter Capacitor Voltage Source
- Inductor
- PWM Source
- N-Channel MOSFET
- Schottky Diode
- Output Capacitor
- Load Resistor

Functions:

- Stores and transfers energy through the inductor.
- Uses high-frequency switching to regulate output voltage.
- Boosts and stabilizes the DC output.
- Minimizes output voltage ripple.
- Supplies power to the load.

---

Block Diagram

Domestic AC Mains (247 V AC)

↓

Isolation & Step-Down Transformer

↓

Bridge Rectifier

↓

Filter Capacitor

↓

Unregulated DC Bus

↓

Boost Converter

├── Inductor

├── PWM Generator

├── N-Channel MOSFET

├── Schottky Diode

└── Output Capacitor

↓

Regulated 12 V DC Output

↓

Consumer Electronic Load

---

Design Methodology

The design process was divided into the following stages:

1. Transformer Modeling and Turns Ratio Calculation
2. Magnetizing Inductance Selection
3. Bridge Rectifier Design
4. Filter Capacitor Sizing
5. Boost Converter Topology Selection
6. Inductor Design
7. PWM Duty Cycle Optimization
8. Output Capacitor Selection
9. Ripple Voltage Analysis
10. Load Regulation Verification
11. Current and Power Flow Analysis

---

Key Learning Outcomes

- Transformer modeling using coupled inductors.
- Practical implementation of AC-DC conversion.
- Full-wave bridge rectification.
- Capacitor filtering and ripple reduction.
- Boost converter operation and control.
- PWM-based voltage regulation.
- Analysis of inrush current and switching waveforms.
- Investigation of transformer current, capacitor current, and load current characteristics.
- Understanding of power flow from mains input to regulated DC output.

---

Future Improvements

- Efficiency optimization.
- Thermal analysis of semiconductor devices.
- Closed-loop feedback control.
- PCB implementation.
- EMI and EMC analysis.
- Hardware prototype development and testing.
