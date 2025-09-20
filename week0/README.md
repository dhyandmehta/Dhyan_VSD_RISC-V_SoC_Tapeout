# RISC-V Reference SoC Tapeout Program - VSD

## Installation of Required Tools

### **System Prerequisites**

Before you begin, ensure that your system meets the following requirements:

* **Memory**: 6/8 GB RAM
* **Disk**: 50 GB HDD
* **OS**: Ubuntu 20.04 or later
* **CPU**: 4/5 vCPUs

### **Adjusting the Ubuntu Window Size**

To make sure the display is appropriately sized, execute the following steps:

```bash
$ sudo apt update
$ sudo apt install build-essential dkms linux-headers-$(uname -r)
$ cd /media/spatha/VBox_GAs_7.1.8/
$ ./autorun.sh
```

### **Tool Installation and Verification**

#### **Yosys**

To install Yosys, follow these steps:

```bash
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make                 # Install make if it’s not already present
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ git submodule update --init
$ make
$ sudo make install
```
<img width="807" height="189" alt="yosys" src="https://github.com/user-attachments/assets/4e30528d-1b6b-4b33-8796-c6f77c0a6060" />

---

#### **Iverilog**

For installing Iverilog, use the following commands:

```bash
$ sudo apt-get update
$ sudo apt-get install iverilog
```
<img width="813" height="687" alt="iverilog" src="https://github.com/user-attachments/assets/a7380bb8-06ab-4bf9-b7f4-a42805ac9c34" />

---

#### **GTkwave**

To install GTkwave, run:

```bash
$ sudo apt-get update
$ sudo apt install gtkwave
```
<img width="452" height="84" alt="gtkwave" src="https://github.com/user-attachments/assets/ff508f3d-5fa7-41dd-8a57-9b8bdb83835c" />

---

This should give you a clean, structured installation process for all the necessary tools in the RISC-V SoC Tapeout Program. Once you've followed the above steps, you should be all set to continue with the rest of the course tasks.
