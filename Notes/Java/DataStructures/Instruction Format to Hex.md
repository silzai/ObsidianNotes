- (opCode-4)(imm-8)(Rd-4)
- (opcode-4)(Rd-4)(Rs-4)
- (opCode-4)(Address-8)

## Code For Main Commands
| Instructions          | Hex |
| --------------------- | --- |
| **MOV** Rd, Rs        | 0x0 |
| **MOV** Rd, imm       | 0x1 |
| **LDR** Rd, (Address) | 0x2 |
| **STR** (Address), Rs | 0x3 |
| **ADD** Rd, Rs        | 0x4 |
| **SUB** Rd, Rs        | 0x5 |
| **AND** Rd, Rs        | 0x6 |
| **LSR** Rd, Rs        | 0x7 |
| **LSL** Rd, Rs        | 0x8 |
| **BRZ** (Address)               | 0x9 |
| **BRC** (Address)      | 0xA |

## Code For Registers and Memory
| Registers | Hex |
| --------- | --- |
| R0        | 0x0 |
| R1        | 0x1 |
| R2        | 0x2 |
| R3        | 0x3 |
| R4        | 0x4 |
| R5        | 0x5 |
| R6        | 0x6 |
| R7        | 0x7    |

- Whenever you want to write the hex for a memory address, just write 0x8, for example when rd = 0, and the source is memory:
```
LDR Rd, <Address>
```
- so in hex, you can write:
```
0x1 0x2 0x0 0x8
```

- break down of the above code:
- First command: 0x0
	- This is the actual memory/RAM address
	- If we are doing LDR or STR, then we will put any value within 0xFF
	- otherwise for any other operation, will write 0x0
- Second command: 0x2
	- This is the "LDR" command, taken from the above table
- Third command: 0x0
	- This is the address of the register to be loaded
- Fourth command: 0x8
	- We will write this whenever we are doing LDR or STR to indicate them.