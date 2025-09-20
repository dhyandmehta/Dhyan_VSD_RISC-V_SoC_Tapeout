
# 🚀 My RISC-V SoC Tapeout Journey | VLSI System Design

Welcome to my **RISC-V SoC Tapeout Program** adventure! This repository chronicles my journey through each step of the program, from setting up the tools to working on advanced **System-on-Chip (SoC)** designs. As I progress, I’ll document my learnings, experiences, and challenges. Stay tuned for updates as I work towards mastering the world of **open-source SoC design**!  

---

### 🌱 What is This Program?

The **RISC-V SoC Tapeout Program** aims to empower engineers and enthusiasts to design and implement their own System-on-Chip (SoC) using the **RISC-V** architecture. This collaborative initiative is part of **India’s largest RISC-V tapeout effort**, involving **3500+ participants**. Together, we’re building the future of silicon in India.

In this program, we will explore the following:
- **RTL design**: Writing and simulating hardware designs.
- **Synthesis**: Converting RTL to gate-level descriptions.
- **Verification**: Ensuring the designs work correctly.
- **Tapeout**: Preparing the design for silicon manufacturing.

---

## 🛠️ Week 0 - Environment Setup & Tool Installation

Week 0 was all about preparing the development environment. I successfully installed the essential **EDA tools** that will be used throughout the program. This includes **Yosys**, **Iverilog**, and **GTKWave**.

### 🔧 Tools Installed:

- **Yosys**: Open-source synthesis tool for Verilog designs.
- **Iverilog**: A simulator for Verilog HDL (Hardware Description Language).
- **GTKWave**: A waveform viewer to visualize simulation results.

---

### ✅ Installation Process

#### **Step 1**: Install Dependencies
We started by updating our system and ensuring that all necessary libraries and tools were available.

```bash
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
````

#### **Step 2**: Installing Yosys

Yosys is a versatile synthesis tool that converts RTL designs to gate-level netlists. Here’s how I installed it:

```bash
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make               # Install make if not present
sudo apt-get install build-essential clang bison flex \
libreadline-dev gawk tcl-dev libffi-dev git \
graphviz xdot pkg-config python3 libboost-system-dev \
libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
git submodule update --init --recursive
make
sudo make install
```

#### **Step 3**: Installing Iverilog

Iverilog is used to compile and simulate Verilog code. Installing it was as easy as running:

```bash
sudo apt-get install iverilog
```

#### **Step 4**: Installing GTKWave

GTKWave is a waveform viewer for visualizing simulation outputs from Iverilog. To install it:

```bash
sudo apt install gtkwave
```

---

Stay tuned for detailed weekly updates, as I’ll be documenting every step of the way!


---

## 📊 Progress Tracker

Each week, I will update this section with the progress made. Here’s a quick look at my journey so far:

| Week       | Task                                  | Status        |
| ---------- | ------------------------------------- | ------------- |
| **Week 0** | Environment Setup & Tool Installation | ✅ Completed   |
| **Week 1** | -         | - |

---

Stay tuned for detailed weekly updates, as I’ll be documenting every step of the way!

---

## 🔗 Connect With Me

Feel free to reach out or follow along as I continue this exciting learning journey.


* [LinkedIn](https://in.linkedin.com/in/dhyan-mehta-7695912b3)

---

> **"The future of computing lies in open-source hardware. Let's build it together!"** 💡
