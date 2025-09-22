# Running the Sky130 RTL Design and Synthesis Workshop Simulation

In this guide, we will walk through the steps to run a simulation for the **good_mux** Verilog module using **Iverilog** and **GTKWave**.

## Step 1: Navigate to the Repository Folder

First, move into the `sky130RTLDesignAndSynthesisWorkshop` directory that you cloned earlier.

```bash
cd sky130RTLDesignAndSynthesisWorkshop  # Navigate to the workshop directory
````

## Step 2: Enter the Verilog Files Folder

Now, go into the folder where the Verilog files are located:

```bash
cd verilog_files  # Change to the 'verilog_files' directory
```

## Step 3: List the Files

Use the `ls` command to list the contents of the directory. You should see the following files:

```bash
ls  # List files inside the directory
```

You should find:

* `good_mux.v` (the Verilog module)
* `tb_good_mux.v` (the testbench for the module)

## Step 4: Compile the Verilog Files Using Iverilog

Now, compile both the `good_mux.v` and `tb_good_mux.v` files using **Iverilog**:

```bash
iverilog good_mux.v tb_good_mux.v  # Compile the Verilog files
```
<img width="898" height="211" alt="Screenshot from 2025-09-22 06-28-15" src="https://github.com/user-attachments/assets/bcd07c8c-0111-497e-866f-c0c102ce3913" />

This will create an executable file named `a.out` in the same directory.

## Step 5: Run the Simulation

Execute the compiled file to run the simulation:

```bash
./a.out  # Run the simulation
```

This will generate a new file called **tb\_good\_mux.vcd**, which contains the simulation waveform data.

## Step 6: Visualize the Waveform Using GTKWave

To view the waveform, use **GTKWave** to open the generated VCD file:

```bash
gtkwave tb_good_mux.vcd  # Open the waveform in GTKWave
```

## Step 7: Drag and Drop Waveform Inputs

In GTKWave, you will see a blank waveform window. Now, **drag and drop** the signals or inputs from the list of available signals on the left-hand side to the waveform display area.

<img width="1567" height="645" alt="Screenshot from 2025-09-22 06-29-21" src="https://github.com/user-attachments/assets/5e4f6c08-1a8a-404f-81ab-45a245dea103" />

This will display the simulation results for your `good_mux` module, allowing you to visually inspect the signal transitions.

---
