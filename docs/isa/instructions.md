# Instructions

RIX8 has 14 assigned opcodes out of 16 available slots. Each instruction
is 16 bits wide.

## Opcode Table

| Opcode | Mnemonic | Syntax | Operation |
| :--- | :--- | :--- | :--- |
| `0000` | ADD | `ADD rd, rs1, rs2` | `rd = rs1 + rs2` |
| `0001` | ADDI | `ADDI rd, rs1, imm6` | `rd = rs1 + imm6` |
| `0010` | SUB | `SUB rd, rs1, rs2` | `rd = rs1 - rs2` |
| `0011` | AND | `AND rd, rs1, rs2` | `rd = rs1 & rs2` |
| `0100` | OR | `OR rd, rs1, rs2` | `rd = rs1 \| rs2` |
| `0101` | XOR | `XOR rd, rs1, rs2` | `rd = rs1 ^ rs2` |
| `0110` | SLL | `SLL rd, rs1, rs2` | `rd = rs1 << rs2` |
| `0111` | SRL | `SRL rd, rs1, rs2` | `rd = rs1 >> rs2` |
| `1000` | LW | `LW rd, [rs1]` | `rd = Mem[rs1]` |
| `1001` | SW | `SW [rs1], rd` | `Mem[rs1] = rd` |
| `1010` | BEQ | `BEQ rs1, rs2, imm6` | `if rs1 == rs2: PC += imm6` |
| `1011` | BNE | `BNE rs1, rs2, imm6` | `if rs1 != rs2: PC += imm6` |
| `1100` | JAL | `JAL rd, imm6` | `rd = PC+1; PC += imm6` |
| `1101` | ANDI | `ANDI rd, rs1, imm6` | `rd = rs1 & imm6` |
| `1110` | ORI | `ORI rd, rs1, imm6` | `rd = rs1 \| imm6` |
| `1111` | LDI | `LDI rd, imm6` | `rd = imm6` |


## Arithmetic

### ADD

```x86asm
ADD rd, rs1, rs2 ; rd = rs1 + rs2
```

Adds two registers. Updates Z and C flags.


### ADDI

```x86asm
ADDI rd, rs1, imm6 ; rd = rs1 + imm6
```

Adds a zero-extended 6-bit immediate to a register. Updates Z and C.

### SUB

```x86asm
SUB rd, rs1, rs2 ; rd = rs1 - rs2
```

Subtracts rs2 from rs1. Updates Z and C. Carry is set on borrow.

## Logic

### AND

```x86asm
AND rd, rs1, rs2 ; rd = rs1 & rs2
```

### OR

```x86asm
OR rd, rs1, rs2 ; rd = rs1 | rs2
```

### XOR

```x86asm
XOR rd, rs1, rs2 ; rd = rs1 ^ rs2
```

### ANDI

```x86asm
ANDI rd, rs1, imm6 ; rd = rs1 & imm6
```

### ORI

```x86asm
ORI rd, rs1, imm6 ; rd = rs1 | imm6
```

### ORI

```x86asm
ORI rd, rs1, imm6 ; rd = rs1 | imm6
```

## Shifts

### SLL

```x86asm
SLL rd, rs1, rs2 ; rd = rs1 << rs2
```

Shifts rs1 left by the low 3 bits of rs2. Updates Z and C.

### SRL

```x86asm
SRL rd, rs1, rs2 ; rd = rs1 >> rs2
```

Shifts rs1 right by the low 3 bits of rs2. Updates Z and C.

## Memory Access

### LW

```x86asm
LW rd, [rs1] ; rd = Mem[rs1]
```

Loads a byte from the address in rs1. The rs2/imm6 field must be zero.

### SW

```x86asm
SW [rs1], rd ; Mem[rs1] = rd
```

Stores a byte to the address in rs1. The rs2/imm6 field must be zero.

## Control Flow

### BEQ

```x86asm
BEQ rs1, rs2, imm6 ; if rs1 == rs2: PC += imm6
```

Branches if two registers are equal. Offset is in instruction words, sign-extended, range -32 to +31.


### BNE

```x86asm
BNE rs1, rs2, imm6 ; if rs1 != rs2: PC += imm6
```

Branches if two registers are not equal.

### JAL

```x86asm
JAL rd, imm6 ; rd = PC+1; PC += imm6
```

Jumps to PC + imm6 and saves the return address in rd. Use `JAL R0, imm6` for an unconditional jump without saving a return address.

## Immediate

### LDI

```x86asm
LDI rd, imm6 ; rd = imm6
```

Loads a zero-extended 6-bit immediate into a register. rs1 is ignored.
