---

# 🧠 Good MUX Netlist

This repository contains a Verilog netlist for a multiplexer (MUX) circuit that has been synthesized and exported using Synopsys Design Compiler.

The process demonstrates how to extract a clean netlist from a synthesized design and view or edit it using a text editor.

---

## 📌 In this example:

* We’ve synthesized a MUX design using Synopsys Design Compiler.
* We then exported the synthesized gate-level design as a Verilog netlist.
* Finally, we opened it using a text editor (`gvim`) to verify or manually inspect the generated logic.

---

## 🔧 Step-by-Step: How the Netlist Was Generated

### 1️⃣ Run Yosys and Synthesize the Design

Inside a terminal, launch `yosys` and run the following command to synthesize your MUX design:

```tcl
write_verilog -noattr good_mux_netlist.v
```

**Explanation:**

* `write_verilog`: Tells Yosys to export the synthesized netlist in Verilog format.
* `-noattr`: Ensures the output file does not include Yosys-specific attributes (like `(* keep *)`, `(* src = ... *)`, etc.), making it cleaner and more portable.
* `good_mux_netlist.v`: The name of the output netlist file.

> ✅ **Tip:** Before running `write_verilog`, make sure you’ve already read, parsed, and synthesized your RTL design inside Yosys. 
---

### 2️⃣ Open the Netlist for Inspection

After generating the netlist, you can open it in a text editor for inspection:

```bash
!gvim good_mux_netlist.v
```
---

<img width="1175" height="619" alt="Screenshot From 2025-09-24 12-14-06" src="https://github.com/user-attachments/assets/1b9f73b4-c4e7-4d5a-89f8-01e067510b53" />

---
## 📁 Files Included

* `good_mux_netlist.v` — This is the gate-level Verilog netlist generated after synthesis. It includes instances of standard cells (e.g., AND, OR, MUX gates) connected to form the MUX logic.
<img width="1521" height="626" alt="Screenshot From 2025-09-24 18-30-50" src="https://github.com/user-attachments/assets/1fbd330f-e21d-454d-a5c7-453d06e1b1ac" />

---

## This file can be used for:

* Formal verification (compare RTL vs gate-level)
* Logic simulation
* Backend flows (e.g., place & route if targeting ASIC or FPGA)

---
