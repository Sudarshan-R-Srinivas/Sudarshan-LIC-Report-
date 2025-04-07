# Current Mirror Circuit

## **Introduction**

A current mirror is a foundational component in analog circuit design, primarily used to replicate a reference current across various branches of a circuit. This replication ensures consistent performance and stable biasing, which is vital in many analog and mixed-signal systems. The circuit works by copying the current from one active device to another, maintaining an output current that is independent of load variations, making it especially valuable in operational amplifiers, analog filters, and voltage references.

## **Theory**

The principle of a current mirror revolves around ensuring that two or more transistors share identical electrical characteristics, allowing one to mimic the behavior of another. This is achieved by configuring the transistors in such a way that they maintain the same gate-source (for MOSFETs) or base-emitter (for BJTs) voltages. 

- **For BJTs:**
  - The base and collector of the reference transistor are shorted.
  - Both transistors share the same base-emitter voltage (V_BE), ensuring mirrored collector currents.

- **For MOSFETs:**
  - The reference transistor has its gate and drain connected together.
  - Both MOSFETs have the same gate-source voltage (V_GS), resulting in matched drain currents.

Assuming ideal conditions and neglecting channel-length modulation, the drain currents of the MOSFETs can be approximated by:

```
I_D = (1/2) * μ_n * C_ox * (W/L) * (V_GS - V_th)^2
```
## Circuit:
![Current Mirror Circuit](https://github.com/user-attachments/assets/336e631a-ef74-44ab-904c-057d68)

## **Design Specifications**

Design a current mirror circuit with the following parameters:
- Voltage Gain, A_V = -10 V/V
- Power Supply, V_DD = 1.8 V
- Power Consumption, P ≤ 1 mW
- Mirror Ratios: 1:1 and 1:2
- Perform both DC and AC analysis

### Power and Current Calculations

To determine total current:
```
I_total = P / V_DD = 1 mW / 1.8 V = 0.55 mA
```
Assuming symmetric mirroring (1:1), the reference and mirrored currents are:
```
I_ref = I_p = I_total / 2 = 0.275 mA
```

The MOSFETs must operate in the saturation region, which implies:
```
V_GS > V_th
```

## **W/L Ratios**

Various cases are analyzed based on different channel lengths (L) while maintaining W/L ratios as per the desired mirroring ratio.

### Case 1: L = 180 nm
- W = 2.38 µm
- W/L = 1:1

![Current Mirror Case 1](https://github.com/user-attachments/assets/336e631a-ef74-44ab--0a45c7557d68)

### Case 2: L = 500 nm
- W = 6.0649 µm
- W/L = 1:1

![Current Mirror Case 2](https://github.com/user-attachments/assets/e8e96bc8-f23b-4837-87aa-6066343dc450)

### Case 3: L = 1 µm
- W = 12.46 µm
- W/L = 1:1

![Current Mirror Case 3](https://github.com/user-attachments/assets/e865ad60-7bc9-433d-c644a4ca1d29)

### Case 4: Unequal Ratio (1:2)
- M1: L = 180 nm, W = 2.38 µm
- M2: L = 180 nm, W = 4.76 µm
- W/L Ratio = 1:2

![Current Mirror 1:2 Ratio](https://github.com/user-attachments/assets/f35d69eb-e8f1-93a3-1aa31d9e8475)

## **DC Analysis**

- In 1:1 configurations, current through both transistors is nearly identical.
- In 1:2 configurations, the current in the output branch is approximately double the reference current, validating the mirroring ratio.

![DC Analysis](https://github.com/user-attachments/assets/874a401b-5bd2-470508ab92f668f)

## **Transient Analysis**

- Observed maximum output voltage swing: ~1.175 V peak-to-peak
- The waveform maintains stability and shows consistent mirroring behavior under dynamic conditions.

![Transient Analysis](https://github.com/user-attachments/assets/a2c43cd8-6813-4cc8-adf8768689)

## **AC Analysis**

- Observed Bandwidth: ~2.122 GHz
- High-frequency performance remains stable, indicating suitability for RF and high-speed analog applications.

![AC Analysis](https://github.com/user-attachments/assets/0eed4042-a21b-4a33-05ae847a0)

## **Circuit Performance Summary**

| Case      | Length (L) | Width (W) | W/L Ratio | Mirroring Ratio |
|-----------|------------|-----------|-----------|------------------|
| Case 1    | 180 nm     | 2.38 µm   | 1:1       | 1:1              |
| Case 2    | 500 nm     | 6.0649 µm | 1:1       | 1:1              |
| Case 3    | 1 µm       | 12.46 µm  | 1:1       | 1:1              |
| Case 4    | 180 nm     | 4.76 µm   | 1:2       | 1:2              |

## **Observations**

- Maintaining the same W/L ratios in both transistors ensures accurate current mirroring.
- Increasing the channel length requires increasing the width to maintain W/L ratio, which affects layout area.
- In a 1:2 configuration, the output current is twice the reference, as expected.
- 1:1 mirrors offer better current accuracy and require less chip area and power.
- The current mirror’s performance is dependent on precise transistor matching and operation in the saturation region.

   # Results
**case1**
LENGTH:180nm, WIDTH:2.38um  W/L = 1:1


**case2**
LENGTH:500nm, WIDTH:6.0649um  W/L = 1:1


**case3**
LENGTH:1um, WIDTH:12.46um  W/L = 1:1


**case4**
LENGTH:180nm, WIDTH:4.76um  W/L = 1:2


## **Inference**

- **Accuracy:**
  - 1:1 ratio offers higher precision.
  - 1:2 ratio introduces minor mismatches due to wider devices.

- **Power Efficiency:**
  - 1:1 uses smaller transistors, consuming less power.
  - 1:2 consumes slightly more power due to larger area.

- **Area Utilization:**
  - 1:1 is more chip-area efficient.
  - 1:2 consumes more silicon real estate.

- **Voltage Gain:**
  - A_V = V_out / V_in = 1.53 / 0.099 ≈ 15.45 V/V

- **Bandwidth:**
  - B_W ≈ 1.94 GHz for the designed configuration.

## **Conclusion**

The current mirror is a simple yet powerful analog building block. Through precise transistor sizing and careful design considerations, the mirror can accurately replicate currents for both low-power and high-frequency applications. The experiment demonstrated both theoretical and practical understanding by validating current ratios under various configurations and performing DC, transient, and AC analyses effectively.

This project serves as a key reference in understanding analog biasing, device matching, and the impact of geometrical design on circuit performance.






## CIRCUIT DIAGRAM 2
![Circuit Diagram](https://github.com/user-attachments/assets/46bcc5ef-9c81-437a7b5535a0eb7)

---

### DC characteristics:
![DC Analysis](https://github.com/user-attachments/assets/874a401b-582ea-508ab92f668f)

---

### Observations(DC):
- The current through transistors **M6** and **M3** is nearly twice as high, which is expected due to the **2:1 width-to-length (W/L) ratio**, enhancing current driving capability.
- Transistors **M5** and **M4**, both sized in a **1:1 W/L ratio**, demonstrate matching current values, ensuring symmetry in operation.
- This behavior confirms that transistor sizing directly affects current replication in a current mirror structure.

---

### TRANSIENT ANALYSIS
![Transient Analysis](https://github.com/user-attachments/assets/e7c8540a-1c43-4fba-a4ab-9f1a69178629)

#### Voltage Gain Calculation:
\[ A_v = \frac{V_{out}}{V_{in}} = \frac{1.53}{0.099} \approx 15.45\ \text{V/V} \]
- The high gain indicates a strong amplification capability, suitable for analog applications such as signal conditioning and buffering.

---

### AC ANALYSIS)
![AC Analysis](https://github.com/user-attachments/assets/c17724f5-842e-b787-99a0176e08f5)

#### Bandwidth Observation:
\[ B_w = 1.94\ \text{GHz} \]
- The wide bandwidth implies that the circuit can efficiently handle high-frequency signals, making it applicable in RF and fast analog circuits.

---

## Inference:

### Current Mirror Precision
- **Equal Sizing (1:1):** Provides better matching accuracy due to identical physical dimensions, minimizing mismatch errors.
- **Unequal Sizing (1:2):** Minor deviations are seen because of asymmetrical sizing, which can introduce variation in mirrored current.
- **Conclusion:** A balanced W/L ratio enhances current mirroring fidelity.

### Layout Area Implications
- **1:1 Configuration:** Economical in terms of silicon area, making it suitable for compact IC layouts.
- **1:2 Configuration:** Requires larger layout space, which could be a limitation in high-density chip designs.
- **Conclusion:** For area-constrained designs, equal transistor ratios are advantageous.

### Power Usage Considerations
- **1:1 Ratio:** Reduced power consumption is achieved due to smaller transistor sizes and lower gate capacitances.
- **1:2 Ratio:** Higher power draw is expected due to increased gate and drain capacitance of larger transistors.
- **Conclusion:** 1:1 ratios are preferable for energy-efficient circuit implementations.

### Additional Remarks
- The proper selection of transistor sizing is crucial in designing analog blocks like current mirrors.
- Variations in W/L ratio not only influence current levels but also affect overall circuit performance in terms of gain, speed, and power.
- While the 1:2 configuration enables higher output current, it trades off area and efficiency.
- Designers often choose ratios based on specific application needs — for instance, high-current output stages may justify larger sizes.

---

**Concusion:** Balancing between accuracy, area, and power is essential. For applications needing precision and efficiency, 1:1 sizing offers significant benefits, whereas larger ratios suit high-current requirements despite some compromise in other metrics.

