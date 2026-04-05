# Analog Lab Bench Work — Circuit Implementation & Measurement

**Course:** Circuits Laboratory  
**Tools:** Proto-Board PB-503, Tektronix MDO3024 Oscilloscope, Agilent 33220A Function Generator, Agilent 34405A Multimeter, Kepco Precision AC/DC Power Supply

---

## Overview

This project documents hands-on analog circuit implementation and measurement work conducted in the electrical engineering lab. Circuits were built on the **Global Specialties Proto-Board PB-503** and verified using professional bench instrumentation including a mixed domain oscilloscope, function generator, and precision multimeter.

---

## Equipment Used

| Instrument | Model | Purpose |
|------------|-------|---------|
| Oscilloscope | Tektronix MDO3024 | Waveform capture and analysis |
| Function Generator | Agilent 33220A | Signal source (sine, square, ramp) |
| Multimeter | Agilent 34405A 5½ Digit | Voltage, current, resistance measurement |
| Power Supply | Kepco Precision AC/DC | Regulated circuit power |
| Prototyping Board | Global Specialties PB-503 | Circuit construction |

---

## Lab Work

### Oscilloscope Measurements
Waveforms were captured using the Tektronix MDO3024 Mixed Domain Oscilloscope at 250MS/s. The function generator was configured to drive the circuit under test, with multiple channels monitored simultaneously to observe signal behavior across different circuit nodes.

![Oscilloscope Setup](https://github.com/user-attachments/assets/9a153f53-aa4d-431b-a740-8fe4ae8c0ab7)
)

---

### Circuit Implementation
Multiple analog circuits were constructed on the Proto-Board PB-503, utilizing the onboard DIP switches, potentiometers, SPDT switches, and debounced pushbuttons for input control. Logic indicators were used to verify digital output states where applicable.

![Full Bench Setup](https://github.com/user-attachments/assets/fd4777d9-3213-4806-83e9-1b8867c06b3a)
./images/IMG_4048.jepg)

---

### Multi-IC Breadboard Circuit
A more complex analog circuit was implemented using multiple ICs wired across the breadboard. Color-coded jumper wires were used to organize signal paths, power rails, and ground connections for clarity during testing and debugging.

![Breadboard Circuit](./images/IMG_2634.jpeg)

---


## Key Takeaways

- Hands-on breadboarding builds intuition for signal flow and circuit behavior that simulation alone cannot provide
- Proper use of bench instruments — triggering, scaling, and cursor measurements on an oscilloscope — is essential for accurate data collection
- Color-coded wiring significantly reduces debugging time on complex multi-IC circuits
- Real-world results don't always match simulation exactly — understanding why is part of the engineering process

---

