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

PLEASE WRITE 2-3 sentences to sum up the mess below.

### Introduction to OpenFPGA and VTR verilog-to-routing

What is OpenFPGA?? - Xifan's project owned by Uof Utah lol, what really is it though?

Currently there are certain methodologies required to produce FPGA fabric, involves several HW & SW engineers & the design cycle lasts several months. 

Xifan wanted to improve this methodology so that one can produce FPGA fabric without all those resources and in less time. In 24 hours "CUSTOM" FPGA fabric could be designed. 

Why do we need customer FPGAs?
Well for domain-specific applications, there isn't always an off the shelf solution & you might not want to use an ASIC so in this case an FPGA that just about accomplishes your personal application's needs is ideal. It will save money on resources that you will not be using. 

Domain specific applications include 
- DSP
- Video/Image processing 
These applications can be accelerated when using FPGA instead of MCU. 

Producing custom FPGAs are normally costly & time-consuming, that's what makes OpenFPGA so powerful. It has 20+ architecture templates in xml files which are optimized for different applications. In addition OpenFPGA allows users to write their own architecture using the architecture description language based on xml files. 

OpenFPGA uses the xml files to then generate Verilog netlists which will describe the FPGA fabric. It also autimatically generates Verilog testbenches to validate the fabric. (LUTs, Flip-flops, MUXs, etc. CLBs as well all are part of the fabric.)

Lastly OpenFPGA will generate bitsream using the sme xml based description file.

OpenFPGA can generate the following files formats
FPGA-Verilog
FPGA-SDC
FPGA-Bitsream
FPGA-SPICE


We will use RTL and go through VTR flow, 
map design to XML, 
then goes through VPR, which gives us Verilog files
These files go through Fabric generator to output fabric netlists. As well as Testbench generator to output full testbench for validation.

<inset picture for ref>

The XML files allow us to define all parts of an FPGA's fabric, such as CLBs, MUX in the form of code. This archietecuture langauage based on XML allows the user to also design their own architecture to add to the 20+ templates available. (I guess Lex is helping Xifan do that now).

We have to use VTR (Verilog to Routing) in order for the XML files to be translated to FPGA architecture. 

https://docs.verilogtorouting.org/en/latest/quickstart/

VTR Flow:

Consists of 3 different tools

VTR Requires 2 inputs;
1. Verilog File to describe the digital circuit e.g. ALU/Counter/Processor

2. An XML file to describe the target FPGA's architecture. Any one of the 20 templates can be used as an example.

Step 1: Elaborate & Synthesis using Odin II (VTR inbuilt tool)

Step 2: Logic Optimization & technolog mapping to LUTs with the ABC tool developed at UC Berkeley. https://people.eecs.berkeley.edu/~alanmi/abc/

Step 3: Packs the netlist, placement, routing & timing analysis using VPR. It's all automated using scripts. 

Outputs:
1. Post Implementation netlist
2. Key Statistics
- min of of tracks for routing
- wire length
- speed
- power
- area.

To sum it up, the VTR flow maps the RTL design to the FPGA arch to produce a placed-and routed FPGA fabric. 

This very much sounds like how one would design an ASIC, which Eric has said many times. So OpenFPGA is very important for customers who need an ASIC, BUT don't want to build an ASIC for whatever reason.
- Low volume projects don't warrant ASIC fabrication. 
- Want soft IPs implemented
- DSP/Image/video for AI, FPGA is suited. 


VTR flow for US
- Odin II -> ABC ->VPR

producing post implementation matrix, providing area, timing and power requirements. 

How do we run the tool, most of the documentation is found on the VTR readthedocs quickstart guide.
1. Build OpenFPGA
2. Build VTR

1st 
- Try to Run VPR on a Pre-synthesized circuit
- Visualize the result & circuit on GUI

2nd Try to run the entire VTR flow automatically 
- implement our own circuit (blink.v and counter.v) on a pre-existing FPGA arch (Earch.xml located at VTR_rOOT/vtr_flow/arch)
- Use an automated approach (Odin II & ABC are automatically run, along with VPR)
- Lastly Perform timing simulation on the generated fabric. to see it's results (this is from the testbench I'm assuming)

### Introduction to VPR versatile-place-and-route using basic Earch fabric

Running VPR on a pre-sythesized circuit!

Input: 
1. .blif (Technology mapped netlist of a design e.g. a counter)
blif Format is based on model descriptions;
- .inputs
- .outputs
- .latches representing flip-flops used in the design
- .names representing mainly LUTs used in the design

This file is generated by the tool ABC in previous steps within VTR.

