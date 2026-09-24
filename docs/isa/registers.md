# Registers

RIX8 has eight 8-bit general-purpose registers, encoded as 3-bit fields in every instruction.

## General-Purpose Registers

| Code | Register | Description |
| :--- | :--- | :--- |
| `000` | R0 | Hardwired to zero. Reads return 0x00. Writes are ignored. |
| `001` | R1 | General purpose |
| `010` | R2 | General purpose |
| `011` | R3 | General purpose |
| `100` | R4 | General purpose |
| `101` | R5 | General purpose |
| `110` | R6 | General purpose |
| `111` | R7 | General purpose |


R0 is a constant zero. It cannot be written. This simplifies operations that need a zero operand, such as clearing a register or comparing a value against zero.

## Program Counter

The program counter (PC) is 16 bits wide and is not directly accessible as a general-purpose register. It is updated by:

- Normal instruction fetch (PC increments by 1 word)
- Branches (`BEQ`, `BNE`) when the condition is met
- `JAL`, which saves `PC+1` into `rd` before jumping


## Stack Pointer

RIX8 does not have a dedicated hardware stack pointer. Subroutine calls are handled by `JAL`, which saves the return address in a register. A software stack can be implemented using R6 or R7 as a pointer, but this is not enforced by hardware.

## Flags

Two condition flags are maintained in a flags register:

| Flag | Bit | Description |
| :--- | :--- | :--- |
| Z | 0 | Zero flag. Set when the result of an operation is 0x00. |
| C | 1 | Carry flag. Set on carry-out or borrow from arithmetic. |

The flags register is not directly readable or writable by software. Flags are updated by arithmetic, logic, and shift instructions.

