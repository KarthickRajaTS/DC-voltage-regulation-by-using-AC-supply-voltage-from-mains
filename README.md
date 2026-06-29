# DC-voltage-regulation-by-using-AC-supply-voltage-from-mains
Conversion of Domestic AC Mains to a Regulated 12 V DC Supply for Consumer Electronics Applications
Conversion of Domestic AC Mains to a Regulated 12 V DC Supply for Consumer Electronics Applications

Project Overview

This project demonstrates the complete design and simulation of an AC-DC power supply capable of converting domestic mains voltage into a regulated 12 V DC output suitable for powering consumer electronic devices.

## Circuit Diagram

![Circuit](IMG-20260625-WA0016.jpg)


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
Output Current| 2 A
Output Power| 24 W
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

Transformer Modeling

Objective

The transformer stage provides galvanic isolation from the AC mains and steps down the domestic supply voltage to a lower AC voltage suitable for rectification and regulation.

Design Specifications

Parameter| Value
Input Voltage| 247 V AC RMS
Output Voltage| 9 V AC RMS
Output Current| 2 A RMS
Frequency| 50 Hz

The input voltage was assumed to be 247 V RMS to account for practical variations in the distribution network.

---

Transformer Model

The transformer was modeled in LTSpice using two coupled inductors.

The relationship between transformer voltage ratio, turns ratio and inductance ratio is given by:

Vp/Vs = N1/N2

L1/L2 = (N1/N2)²

Where:

- Vp = Primary Voltage
- Vs = Secondary Voltage
- N1 = Primary Turns
- N2 = Secondary Turns
- L1 = Primary Inductance
- L2 = Secondary Inductance

---

Turns Ratio Calculation

Given:

Vp = 247 V

Vs = 9 V

Therefore,

N1/N2 = Vp/Vs

N1/N2 = 247/9

N1/N2 ≈ 27

Thus,

L1/L2 = 27²

L1/L2 = 729

---

Primary Inductance Calculation

The primary inductance was selected based on the desired magnetizing current under no-load conditions.

The inductance can be estimated using:

L1 = Vp / (2πfIm)

Where:

- Vp = 247 V
- f = 50 Hz
- Im = Magnetizing Current

The no-load magnetizing current was assumed to be approximately 30 mA, which falls within a practical range for a transformer of this size.

Substituting the values:

L1 = 247 / (2 × π × 50 × 0.03)

L1 ≈ 26 H

Therefore,

Primary Inductance (L1) = 26 H

---

Secondary Inductance Calculation

Using the inductance ratio:

L1/L2 = 729

Substituting L1 = 26 H:

26/L2 = 729

L2 = 26/729

L2 = 0.0356 H

L2 ≈ 36 mH

Therefore,

Secondary Inductance (L2) = 36 mH

---

Coupling Coefficient

The transformer coupling factor was chosen as:

K = 0.995

A coupling coefficient slightly less than unity introduces realistic leakage flux and magnetic losses that are present in practical transformers.

---

Winding Resistance Modeling

Real transformers are not ideal components. The copper windings possess finite resistance which causes:

- Copper losses (I²R losses)
- Voltage drop under load
- Reduced efficiency
- Heat generation

To account for these practical effects, winding resistance was included in the simulation model.

Selected Values

Winding| Resistance
Primary| 0.1 Ω
Secondary| 0.05 Ω

Justification

These values were selected as practical non-ideal winding resistances for simulation purposes.

The primary winding contains a larger number of turns and therefore a longer conductor length. Consequently, a slightly higher winding resistance was assigned.

The secondary winding contains fewer turns and a shorter conductor length, resulting in a lower winding resistance.

Including winding resistance provides:

- More realistic transformer behavior
- Improved load regulation analysis
- Representation of copper losses
- Prevention of unrealistic ideal transformer performance

The chosen values are approximations intended to model practical transformer behavior and can be refined further if measured winding resistance data becomes available.

---

Final Transformer Parameters

Parameter| Value
Primary Inductance (L1)| 26 H
Secondary Inductance (L2)| 36 mH
Coupling Coefficient| 0.995
Primary Resistance| 0.1 Ω
Secondary Resistance| 0.05 Ω
Input Voltage| 247 V AC RMS
Output Voltage| 9 V AC RMS
Output Current| 2 A RMS

The resulting transformer model was used as the front-end isolation and voltage step-down stage for the AC-DC converter simulation.

Rectification Stage

Objective

