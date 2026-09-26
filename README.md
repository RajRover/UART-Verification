AMBA APB UART (8-E-1) — Design & Verification

A synthesizable UART peripheral with an AMBA APB3 slave interface, designed in RTL and verified using SystemVerilog, SystemVerilog Assertions (SVA), and functional coverage.

Overview

This project combines a standard UART communication interface with an AMBA APB3 register interface.

The APB interface allows a processor or bus master to configure and control the UART through memory-mapped registers, while the UART handles serial data transmission and reception.

Key Features
AMBA APB3 slave interface
UART transmitter and receiver
8-bit data
No parity
1 stop bit
Configurable baud-rate support
Memory-mapped UART registers
Synthesizable RTL design
SystemVerilog-based verification
SystemVerilog Assertions (SVA)
Functional coverage
Simulation waveform analysis
Architecture
                 APB BUS
                    │
                    ▼
          ┌──────────────────┐
          │   APB Interface  │
          │                  │
          │ SETUP / ACCESS   │
          └────────┬─────────┘
                   │
                   ▼
          ┌──────────────────┐
          │ UART Registers   │
          │                  │
          │ Control          │
          │ Status           │
          │ TX Data          │
          │ RX Data          │
          │ Baud Control     │
          └───────┬──────────┘
                  │
          ┌───────┴────────┐
          ▼                ▼
   ┌──────────────┐ ┌──────────────┐
   │ UART         │ │ UART         │
   │ Transmitter  │ │ Receiver     │
   └──────┬───────┘ └──────┬───────┘
          │                │
         TX               RX
UART Configuration

The UART uses the following frame format:

8 Data Bits
No Parity
1 Stop Bit

8-N-1

A typical UART frame consists of:

Idle → Start Bit → 8 Data Bits → Stop Bit → Idle
AMBA APB Interface

The UART is controlled through an AMBA APB3 slave interface.

APB transactions consist of two main phases:

SETUP Phase
PSEL  = 1
PENABLE = 0

The address and control signals are presented to the peripheral.

ACCESS Phase
PSEL    = 1
PENABLE = 1

The actual read or write transaction takes place.

For a write transaction:

PWRITE = 1
PWDATA = Write Data

For a read transaction:

PWRITE = 0
PRDATA = Read Data
UART Transmitter

The transmitter converts parallel data into a serial UART stream.

Parallel Data
     │
     ▼
TX Register
     │
     ▼
Start Bit
     │
     ▼
8 Data Bits
     │
     ▼
Stop Bit
     │
     ▼
Serial TX Output
UART Receiver

The receiver samples the serial input and reconstructs the received byte.

Serial RX Input
       │
       ▼
Start Detection
       │
       ▼
Data Sampling
       │
       ▼
8-bit Data
       │
       ▼
RX Register
Design Components

The RTL design consists of modules responsible for:

APB interface handling
APB read/write transactions
UART transmission
UART reception
Baud-rate generation
Control and status registers
TX/RX data registers
Serial data handling
Verification

The design is verified using SystemVerilog-based verification components.

The verification environment checks:

APB read transactions
APB write transactions
UART transmission
UART reception
Register access
UART frame format
Reset behavior
Control and status functionality
Boundary and corner cases
SystemVerilog Assertions

SystemVerilog Assertions are used to verify protocol and design properties.

Examples of properties that can be checked include:

Correct APB transaction sequencing
Valid APB control signals
Correct UART start-bit behavior
Correct UART stop-bit behavior
Valid state transitions
Correct reset behavior
Functional Coverage

Functional coverage is used to measure whether important scenarios have been exercised during simulation.

Coverage areas include:

APB read/write operations
UART transmission scenarios
UART reception scenarios
Register accesses
UART states
Corner cases
Protocol conditions
Verification Flow
Test Case
    │
    ▼
SystemVerilog Testbench
    │
    ├──────────────► APB Transactions
    │
    ├──────────────► UART Stimulus
    │
    ▼
     DUT
    │
    ├──────────────► Assertions
    │
    ├──────────────► Functional Coverage
    │
    ▼
Simulation Results
Project Structure
UART-APB-Verification/
│
├── docs/
│
├── rtl/
│   └── UART and APB RTL modules
│
├── tb/
│   └── Basic testbench
│
├── tb_sv/
│   └── SystemVerilog verification environment
│
├── waveforms/
│   └── Simulation waveforms
│
├── .gitignore
│
└── README.md
Technologies
Verilog HDL
SystemVerilog
AMBA APB3
UART
SystemVerilog Assertions (SVA)
Functional Coverage
RTL Design
Digital Design
Simulation
Git/GitHub
Learning Outcomes

This project provides practical experience with:

RTL design of communication peripherals
AMBA APB protocol
UART protocol
Memory-mapped peripheral design
SystemVerilog verification
Assertion-based verification
Functional coverage
Simulation and waveform analysis
Hardware interface design
Future Improvements
Add configurable baud-rate control
Add interrupt support
Add FIFO buffers
Extend APB register map
Add constrained-random verification
Improve functional coverage
Develop a complete UVM-based verification environment
FPGA hardware implementation
Author

Raj Vishwakarma

B.Tech – Electronics & Communication Engineering
National Institute of Technology Andhra Pradesh
