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

Introduction to RISC-V core programming on Vivado

RVMyth vivado rtl-to-synthesis

RVMyth is a RISC-V Processor core, and we can implement it on an FPGA as soft IP core. 

mythcore_test.v designs the processor on FPGA

This is a 5 stage pipelined processor
1. Fetch - fetches instructions from instruction memory 

2. First instruction goes through decoder, at the same time the second instruction is being fetched. 

3. Execute after decode
- ALU
- Branch
- Load
- Jump

4. Memory Access Step

5. Back to register

### Rvmyth Vivado RTL to synthesis flow
  
We have a test.v file which serves as our test bench. It's a 1 bit counter, so essentially it goes between 0 and 1 & has delays in between changes. 


Vivado project using Basys3, added mythcore_test.v as design source & test.v as simulation source. 


Running simulation gives us a waveform. 



Now we can click Open Elaborated Design under RTL Analysis. 

It allows us to define the ports/package pins for the inputs (clk to W5 & reset to R2, a switch on the board)


On Verilog file, we will delete output port, so it doesn't need to be mapped to any LED. Then reload the elaboration. DON't run Simulation right now, it will show error due to the output being deleted. 

Now we don't have output port on I/O ports section. We therefore don't need to define any LEDs to act as Output, we just define input pins. 


In order to use integrated logic analyzer, we go to IP catalogue toolbar and search ILA.  select ILA, double click. Asks us how many probes we want to add, we select 2 for reset & also output. 

Under Probe ports, we have to select the width or size of the signals (probe0 is reset to it is 1 bit, 0 or 1. Probe1 is output which will be 8 bit signal.) We then clock "okay" & when the next window opens "Generate"

Once we do this, there is now a .veo file in our project folder. We double click on it to view. On this file there is an instance of the ILA, we need to copy & paste this instance onto the top verilog module (mythcore_test.v)

We paste it into the module core, where we declare the signals. We don't just copy and paste, we need to CONNECT this instance with the rest of our code. Change the naming of parameters! Map it using the variables clk, out & reset. 

Now we can re-run synthesis, however we didnt define any constraints. We can do this by now by clicking the timing constraints wizard. It shows that we have a clk which has no defined frequency or period. We then define it as 100MHz  10ns. Clicking next & then skip to finish. Now we have a constraints.sdc file that has been created & the clk has been added.

Re-running Snythesis now is the final step. 

After synthesis is complete, we can click report utilization. summary shows the resources we have used. 

By highlighting core, and clicking schematics we can see the whole processor's schematic!

Next let's try to run implementation & open implementation design once it's complete. 

We can now see the  layout showing how the logic cells have been placed for our design. Going on the netlist, we can click on Net & then select nets one by one, showing what part of the processor they have been used for. 

With one net selected, we can click report timing summary under synthesis. 

### Rvmyth Vivado Synthesis to bitstream

Elaborated session
- define I/O
- clk to pin W5 (in-built CLK)
- reset to Pin R2 (switch)
- We don't define outputs, instead we go to verilog file & remove the output from the module (line 194). We keep it as a reg on line 197 though. 


After reloading elaboration, we don't run another simulation. it will cause an error because outputs dont match on the test.v file. 


Now on elaboration we dont see output! let's run synthesis. 

IP catalogue -> ILA then copy paste the instantiation.




After that we add ILA to verilog code on Lines 205 to 211. It will probe the output signals, even though they arent defined now on the file. MAP the outputs & clock to clk in the template.


RE-Run Synthesis


Now we need to go to constraints wizard to add a clk with 100Hz, 10 Ns period.

Re-run sythesis. 


Run implementation after checking out the synthesis info, like timing summary & schematic of the core. 


Once implementation is done, we open the implementation window where it shows the floor plans. 


We can then look at Time Summary Report which shows even in worst case the constraints are being met.


Lastly we can click generate bitstream

We can click generate bitsrream, then open hardware manager. Then open target, then auto connect. 

We can select the FPGA and right click program device. The ILA will work to show us the signals. 

Clicking on the plus symbol under trigger setup, then we select the reset. We only want to trigger probs when reset is changed from 1 to 0. This will trigger ILA and the probes will check out the 8 bit output signal. 

When you flash, nothing changes on the screen, the user then can switch the trigger reset button from low to high, still no change, now when we switch it from high to low. The ILU is triggered! 
  
  
## Day 4

This is an h1 heading

### Introduction to opensource SOFA FPGA fabric

These are a series of open-source FPGA IPs using open-source Skywater 130nm PDK & OpenFPGA framework. 

to do timing analysis, just like with general OpenFPGA, all we need to do is define CLK constraints on sdc file. Since SOFA automates much of the OpenFPGA scripts we just add --sdc_file "path to file".sdc in the pre-existing script. 

