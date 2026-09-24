# Principle

RIX8 uses a modified Harvard architecture: instructions are fetched from external SPI Flash through a dedicated prefetch buffer, while data accesses go to an on-chip scratchpad and memory-mapped peripherals. The two paths share the external SPI controller, so the design sits between strict Harvard and a unified von Neumann model.

## Sub-pages

- [Registers](registers.md)
- [Instructions](instructions.md)
- [Addressing Modes](addressing-modes.md)
- [Flags](flags.md)

