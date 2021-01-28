# Advanced Physical Design using OPENLANE/SKY130
VLSI System Design workshop on Physical Design Flow from RTL to GDSII using OPENLANE and SKY130 PDK.
# Chip Design
Each chip has its core, the core considered here is of RISC-V based SoC. RISC-V is an instruction set architecture that helps to communicate with the computer.

<img width="617" alt="Chip design" src="https://user-images.githubusercontent.com/72096419/105984549-4b679900-60c0-11eb-91ff-c1f901c42d2c.png">

### Foundry IP's
PLLs, DAC, ADC and SRAMs are known as Foundry IP's. They are manually designed.
### Macros
Macros are digital blocks which are made up of digital logic.

# OpenLANE ASIC Flow
Using openlane, we can produce a GDSII from a chip RTL.

<img width="532" alt="openlane flow" src="https://user-images.githubusercontent.com/72096419/105984775-9b466000-60c0-11eb-9cf9-a217bd37b9a1.png">

Openlane will automate the entire RTL to GDSII flow based on several components including openRaod, yosys, Magic, Netgen, Fault and custom methodology scripts for design exploration and optimization.

## PDK
Process Design Kit is a collection of files used to model a fabrication process for the EDA tools used to design an IC. It acts as an interface between the CAD designers and the foundry.

## Design Stages and Tools
### 1) Synthesis
  * yosys - Performs RTL synthesis
  * abc - Performs technology mapping
  * OpenSTA - Pefroms static timing analysis on the resulting netlist to generate timing reports
### 2) Floorplan and PDN
  * init_fp - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)
  * ioplacer - Places the macro input and output ports
  * pdn - Generates the power distribution network
  * tapcell - Inserts welltap and decap cells in the floorplan
### 3) Placement
  * RePLace - Performs global placement
  * Resizer - Performs optional optimizations on the design
  * OpenPhySyn - Performs timing optimizations on the design
  * OpenDP - Perfroms detailed placement to legalize the globally placed components
### 4) CTS
  * TritonCTS - Synthesizes the clock distribution network (the clock tre
### 5) Routing 
  * FastRoute - Performs global routing to generate a guide file for the detailed router
  * TritonRoute - Performs detailed routing
  * SPEF-Extractor - Performs SPEF extraction
### 6) GDSII Generation
  * Magic - Streams out the final GDSII layout file from the routed def
### 7) Checks
  * Magic - Performs DRC Checks & Antenna Checks
  * Netgen - Performs LVS Checks
  
# DAY 1
 
 <img width="612" alt="1" src="https://user-images.githubusercontent.com/72096419/106121150-3d2b8280-617d-11eb-9933-5b2b3e5e83d8.png">
 
The ./flow.tcl -interactive command runs the OpenLane in interactive mode.

## Design Preparation Step 

<img width="503" alt="2" src="https://user-images.githubusercontent.com/72096419/106121803-f8541b80-617d-11eb-8b11-c498ff787a0e.png">

Openlane has many built-in designs and we design for picorv32a. We will be performing the synthesis first.
The mergeLEF.py indicates the merging of the two LEF files into one. 
The config.tcl file shows the default parameters taken by run.

## Synthesis

After the preparation is done as shown above, the next command is,

   run_synthesis 

This will run the yosys synthesis as well as the abc.

<img width="956" alt="3" src="https://user-images.githubusercontent.com/72096419/106122095-4f59f080-617e-11eb-8aff-4ccaa5c23dc8.png">


Chip area for module '\picorv32a': 237049.849600 

The challenge of day 1 is to find the flop ratio which is the number of D flip flops to total number of cells 

The total number of cells are 17323 

The D flip flops are 1634 

Therefore the flop ratio is 0.094 

# Day 2
## Floorplan
The command to run floorplan in openlane is run_floorplan

<img width="506" alt="1" src="https://user-images.githubusercontent.com/72096419/106123552-10c53580-6180-11eb-8d2a-a2cc69281f85.png">

<img width="505" alt="3 deffile" src="https://user-images.githubusercontent.com/72096419/106123567-1589e980-6180-11eb-946a-2ddd3f62793a.png">

### Floorplan in Magic

<img width="619" alt="magicT cmd 4" src="https://user-images.githubusercontent.com/72096419/106123933-8a5d2380-6180-11eb-9300-cba35c86cccd.png">

<img width="615" alt="5" src="https://user-images.githubusercontent.com/72096419/106123948-8f21d780-6180-11eb-8fd4-30bbae3edd95.png">

We can see the standard cell placement in the left corner.





