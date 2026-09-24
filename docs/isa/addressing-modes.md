# Addressing Modes

RIX8 supports three addressing modes. Each mode is tied to a specific instruction, so the decoder can resolve the mode from the opcode alone.

## Immediate

The operand is a constant encoded in the instruction.

```x86asm
LDI     rd, imm6        ; rd = imm6
ADDI    rd, rs1, imm6   ; rd = rs1 + imm6
ANDI    rd, rs1, imm6   ; rd = rs1 & imm6
ORI     rd, rs1, imm6   ; rd = rs1 | imm6
```

Immediates are **zero-extended** to 8 bits. Range: 0 to 63.

## Register Direct

The operand is a register, selected by a 3-bit field.

```x86asm
ADD     rd, rs1, rs2
SUB     rd, rs1, rs2
AND     rd, rs1, rs2
OR      rd, rs1, rs2
XOR     rd, rs1, rs2
SLL     rd, rs1, rs2
SRL     rd, rs1, rs2
```

## Register Indirect

The operand is a memory location whose address is held in a register. This is the only mode that accesses memory, and it is used exclusively by `LW` and `SW`.

```x86asm
LW  rd, [rs1]   ; rd = Mem[rs1]
SW  [rs1], rd   ; Mem[rs1] = rd
```
The address in rs1 is **zero-extended** to 16 bits, giving access to the lower 256 bytes of the address space. This is sufficient for the memory-mapped UART and SPI control registers.

## PC-Relative

Branches and jumps use a PC-relative offset encoded as a 6-bit signed immediate. The offset is counted in **instruction words** (2 bytes), not bytes.

```x86asm
BEQ     rs1, rs2, imm6  ; if rs1 == rs2: PC += imm6
BNE     rs1, rs2, imm6  ; if rs1 != rs2: PC += imm6
JAL     rd, imm6        ; rd = PC+1; PC += imm6
```

Range: -32 to +31 instructions.

