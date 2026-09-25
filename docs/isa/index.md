---
title: ISA Overview
description: Instruction set architecture, registers, instructions, addressing modes, and flags for the RIX8 CPU.
---

## Architecture Summary

| Parameter | Value |
| :--- | :--- |
| Data width | 8 bits |
| Instruction width | 16 bits |
| Address width | 16 bits |
| Registers | 8 x 8-bit (R0 = zero) |
| Flags | Z (zero), C (carry) |
| Memory access | Register-indirect |
| Branches | PC-relative, 6-bit offset |
| Execution model | Multi-cycle FSM |

## Instruction Classes

RIX8 instructions fall into four classes:

| Class | Instructions | Purpose |
| :--- | :--- | :--- |
| Register-Register | ADD, SUB, AND, OR, XOR, SLL, SRL | ALU operations |
| Register-Immediate | ADDI, ANDI, ORI, LDI | Constant arithmetic |
| Memory Access | LW, SW | Load and store bytes |
| Control Flow | BEQ, BNE, JAL | Branches and jumps |

# Principle

RIX8 uses a modified Harvard architecture. Instructions are fetched from external SPI Flash, while data accesses go to external SPI SRAM and memory-mapped peripherals. Both paths share the same SPI controller, placing the design between strict Harvard and a unified von Neumann model.

## ISA Components

- [Registers](registers.md)
- [Instructions](instructions.md)
- [Instruction Format](instruction-format.md)
- [Addressing Modes](addressing-modes.md)
- [Flags](flags.md)

## Related

- [Architecture Overview](../architecture/index.md)
- [Memory Map](../architecture/memory-map.md)
- [Assembler Usage](../development/assembler.md)
