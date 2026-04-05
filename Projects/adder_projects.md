# 4-Bit & 8-Bit Ripple Carry Adder — FPGA Implementation (Quartus II)

**Course:** Digital Logic Design  
**Tools:** Quartus II, Altera DE2 Board (Cyclone II EP2C35F672C6), VHDL  
**ICs Referenced:** 74283 4-Bit Binary Full Adder

---

## Overview

This project demonstrates a progression from a **4-bit adder** to a full **8-bit adder** built by cascading two 74283-equivalent adder blocks. Both designs were implemented as block diagrams (`.bdf`) in Quartus II, simulated for functional and timing correctness, and synthesized onto the Altera DE2 FPGA board.

The 8-bit design extends the 4-bit version by chaining the carry-out (COUT) of the lower nibble adder into the carry-in (CIN) of the upper nibble adder — the classic **ripple carry** architecture.

---

## Part 1 — 4-Bit Adder (`fourbit`)

### Block Diagram
A single 74283 4-bit adder IC was instantiated in the Quartus II block diagram editor with:
- 4-bit inputs: `A[3:0]`, `B[3:0]`
- Carry in: `CIN` (tied to GND)
- 4-bit sum output: `SUM[3:0]`
- Carry out: `COUT`

![4-bit Block Diagram](./images/IMG_4076.jpeg)

### VHDL Equivalent

```vhdl
Library ieee;
use ieee.std_logic_1164.ALL;
use ieee.std_logic_unsigned.ALL;

Entity fourbit IS
  port (
    A    : in  std_logic_vector(3 downto 0);
    B    : in  std_logic_vector(3 downto 0);
    SUM  : out std_logic_vector(3 downto 0);
    COUT : out std_logic
  );
End fourbit;

Architecture arc of fourbit IS
  signal result : std_logic_vector(4 downto 0);
Begin
  result <= ('0' & A) + ('0' & B);
  SUM    <= result(3 downto 0);
  COUT   <= result(4);
END arc;
```

### Simulation Results
Functional simulation confirmed correct addition across all tested input combinations with **0 errors, 0 warnings** (92.5% simulation coverage).

| A | B | Expected SUM | COUT |
|---|---|-------------|------|
| 5 | A | F | 0 |
| A | 2 | C | 0 |
| 2 | 7 | 9 | 0 |
| 9 | 8 | 1 | 1 |
| 6 | A | 0 | 1 |

![4-bit Simulation Waveforms](./images/IMG_4074.jpeg)

---

## Part 2 — 8-Bit Adder (`eight`)

### Block Diagram
Two 74283 adder blocks were cascaded in the Quartus II block diagram editor:
- Lower nibble: handles `A[3:0]` + `B[3:0]`, CIN tied to GND
- Upper nibble: handles `A[7:4]` + `B[7:4]`, CIN connected to lower COUT
- Final 8-bit sum: `SUM[7:0]`
- Final carry out: `COUT`

![8-bit Block Diagram](./images/IMG_4078.jpeg)

### VHDL Equivalent

```vhdl
Library ieee;
use ieee.std_logic_1164.ALL;
use ieee.std_logic_unsigned.ALL;

Entity eight IS
  port (
    A    : in  std_logic_vector(7 downto 0);
    B    : in  std_logic_vector(7 downto 0);
    SUM  : out std_logic_vector(7 downto 0);
    COUT : out std_logic
  );
End eight;

Architecture arc of eight IS
  signal result      : std_logic_vector(8 downto 0);
  signal low_sum     : std_logic_vector(4 downto 0);
  signal carry_mid   : std_logic;
Begin
  -- Lower nibble addition
  low_sum   <= ('0' & A(3 downto 0)) + ('0' & B(3 downto 0));
  carry_mid <= low_sum(4);

  -- Upper nibble addition with carry-in from lower
  result    <= ('0' & A(7 downto 4)) + ('0' & B(7 downto 4)) + carry_mid;

  -- Combine outputs
  SUM  <= result(3 downto 0) & low_sum(3 downto 0);
  COUT <= result(4);
END arc;
```

### Simulation Results
Both functional and timing simulations were run. Results confirmed correct 8-bit addition with carry propagation across all tested vectors. **0 errors, 0 warnings** (100% simulation coverage).

| A (hex) | B (hex) | Expected SUM | COUT |
|---------|---------|-------------|------|
| 64      | 36      | 9A          | 0    |
| 58      | 52      | AA          | 0    |  
| 59      | 12      | 6B          | 0    |
| 03      | 25      | 28          | 0    |
| 85      | 7E      | 03          | 1    |

![8-bit Timing Simulation](./images/IMG_4080.jpeg)

---

## Resource Utilization

| Project | Logic Cells | Dedicated Logic | Status |
|---------|-------------|-----------------|--------|
| fourbit | 7 / EP2C35F672C6 | 0 | ✅ 0 errors |
| eight   | 17 / EP2C35F672C6 | 0 | ✅ 0 errors |

---

## Key Takeaways

- The 74283 ripple carry architecture is simple but introduces **carry propagation delay** that grows with bit width — a key tradeoff vs. carry-lookahead designs
- Cascading adder blocks in a block diagram directly mirrors how physical IC chaining works on a breadboard
- Both functional and timing simulation modes were used — timing simulation catches real-world propagation delays that functional simulation ignores

---

