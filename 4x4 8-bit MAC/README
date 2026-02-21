# 4×4 MAC Accelerator Design Project

## Project Overview

This project implements a 4×4 MAC (Multiply-Accumulate) array hardware accelerator using SystemVerilog. Compared to the 2×2 version, this design supports internal matrix buffering, FSM-controlled N-cycle accumulation, and register-mapped output readback.

MAC units are fundamental building blocks in digital signal processing and AI accelerators, especially for matrix multiplication and neural network inference engines.

---

## What is a MAC?

A MAC performs the following operation:

**accumulator = accumulator + (A × B)**

This operation is the foundation of matrix multiplication, convolutional neural networks, digital filters (FIR/IIR), and many signal processing pipelines. In hardware accelerators, MAC units enable high-throughput parallel computation.

In this design:

- Inputs are **signed 8-bit integers**
- Accumulation is performed using **signed 32-bit precision**

---

## Design Architecture

The design follows a **hierarchical and modular architecture**.

### 1. Basic MAC Unit (`mac_unit`)

- Accepts two signed 8-bit inputs (`a` and `b`)
- Computes signed multiplication (8×8 → 16-bit)
- Accumulates into a signed 32-bit accumulator
- Performs sign extension before accumulation
- Fully synthesizable combinational MAC block
Precision path:
int8 × int8 → 16-bit product → 32-bit accumulation

### 2. Controller FSM (`controller_fsm`)

- Controls N-cycle accumulation
- Generates `k_index` (0 to 3)
- Implements state transitions:
IDLE → LOAD → CLEAR → SETUP → COMPUTE → DONE

