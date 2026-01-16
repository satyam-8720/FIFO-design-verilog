# Synchronous FIFO

## Overview
A **Synchronous FIFO** operates with a single clock for both read and write operations.

Because there is no clock domain crossing, the design is simpler, faster, and easier to verify than an asynchronous FIFO.

---

## Key Characteristics

- Single clock domain
- No synchronizers required
- Simple pointer comparison
- Lower latency compared to async FIFO

---

## Architecture

The synchronous FIFO consists of:
- FIFO memory array
- Read pointer
- Write pointer
- Full and empty detection logic

Both pointers are updated on the same clock edge.

---

## Full Condition Detection

FIFO is **full** when the write pointer catches up to the read pointer with wrap-around consideration.

Typically implemented using:
- Extra MSB in pointers
- Binary comparison logic

---

## Empty Condition Detection

FIFO is **empty** when:   write_pointer == read_pointer

---

## Memory Operation

- Read and write operations occur on the same clock
- Supports simultaneous read and write
- Data throughput is deterministic

---

## Advantages Over Asynchronous FIFO

| Feature | Synchronous FIFO | Asynchronous FIFO |
|------|------------------|-------------------|
| CDC handling | Not required | Required |
| Complexity | Low | High |
| Latency | Low | Higher |
| Debug difficulty | Easy | Hard |

---

## When to Use a Synchronous FIFO

- All modules share the same clock
- CDC must be avoided
- Simplicity and performance are priorities

---

## Project Scope

- Implement a basic synchronous FIFO
- Compare behavior with asynchronous FIFO
- Understand design trade-offs

---
