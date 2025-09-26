
#  DAY 1

## Introduction to Verilog RTL design and Synthesis

## Contents
- [Commands](## Commands)
### **Tool Check**

## Commands
### iverilog
```bash
$ iverilog good_mux.v tb_good_mux.v
```
### To generate the VCD file 
```bash
$ ./a.out
```
### Wave Analysis using GTKWave
```bash
$ gtkwave tb_good_mux.vcd
```

## Design MUX 2:1 

### Design
-The 2:1 Mux was implemented using behavioral Verilog with inputs i0, i1, sel and output y
![2*1-MUX-Verilog](Day1/mux_2_1_verilog.png)

### Testbench 
-Instantiates the good_mux module and applies stimulus through internal registers i0, i1, and sel.
-Generates a VCD waveform file using $dumpfile and $dumpvars for output signal observation via gtkwave.
![2*1-MUX-Testbench](Day1/mux_2_1_tb.png)

## Yosys Synthesis Flow for 2_1_mux
### Yosys Commands
Step 0: Invoke Yosys
```bash
$ yosys
```
Step 1: Read liberty file - You are reading the Liberty file for the Sky130 standard cells, which is necessary for mapping the synthesized netlist to specific technology cells.

```bash
$ read_liberty -lib ~/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Step 2: Read RTL Verilog - You are reading the Verilog file that contains your RTL design. You should see the message "Successfully finished verilog frontend" if the file is read correctly.
```bash
$ read_verilog good_mux.v
```
Step 3: Synthesize the top-level module - You are synthesizing the top-level module, which converts the RTL design into a technology-independent netlist.
```bash
$ synth -top good_mux
```
Step 4: Map synthesized RTL to standard cells - You are mapping the synthesized netlist to the standard cells defined in the Liberty file, creating a technology-dependent netlist.
```bash
$ abc -liberty ~/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Step 5: View synthesized netlist as a schematic - You can view the synthesized netlist as a schematic, which provides a graphical representation of the logic realized by the tool.
```bash
$ show
```
Step 6: Write the synthesized gate-level netlist - You are writing the synthesized gate-level netlist to a Verilog file, excluding attributes to make it simpler and easier to read.
```bash
write_verilog -noattr good_mux_netlist.v
```
![Cells](Day1/2_1_MUX.png)
![2*1 MUX Design](Day1/2_1_MUX_design.png)