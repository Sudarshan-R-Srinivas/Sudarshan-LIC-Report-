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



# Circuit 2

![Circuit Image](image_placeholder.png)

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
- The DC characteristics indicate stable operation, with the MOSFET functioning within expected parameters.
- Variations in the gate-source voltage were analyzed to ensure consistency in circuit behavior.

### AC Analysis:
- The amplifier's gain was observed across different frequencies, and the -3dB cutoff frequency was determined accurately.
- The frequency response curve demonstrated that the circuit maintains stable gain over a defined range.
- The bandwidth was calculated, and the results matched theoretical expectations.

### Transient Analysis:
- The circuit successfully amplified the AC input signal, maintaining waveform integrity with minimal distortion.
- The transient response was analyzed to identify any potential delays or phase shifts in signal processing.
- The output waveforms confirmed that the circuit effectively follows input variations without unwanted oscillations.

---

## Inference
From the analysis, it is evident that the CMOS inverter functions effectively as a common-source amplifier with an active load. The DC analysis ensured proper biasing, confirming that the MOSFET operates in the expected region. The AC analysis provided insights into the frequency response, highlighting the amplifier’s gain stability and bandwidth characteristics. Transient analysis further confirmed the circuit’s ability to amplify signals with minimal distortion and phase shifts. 

Overall, the results validate that this circuit is well-suited for amplification applications, offering high efficiency and gain. The observed performance aligns with theoretical predictions, making it a reliable choice for signal processing circuits. Potential areas for improvement could include optimizing MOSFET parameters for enhanced gain and minimizing any residual distortion for even better performance.




