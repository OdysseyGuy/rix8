# RIX8

RIX8 is a compact 8-bit CPU with a custom 16-bit fixed-length instruction set architecture, designed as a complete system-on-chip.

# Architecture

* __Data width:__ 8-bit
* __Instruction width:__ 16-bit fixed
* __Pipeline:__ 3-stage in-order
* __Registers:__ 8 general-purpose 8-bit registers
* __Address space:__ 16-bit (64 KB)

# Peripherals

* __SPI Flash controller__ with prefetch buffer for instruction fetch
* __UART__ for serial I/O
* __Memory-mapped I/O__ for peripheral access

# Toolchain

A Python assembler (rix8_asm.py) converts RIX8 assembly into binary for loading into SPI Flash.
