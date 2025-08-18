# Design-and-Implementation-of-a-5-Stage-Pipelined-32-bit-MIPS-Processor-using-Verilog
An educational Verilog-based implementation of a 5-stage pipelined MIPS processor, simulating the instruction flow through standard MIPS stages: IF, ID, EX, MEM, and WB. This project is designed to help understand pipelined architecture and hazards in RISC-based processors.

5 Pipeline Stages: Implements all five classical MIPS pipeline stages:

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
