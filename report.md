# Experiment 1: Common Source Amplifier in LTspice

## Aim:
To perform DC analysis, transient analysis, and AC analysis of a common-source (CS) amplifier circuit with a resistive load using LTSpice and extract various performance parameters.

## Components Required:
- MOSFETs (nmos4, pmos4)
- Resistor (1kΩ)
- Voltage sources (1.8V, 0.9V)
- Connecting wires

## Introduction:
MOSFETs (Metal-Oxide-Semiconductor Field-Effect Transistors) are fundamental in electronics due to their compact size, low power consumption, and suitability for VLSI technology. They can be configured in three primary ways: common drain, common gate, and common source, with the latter being the most widely used for amplification.

In the saturation region, a MOSFET functions as an amplifier, where:

- \(V_{gs} > V_{th}\)
- \(V_{gd} < V_{th}\)
- \(V_{ds} \geq V_{ov}\) (for an N-channel MOSFET)

A common-source amplifier introduces a 180-degree phase shift between the input and output while maintaining high input impedance (ideally infinite).

The drain current is given by:
\[
I_d = \frac{1}{2} k_n V_{ov}^2
\]
where \(V_{ov} = V_{gs} - V_{th}\) and \(k_n = \mu_n C_{ox} \frac{W}{L}\).

## Analysis Methods:

### 1. DC Analysis:
- Determines the MOSFET's operating point in saturation.
- Helps in selecting proper biasing resistors to stabilize circuit performance.
- Ensures minimal signal distortion.

### 2. Transient Analysis:
- Evaluates the circuit’s response to time-varying signals.
- Detects signal distortions and phase shifts.
- Essential for high-speed applications such as communication systems.

### 3. AC Analysis:
- Examines the small-signal behavior and frequency response of the circuit.
- Determines amplifier gain using:
  \[
  A_v = -g_m R_d
  \]

## Procedure:
1. Open LTspice and create a new schematic.
2. Add the NMOS transistor, resistor, DC voltage source, and AC signal source with appropriate values.
3. Connect the components as per the circuit diagram.
4. Run DC analysis to determine the biasing conditions. Take `.op`.
5. Perform AC analysis to observe the voltage gain and frequency response. Take `.ac dec 20 0.1 1T`.
6. Execute transient analysis to visualize the amplifier's response over time. Take `.trans 5m`.
7. Analyze the output waveform to verify amplification.

## Circuit Analysis & Calculations:
- Power: 50µW
- Loop Equation: 
  \[
  V_{dd} = V_{ds} + I_d R_d
  \]
- Given \(I_d = 27.7\)µA, \(V_{dd} = 1.8V\), we calculate: 
  \[
  R_d = 1kΩ
  \]
- Adjust width (\(W\)) to achieve desired current levels.
- Gain obtained: -20dB.
- Q-point: (1.77V, 27.7µA).

## Results:

### 1. DC Analysis:
- \(I_d = 27.7\)µA
- \(V_{out} = 1.77V\)
- Optimal operating point: (1.77V, 27.7µA) for \(W = 487\)nm

### 2. Transient Analysis:
- Confirmed 180-degree phase shift between input and output.
- DC level shift observed.

### 3. AC Analysis:
- Gain: -20dB.

## Inference & Analysis:

- **Width Dependency:** The MOSFET width directly influences the drain current \(I_d\), impacting the gain and operating point of the amplifier.
- **DC Analysis Significance:** Ensuring the MOSFET operates in the saturation region is crucial for achieving consistent amplification without distortion.
- **Transient Analysis Insight:** The observed phase shift and signal distortion characteristics help in assessing the amplifier’s effectiveness in real-world signal processing applications.
- **AC Analysis Importance:** The frequency response analysis aids in understanding bandwidth limitations and optimizing gain for better performance in communication and signal processing applications.
- **Overall Performance:** The amplifier exhibits stable performance, with predictable phase shift and gain characteristics, making it suitable for amplification tasks in integrated circuits. The results align with theoretical expectations, demonstrating that careful selection of MOSFET dimensions and biasing parameters significantly impacts circuit behavior.
