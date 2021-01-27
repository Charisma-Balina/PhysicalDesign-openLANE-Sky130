# Advanced Physical Design using OPENLANE/SKY130
VLSI System Design workshop on Physical Design Flow from RTL to GDSII using OPENLANE and SKY130 PDK.
# Chip Design
<img width="617" alt="Chip design" src="https://user-images.githubusercontent.com/72096419/105984549-4b679900-60c0-11eb-91ff-c1f901c42d2c.png">



# OpenLANE ASIC Flow
<img width="532" alt="openlane flow" src="https://user-images.githubusercontent.com/72096419/105984775-9b466000-60c0-11eb-9cf9-a217bd37b9a1.png">

Openlane will automate the entire RTL to GDSII flow based on several components including openRaod, yosys, Magic, Netgen, Fault and custom methodology scripts for design exploration and optimization.

## PDK
Process Design Kit is a collection of files used to model a fabrication process for the EDA tools used to design an IC. It acts as an interface between the CAD designers and the foundry.

## Design Stages and Tools
1) Synthesis
  * yosys - Performs RTL synthesis
  * abc - Performs technology mapping
  * OpenSTA - Pefroms static timing analysis on the resulting netlist to generate timing reports



