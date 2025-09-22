# Iverilog Based Simulation Flow

The Iverilog simulation flow is a simple yet effective process for digital design verification. Below is the step-by-step workflow:

## 1. Provide Design and Testbench to Iverilog

- We start by providing both the **design** (the Verilog code you want to simulate) and the **testbench** (the test code used to apply inputs to the design) to **Iverilog**.

## 2. Generate Value Change Dump (VCD) File

- Iverilog compiles and simulates the design, and then generates a **Value Change Dump (VCD)** file. This file contains the simulation results, recording all the signal transitions over time.

## 3. Load VCD into GTKWave

- The generated VCD file is then fed into **GTKWave**, a waveform viewer.

## 4. Visualize the Waveform

- GTKWave opens the VCD file, and you can now visually inspect the **waveform** that represents the behavior of your design over time. It provides valuable insights into timing and signal values throughout the simulation.

---

### Tools Used:

- **Iverilog**: Open-source Verilog simulation tool.
- **GTKWave**: Open-source waveform viewer for analyzing simulation results.
