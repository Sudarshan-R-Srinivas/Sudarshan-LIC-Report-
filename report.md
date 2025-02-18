# Experiment 1: Common Source Amplifier in LTspice

## Aim
To perform DC analysis, transient analysis, and AC analysis of a common-source (CS) amplifier circuit with a resistive load using LTSpice and extract various performance parameters.

## Components Required
- MOSFETs (`nmos4`, `pmos4`)
- Resistor (`1kΩ`)
- Voltage sources (`1.8V`, `0.9V`)
- Connecting wires

## Introduction
MOSFETs (Metal-Oxide-Semiconductor Field-Effect Transistors) are fundamental in electronics due to their compact size, low power consumption, and suitability for VLSI technology. They can be configured in three primary ways: common drain, common gate, and common source, with the latter being the most widely used for amplification.

In the saturation region, a MOSFET functions as an amplifier, where:

- `Vgs > Vth`
- `Vgd < Vth`
- `Vds ≥ Vov` (for an N-channel MOSFET)

A common-source amplifier introduces a 180-degree phase shift between the input and output while maintaining high input impedance (ideally infinite).

The drain current is given by:

```
Id = (1/2) * kn * Vov^2
```

where `Vov = Vgs - Vth` and `kn = μn * Cox * (W/L)`.

## Analysis Methods

### 1. DC Analysis
- Determines the MOSFET's operating point in saturation.
- Helps in selecting proper biasing resistors to stabilize circuit performance.
- Ensures minimal signal distortion.

### 2. Transient Analysis
- Evaluates the circuit’s response to time-varying signals.
- Detects signal distortions and phase shifts.
- Essential for high-speed applications such as communication systems.

### 3. AC Analysis
- Examines the small-signal behavior and frequency response of the circuit.
- Determines amplifier gain using:

```
Av = -gm * Rd
```

## Procedure

1. Open LTspice and create a new schematic.
2. Add the NMOS transistor, resistor, DC voltage source, and AC signal source with appropriate values.
3. Connect the components as per the circuit diagram.
4. Run DC analysis to determine the biasing conditions.
   - Use `.op` to find the operating point and ensure the MOSFET is in saturation.
5. Perform AC analysis to observe the voltage gain and frequency response.
   - Use `.ac dec 20 0.1 1T` to analyze the gain over a range of frequencies.
6. Execute transient analysis to visualize the amplifier's response over time.
   - Use `.trans 5m` to observe the amplifier's behavior for different time intervals and ensure a proper 180-degree phase shift.
7. Extract key performance parameters such as gain, phase shift, and distortion levels.
8. Compare theoretical calculations with the simulation results to validate the circuit design.

