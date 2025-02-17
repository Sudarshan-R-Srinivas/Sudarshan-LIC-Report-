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

## Circuit:
![Circuit](https://github.com/user-attachments/assets/dd49c7d4-612a-455d-bdac-7917f3367fb2)



## Analysis & Calculations:
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
![DC Analysis](https://github.com/user-attachments/assets/3987f72b-4477-44b8-85b2-6fb333b8ea2b)

- \(I_d = 27.7\)µA
- \(V_{out} = 1.77V\)
- Optimal operating point: (1.77V, 27.7µA) for \(W = 487\)nm

### 2. Transient Analysis:
![Transient Analysis Graph](https://github.com/user-attachments/assets/6c3257c2-e93d-4a27-9af7-c4867c4cc393)

- Confirmed 180-degree phase shift between input and output.
- DC level shift observed.

### 3. AC Analysis:
![AC Analysis Graph](https://github.com/user-attachments/assets/912e7032-b2ad-4883-8136-224b350727a1)

- Gain: -20dB.

## Inference:

- **Width Dependency:** The MOSFET width directly influences the drain current \(I_d\), impacting the gain and operating point of the amplifier.
  
- **DC Analysis Significance:** Ensuring the MOSFET operates in the saturation region is crucial for achieving consistent amplification without distortion.
  
- **Transient Analysis Insight:** The observed phase shift and signal distortion characteristics help in assessing the amplifier’s effectiveness in real-world signal processing applications.
  
- **AC Analysis Importance:** The frequency response analysis aids in understanding bandwidth limitations and optimizing gain for better performance in communication and signal processing applications.
  
- **Overall Performance:** The amplifier exhibits stable performance, with predictable phase shift and gain characteristics, making it suitable for amplification tasks in integrated circuits. The results align with theoretical expectations, demonstrating that careful selection of MOSFET dimensions and biasing parameters significantly impacts circuit behavior.



# Circuit 2:
 ![pmos](https://github.com/user-attachments/assets/96a999f3-2b65-4d22-9943-12b5044ae72d)

## Working
This circuit represents a CMOS inverter, implemented using a common-source amplifier with an active load. It consists of two MOSFETs: an NMOS transistor (M1) and a PMOS transistor (M2), which work together to process input signals. The PMOS transistor functions as the pull-up component, while the NMOS transistor serves as the pull-down component. When the input voltage is high, the NMOS transistor turns on, pulling the output low. Conversely, when the input voltage is low, the PMOS transistor is activated, pulling the output high. This design is commonly used in amplifier circuits due to its high efficiency and gain properties.

---

## Procedure
1. **Circuit Design:** Create the schematic of the CMOS inverter using LTspice, incorporating an NMOS and PMOS transistor.
2. **Component Selection:** Define appropriate MOSFET parameters, resistances, and voltage sources required for the simulation.
3. **Simulation Setup:**
   - Perform **DC analysis** to determine the MOSFET’s operating point.
   - Conduct **AC analysis** to observe frequency-dependent gain variations.
   - Run **transient analysis** to study the circuit’s response to time-varying signals.
4. **Execution:** Run each analysis using LTspice simulation commands.
5. **Data Collection:** Record voltage and current values, frequency response, and transient waveforms for further interpretation.

---

## Different Types of Analysis

### DC Analysis
DC analysis is conducted to determine the MOSFET’s biasing conditions by evaluating voltage and current levels at various circuit points. For a common-source amplifier, this includes calculating:
- **Drain current (ID)**
- **Gate-source voltage (VGS)**
- **Operation mode verification** (cutoff, triode, or saturation region)

Setting an appropriate DC bias ensures the amplifier operates efficiently before an AC signal is applied. In LTspice, this is executed using the `.op` command.

---

### AC Analysis
AC analysis examines the gain (Av) of the amplifier over a range of frequencies to study its response characteristics. This helps in determining:
- **Bandwidth** (range over which the amplifier functions effectively)
- **-3dB cutoff frequency** (point where gain drops by 3dB)

Since small-signal operation is assumed, the MOSFET’s behavior is linearized around its bias point. The analysis is performed using the `.ac dec 20 0.1 1T` command in LTspice, which conducts a frequency sweep from 0.1 Hz to 1 THz. The gain is calculated using the equation:
```math
A_v = - g_m \times R_D
```

---

### Transient Analysis
Transient analysis is used to observe how the circuit behaves in real time when an AC input signal is applied. This analysis helps in visualizing:
- **Signal amplification**
- **Time-domain waveform response**
- **Possible distortion effects**

It simulates how the circuit processes different input waveforms, such as sine waves and pulses. In LTspice, this is executed using the `.tran 5m` command, which runs a 5-millisecond simulation to analyze real-time behavior.

---

## Analysis and Calculation

### DC Analysis:
- **Drain Current (ID):** Calculated using MOSFET equations.
- **Gate-Source Voltage (VGS):** Measured to verify the operating region.
- **Operating Mode:** Confirm whether the MOSFET is in the active region.

### AC Analysis:
- **Gain Calculation:**
```math
A_v = - g_m \times R_D
```
- **Cutoff Frequency Determination:** Extracted from the frequency response graph.

### Transient Analysis:
- **Output Waveform Verification:** Compare the output signal to the expected amplification behavior.
- **Signal Integrity Check:** Observe any distortions or phase shifts.

---

## Results

### DC Analysis:
- The biasing voltages and currents were verified, confirming that the MOSFET operates in the correct region.

### AC Analysis:
- The amplifier's gain was observed across different frequencies. The -3dB cutoff frequency and bandwidth were determined.

### Transient Analysis:
- The circuit successfully amplified the AC input signal, maintaining waveform integrity with minimal distortion.

---

## Inference
From the analysis, it is evident that the CMOS inverter functions effectively as a common-source amplifier with an active load. The DC analysis ensured proper biasing, while AC analysis provided insights into the frequency response. Transient analysis further confirmed signal amplification capabilities with minimal distortion. The results validate that this circuit is suitable for amplification applications, offering high efficiency and gain.



