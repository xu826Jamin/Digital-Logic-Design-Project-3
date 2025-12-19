# Digital-Logic-Design-Project-3
## Part 3: Programmable Logic & HDL Design
[cite_start]**Course:** CompEng 2DI4 - Laboratory 3 [cite: 563]
[cite_start]**Objective:** Establish proficiency in combinational logic design using commercial Programmable Logic Device (PLD) design packages and Verilog Hardware Description Language (HDL). [cite: 598, 599]

### 1. Hardware Description Language (HDL) Integration
- [cite_start]**Assumptions**: Logic is implemented on a **MAX10 FPGA** (10M50DAF484C7G) utilizing the Terasic DE10-Lite development board. [cite: 640, 693]
- [cite_start]**Conditions**: All Verilog modules must be compiled in Quartus Prime Lite Edition and loaded into the FPGA to interface with physical onboard components. [cite: 603, 655]
- [cite_start]**Design Methodology**: Transitioned from discrete breadboard circuits to HDL-based design using Verilog design entry and Schematic Capture. [cite: 600, 629]
- [cite_start]**Logical Reasoning**: Programmable logic allows for the simulation of physical connections and functional testing of "programmed" circuits within a single software environment. [cite: 600, 688]

### 2. Lamp Controller Verification
- [cite_start]**Boolean Equation**: The two-way lamp controller is defined by the XOR relationship $f = (x1 \cdot \sim x2) + (\sim x1 \cdot x2)$. [cite: 614]
- [cite_start]**Truth Table**: The output $f$ is HI (1) only when inputs $x1$ and $x2$ are different ($01$ or $10$). [cite: 620, 622]
- [cite_start]**Implementation**: Verified the module by mapping switches to inputs and onboard LEDs to outputs on the CPLD/FPGA. [cite: 654, 655]
- [cite_start]**HDL Verification**: The project used a Verilog module to assign logic directly to hardware pins. [cite: 560]

### 3. 3-to-8 Line Decoder Design
- [cite_start]**Functional Goal**: Develop a circuit that accepts a 3-bit binary code and activates exactly one of eight output lines. [cite: 660]
- [cite_start]**Design Logic**: Each of the eight outputs corresponds to a specific minterm ($D_0 \dots D_7$) of the input variables $x, y, z$. [cite: 561]
- [cite_start]**The "Why"**: Decoders are fundamental for memory addressing and selecting specific hardware outputs based on binary addresses. [cite: 661]
- [cite_start]**Dataflow Modeling**: Utilized internal `wire` assignments for inverted signals ($x\_n, y\_n, z\_n$) to implement all minterms from $x'y'z'$ to $xyz$. [cite: 561]

### 4. Binary to Decimal Display Driver
- [cite_start]**Custom Logic**: Engineered a minimized combinational circuit to drive a seven-segment display based on a 2-bit binary input. [cite: 635, 668]
- [cite_start]**Mapping Logic**: An input of $00$ displays "0", $01$ displays "1", $10$ displays "2", and $11$ displays "3". [cite: 635]
- [cite_start]**Segment Optimization**: Derived unique Boolean equations for segments $a$ through $g$ using K-Map minimization from pre-lab preparations. [cite: 562, 636]

- [cite_start]**Active-High Configuration**: The implementation in `milestone3` uses active-high logic to light the segments of the DE10-Lite onboard display. [cite: 562]

### Mathematical Foundations (LaTeX)
#### Decoder Minterm Logic
[cite_start]The outputs for a 3-to-8 decoder represent all possible 3-variable minterms[cite: 561]:
$$D_n = L_2 \cdot L_1 \cdot L_0$$
*Where $L_i$ represents either the input $x_i$ or its complement $\sim x_i$.*

#### XOR Lamp Controller Function
[cite_start]$$f = (x1 \cdot \sim x2) + (\sim x1 \cdot x2) = x1 \oplus x2$$ [cite: 614]

#### Minimized Display Equations (Partial)
[cite_start]Based on experimental Verilog modeling[cite: 562]:
* **Segment A**: $a = in0 + in1'$
* **Segment E**: $e = in0'$
* **Segment G**: $g = in1$

### ⚠️ Potential Pitfalls
- [cite_start]**Pin Assignment Errors**: If the generic device properties differ from the physical hardware (MAX10), the circuit may fail to interface with switches or LEDs. [cite: 693]
- [cite_start]**Indeterminate Simulation**: Functional simulations must account for propagation delays; outputs do not change immediately with inputs due to hardware gate latency. [cite: 716, 717]
- [cite_start]**Documentation Standards**: Quartus design entries must include student names and IDs as embedded comments to be valid for grading. [cite: 648, 649]

***
[cite_start]*Results verified by TA Milestones 1-3.* [cite: 654, 659, 667]
