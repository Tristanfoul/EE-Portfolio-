RLC Resonance Circuit — PSpice & Multisim Simulation
Course: Circuit Analysis
Tools: OrCAD PSpice, Multisim, Tektronix MDO3024 Oscilloscope, Agilent 33220A Function Generator

Overview
This project involved designing and simulating a series RLC circuit to observe resonance behavior and transient voltage response. The circuit was built and analyzed in both OrCAD PSpice and Multisim, with waveform outputs captured and compared across both platforms to confirm design correctness.

Circuit Design
Two circuit configurations were simulated across both platforms:
ComponentPSpice ValueMultisim ValueResistor (R)7kΩ1kΩInductor (L)100mH100mHCapacitor (C)—0.01µFSource Voltage2V pulse2.10V ACFrequency200Hz (5ms period)1kHz

Note: Different component values were used across platforms to explore resonance behavior at different frequency ranges.


Resonant Frequency
The theoretical resonant frequency was calculated using:
f₀ = 1 / (2π√LC)
CircuitLCCalculated f₀Multisim100mH0.01µF≈ 5.03 kHz
At resonance, the inductive and capacitive reactances cancel out, leaving only the resistive component to limit current — producing the peak voltage response visible in the simulation waveforms.

Simulation
OrCAD PSpice — Schematic
The PSpice circuit was configured with a pulse voltage source (V1 = 2Vdc, PW = 2.5ms, PER = 5ms) driving a series RL network with a 7kΩ resistor and 100mH inductor. Node voltages were measured at 2.000V across key nodes confirming proper bias point calculation.
(https://github.com/user-attachments/assets/50ca467a-dfe1-4ea2-9eb1-92e3159ef467)


OrCAD PSpice — Transient Analysis
A transient analysis was run to observe voltage behavior over time. The simulation confirmed the expected waveform response with oscillating voltage centered around 2.00V, ranging between approximately 1.50V and 3.50V peak.

Simulation completed with 0 errors
Transient analysis captured voltage at L4 and C1 nodes
Waveform showed high-frequency oscillations consistent with RLC resonance behavior

(https://github.com/user-attachments/assets/860ec6e9-5178-4a9b-85b4-050539639592)


Multisim — Interactive Simulation
The Multisim circuit used a 2.10V AC source at 1kHz driving a series RLC network with a 1kΩ resistor, 100mH inductor, and 0.01µF capacitor. The interactive grapher displayed the characteristic resonance oscillation waveform.

Cursor 1 measured at 1.8917s, −38.890 mV
Cursor 2 measured at 1.8933s, 2.6481V
Output frequency confirmed at 606.06 Hz
ΔX interval: 1.6500ms

(https://github.com/user-attachments/assets/b36f8229-58bb-46f3-a5b7-6724b4529bcb)


Simulation Results Comparison
ParameterPSpiceMultisimSource Voltage2V pulse2.10V ACResistor7kΩ1kΩInductor100mH100mHWaveform Center~2.00V~0VOutput Frequency—606.06HzSimulation Result0 errors0 errors

Key Takeaways

Series RLC circuits exhibit resonance at a specific frequency determined by the L and C values
Transient analysis in PSpice provides accurate voltage and current behavior over time
Adjusting resistance changes the damping characteristics — lower resistance produces more pronounced oscillations as seen in the Multisim waveform
Cross-platform simulation in both OrCAD and Multisim reinforced confidence in the design results
Simulation results aligned with theoretical expectations for series RLC resonance behavior