The transformer output is an AC waveform, whereas the subsequent stages of the power supply require a DC voltage source.

The purpose of the rectification stage is to convert the low-voltage AC output from the transformer into pulsating DC suitable for capacitor filtering and further voltage regulation.

---

Rectifier Topology

A full-wave bridge rectifier configuration was used.

The bridge rectifier consists of four diodes connected in a bridge arrangement.

This configuration enables both positive and negative half cycles of the AC waveform to contribute to the output, resulting in:

- Improved transformer utilization
- Higher average DC output voltage
- Reduced output ripple compared to half-wave rectification
- Better efficiency in power conversion

---

Diode Selection

Parameter| Value
Part Number| RFN5BM6S
Device Type| Silicon Rectifier Diode
Application| Full-Wave Bridge Rectifier

---

Operating Principle

A diode is a semiconductor device that permits current flow in the forward direction while blocking current flow in the reverse direction.

During each AC cycle:

- Two diodes conduct during the positive half cycle.
- The remaining two diodes conduct during the negative half cycle.

As a result, the load experiences current flow in a single direction for both halves of the AC waveform.

This process converts alternating current into pulsating direct current.

---

Forward Voltage Drop

Silicon rectifier diodes typically exhibit a forward voltage drop in the range:

0.8 V to 1.1 V

Since a bridge rectifier conducts through two diodes simultaneously during each half cycle, the total voltage drop becomes:

Vdrop = 2 × Vf

Assuming:

Vf ≈ 0.9 V

Total bridge voltage drop:

Vdrop ≈ 1.8 V

This voltage loss must be considered when estimating the DC voltage available after rectification.

---

Design Considerations

The selected diode must be capable of:

- Handling the secondary current of the transformer.
- Withstanding repetitive charging pulses from the filter capacitor.
- Tolerating reverse voltage stress during non-conducting intervals.
- Operating reliably at the intended load current.

The RFN5BM6S diode was selected to perform full-wave rectification while introducing realistic forward voltage losses into the simulation.

---

Output of the Rectification Stage

The bridge rectifier converts the transformer secondary AC voltage into pulsating DC.

This pulsating DC is subsequently filtered using a bulk capacitor to produce a smoother DC voltage for the boost converter stage.

Transformer Secondary AC

↓

Bridge Rectifier

↓

Pulsating DC

↓

Filter Capacitor

↓

Smoothed DC Bus

Capacitor Filter

Objective

The output of the bridge rectifier is a pulsating DC waveform containing ripple components. A bulk capacitor is placed across the rectifier output to store energy during voltage peaks and supply energy during voltage valleys, thereby reducing ripple before feeding the boost converter stage.

---

Capacitor Selection

The capacitance required to achieve a desired ripple voltage can be estimated using:

[
C = I_L/f_ripple×∆V
]

Where:

- C = Capacitance (F)
- I_L = Load Current (A)
- f_{ripple} = Ripple Frequency (Hz)
- \Delta V = Allowable Ripple Voltage (V)

For a full-wave bridge rectifier operating from a 50 Hz mains supply:

[
f_{ripple} = 2*50 = 100Hz
]

---

Initial Calculation

Assuming:

- Load Current = 2 A
- Ripple Frequency = 100 Hz
- Allowable Ripple Voltage = 0.5 V

[
C = 2/(100×0.5)
]

[
C = 0.04F
]

[
C = 40,000\mu F
]

This calculation indicates that approximately 40,000 µF would be required to limit the ripple voltage to 0.5 V.

---

Practical Design Consideration

The capacitor output is not directly connected to the load. Instead, it serves as the input source for a boost converter stage.

Since the boost converter provides voltage regulation and has sufficient headroom to compensate for moderate variations in input voltage, a larger ripple voltage can be tolerated at the capacitor output.

Allowing a ripple voltage of approximately 3 V significantly reduces the required capacitance while maintaining proper converter operation.

Assuming:

- Load Current = 2 A
- Ripple Frequency = 100 Hz
- Allowable Ripple Voltage = 3 V

[
C = 2/(100*3)
]

[
C = 0.00667F
]

[
C = 6,670 uF
]

The nearest standard capacitor value selected is:

[
C = 6,800 uF
]

---

Capacitor Voltage Rating

The rectified DC voltage across the capacitor remains below 12 V during normal operation.

To provide adequate design margin against startup transients, ripple voltage, and component tolerances, a voltage rating significantly higher than the operating voltage was selected.

