# Flags

RIX8 maintains two condition flags: **Z (Zero)** and **C (Carry)**. They are stored in a flags register that is not directly readable or writable by software.

## Flag Definitions

| Flag | Bit | Name | Meaning |
| :--- | :--- | :--- | :--- |
| Z | 0 | Zero | Set when the result of an operation is 0x00 |
| C | 1 | Carry | Set on carry-out (ADD) or borrow (SUB) |

## Instructions That Update Flags

| Instruction | Updates Z | Updates C |
| :--- | :--- | :--- |
| ADD | Yes | Yes |
| ADDI | Yes | Yes |
| SUB | Yes | Yes |
| AND | Yes | No |
| OR | Yes | No |
| XOR | Yes | No |
| ANDI | Yes | No |
| ORI | Yes | No |
| SLL | Yes | Yes |
| SRL | Yes | Yes |
| LW | Yes | No |
| SW | No | No |
| BEQ | No | No |
| BNE | No | No |
| JAL | No | No |
| LDI | Yes | No |

## How Flags Are Used

In the current instruction set, branches (`BEQ`, `BNE`) compare two registers directly and do not consult the flags. The flags are maintained for future conditional instructions and for software that wishes to inspect them (though there is no instruction to read them directly).

## Carry Semantics

- **ADD / ADDI**: C is set if the unsigned sum exceeds 0xFF.
- **SUB**: C is set if rs1 < rs2 (borrow occurred).
- **SLL**: C is set to the last bit shifted out.
- **SRL**: C is set to the last bit shifted out.

## Zero Semantics

Z is set when the 8-bit result of the operation is 0x00. It is cleared otherwise.
