

# pipe_reg_1stage (Valid/Ready Pipeline Register)

## Overview
This repository contains a **single-stage pipeline register** (1-deep buffer) implemented in **SystemVerilog** using the standard **valid/ready handshake protocol**.

It is commonly used between two hardware modules to safely transfer data while supporting **backpressure** (stalling) without any data loss or duplication.

---

## Features
- Fully synthesizable SystemVerilog RTL
- Implements standard **valid/ready** handshake
- Stores exactly **one data word** (single-stage buffer)
- Correctly handles **stall/backpressure**
- No data loss, no duplication
- Clean reset (buffer becomes empty)

---

## Handshake Protocol
### Input Interface
| Signal | Direction | Description |
|--------|----------|-------------|
| `in_data`  | Input  | Data from upstream module |
| `in_valid` | Input  | Upstream asserts when `in_data` is valid |
| `in_ready` | Output | Module asserts when it can accept new data |

### Output Interface
| Signal | Direction | Description |
|--------|----------|-------------|
| `out_data`  | Output | Data presented to downstream module |
| `out_valid` | Output | Asserted when `out_data` is valid |
| `out_ready` | Input  | Downstream asserts when it is ready to accept data |

---

## Transfer Conditions
### Input Accept (Write into register)
A new input word is accepted when: in_valid && in_ready

### Output Consume (Read by downstream)
The stored output word is consumed when: out_valid && out_ready




