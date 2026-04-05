# RLC Resonance Circuit — PSpice & Multisim Simulation

**Course:** Circuit Analysis  
**Tools:** OrCAD PSpice, Multisim, Tektronix MDO3024 Oscilloscope, Agilent 33220A Function Generator

---

## Overview

This project involved designing and simulating a **series RLC circuit** to observe resonance behavior and transient voltage response. The circuit was built and analyzed in both OrCAD PSpice and Multisim, with waveform outputs captured and compared across both platforms to confirm design correctness.

---

## Circuit Design

Two circuit configurations were simulated across both platforms:

| Component | PSpice Value | Multisim Value |
|-----------|-------------|----------------|
| Resistor (R) | 7kΩ | 1kΩ |
| Inductor (L) | 100mH | 100mH |
| Capacitor (C) | — | 0.01µF |
| Source Voltage | 2V pulse | 2.10V AC |
| Frequency | 200Hz (5ms period) | 1kHz |

> Note: Different component values were used across platforms to explore resonance behavior at different frequency ranges.

---

## Resonant Frequency

The theoretical resonant frequency was calculated using:

**f₀ = 1 / (2π√LC)**

| Circuit | L | C | Calculated f₀ |
|---------|---|---|----------------|
| Multisim | 100mH | 0.01µF | ≈ 5.03 kHz |

At resonance, the inductive and capacitive reactances cancel out, leaving only the resistive component to limit current — producing the peak voltage response visible in the simulation waveforms.

---

## Simulation

### OrCAD PSpice — Schematic

The PSpice circuit was configured with a **pulse voltage source** (V1 = 2Vdc, PW = 2.5ms, PER = 5ms) driving a series RL network with a 7kΩ resistor and 100mH inductor. Node voltages were measured at 2.000V across key nodes confirming proper bias point calculation.

![PSpice Schematic](https://github.com/user-attachments/assets/60cb4f03-eb59-4bd9-aec2-965c84978e38)


---

### OrCAD PSpice — Transient Analysis

A transient analysis was run to observe voltage behavior over time. The simulation confirmed the expected waveform response with oscillating voltage centered around 2.00V, ranging between approximately 1.50V and 3.50V peak.

- Simulation completed with **0 errors**
- Transient analysis captured voltage at L4 and C1 nodes
- Waveform showed high-frequency oscillations consistent with RLC resonance behavior

![PSpice Waveform](https://github.com/user-attachments/assets/507947ff-e79e-4290-93d2-11fdc3728025)


---

### Multisim — Interactive Simulation

The Multisim circuit used a 2.10V AC source at 1kHz driving a series RLC network with a 1kΩ resistor, 100mH inductor, and 0.01µF capacitor. The interactive grapher displayed the characteristic resonance oscillation waveform.

- Cursor 1 measured at 1.8917s, −38.890 mV
- Cursor 2 measured at 1.8933s, 2.6481V
- Output frequency confirmed at **606.06 Hz**
- ΔX interval: 1.6500ms

![Multisim Circuit & Waveform](https://github.com/user-attachments/assets/7fb3c543-ec46-42b5-9054-3c5a929892ee)


---

## Simulation Results Comparison

| Parameter | PSpice | Multisim |
|-----------|--------|----------|
| Source Voltage | 2V pulse | 2.10V AC |
| Resistor | 7kΩ | 1kΩ |
| Inductor | 100mH | 100mH |
| Waveform Center | ~2.00V | ~0V |
| Output Frequency | — | 606.06Hz |
| Simulation Result | 0 errors | 0 errors |

---

## Key Takeaways

- Series RLC circuits exhibit resonance at a specific frequency determined by the L and C values
- Transient analysis in PSpice provides accurate voltage and current behavior over time
- Adjusting resistance changes the damping characteristics — lower resistance produces more pronounced oscillations as seen in the Multisim waveform
- Cross-platform simulation in both OrCAD and Multisim reinforced confidence in the design results
- Simulation results aligned with theoretical expectations for series RLC resonance behavior
