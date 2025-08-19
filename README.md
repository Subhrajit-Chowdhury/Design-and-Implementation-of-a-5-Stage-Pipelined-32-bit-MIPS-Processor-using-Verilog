# Design-and-Implementation-of-a-5-Stage-Pipelined-32-bit-MIPS-Processor-using-Verilog

## Overview

An educational Verilog-based implementation of a 5-stage pipelined MIPS processor. This project is designed to help understand pipelined architecture and hazards in RISC-based processors.
This repository documents the development of a five-stage pipelined 32-bit MIPS processor using Verilog. The implementation is based on a subset of the MIPS32 instruction set architecture and follows the classical RISC pipeline stages: Instruction Fetch (IF), Instruction Decode (ID), Execute (EX), Memory Access (MEM), and Write Back (WB). 

5 Pipeline Stages:

Instruction Fetch (IF)

Instruction Decode/Register Fetch (ID)

Execute (EX)

Memory Access (MEM)

Write Back (WB)

▫️ MIPS32

32 x 32 bit GPRs [R0 to R31]

R0 hardwired to logic0

32 bit Program Counter (PC)

No flag registers (carry, zero, sign..etc)

Few Addresing Modes

Only Load and Store instructions can access memory

We assume memory word size is 32 bits (word addressable)

▫️ ** Instruction Encoding**

<img width="966" height="542" alt="Image" src="https://github.com/user-attachments/assets/39cb543d-1b17-4e07-9ea7-001fe85754b4" />
shamt : shift amount, funct : opcode extension for additional functions.

Some instructions require two register operands rs & rt as input, while some require only rs.

This requirement is only identified only after the instruction is decoded.

While decoding is going on, we can prefetch the registers in parallel, which may or may not be used later.

Similarly, the 16-bit and 26-bit immediate data are retrieved and signextended to 32-bits in case they are required later.


<img width="1156" height="556" alt="Image" src="https://github.com/user-attachments/assets/04edc521-63af-463b-85c6-f33633fa0208" />

<img width="1442" height="727" alt="Image" src="https://github.com/user-attachments/assets/7e9c8b56-5093-4ab4-9f6c-018049092ab4" />


***
## Features

- **MIPS32 Instruction Set Subset:**  
  - Load/Store: `LW`, `SW`
  - Arithmetic/Logic: `ADD`, `SUB`, `AND`, `OR`, `MUL`, `SLT`
  - Immediate Arithmetic: `ADDI`, `SUBI`, `SLTI`
  - Branch: `BEQZ`, `BNEQZ`
  - Jump: `J`
  - Halt: `HLT`
- **Three Instruction Formats:**  
  - R-type (Register)
  - I-type (Immediate)
  - J-type (Jump)
- **32 General-Purpose Registers** plus a program counter (PC)
- **32-bit Data Path:** Word-addressable memory
- **Pipelined Implementation:**  
  - Five distinct pipeline stages: IF, ID, EX, MEM, WB  
  - Inter-stage latches: `IF_ID`, `ID_EX`, `EX_MEM`, `MEM_WB`
  - Behavioral modeling in Verilog with explicit handling for HALT and branch control
  
## Pipeline Stages

1. **Instruction Fetch (IF):** Fetches instruction from memory and computes the next PC.
2. **Instruction Decode/Register Fetch (ID):** Decodes instruction, reads registers, and sign-extends immediates.
3. **Execution/Address Calculation (EX):** ALU operations and effective address computation.
4. **Memory Access/Branch Completion (MEM):** Loads, stores, and branch decision/update.
5. **Write Back (WB):** Result written to the register file.

## Testbenches

The repo includes testbenches for:
- **Arithmetic Operations:** Adding multiple values in registers
- **Memory Operations:** Loading value from memory, computation, and storing results
- **Control Flow:** Loop and branch execution (e.g., factorial computation)

## Usage & Simulation

- Two-phase clocking scheme utilized (`clk1`, `clk2`)
- Sample memory initialization and register setup via testbenches
- Output verification through register/memory dumps after simulation
- Example VCD files and GTKWave instructions included for waveform viewing

## Notes

- **Hazard Handling:** Data/control hazard avoidance is not implemented; dummy instructions are inserted manually where required in examples.
- **Behavioral Model:** Primary focus is educational; synthesis/structural optimizations are not included.

## References

- Based on NPTEL course "Hardware Modeling Using Verilog" (IIT Kharagpur, Prof. Indranil Sengupta)

[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/52466036/819ac10e-1085-4fe0-8da9-bc185e69281c/week8-slides_watermark.pdf
