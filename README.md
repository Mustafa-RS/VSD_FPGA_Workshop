# VSD_FPGA_Workshop
FPGA - Fabric, Design and Architecture Workshop by VSD-IAT

## Table of Contents

- [Day 1](#day-1)
  1. [Introduction to FPGA](#introduction-to-fpga)
  2. [Counter example using Vivado](#counter-example-using-vivado)
  3. [Counter Verilog explanation and implementation using Vivado](#counter-verilog-explanation-and-implementation-using-vivado)
  4. [Vivado timing power and area measurement for counter](#vivado-timing-power-and-area-measurement-for-counter)
  5. [Introduction to VIO](#introduction-to-vio)
    + [Sub-sub-heading](#sub-sub-heading)
- [Day 2](#day-2)
  1. [Introduction to OpenFPGA and VTR (verilog-to-routing)](#introduction-to-openfpga-and-vtr-verilog-to-routing)
  2. [Introduction to VPR (versatile-place-and-route) using basic Earch fabric](#introduction-to-vpr-versatile-place-and-route-using-basic-earch-fabric)
  3. [Counter example using VPR/VTR openfpga flow](#counter-example-using-vpr-and-vtr-openfpga-flow)
    + [Sub-sub-heading](#sub-sub-heading-1)
- [Day 3](#day-3)
  1. [Introduction to basic RISC-V core – rvmyth](#introduction-to-basic-risc-v-core-rvmyth)
  2. [Rvmyth – Vivado RTL to synthesis flow](#rvmyth-vivado-rtl-to-synthesis-flow)
  3. [Rvmyth – Vivado Synthesis to bitstream](#rvmyth-vivado-synthesis-to-bitstream)
    + [Sub-sub-heading](#sub-sub-heading-2)
- [Day 4](#day-4)
  1. [Introduction to opensource SOFA FPGA fabric](#introduction-to-opensource-sofa-fpga-fabric)
  2. [Steps to run counter example on SOFA](#steps-to-run-counter-example-on-sofa)
  3. [Characterize counter example in terms of area and timing](#characterize-counter-example-in-terms-of-area-and-timing)
  4. [Post-implementation netlist and simulation using SOFA](#post-implementation-netlist-and-simulation-using-sofa)
    + [Sub-sub-heading](#sub-sub-heading-2)
- [Day 5](#day-5)
  1. [Steps to run RISC-V Core - on SOFA](#steps-to-run-risc-v-core-on-sofa)
  2. [Characterize RVmyth in terms of performance and area](#characterize-rvmyth-in-terms-of-performance-and-area)
  3. [Steps to generate rvmyth post implementation netlist](#steps-to-generate-rvmyth-post-implementation-netlist)
  4. [Confirm RVmyth on SOFA behavioral simulation using Vivado](#confirm-rvmyth-on-sofa-behavioral-simulation-using-vivado)
    + [Sub-sub-heading](#sub-sub-heading-2)

## Day 1

This is an h1 heading

### Introduction to FPGA

History of programmable logic

- PLA: had arrays of logic & gates that could be programmed
- CPLD (few gates than FPGA)
- FPGA: Contains several large components which can be programmed

The idea behind these devices was to program & re-program digital logic circuits. To create CUSTOMIZEABLE Hardware. And to study the area, speed & power of the circuits we design. 

An FPGA is an IC which can be designed & configured by a user. In an ASIC you can design and manufacturing it once, but in FPGA you can keep redesigning. 

FPGA configuration is specified by an an RTL or HDL (Verilog or VHDL)

The way it gets programmed is quite different from ASIC. It uses LUTs, FLip-flops & configurable logic blocks.

ASIC VS FPGA

ASIC is application specific e.g. processor
RTL -> Layout -> Sent to foundry for fabrication
I cannot be reprogrammed

FPGA is reprogrammable
Design -> RTL -> bitstream (configuration an FPGA understands. runs on FPGA)


Applications of FPGA
- Hardware acceleration
- DSP
- Device controller
- Embedded Systems
- ML 
- High performance computing
- Aerospace

FPGA Architecture

Unlike on ASIC, where if we want to program an ALU for instance, we use logic gates (AND/OR/NOR) and then the gate design is converted to transistor level design to create the real circuit in fabrication. The result is the ASIC.

FPGA has existing logic! we just configure it!
It consists of configurable logic blocks (CLBs) 

CLBs contain a set of LUTs either 4 or 6 inputs, then a set of carry chain, set of MUXs or just 1, and then set of flip-flops. Each FPGAs CLB could have its own unique CLB architecture. 

Using a Xilinx toolchain for instance, you would be able to program your ALU design on Verilog & it would be converted by the toolchain to convert to the Xilinx FPGA's specific CLB architecture. 

Programmable interconnects join the CLBs together & we also have programmable I/O which can be used by the user to send a 1 or 0. using button/switch or electric current. like we did in Digital Logic Class with switches. 

User will define a design then it is sythesized and converted to bitstream. It is stored in the configuration memory, and every time we turn the FPGA on, it will program the bitstream to run on the CLBs. Bitstream defines the behavior of the design. It connects CLBs, interconnects, inputs/outputs. 

FPGAs also have Block RAM, Clock tiles, DSP blocks, multiplier blocks which can also be used to design/enhance our design

### Counter example using Vivado

Vivado Counter 

Vivado-Verilog explanation

We start with a 4 bit up counter. It will be mapped to 4 LEDs. 

Let's launch vivado, -/vivado

On vivado when a file shows 3 dots, that means it's the top module!

Now we are ready to run;
 - Simulation
 - Elaboration
 - Synthesis
 - Implementation



Vivado map pins

Vivado lets us choose pins and autimatically creates the constraints file. 

<see pic for reference>

Theory slack



Vivado Synthesis

Click run synthesis, then max number of jobs that will run at the same time. then hit okay. 

Once synthesis is completed, let's open the synthesized design. We get the following reports
- timing summary 
- clock networks
- power
- etc. 

the Timing summary says, "No timing constraints.." because we didnt set clk frequency or delays in the constraints file!!


Constraints to bitstream

We can set constraints using constrants wizard, it will autimatically show name of clock pin, says its undefined.

We click undefned and replace it with 100MHz. 

On the bottom it will show the respctive command for this. It adds this command to the constraints file, we can see it in the text editor window. 

We now RE-run synthesis, now the timing summary shows the that the timing constraints are met!!

Implementation step, when com

Generate bitsream, when its done it will say bitsream gen is complete. 


Vivado timing


Vivado slack, power, area


Vivado summary

### Counter Verilog explanation and implementation using Vivado

### Vivado timing, power, and area measurement for counter

### Introduction to VIO

#### Sub-sub-heading

This is an h3 heading

## Day 2

This is an h1 heading

### Introduction to OpenFPGA and VTR verilog-to-routing

This is an h2 heading

### Introduction to VPR versatile-place-and-route using basic Earch fabric

This is an h3 heading

### Counter example using VPR and VTR openfpga flow

## Day 3

This is an h1 heading

### Introduction to basic RISC-V core rvmyth

This is an h2 heading

### Rvmyth Vivado RTL to synthesis flow

This is an h3 heading

### Rvmyth Vivado Synthesis to bitstream

## Day 4

This is an h1 heading

### Introduction to opensource SOFA FPGA fabric

This is an h2 heading

### Steps to run counter example on SOFA

This is an h3 heading

### Characterize counter example in terms of area and timing

### Post implementation netlist and simulation using SOFA

## Day 5

This is an h1 heading

### Steps to run RISC V Core on SOFA

This is an h2 heading

### Characterize RVmyth in terms of performance and area

This is an h3 heading

### Steps to generate rvmyth post implementation netlist

### Confirm RVmyth on SOFA behavioral simulation using Vivado

## Table of Contents

### Day 1
1. Introduction to FPGA
2. Counter example using Vivado
3. Counter Verilog explanation and implementation using Vivado
4. Vivado timing, power, and area measurement for counter
5. Introduction to VIO

### Day 2: 
1. Introduction to OpenFPGA and VTR (verilog-to-routing)
2. Introduction to VPR (versatile-place-and-route) using basic Earch fabric
3. Counter example using VPR/VTR openfpga flow

### Day 3:
1. Introduction to basic RISC-V core – rvmyth
2. Rvmyth – Vivado RTL to synthesis flow
3. Rvmyth – Vivado Synthesis to bitstream

### Day 4:
1. Introduction to opensource SOFA FPGA fabric
2. Steps to run counter example on SOFA
3. Characterize counter example in terms of area and timing
4. Post-implementation netlist and simulation using SOFA

### Day 5:
1. Steps to run RISC-V Core - on SOFA
2. Characterize RVmyth in terms of performance and area
3. Steps to generate rvmyth post implementation netlist
4. Confirm RVmyth on SOFA behavioral simulation using Vivado