2. .xml (FPGA architecture)
- This is tells us what the target FPGA architecture is, our EArtch.xml shows it is a Heterogeneous FPGA, 40nm technology, built with general purpose logic blocks (K=6, N=10): These LUTs can be used as LUT6 by themselves or 2 can combine to form a 2 LUT5s when needed.
- Format is based on <tags>, 
- begins with <architecture>
- followed by <models> All models used will be inside this block (includes ram, combinational circuit, adder, and others) all are built into this particular architecture.
- <tiles> contains all the core FPGA blocks required (I/O, CLB, memory, 
- <layout> The entire FPGA grid layout is specified here
- <device> Shows how the device transistors are being defined. 
- <switchlist> Consists of switch matrix is being described. 
- <segmentlist> routing information
- <directlist> only has adder_carry in our arch
- <complexblocklist> Describes the types of the functional blocks used in our arch.


Output of step 1 - Pack
- .net file
packed netlist format showing post-packed netlist, shows inputs/outputs etc.

Output for step 2 - Placement
- .place file
lists netlist showing the architecture, the blocks, where they are placed & the block specs.

Output of step 3 - Routing
- .route file
Contains the nodes & how they are connected

Once placement & Route is complete, VPR does Analysis in terms of the following Outputs of step 4 - Analysis;
- area reports 
- timing reports - shows the time it takes for the circuit to function & transfer data from input to output. Shows the path the data takes in the circuit. In the end it shows the data required time & data arrival time. (WE MUST create SDC file showing clock time period for this to work) 
- power reports
- post-implementation netlist (has info such a resource useage, block types, wire, delays, power usage by each block)


Running VPR tseng GUI

We can run the same VPR command again, but this time we add a line "--analysis --disp on" (to give us GUI showing only analysis step, it already does pack, place & route before opening GUI for us) or just "--disp on" (opens GUI & lets us see all  all the steps!)

It created an interactive GUI which we can use to visualize the layout, and then also features of the architecture running the design! 

When we do this the terminal does Step 1 - Pack & step 2 - Placement, then is pauses and open the GUI where we can see the FPGA layout.

Options;
- toggle nets: shows the connections being made between the blocks and clicking proceed lets the terminal resume and does step 3 - routing. In this period we see the connections on the layout change rapidly, visualizing the routing process.

Clicking proceed again now shows alot of options for the FPGA.
- toggle nets has different views
- toggle routing resources
- congestion shows the areas that are relatively congested and relatively less congested. 
- Routing utilization shows which structures have routing resources used (close to max and much less than max)
- Block Internal & zooming into a block, shows what has been implemented within each CLB! super details!

Clicking on proceed for the last time closes the window and the terminal now shoes the VPR has been completed. 

### Counter example using VPR and VTR openfpga flow
  
Automatically Running the VTR-flow

Normally VTR starts with Odin, followed by ABC & then lastly ..., instead of running through each of these tools, we use a python script called run_vtr_flow to automate it. 

Works with the VTR example: blink.v - Success
Now let's try the Workshop example: counter.v - Success

Output file
- Odin.blif
- abc.blif
- pre-vpr.blif: This is the one that will be passed for vpr when we do vpr.

We can go ahead and run VPR now using "counter.pre-vpr.blif along with EArch.xml. 

The result works like it did before when we had an existing blif file already to use. 


We can run the same VPR command again, but this time we add a line "--analysis --disp on" (to give us GUI showing only analysis step, it already does pack, place & route before opening GUI for us) or just "--disp on" (opens GUI & lets us see all  all the steps!)

It created an interactive GUI which we can use to visualize the layout, and then also features of the architecture running the design! 

When we do this the terminal does Step 1 - Pack & step 2 - Placement, then is pauses and open the GUI where we can see the FPGA layout.

Options;
- toggle nets: shows the connections being made between the blocks and clicking proceed lets the terminal resume and does step 3 - routing. In this period we see the connections on the layout change rapidly, visualizing the routing process.

Clicking proceed again now shows alot of options for the FPGA.
- toggle nets has different views
- toggle routing resources
- congestion shows the areas that are relatively congested and relatively less congested. 
- Routing utilization shows which structures have routing resources used (close to max and much less than max)
- Block Internal & zooming into a block, shows what has been implemented within each CLB! super details!

Clicking on proceed for the last time closes the window and the terminal now shoes the VPR has been completed. 


Post-Implementation Timing Simulation

We just run VPR again, but now we add another arguement (--gen_post_synthesis_netlist on)

The output:
- up_counter_post_synthesis.v file
- up_counter_post_synthesis.sdf file

Before we can simulate the post-synthesis files, however we need to define some of the modules that are used in the verilog file. We use primitives.v to do so. It is located at:
$VTR_ROOT/vtr_flow/primitives.v - ensure that the module names are the same as verilog file. 

Now we use Vivado and open include the following files;
- primitives.v.
- up_counter_post_synthesis.v file
- counter_tb.v 

It doesn't matter what FPGA we select, as we are only usng vivado for simulation. Not for synthesis, implementation or others that we already did on OpenFPGA 



Just like before if we want proper timing reports, we need to make sdc file. so we do that again. 


We got an error, but it's expected due to syntax. We need to replace ^ with _ in both blif and sdc. Now there's no error.


To check area specs, we can check the log file output with the VPR & it shows area specs.

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
