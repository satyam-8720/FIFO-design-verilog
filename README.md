# FIFO Design Project (Synchronous & Asynchronous)

## Overview
This repository contains the implementation and verification of **FIFO (First-In First-Out)** buffers, focusing on both **Synchronous FIFO** and **Asynchronous FIFO** designs.

FIFO buffers are widely used in digital systems to:
- Buffer data between modules
- Handle data rate mismatches
- Decouple producer and consumer logic
- Enable safe data transfer across clock domains

---

## Types of FIFO Implemented

### 1. Synchronous FIFO
- Single clock for read and write
- Simple control logic
- No clock domain crossing (CDC) issues
- Lower latency and easier verification

### 2. Asynchronous FIFO
- Separate clocks for write and read
- Requires CDC-safe design
- Uses Gray-coded pointers and synchronizers
- Suitable for multi-clock systems

---

## Key FIFO Signals

| Signal | Description |
|------|------------|
| `w_en` | Write enable |
| `r_en` | Read enable |
| `data_in` | Input data |
| `data_out` | Output data |
| `full` | FIFO full indicator |
| `empty` | FIFO empty indicator |

---

## Project Objectives

- Understand FIFO fundamentals
- Study differences between synchronous and asynchronous FIFOs
- Implement pointer-based FIFO control
- Learn CDC-safe techniques for async FIFOs
- Verify designs using SystemVerilog testbenches

---


## Repository Structure
.
├── synchronous_fifo/
│ ├── README.md
│ ├── rtl/
│ └── testbench/
├── asynchronous_fifo/
│ ├── README.md
│ ├── rtl/
│ └── testbench/
└── README.md

---

## Notes

- The asynchronous FIFO design follows standard industry concepts
  (binary pointers, Gray code conversion, pointer synchronization).
- Testbenches are written for functional verification only.


