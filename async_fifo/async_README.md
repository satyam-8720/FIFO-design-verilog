# Asynchronous FIFO

## Overview
An **Asynchronous FIFO** enables safe data transfer between two independent clock domains:
- Write clock domain (`wclk`)
- Read clock domain (`rclk`)

Since the clocks are asynchronous, special techniques are required to prevent metastability and ensure correct FIFO operation.

---

## Design Challenges

- Clock Domain Crossing (CDC)
- Safe full and empty detection
- Pointer synchronization
- Preventing data corruption

---

## Architecture

The asynchronous FIFO design uses:

- Binary pointers for memory addressing
- Gray-coded pointers for cross-domain transfer
- Two-flip-flop synchronizers for CDC safety
- Separate write and read control logic

---

## Block Diagram

The following block diagram illustrates the high-level architecture of an
asynchronous FIFO. Write and read operations are controlled by independent
clock domains, requiring clock domain crossing (CDC) handling for safe data
transfer.

The design uses binary read/write pointers for memory addressing, Gray-coded
pointers for cross-domain synchronization, and dual flip-flop synchronizers to
mitigate metastability.

![Asynchronous FIFO Block Diagram](images/async_fifo_block_diagram.png)

*Note: This diagram is used for conceptual understanding of asynchronous FIFO
operation. The RTL implementation in this repository follows the same logical
structure.*


## Pointer Management

### Binary Pointer
- Used locally in each clock domain
- Provides FIFO memory addressing

### Gray Pointer
- Generated from binary pointer
- Only one bit changes per increment
- Safe to synchronize across clock domains

---

## Full Condition Detection

FIFO is **full** when the next write Gray pointer equals the synchronized read Gray pointer with its two MSBs inverted.

This technique safely detects pointer wrap-around without comparing unsynchronized binary values.

---

## Empty Condition Detection

FIFO is **empty** when the next read Gray pointer equals the synchronized write Gray pointer.

---

## Clock Domain Crossing Strategy

- Write pointer is synchronized into the read clock domain
- Read pointer is synchronized into the write clock domain
- Two-stage flip-flop synchronizers reduce metastability risk

---

## Memory Operation

- Write operation occurs on `wclk` when `w_en && !full`
- Read operation occurs on `rclk` when `r_en && !empty`
- Data order is strictly preserved

---

## Verification

- Independent write and read clocks
- Randomized read/write enable patterns
- Scoreboard-based data comparison
- Detection of overflow and underflow scenarios

---

## Limitations

- Read latency of at least one read clock cycle
- No built-in flow control beyond full/empty flags
- Intended for educational and experimental use

---
