# common-source-amplifier# Common-Source Amplifier Analysis Report
# Project Overview (introduction)

This project analyzes a Common Source Amplifier (CSA) using a MOSFET with DC, AC, Transient, and DC Transfer Analysis in LTSpice.

This report presents the analysis of a common-source amplifier (CSA) with the following specifications:
- **W (Width)**: 180 nm
- **L (Length)**: 1 µm
- **VDD**: 1.8V
- **RD (Drain Resistor)**: 1 kΩ
- **Vin**: 0.9V

The analyses performed include DC operating point analysis, DC transfer characteristics, AC analysis, and transient analysis.
# circuit daigram
![Screenshot 2025-02-17 221533](https://github.com/user-attachments/assets/169f0a54-2568-417e-98ca-54d35109ffa4)

---

## 1. DC Operating Point Analysis

The DC operating point analysis helps determine the quiescent (steady-state) operating point of the amplifier. This is important for ensuring that the MOSFET operates in the saturation region.

- **ID (Drain Current)**: Calculated using the MOSFET equation in saturation:
  
  \[ I_D = \frac{1}{2} \mu C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2 \]
  
- **VDS (Drain-Source Voltage)**: Verified to ensure VDS > VGS - Vth to keep the transistor in saturation.

*Simulation Results:* 
- ID = 0.3 mA
- VDS = 0.9V (Ensures saturation region operation)
![Screenshot 2025-02-13 095918](https://github.com/user-attachments/assets/d62398c1-423a-49e1-8b84-cb21dd9b75b3)

---

## 2. DC Transfer Characteristics

The DC transfer characteristics show the relationship between the input voltage (Vin) and the output voltage (Vout).

- A sweep of Vin from 0 to 1.8V was performed.
- The amplifier shows a linear region within a certain input voltage range.

*Observations:* 
- The linear region is observed between 0.5V and 1.2V.
- Beyond this range, the amplifier either saturates or cuts off.
![Screenshot 2025-02-13 095200](https://github.com/user-attachments/assets/c2808a35-e61f-4241-8749-593248b213f0)

---

## 3. AC Analysis

AC analysis evaluates the amplifier's frequency response and gain.

- **Gain Calculation:**
  
  \[ A_v = - g_m R_D \] 
  
  Where \( g_m \) is the transconductance.

  - gm = 1.2 mS (calculated based on operating point)
  - RD = 1 kΩ
  - Gain = -1.2 (indicating phase inversion)

- **Frequency Response:**
  - Bandwidth = 1 MHz
  - Cutoff Frequency = 1.5 MHz

*Conclusion:* The amplifier operates effectively within its bandwidth.
![Screenshot 2025-02-17 063516](https://github.com/user-attachments/assets/c0abb9ff-93dc-4c8f-9496-ea5e6e384da8)

---

## 4. Transient Analysis

The transient analysis evaluates the amplifier's time-domain behavior for a sinusoidal input.

- Input: 1 kHz sine wave with an amplitude of 0.5V.
- Output: Amplified sine wave with an amplitude of 0.6V (showing some distortion at higher amplitudes).

*Observations:* 
- The output waveform shows proper amplification with slight distortion at the peaks.
- Rise and fall times are within acceptable limits.
![Screenshot 2025-02-17 063558](https://github.com/user-attachments/assets/ec3f15f5-caab-467d-a197-59d517f4b210)

---

## Conclusion

The common-source amplifier with the specified parameters was analyzed successfully. It shows:
- Proper DC operating point.
- A linear response over a defined input range.
- Good frequency response and amplification.
- Minimal distortion for small signals.

### Inference
- The amplifier works well for basic signal amplification.
- It provides phase inversion, which is expected in a common-source amplifier.
- The gain is moderate, and while it can be improved, it is sufficient for general use.
- Distortion happens at higher input voltages, so care must be taken to stay within the linear range.
- The frequency response is good for low-frequency signals, but for higher-frequency applications, further tuning would be necessary.

Further improvements can include:
- Increasing RD to improve gain.
- Optimizing W/L ratio for better linearity.
- Adding feedback for stability.

---

*Prepared by: shwetha m*

*Date: [17/02/2025]*

*Simulation Tool Used: Ngspice / LTSpice*

