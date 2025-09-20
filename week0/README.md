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

---

#### **Iverilog**

For installing Iverilog, use the following commands:

```bash
$ sudo apt-get update
$ sudo apt-get install iverilog
```

---

#### **GTkwave**

To install GTkwave, run:

```bash
$ sudo apt-get update
$ sudo apt install gtkwave
```

---

This should give you a clean, structured installation process for all the necessary tools in the RISC-V SoC Tapeout Program. Once you've followed the above steps, you should be all set to continue with the rest of the course tasks.
