# RLC Resonance Circuit — PSpice & Multisim Simulation

**Course:** Circuit Analysis  
**Tools:** OrCAD PSpice, Multisim, Tektronix MDO3024 Oscilloscope, Agilent 33220A Function Generator

---

## Overview

This project involved designing and simulating a **series RLC circuit** to observe resonance behavior and transient voltage response. The circuit was built and analyzed in both OrCAD PSpice and Multisim, with waveform outputs captured and compared across both platforms.

---

## Circuit Design

The series RLC circuit was configured with the following components:

| Component | Value |
|-----------|-------|
| Capacitor (C1) | 1µF |
| Inductor (L1) | 230µH |
| Source Voltage | 1Vpp AC |
| Frequency | 1kHz |
| Offset | 0V |

![PSpice Schematic](./images/pspice_schematic.jpg)

---

## Simulation

### OrCAD PSpice — Transient Analysis
A transient analysis was run to observe the voltage waveforms across the resistor over time. The simulation confirmed resonance behavior with the expected oscillating waveform pattern.

- Simulation completed with **0 errors**
- Transient analysis captured voltage at R1 and R2 nodes
- Waveform displayed peak-to-peak voltage of approximately 300mV

![PSpice Waveform](./images/pspice_waveform.jpg)

---

### Multisim — Interactive Simulation
The same circuit was recreated in Multisim with a 2.10V source at 1kHz driving a series RLC network consisting of a 7kΩ resistor, 100mH inductor, and 0.01µF capacitor. The interactive grapher confirmed the expected voltage waveform behavior.

- Cursor measurements recorded at 2.8117s and 2.8134s
- Voltage difference of approximately 2.0973V measured between cursors
- Output frequency confirmed at 606.06Hz

![Multisim Circuit](./images/multisim_circuit.jpg)

---

## Lab Bench Verification

Circuit behavior was also observed on the **Tektronix MDO3024 Mixed Domain Oscilloscope** paired with an **Agilent 33220A Function/Arbitrary Waveform Generator**, confirming that simulated waveforms matched real-world signal behavior.

---

## Key Takeaways

- Series RLC circuits exhibit resonance at a specific frequency determined by the L and C values
- Transient analysis in PSpice provides accurate voltage and current behavior over time
- Cross-platform simulation in both OrCAD and Multisim reinforced confidence in the design results
- Simulation results aligned with theoretical expectations for series RLC resonance behavior

---