Selected capacitor voltage rating:

[
V_{rating} = 25V
]

This provides sufficient safety margin while ensuring reliable operation.

---

Final Capacitor Selection

Parameter| Value
Capacitance| 6800 µF
Voltage Rating| 25 V
Ripple Frequency| 100 Hz
Allowable Ripple Voltage| 3 V
Application| Rectifier Output Filter Capacitor

The selected 6800 µF / 25 V capacitor provides adequate energy storage, reduces rectifier ripple, and supplies a stable input source for the boost converter stage while maintaining a practical component size.

Boost Converter Inductor Selection

Objective

The inductor is the primary energy storage element in a boost converter. During the MOSFET ON period, energy is stored in the magnetic field of the inductor. During the MOSFET OFF period, the stored energy is transferred to the output through the Schottky diode, resulting in a boosted output voltage.

Proper inductor selection is essential to control current ripple, maintain continuous conduction, and ensure stable converter operation.

---

Inductor Selection

The boost converter inductance can be estimated using:

[
L = Vin×D/(∆I_L*f_s)
]

Where:

- L = Inductance (H)
- V_{in} = Input Voltage (V)
- D = Duty Cycle
- ∆I_L = Inductor Current Ripple (A)
- f_s = Switching Frequency (Hz)

---

Design Approach

The minimum inductance requirement was estimated using the standard boost converter inductor sizing equation:

[
L = V_in×D/∆I_L×f_s
]

Using the expected operating conditions, the calculated inductance was approximately:

[
L = 13.8 uH
]

A standard value of 56 µH was selected to provide additional ripple current reduction and improve converter stability.

The PWM duty cycle was not fixed solely from theoretical calculations. Instead, LTSpice simulations were performed and the duty cycle was adjusted iteratively until the desired output voltage and load performance were achieved.

This approach allowed verification of converter behavior under realistic operating conditions, including component non-idealities, voltage drops, and load effects.

The final duty cycle used in the simulation was obtained through tuning and validation of the converter output rather than direct analytical calculation alone.
---

Inductance Calculation

Substituting the design parameters:

[
L = 11.4×0.073/(0.6×100000)
]

[
L = 13.8 uH
]

Therefore, the minimum calculated inductance required for the converter is:

[
L_{min} = 13.8 uH
]

---

Practical Component Selection

In practical designs, a standard inductor value larger than the theoretical minimum is often selected to:

- Reduce inductor current ripple.
- Improve current stability.
- Minimize peak current stress on the MOSFET.
- Reduce output voltage ripple.
- Improve converter robustness under varying load conditions.

Based on these considerations, a standard value of:

[
L = 56 uH
]

was selected.

The chosen inductance is approximately four times the minimum calculated value, providing additional ripple reduction and stable operation while remaining suitable for the selected switching frequency.

---

Final Inductor Selection

Parameter| Value
Calculated Inductance| 13.8 µH
Selected Inductance| 56 µH
Switching Frequency| 100 kHz
Application| Boost Converter Energy Storage Element

The selected 56 µH inductor provides adequate energy storage, reduced current ripple, and reliable operation for the 12 V DC output power stage.

PWM Source Configuration

Objective

A PWM (Pulse Width Modulation) source is used to drive the gate of the N-channel MOSFET in the boost converter. By controlling the MOSFET switching interval, the converter regulates the transfer of energy from the inductor to the output.

---

PWM Parameters

Parameter| Value
Initial Voltage (Vinitial)| 0 V
ON Voltage (Von)| 10 V
Delay Time (Tdelay)| 0 s
Rise Time (Trise)| 100 ns
Fall Time (Tfall)| 100 ns
ON Time (Ton)| 2.6 µs
Period (Tperiod)| 10 µs

---

Parameter Description

Initial Voltage (Vinitial)

When the PWM signal is in the OFF state, the MOSFET gate voltage remains at:

[
V_{initial}=0V
]

This keeps the MOSFET turned OFF.

---

ON Voltage (Von)

When the PWM signal is in the ON state, the MOSFET gate receives:

[
V_{on}=10V
]

This voltage is sufficient to drive the MOSFET into conduction.

---

Delay Time (Tdelay)

[
T_{delay}=0s
]

The PWM waveform begins immediately at the start of the simulation.

---

Rise Time (Trise)

[
T_{rise}=100ns
]

This is the time required for the PWM signal to transition from 0 V to 10 V.

---

Fall Time (Tfall)

[
T_{fall}=100ns
]

