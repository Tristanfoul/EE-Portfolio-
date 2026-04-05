# Industrial Robot Sensor Network — Combinational Logic Design

**Course:** ELEN 305: Digital Logic Design Lab  
**Semester:** Spring 2026  
**Tools:** Logic gates (physical ICs), Global Specialties Proto-Board PB-503, Agilent 34405A Multimeter

---

## Overview

This project involved designing and implementing a fail-safe combinational logic circuit for an industrial PCB assembly robot. The system monitors four sensors (A, B, C, D) arranged in a cyclic configuration and generates a **shutdown signal** whenever any two adjacent sensors are triggered simultaneously — indicating a potential fault condition.

Adjacent sensor pairs:
- A & B
- B & C
- C & D
- D & A

---

## Design Process

### 1. Truth Table
A complete 4-variable truth table was constructed across all 16 input combinations. The shutdown output `X` was set to `1` for any combination where at least one adjacent pair was simultaneously active — yielding 9 high-output conditions.

### 2. Boolean Expression (Unsimplified)
```
X = CD + BC + BCD + AD + ABD + ABC + ABCD
```

### 3. Simplification via K-Map
A Karnaugh Map was used to minimize the expression. Boolean algebra was applied to confirm the result:

```
X = AB + BC + CD + DA
```

This reduced the implementation from a complex multi-term expression to just **four 2-input AND gates and one OR gate**.

### 4. Gate-Level Implementation
| Gate | Function |
|------|----------|
| AND₁ | Detects A & B active |
| AND₂ | Detects B & C active |
| AND₃ | Detects C & D active |
| AND₄ | Detects D & A active |
| OR   | Outputs shutdown signal X |

---

## Hardware Implementation

Built on a **Global Specialties Proto-Board PB-503** using physical TTL logic gate ICs. DIP switches were used to simulate sensor inputs, and the onboard logic indicators confirmed the output state of X for each input combination.

All 16 input combinations were tested against the expected truth table. **No mismatches were observed.**

![Breadboard Implementation](./images/breadboard.jpg)

---

## Results

| Condition | Expected Output | Observed Output |
|-----------|----------------|-----------------|
| No adjacent pair active | X = 0 | X = 0 ✅ |
| Any adjacent pair active | X = 1 | X = 1 ✅ |

Hardware results matched simulation results across all tested conditions.

---

## Key Takeaways

- Boolean simplification directly reduces hardware complexity — from 9 minterms down to a 5-gate implementation
- K-map minimization and algebraic methods produced identical results, confirming correctness
- Physical verification reinforced that mathematical simplification preserves correct circuit behavior

---

## Files
```
/
├── README.md
├── truth_table.pdf
├── kmap.pdf
├── lab_report.pdf
└── images/
    ├── breadboard.jpg
    └── logic_indicators.jpg
```
