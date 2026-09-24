# Memory Map

RIX8 uses a 16-bit address space, giving 64 KB total. The space is divided between external SPI Flash, external SPI SRAM, and memory-mapped peripherals.

## Address Space Layout

| Range | Size | Region | Access |
| :--- | :--- | :--- | :--- |
| `0x0000` – `0x7EFF` | ~32 KB | SPI Flash (instructions) | Read-only |
| `0x7F00` – `0x7FFF` | 256 B | Memory-mapped I/O | Read/write |
| `0x8000` – `0xFFFF` | 32 KB | SPI SRAM (data) | Read/write |

## Memory-Mapped I/O

The I/O region at `0x7F00` contains peripheral registers.

| Address | Register | Access | Description |
| :--- | :--- | :--- | :--- |
| `0x7F00` | UART_TX | Write | Write a byte to transmit |
| `0x7F01` | UART_RX | Read | Read a received byte |
| `0x7F02` | UART_STATUS | Read | Bit 0: RX ready, Bit 1: TX busy |
| `0x7F10` | SPI_DATA | Read/write | QSPI data register |
| `0x7F11` | SPI_CTRL | Write | QSPI control (start, CS) |
| `0x7F12` | SPI_STATUS | Read | Bit 0: busy |


## Reset Vector

On reset, the PC is set to `0x0000`. The first instruction is fetched from SPI Flash at address `0x0000`.