This is the time required for the PWM signal to transition from 10 V to 0 V.

---

ON Time (Ton)

[
T_{on}=2.6 us
]

The MOSFET remains ON for 2.6 µs during each switching cycle, allowing the inductor to store energy.

---

Switching Period (Tperiod)

[
T_{period}=10 us
]

One complete PWM cycle lasts 10 µs.

---

Switching Frequency

The switching frequency is calculated using:

[
f=1/T
]

Substituting:

[
f=1/10 us
]

[
f=100,000Hz
]

[
f=100kHz
]

Therefore, the boost converter operates at a switching frequency of 100 kHz.

---

Duty Cycle

The duty cycle is calculated as:

[
D=T_on/T_period
]

[
D= 2.6 us/10 us
]

[
D=0.26
]

[
D=26%
]

This means the MOSFET remains ON for 26% of each switching cycle and OFF for the remaining 74%.

---

Function in the Boost Converter

During the ON interval:

- The MOSFET conducts.
- Energy is stored in the inductor magnetic field.

During the OFF interval:

- The MOSFET turns OFF.
- The inductor releases stored energy through the Schottky diode.
- Energy is transferred to the output capacitor and load.

This switching process repeats at 100 kHz to regulate the converter output voltage.

MOSFET Selection

Objective

The MOSFET acts as the primary switching device in the boost converter. It is controlled by the PWM source and enables the periodic storage and transfer of energy through the inductor.

---

MOSFET Selection Guideline

The choice between an N-channel and P-channel MOSFET depends on the switching configuration.

In this design, the MOSFET is placed between the inductor and ground, which is commonly referred to as low-side switching.

Since the source terminal remains near ground potential, an N-channel MOSFET can be driven easily using a positive gate voltage from the PWM source.

Advantages of low-side switching include:

- Simpler gate drive circuitry
- Lower conduction losses
- Better switching performance
- Wide availability of high-performance N-channel MOSFETs

Therefore, an N-channel MOSFET was selected.

---

Selected Device

Parameter| Value
Part Number| BSB012N03LX3
Device Type| N-Channel MOSFET
Application| Low-Side Switch in Boost Converter

---

Key Datasheet Parameters

Parameter| Value
Drain-Source Voltage (VDS)| 30 V
Continuous Drain Current (ID)| 180 A
ON-State Resistance (RDS(on))| 1.2 mΩ
Gate-Source Voltage (VGS)| ±20 V

---

Selection Justification

Drain-Source Voltage Rating

The MOSFET must withstand the voltage present across the switch during operation.

A common design practice is to select a MOSFET with a voltage rating significantly higher than the expected operating voltage.

[
V_{DS} = 30V
]

This exceeds the converter output voltage by a comfortable margin and provides protection against switching transients and voltage spikes.

---

ON-State Resistance

The selected MOSFET has:

[
R_DS(on) = 1.2 mOhm
]

A low ON-state resistance minimizes conduction losses:

[
P = I^2R
]

Lower conduction loss results in:

- Improved efficiency
- Reduced heat generation
- Better overall converter performance

---

Drain Current Rating

The MOSFET is rated for:

[
I_D = 180A
]

This rating is substantially higher than the required load current, providing a large operating margin and ensuring reliable operation within the device's safe operating limits.

---

Gate-Source Voltage Rating

The MOSFET has a maximum gate-source voltage rating of:

[
V_GS(max) = pm20V
]

The PWM source provides a gate drive voltage of:

[
V_{GS} = 10V
]

which is safely within the allowable limit and sufficient to fully enhance the MOSFET.

---

Function in the Boost Converter

MOSFET ON

- Gate receives 10 V from the PWM source.
- MOSFET conducts.
- Current flows through the inductor.
- Energy is stored in the magnetic field.

MOSFET OFF

- Gate voltage returns to 0 V.
- MOSFET stops conducting.
- The inductor releases stored energy.
- Current flows through the Schottky diode to the output capacitor and load.

This switching process enables the converter to produce a regulated output voltage greater than the input voltage.

---

Final Selection

The BSB012N03LX3 N-channel MOSFET satisfies the voltage, current, gate-drive, and efficiency requirements of the boost converter while providing significant design margin for reliable operation.

Schottky Diode Selection

Objective

The Schottky diode provides a current path for the inductor when the MOSFET turns OFF.

During the OFF interval of the switching cycle, the energy stored in the inductor is transferred through the diode to the output capacitor and load.

