# AMBA APB UART (8-E-1) — Design & Verification

A synthesizable UART peripheral with an AMBA APB3 slave interface, designed in RTL and verified using SystemVerilog, SystemVerilog Assertions (SVA), and functional coverage.

## Overview

This project combines a standard UART communication interface with an AMBA APB3 register interface.

The APB interface allows a processor or bus master to configure and control the UART through memory-mapped registers, while the UART handles serial data transmission and reception.

## Key Features

- AMBA APB3 slave interface
- UART transmitter and receiver
- 8-bit data
- Even parity *(Note: change to "No parity" if this is 8-N-1)*
- 1 stop bit
- Configurable baud-rate support
- Memory-mapped UART registers
- Synthesizable RTL design
- SystemVerilog-based verification
- SystemVerilog Assertions (SVA)
- Functional coverage
- Simulation waveform analysis

## Architecture
