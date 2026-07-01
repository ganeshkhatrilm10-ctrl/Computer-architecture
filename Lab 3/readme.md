# Lab 5: VHDL Code for Combinational Circuits: Comparator

**Course:** Computer Architecture (CMP 262)  
**Program:** Bachelor of Computer Engineering  
**Semester:** Fourth Semester  
**College:** Cosmos College of Management and Technology  
**Department:** Department of Information and Communication Technology  

---

## Objective
- To design and simulate a 2-bit magnitude comparator in VHDL.
- To understand how comparison operations are implemented in hardware.

---

## Theory
A magnitude comparator compares two binary numbers and produces three output signals:
- **EQ (Equal):** HIGH when A = B
- **GT (Greater Than):** HIGH when A > B
- **LT (Less Than):** HIGH when A < B

For a 2-bit comparator with inputs A (A₁A₀) and B (B₁B₀), the logic can be described using standard comparison operators in VHDL by casting the vectors to `unsigned` types.

### Expected Truth Table

| A (bin) | B (bin) | EQ | GT | LT |
|---------|---------|----|----|----|
| 00      | 00      | 1  | 0  | 0  |
| 01      | 00      | 0  | 1  | 0  |
| 00      | 01      | 0  | 0  | 1  |
| 10      | 11      | 0  | 0  | 1  |
| 11      | 10      | 0  | 1  | 0  |
| 11      | 11      | 1  | 0  | 0  |

---

## Design Files

### 2-bit Magnitude Comparator
**Filename:** `comparator_2bit.vhd`  
Implements the comparison logic using a behavioral process with `if-elsif-else` statements.

### Testbench
**Filename:** `comparator_tb.vhd`  
Verifies the design by cycling through various input combinations of A and B.

---

## Simulation Commands

```bash
# 1. Analyze design and testbench files
ghdl -a comparator_2bit.vhd comparator_tb.vhd

# 2. Elaborate the testbench
ghdl -e COMPARATOR_TB

# 3. Simulate and export waveform
ghdl -r COMPARATOR_TB --vcd=comparator.vcd

# 4. Open waveform in GTKWave
gtkwave comparator.vcd
```

---

## Output
The GTKWave simulation confirms the logic:

**Waveform Analysis:**
- **0-10 ns:** A="00", B="00" → EQ=1
- **10-20 ns:** A="01", B="00" → GT=1
- **20-30 ns:** A="00", B="01" → LT=1
- **30-40 ns:** A="10", B="11" → LT=1
- **40-50 ns:** A="11", B="10" → GT=1
- **50-60 ns:** A="11", B="11" → EQ=1

## Conclusion
The 2-bit magnitude comparator was successfully designed and simulated. The behavioral model correctly identifies the relationship between the two 2-bit binary inputs, matching the expected truth table exactly.