Therefore, the diode must be capable of:

- Handling the output current.
- Operating at high switching frequencies.
- Minimizing conduction losses.
- Recovering quickly during switching transitions.

---

Selected Device

Parameter| Value
Part Number| RBR3MM40B
Device Type| Schottky Barrier Rectifier
Application| Boost Converter Freewheeling Diode

---

Why a Schottky Diode?

A conventional silicon diode is generally not preferred in high-frequency switching converters because it exhibits:

- Higher forward voltage drop
- Reverse recovery losses
- Increased switching losses

A Schottky diode offers:

- Lower forward voltage drop
- Faster switching response
- Negligible reverse recovery time
- Improved converter efficiency

For these reasons, a Schottky diode was selected for the boost converter stage.

---

Key Datasheet Parameters

Parameter| Value
Reverse Voltage Rating (VRRM)| 40 V
Average Forward Current (IF)| 3 A
Diode Type| Schottky

---

Selection Justification

Reverse Voltage Rating

The diode must withstand the output voltage when it is reverse biased.

A common design practice is to select a reverse voltage rating significantly higher than the expected output voltage.

[
V_{RRM}=40V
]

Since the converter output voltage is approximately:

[
V_{OUT}=12V
]

the selected diode provides more than three times the required voltage rating, ensuring reliable operation and protection against switching transients.

---

Forward Current Rating

The diode is rated for:

[
I_F=3A
]

The converter load current is approximately:

[
I_{LOAD}=1.5A
]

Therefore, the diode current rating is approximately twice the required load current, providing sufficient operating margin and improved reliability.

---

Low Forward Voltage Drop

A Schottky diode typically exhibits a forward voltage drop in the range of:

[
0.2V - 0.5V
]

which is significantly lower than a conventional silicon diode.

Lower forward voltage drop results in:

- Reduced power dissipation
- Improved efficiency
- Lower device temperature

The power loss across the diode is:

[
P_D = V_F×I_F
]

Reducing V_F directly reduces conduction losses.

---

High-Speed Switching Performance

The boost converter operates at:

[
f_s = 100kHz
]

At this frequency, reverse recovery losses become important.

Schottky diodes have extremely small reverse recovery times, making them well suited for high-frequency switching applications.

This minimizes switching losses and improves overall converter efficiency.

---

Function in the Boost Converter

MOSFET ON

- MOSFET conducts.
- Inductor stores energy.
- Diode becomes reverse biased.
- Output capacitor supplies the load.

MOSFET OFF

- MOSFET stops conducting.
- Inductor polarity reverses.
- Diode becomes forward biased.
- Stored energy is transferred to the output capacitor and load.

This process enables the converter to boost the input voltage and maintain a regulated output.

---

Final Selection

The RBR3MM40B Schottky diode was selected because it provides:

- Adequate reverse voltage margin.
- Sufficient current carrying capability.
- Low forward voltage drop.
- Excellent high-frequency switching performance.

These characteristics make it suitable for use as the freewheeling diode in the 12 V, 2 A boost converter.

Output Capacitor Selection

Objective
The output capacitor reduces the voltage ripple produced by the switching operation of the boost converter and provides energy to the load during the MOSFET ON interval.
Since the output voltage regulation depends on the switching duty cycle, the capacitor value is selected based on the allowable output ripple voltage, switching frequency, load current, and duty cycle.

Capacitor Selection

The required output capacitance can be estimated using:

I_out×D/f_s×∆V_out

Where:
C = Output Capacitance (F)
I_out = Output Current (A)
D = Duty Cycle
f_s = Switching Frequency (Hz)
∆V_out = Allowable Output Ripple Voltage (V)
Design Parameters
Parameter
Value
Output Current (I_ouy)
1.5 A
Duty Cycle (D)
0.26
Switching Frequency (f_s)
100 kHz
Allowable Ripple Voltage (∆V_out)
18 mV
Calculation
The nearest standard capacitor value is:

220 uF

Voltage Rating Selection

The converter output voltage is approximately:

V_out=12 V

To provide sufficient design margin against ripple, transient voltages, and component tolerances, a capacitor voltage rating of:

25 V

was selected.

Final Selection
Parameter
Value
Capacitance
220 µF
Voltage Rating
25 V
Application
Boost Converter Output Filter

The selected 220 µF / 25 V capacitor provides adequate energy storage and maintains a low output ripple voltage while supporting stable operation of the 12 V, 1.5 A boost converter
