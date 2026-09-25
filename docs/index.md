---
title: RIX-SoC
description: RIX8 is a compact 8-bit CPU with a custom 16-bit instruction set, SPI Flash instruction fetch, and UART, designed for a 3-stage in-order pipeline.
---

# RIX-SoC

RIX-SoC is a compact 8-bit system-on-chip designed for a 1x2 Tiny Tapeout tile. It integrates a custom CPU core, an SPI memory controller for external Flash and SRAM, and a UART on a single die.

# RIX8

RIX8 is a compact 8-bit CPU with a custom 16-bit fixed-length instruction set. Its multi-cycle execution model, 8 general-purpose registers, and 16-bit address space keep the core small and predictable, leaving room for the SoC peripherals.

* __Data width:__ 8-bit
* __Instruction width:__ 16-bit fixed
* __Execution model:__ Multi-cycle
* __Registers:__ 8 general-purpose 8-bit registers
* __Address space:__ 16-bit (64 KB)

# Peripherals

* __SPI Flash controller__ with prefetch buffer for instruction fetch
* __UART__ for serial I/O
* __Memory-mapped I/O__ for peripheral access
