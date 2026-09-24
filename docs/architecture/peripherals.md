# Peripherals

RIX8 includes two peripherals: a QSPI controller for external Flash and SRAM, and a UART for serial communication.

## QSPI Controller

The QSPI controller is a bit-banged SPI master. It runs on the system clock and generates SCK by dividing the system clock.

## UART Controller

The UART provides serial TX and RX at a fixed baud rate derived from the system clock.

### Baud Rate

The baud rate is set by a divider in the UART controller. For a system clock of 24 MHz and a target of 115200 baud, the divisor is approximately 208.

### Registers

| Register | Address | Description |
| :--- | :--- | :--- |
| `UART_TX` | `0x7F00` | Write a byte to transmit |
| `UART_RX` | `0x7F01` | Read a received byte |
| `UART_STATUS` | `0x7F02` | Bit 0: RX ready, Bit 1: TX busy |


