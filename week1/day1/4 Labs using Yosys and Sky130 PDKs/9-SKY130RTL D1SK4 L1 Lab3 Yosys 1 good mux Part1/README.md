---

# Yosys Synthesis Workflow for Sky130 RTL Design

## Introduction

In this guide, we walk through the steps involved in synthesizing a Verilog design using **Yosys** for the **Sky130** process library. We will focus on a Verilog file (`good_mux.v`) and its testbench, and outline the differences that can arise when using different versions of Yosys.

## Prerequisites

Ensure that you have the following installed and available:

* **Yosys** for synthesis
* **Sky130 process library** (`sky130_fd_sc_hd__tt_025C_1v80.lib`)
* **Verilog source files** (e.g., `good_mux.v`)
* **Testbenches** for verification

## Steps to Synthesize

### 1. Clone the Git Repository

Start by cloning the repository containing the RTL design:

```bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop
```

This repository contains the Verilog files, including `mux` files and corresponding testbenches.

### 2. Navigate to the Verilog Directory

Go to the directory containing the Verilog files:

```bash
cd sky130RTLDesignAndSynthesisWorkshop
```

### 3. Invoke Yosys for Synthesis

Run Yosys, the open-source synthesis tool, to process the design.

```bash
yosys
```

Absolutely — here’s a much more **detailed and expanded explanation** of steps 4 through 8 in the context of using **Yosys** and the **Sky130 Liberty library** for RTL synthesis. This version adds deeper context to what each command does and why it’s important.

---

### 4. Read the Liberty Library

```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

The Liberty file (`.lib`) contains the **standard cell definitions** used for technology-mapped synthesis. It describes the **timing**, **power**, **area**, and **functionality** of logic gates in the target technology — in this case, the **Sky130** process.

By loading this file, you tell Yosys:

* What standard cells are available (e.g., NAND, NOR, MUX, INV, etc.)
* How fast these cells are
* How much power they consume
* What logical functions they perform

This step is crucial because, during technology mapping (which happens later), Yosys needs to replace your generic logic with specific gates from this `.lib` file.

> 🔍 **Note:** The `-lib` flag indicates that this is a library file to be used for mapping during synthesis, not a functional model for simulation.

---

### 5. Read the Verilog File

```bash
read_verilog good_mux.v
```

This command loads your **RTL design** into Yosys — in this case, a file named `good_mux.v`, which presumably defines a **2:1 multiplexer**.

What this does:

* Parses the Verilog source code
* Builds an **internal representation** (netlist or dataflow graph) of your design
* Prepares it for synthesis and optimization

You can load multiple Verilog files if your design is split across several modules.

> 🛠️ If your Verilog code contains syntax errors or unsupported constructs, Yosys will throw an error here.

---

### 6. Synthesize the Design

```bash
synth -top good_mux
```

This is the main synthesis step. Here's what happens internally:

* Yosys identifies `good_mux` as the **top-level module**
* It converts your RTL (register-transfer level) code into a **gate-level representation**
* Performs **optimizations** like:

  * Constant propagation
  * Dead-code elimination
  * Expression simplification
  * Resource sharing
* Converts the design into a technology-independent netlist
* Prepares the design for technology mapping

This step does **not yet map** your logic to actual standard cells (like NAND, MUX, etc.) — that comes next in the ABC step.

> ⚠️ If you forget to specify `-top`, Yosys might choose the top module automatically, which could be incorrect if your project has testbenches or helper modules.

<img width="1174" height="610" alt="Screenshot From 2025-09-24 12-11-08" src="https://github.com/user-attachments/assets/c5fe6675-5706-4631-be55-a89076344218" />

---

### 7. Perform ABC Optimization

```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

This is where **technology mapping** happens.

**ABC** (A System for Sequential Synthesis and Verification) is a backend tool Yosys uses to:

* Map the technology-independent logic to **actual standard cells** from your `.lib` file
* Optimize the netlist for:

  * **Timing** (faster logic paths)
  * **Area** (smaller number of gates)
  * **Power** (lower consumption, though limited in ABC)
* Apply logic restructuring to improve performance

After this step, your netlist will consist **only** of cells defined in the Sky130 Liberty file — no more generic logic.

> 🧠 The quality of this step heavily depends on your Liberty file — different libraries will lead to different synthesized designs.

<img width="1175" height="619" alt="Screenshot From 2025-09-24 12-11-48" src="https://github.com/user-attachments/assets/a207454a-9c31-441d-8df6-56d5121f4e3d" />

---

### 8. Visualize the Logic

```bash
show
```

After synthesis and mapping, this command opens a **graphical view** (via `yosys-svgviewer` or GTK) showing:

* Logic gates
* Interconnections (wires)
* Hierarchy and module structure

This visual output is helpful to:

* **Debug** unexpected logic structures
* **Verify** that synthesis preserved your intended behavior
* **Understand** how your design was mapped to real gates

> 🖼️ If the `show` command doesn’t work, you might need to install additional tools like Graphviz or GTK viewer. You can also output to a file using:

```bash
write_svg output.svg
```

<img width="1522" height="488" alt="Screenshot From 2025-09-24 11-11-09" src="https://github.com/user-attachments/assets/33ff675a-4923-454d-9657-bdfa939d1be3" />

---

### Summary of Flow:

| Step | Command               | Purpose                                                       |
| ---- | --------------------- | ------------------------------------------------------------- |
| 4    | `read_liberty`        | Load standard cell definitions (timing, power, functionality) |
| 5    | `read_verilog`        | Load your RTL design into Yosys                               |
| 6    | `synth -top <module>` | Convert RTL to gate-level, optimize generically               |
| 7    | `abc -liberty`        | Map logic to actual technology cells using optimization       |
| 8    | `show`                | Visualize the post-synthesis logic netlist                    |

---



## Version Differences

There is a key difference between the version of Yosys I am using and the one in the tutorial. The instructor uses an older version of Yosys, where several cells such as `nand 2_1`, `clkinv_1`, `o2lai_0`, and `buf` are used.

In my case, I only observe a single cell type: `mux2_1`. This difference is due to the changes in the latest version of Yosys, which likely introduces optimizations or different cell mappings compared to the version used by the instructor.

## Conclusion

This workflow helps you synthesize a simple Verilog design using Yosys with the Sky130 process library. Be mindful of version differences, as they may impact the cells and optimizations used during synthesis.

---