Then we run the general command:
make runOpenFPGA

Now our reports have proper timing analysis.

### Steps to run counter example on SOFA

SOFA counter post implementation & simulation

Go to Script again where we added sdc file, now we add --gen_post_synthesis_netlist on 

It will run synthesis and output a post-synthesis netlist for us.

We RE-RUN:
make runOpenFPGA

We now have "up_counter_post_synthesis.v" file

1. Must create test bench
- created instance of up_counter
- create clock and toggle it
2. Primitives.v file, we must change "clk" to "clock" to align with the post_synthesis "clock" name.

Now we can simulate the post-synthesis netlist!

Open Vivado, new project. specificy the correct path

add design source, select up_counter_post_synthesis.v & primitives.v

add simulation source, select test_bench.v file

We can open the test bench file on vivado and check to make sure everything has been defined correctly. then we can click run simulation. 

We can then see the output waveform, showing the counter counting up. 

We don't need to use Vivado to see this waveform and verilog simulator will suffice, but we need SOFA & OpenFPGA to run the scripts, output the post-sythesis simulation file, primitives for us to write the test bench file. 

### Characterize counter example in terms of area and timing
  
Going into the config directory, we then open the tast_simulation.conf file & then we can go to task directory and open the generate_testbench.openfpga. We open and edit this file, adding power and tech commands. <see pic for ref>

Again we run:
make runOpenFPGA, now we have up_counter.power file. 

Opening it shows the power specs!

### Post implementation netlist and simulation using SOFA
  
Re-run through the steps on Day 3 to create post implementation netlist. Then open Vivado to run through any test bench we want to write along with the post-implementation netlist & primitives.v file as design sources.  

## Day 5

This is an h1 heading

### Steps to run RISC V Core on SOFA

SOFA-RVMyth run

After cloning the SOFA repo, 
we then go the following directory and run a make file there. 

cd FPGA1212_QLSOFA_HD_PNR
make runOpenFPGA

There are some files we will need to edit though,
run;
vim task_simulation.conf
In this file we need to change 2 things, 
- openfpga_vpr_device_layour=auto
- openfpga_vpr_route_chan_width=180

We also go and change a file in an earlier directory, 
vim generate_testbench.openfpga
In this file we make the following changes;
<insert pic for reference>

We then go into the "arch" directory & run;
vim vpr_arch.xml

In this file on line 154, 155 & line 256, we comment them out.

Now thats all done, we go back to the original directory & run make runOpenFPGA

This take 5-6 mins to run, it will generate alot of outputs to the folder MIN_ROUTE_CHAN_WIDTH within core<- vpr_arch<-latest

We are very interested in the log file;
vim openfpgashell.log

### Characterize RVmyth in terms of performance and area

Performing area analysis is quite simple

run:
vim vpr_stdout.log

Searching circuit statistics, shows us that 5526 blocks have been used and below that is the rest of the statistics. 

Searching for logic elements, shows us the detailed count as well as Pb usage. 


Timing Analysis, before doing this we need to open the mythcore_test.v file. running
vim mythcore_test.v

The top module's name is core, clock is clk. so we need to make sure the sdc file we create, we define the clock as clk, with a period of 200ns. It's slow because we are doing a whole processor. 

Now opening config file, task_simulation.conf (same as last time) It doesn't change this time, it stays the same. We don't need to update it again like we did the first time. 

Now going into generate_testbench.openfpga

We now edit the script command again, to add --sdc file as the constraints have just been defined. 

< pic for reference>

Now that's all done, we go back to the original directory & run the make command:
make runOpenFPGA

We can see the setup & hold timing reports. 
We start by seeing
- report_timing.setup.rpt - slack has been met, in 10.43 ns. 

- report_timing.hold.rpt - Slack met by 0.96 ns.

### Steps to generate rvmyth post implementation netlist
  
Now we run the post-implementation simulation, first we need a post-implementation netlist.

We add another command to the original generate_testbench.openfpga file & then run make again.

Now we have a file called core_post_synthesis.v

We need to write a test bench for this, in doing so we must check the modules that we need. (LUT_K/DFF/Interconnect)
- DFF is defined differently in the primitive.v file, so we need to align them. the clock is labeled "clock", but in the primitives it "clk" we change it to "clock to make it work.

Now that we are ready with our testbench & primitives file, we can run them through vivado.

File->Project->New to create new project file.

Then, add the sources, by clicking option or "+" icon, 
add design sources - post-synthesis.v & primitives.v
add simulation - testbench.v

Click run simulation -> run behavioral simulation. 

### Confirm RVmyth on SOFA behavioral simulation using Vivado
  
Re-run through the steps on Day 3 to create post implementation netlist. Then open Vivado to run through any test bench we want to write along with the post-implementation netlist & primitives.v file as design sources.  

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