## Circuit:
![Circuit](https://github.com/user-attachments/assets/6c5b07bb-9616-4027-9cf0-b2a8a407fde1)


## Circuit Analysis & Calculations

- **Power Consumption:** `50µW`
- **Loop Equation:**
  
  ```
  Vdd = Vds + Id * Rd
  ```
  
- Given `Id = 27.7µA`, `Vdd = 1.8V`, we calculate:
  
  ```
  Rd = 1kΩ
  ```
  
- Adjust width (`W`) to achieve desired current levels.
- **Gain obtained:** `-20dB`
- **Q-point:** `(1.77V, 27.7µA)`

## Results

### 1. DC Analysis

![DC Analysis](https://github.com/user-attachments/assets/1f4ea0ac-8d6e-4326-b801-1b88cd2f7c0a)

- `Id = 27.7µA`
- `Vout = 1.77V`
- **Optimal Operating Point:** `(1.77V, 27.7µA)` for `W = 487nm`
- The biasing conditions were found to be stable, ensuring the MOSFET operated in the desired region.

### 2. Transient Analysis
![Transient Analysis](https://github.com/user-attachments/assets/f1593c63-082c-4ad6-a2a9-f15b2580130e)


- Confirmed **180-degree phase shift** between input and output.
- **DC level shift** observed, ensuring proper signal amplification.
- The output waveform closely follows the expected amplification characteristics with minimal distortion.

### 3. AC Analysis
![AC Analysis](https://github.com/user-attachments/assets/3fdf8e8d-c1cc-449d-9a86-4d704b49a4d4)
- **Gain:** `-20dB`
- The frequency response demonstrated stable gain up to a certain bandwidth, after which attenuation occurred.
- The small-signal voltage gain matched theoretical calculations, confirming proper circuit design.

## Inference & Analysis

- **Width Dependency:** The MOSFET width directly influences the drain current (`Id`), impacting the gain and operating point of the amplifier. Proper width selection ensures optimized performance.
- **DC Analysis Significance:** Ensuring the MOSFET operates in the saturation region is crucial for achieving consistent amplification without distortion. Incorrect biasing can shift the operating point, leading to signal degradation.
- **Transient Analysis Insight:** The observed phase shift and signal distortion characteristics help in assessing the amplifier’s effectiveness in real-world signal processing applications. Any deviation from the expected behavior can indicate circuit instabilities or incorrect biasing.
- **AC Analysis Importance:** The frequency response analysis aids in understanding bandwidth limitations and optimizing gain for better performance in communication and signal processing applications. The gain roll-off at higher frequencies highlights the need for careful design considerations.
- **Impact of Load Resistance:** The choice of `Rd` affects both the gain and output voltage swing. Higher resistance values increase gain but can reduce bandwidth.
- **Overall Performance:** The amplifier exhibits stable performance, with predictable phase shift and gain characteristics, making it suitable for amplification tasks in integrated circuits. The results align with theoretical expectations, demonstrating that careful selection of MOSFET dimensions and biasing parameters significantly impacts circuit behavior. The gain of `-20dB` and proper phase shift validate the effectiveness of this common-source amplifier design.


# Common-Source (CS) Amplifier with Diode-Connected MOSFET  

## Components Required  
To construct the common-source amplifier with a diode-connected MOSFET, the following components are needed:  
- **NMOS Transistor (nmos4):** Acts as the primary amplifying component.  
- **PMOS Transistor (pmos4):** Used in conjunction with the NMOS to establish the required operating conditions.  
- **Voltage Sources:** Provide the necessary power and biasing to the circuit.  
- **Bias DC Source:** Helps set the appropriate gate voltage for proper transistor operation.  

## Circuit Diagram  
 

## Procedure  

### Transistor Specifications  
Before proceeding with the analysis, the dimensions of the transistors used in the circuit are as follows:  
- **PMOS Transistor (CMOSP):**  
  - Channel Length = **360n**  
  - Channel Width = **309n**  
- **NMOS Transistor:**  
  - Channel Length = **500n**  
  - Channel Width = **487n**  

These dimensions significantly affect the circuit’s electrical characteristics, including drain current, gain, and overall performance.  

---

## DC Analysis  
1. **Setting Up Voltages:**  
   - Power supply voltage: **Vdd = 1.8V**  
   - Input voltage: **Vin = 0.9V**  

2. **Ensuring Operation in the Saturation Region:**  
   - The MOSFET must remain in saturation, meaning **Vgs > Vt**.  
   - The gate voltage **Vb** is chosen such that **Vg = Vb = -2V**.  

3. **Running the DC Analysis:**  
   - A **DC sweep** is performed to determine **Vout** and **Id**.  

**DC Analysis Results:**  
- **Drain Current through NMOS (Id1) = 27.755µA**  
- **Drain Current through PMOS (Id2) = 27.755µA**  
- **Output Voltage (Vout) = 1.79981V**  
- **Q-Point (Operating Point):** ( **Vout = 1.79981V, Id = 27.7µA** )  


---

## Transient Analysis  
1. **Applying an AC Signal:**  
   - A **sine wave** is used as the input signal.  

2. **Observing the Phase Shift:**  
   - The output signal undergoes a **180-degree phase shift** with respect to the input, confirming typical common-source amplifier behavior.  

**Key Observations:**  
- The output waveform is **inverted** compared to the input signal.  
- This phase shift is a fundamental characteristic of a **CS amplifier**.  

*(Insert transient analysis image here)*  

---

## AC Analysis  
1. **Performing Frequency Response Analysis:**  
   - AC analysis is conducted to measure the gain and response across different frequencies.  

2. **Voltage Gain Calculation:**  
   - Gain is calculated using:  

     \[
     A_v = -g_m R_d
     \]

     where  

     \[
     g_m = \frac{1}{\lambda I_d}
     \]  

3. **Measuring Gain at 1 kHz Frequency:**  
   - Practical measurements show **Gain = 36.72** at **1 kHz**.  

  

---

## Inference  
1. **Impact of Transistor Dimensions on Performance:**  
   - The **drain current (Id)** in a MOSFET is affected by its **channel width (W)**.  
   - A wider channel increases current flow, affecting power consumption and circuit behavior.  

2. **Ensuring Saturation for Proper Amplification:**  
   - The MOSFET must be in the **saturation region (Vgs > Vt)** for optimal performance.  
   - If it enters the **linear region**, amplification reduces drastically.  

3. **Transient Analysis for Signal Behavior:**  
   - The **180-degree phase shift** confirms that the CS amplifier inverts signals as expected.  

4. **Importance of AC Analysis:**  
   - Helps determine **gain, bandwidth, and frequency response** for optimized amplifier design.  

5. **Comprehensive Circuit Evaluation:**  
   - A thorough study of DC, transient, and AC performance ensures **stability and efficiency** in real-world applications.  

