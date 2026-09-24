# Instruction Format

RIX8 uses a fixed **16-bit instruction width**. Every instruction is fetched from external flash.

# Bit layout

Every instruction follows this format:

| Field | Bits | Width | Description |
| :--- | :--- | :--- | :--- |
| `opcode` | 15–12 | 4 | Operation selector (16 possible opcodes) |
| `rd` | 11–9 | 3 | Destination register (R0–R7) |
| `rs1` | 8–6 | 3 | First source register (R0–R7) |
| `rs2 / imm6` | 5–0 | 6 | Second source register or 6-bit immediate |

The decoding of last 6-bit depends on the specific instruction. For register-register operation, it selects `rs2`. For immediate operations, it carries a 6-bit constant.

