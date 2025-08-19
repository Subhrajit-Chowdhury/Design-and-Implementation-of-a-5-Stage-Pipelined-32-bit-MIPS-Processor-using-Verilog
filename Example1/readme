***

# Example MIPS32 Testbench Program

This program demonstrates how to initialize registers, perform simple additions, and halt the processor, using a MIPS‑like pipeline model (`pipe_MIPS32`).  

***

## Program Steps

1. **Initialize register R1 = 10**  
2. **Initialize register R2 = 20**  
3. **Initialize register R3 = 25**  
4. **Add R1 + R2 = R4**  
5. **Add R4 + R3 = R5**  
6. **End execution with HLT**

At the end of execution, register **R5 = 55** (10 + 20 + 25).

***

## Instruction Encoding Table

| Assembly Instruction | Machine Code (Binary)                                | Hex Code   |
|-----------------------|------------------------------------------------------|------------|
| `ADDI R1, R0, 10`    | `001010 00000 00001 0000000000001010`                | `2801000a` |
| `ADDI R2, R0, 20`    | `001010 00000 00010 0000000000010100`                | `28020014` |
| `ADDI R3, R0, 25`    | `001010 00000 00011 0000000000011001`                | `28030019` |
| `OR   R7, R7, R7`    | `000000 00111 00111 00111 00000 100000` *(dummy)*    | `0ce77800` |
| `OR   R7, R7, R7`    | `000000 00111 00111 00111 00000 100000` *(dummy)*    | `0ce77800` |
| `ADD  R4, R1, R2`    | `000000 00001 00010 00100 00000 100000`              | `00222000` |
| `OR   R7, R7, R7`    | *(dummy instruction, same as above)*                 | `0ce77800` |
| `ADD  R5, R4, R3`    | `000000 00100 00011 00101 00000 100000`              | `00832800` |
| `HLT`                | `111111 00000 00000 00000 00000 000000`              | `fc000000` |

***

## Expected Output

```
R1 = 10
R2 = 20
R3 = 25
R4 = 30   (10 + 20)
R5 = 55   (30 + 25)
```

At this point the processor halts.

***
