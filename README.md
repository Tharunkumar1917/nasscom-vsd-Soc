# NASSCOM-VSD-SoC Design and Planning workshop (Dec 11- Dec 24)

### About the workshop:
Welcome to the NASCOM SoC Design and Planning Workshop repository! This repository documents my journey through a two-week workshop focused on various aspects of System-on-Chip (SoC) design and planning, including hands-on experience with tools like OpenLane, Magic, and ngSpice.

## DAY 1 
Topics covered:
<details>
           
-  __Soc__(System on chip)

  A System on Chip (SoC) integrates all essential components of a computer or electronic system, such as the processor, memory, peripherals, and I/O, onto a single chip. This compact 
  design improves performance, power efficiency, and cost, making SoCs ideal for applications like smartphones, IoT devices, and embedded systems.

![soc](https://github.com/user-attachments/assets/4020ccd0-dbd3-4445-820a-388609ad3020)

- __RISC-5__ (Reduced Instruction Set Computer)

  RISC-V is an open, free, and extensible Instruction Set Architecture (ISA) designed for flexibility and scalability, enabling use across a wide range of applications from 
  microcontrollers to supercomputers. Its open-source nature encourages innovation and eliminates licensing fees, making it popular in academia, industry, and open hardware projects.

- __RTL__ to __GDS-2__

  RTL to GDSII is the complete design flow that converts a high-level hardware description (RTL) into a manufacturable chip layout (GDSII format). This process includes synthesis, 
  floorplanning, placement, clock tree synthesis, routing, and verification to ensure the design meets functionality, timing, and manufacturing requirements.
  
![WhatsApp Image 2024-12-16 at 18 03 57_542190b3](https://github.com/user-attachments/assets/bfc83aff-a25b-4bbd-8521-50d7cf3197c5)

![WhatsApp Image 2024-12-16 at 18 04 10_04aa9897](https://github.com/user-attachments/assets/b7a47535-880d-4bf9-8642-a5824a9ad2b3)


- __what are PDK's ?__(Process Design Kits)

 A Process Design Kit (PDK) is a collection of files and data provided by a semiconductor foundry that describes the manufacturing process of a chip at a specific technology node (e.g., 
 130nm, 28nm). It includes information such as design rules, standard cell libraries, SPICE models, and technology files required for physical design, simulation, and verification.
 
-  __Google sky 130nm PDK__
  
  The SkyWater 130nm PDK is an open-source PDK developed by SkyWater Technology and released in collaboration with Google. It targets the 130nm technology node and provides resources for 
  chip designers to create silicon without proprietary restrictions, democratizing chip design by allowing free and open access to the design tools and libraries.
  
- __Role of Openlane in RTS to GDS 2__

  OpenLane is an open-source ASIC design flow that automates the conversion of RTL to GDSII, leveraging tools like Yosys for synthesis, OpenROAD for physical design, and Magic for layout 
  verification. It simplifies the design process by integrating all necessary tools and ensuring the design complies with the PDK's rules, making it an essential platform for open 
  hardware projects using PDKs like SkyWater 130nm.

![WhatsApp Image 2024-12-16 at 18 07 53_f2f10507](https://github.com/user-attachments/assets/1bf356ac-7c6e-4e7b-b0da-db03ac930af1)

- __EDA tools__

  ![WhatsApp Image 2024-12-16 at 18 04 06_0fe86e51](https://github.com/user-attachments/assets/5bb66cec-9586-43f6-a731-b8dede6889c9)
                    
</details>

OPENLANE DIRECTORY STRUCTURE : 
```
Desktop/work/tools/openlane_working_dir/openlane$
```
## Docker
<details>
Pre-configured Environment: OpenLane is distributed as a Docker image, meaning all required tools (e.g., tools for synthesis, placement, routing) and dependencies are pre-installed in a self-contained environment.
</details>

- initial setup commands to invoke __openlane__ :

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane
docker
pwd
./flow.tcl -interactive
```
to check package version:
```
  package require openlane 0.9
```
to perform preparation
```
prep -design picorv32a
```
<img width="639" alt="docker" src="https://github.com/user-attachments/assets/95a46e6d-36bc-459b-bd7b-e1b5420bba9e" />

## Familirisation with openlane

### designs folder :
```
 Desktop/work/tools/openlane_working_dir/openlane/designs
```
<img width="641" alt="designs" src="https://github.com/user-attachments/assets/b4accfce-5e61-4736-ace7-8a449cc09577" />


### Picorv32a folder:

```
Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a
```
<img width="640" alt="dated(runs current dirctory)" src="https://github.com/user-attachments/assets/34ce5d11-d865-413a-bfef-70311bb442d8" />

### Files created on Dec 12-12_14-35
<img width="640" alt="files that are created currently" src="https://github.com/user-attachments/assets/e5e310c5-688f-439d-b97e-4b8b8777e2b1" />

### Synthesized file 
- to run synythesis
```
run_synyhesis
```
- Mapping info
<img width="637" alt="synthesis file(mappings)" src="https://github.com/user-attachments/assets/df9dff1b-3a23-47cf-b8c2-1872751195f1" />

- directory root for yosys stat report:
``` 
Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-12_17-12/reports/synthesis
```
- to open yosys stat report
```
less 1-yosys_4.stat.rpt
```
<img width="638" alt="inside synthesis file" src="https://github.com/user-attachments/assets/7a15ffbd-1fad-41cc-9f48-45c838c40e30" />

## Yosys stat report:
<details>
 The Yosys stat report in OpenLane summarizes the results of logic synthesis, including the total number of cells, their types (e.g., logic gates, flip-flops), and the estimated area utilization. It provides a breakdown of the cell distribution and key design statistics, such as wire counts and memory usage. This report helps designers analyze the design’s complexity and area requirements before proceeding to the physical design stages.          
</details>


<img width="638" alt="yosys stat report" src="https://github.com/user-attachments/assets/2183bf5a-9eae-4b4e-983e-7748a578f9a2" />



```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
- By observing the __yosys stat report__ , it can be noticed that numner of D flip-flops are 1613 and Total number of cells in  the current created folder is 14876, hence flop ratio becomes
  
```math
Flop\ Ratio = \frac{1613}{14876}
```
 = 0.1084 or 10.84% 




## DAY 2

Topics covered:
<details>
           
- __Chip Floor-Planning consderations__

__Die__

The die is the entire physical piece of silicon that contains all the elements of the chip, including the core and peripheral components.

__Core__

The core of a chip refers to the part of the chip where the active components (such as processors, logic gates, memory cells, and transistors) are located.


__Utilization factor__

```math
Utilisation\ factor = \frac{ Area\ occupied\ by\ Netlist\ }{Total\ area\ of\ the\ core}
```
  
__Aspect ratio__

```math
Aspect\ ratio = \frac{Height\ \ of\ core\ }{Width\ of\ core}
```
![WhatsApp Image 2024-12-16 at 18 13 15_daa7a595](https://github.com/user-attachments/assets/5290af53-c3c2-4b87-8a20-d57f905150f6)

- __Preplaced Cells__

In chip floor planning, preplaced cells refer to specific cells or components that are placed in fixed locations on the chip before the actual floor planning and layout design process begins. These cells typically serve important functions, such as power distribution, input/output (I/O) pads, or specialized areas that need to be placed in specific locations due to design or manufacturing constraints.


![WhatsApp Image 2024-12-16 at 18 13 15_5db43246](https://github.com/user-attachments/assets/4746de4b-2be8-4f97-b039-a5f1422ce894)


![WhatsApp Image 2024-12-16 at 18 13 14_470c051e](https://github.com/user-attachments/assets/4fe84fcb-4d76-4214-8db3-359c535019d7)

- __Decouplng Capacitors__

  Decoupling capacitors are capacitors placed between the power supply (Vcc) and ground (GND) to smooth out voltage fluctuations and filter noise from the power lines that could affect the performance of sensitive components in the circuit.
  
__How Do Decoupling Capacitors Work?__
When the power supply experiences a transient or voltage dip (such as when a component suddenly switches on), the decoupling capacitor charges to supply the required current.
Similarly, if there is a voltage spike, the capacitor discharges, absorbing the excess energy and preventing it from reaching the rest of the circuit.

![WhatsApp Image 2024-12-16 at 18 19 26_944c0359](https://github.com/user-attachments/assets/4b966851-f79d-4fe0-b415-a4d984e9545a)

- __Power-Planning__

Power planning in chip design refers to the process of designing and organizing the power distribution network within an integrated circuit (IC) or chip. This network ensures that all components on the chip receive the required voltage and current levels to function correctly, efficiently, and reliably.

![WhatsApp Image 2024-12-16 at 18 29 28_5e322764](https://github.com/user-attachments/assets/f311d9e5-8751-4c38-aab6-374b5b3ab051)

 - __why do multiple VDD and VSS are used in Floor-planning?__

VDD and VSS are the primary power and ground connections for the entire chip. As chips grow in size and complexity, a single pair of VDD and VSS lines may not be sufficient to deliver power evenly to all parts of the chip.
Multiple VDD and VSS lines help distribute power efficiently across the chip, ensuring that all components have stable and reliable access to the voltage they require.

![WhatsApp Image 2024-12-16 at 18 29 28_64951501](https://github.com/user-attachments/assets/9e762ffa-d0b9-43f4-8e2a-bd48c4671691)

 - __Pin-Placement__

 Pin placement in chip floor planning refers to the process of determining where the input/output (I/O) pins of an integrated circuit (IC) will be located on the chip's 
 surface. These pins are the electrical contacts through which the chip interacts with the external environment, including other chips, devices, or the power supply.

![WhatsApp Image 2024-12-16 at 18 30 59_e7cd1815](https://github.com/user-attachments/assets/a762cbf7-4204-4359-8195-0653ace2d510)

__Logical cell placement blockage__

![WhatsApp Image 2024-12-16 at 18 30 58_16c67481](https://github.com/user-attachments/assets/74fdc244-71df-42ed-a439-fc1c76765999)


Types of Pin-Placement

<details>
           
__Periphery Pin Placement__

__Central Pin Placement__

__Corner Pin Placement__

__Clustered Pin Placement__

__Power and Ground Pin Placement__

__Symmetric Pin Placement__

</details>


- __Placement optimization__

Placement optimization in chip design refers to the process of improving the location of cells (standard cells, macros, or other components) on the chip to achieve specific design goals. These goals typically include maximizing performance, minimizing power consumption, reducing area, and ensuring proper functionality. The placement stage occurs after the logic synthesis and before the routing phase in the chip design flow.

![WhatsApp Image 2024-12-16 at 18 35 39_e761eab9](https://github.com/user-attachments/assets/1c623966-c474-4aad-95ea-6e96d588575c)


- __Library__

A library in chip design, specifically in the context of digital IC design, contains a collection of pre-characterized cells that represent standard building blocks for creating circuits. These cells are used to design complex digital systems and include information about their functionality, electrical characteristics, timing behavior, and more.


-Based on the information of shapes and size of cells
-Based on the information of  Delay and STA

![WhatsApp Image 2024-12-16 at 18 37 06_4f6f0ce8](https://github.com/user-attachments/assets/3ffffd78-0d2f-4a7f-aab6-0ae980115649)

- __Library characterisation and Modelling__
![WhatsApp Image 2024-12-16 at 18 37 05_7bcdd487](https://github.com/user-attachments/assets/508f4daf-665a-4463-94fe-b5d70a08f9c4)

</details>

## Cell design flow

Cell design flow refers to the series of steps or stages involved in the creation of a standard cell for an integrated circuit (IC). Standard cells are the fundamental building blocks used in digital ICs (such as logic gates, flip-flops, multiplexers, etc.), and the design of these cells involves a detailed process that ensures they meet the required performance, area, and power specifications.
<details>
Steps in the Cell Design Flow:
           
- __Specification and Architecture Definition:__

Functional Specification: Define the desired functionality of the cell (e.g., an AND gate, D flip-flop).
Performance Goals: Determine the target performance, including timing constraints (e.g., propagation delay, setup time, etc.), power consumption, and area requirements.
Power Consumption Requirements: Specify the maximum allowable power consumption and leakage currents.

-__Schematic Design:__

Create a schematic diagram of the cell that represents the logical connections between components (transistors, resistors, capacitors, etc.).
The schematic should accurately reflect the intended functionality of the cell.

-__Transistor Sizing:__
Choose appropriate sizes for the transistors in the cell based on the required electrical characteristics like drive strength, switching speed, and power consumption.
Aspect ratio (width to length) of transistors plays a key role in determining the cell's performance and area.

-__Layout Design:__

The schematic is translated into a physical layout, where the actual placement and routing of transistors and other components are defined.
The layout is optimized for the process node (e.g., 7nm, 14nm) and considers factors like density, congestion, and design rules for the fabrication process.

-__DRC (Design Rule Check):__

Perform a Design Rule Check (DRC) to ensure the layout complies with the manufacturing process’s geometrical constraints (minimum width, spacing, etc.). DRC ensures the design can be fabricated correctly and avoids physical errors like shorts or opens.

-__Extraction and Parasitic Modeling:__

- Extract the parasitic capacitances, resistances, and inductances from the layout.
Create parasitic models that are used to simulate the behavior of the cell under real-world conditions, accounting for the physical layout's impact on electrical performance.
Timing and Electrical Analysis:

- Perform timing analysis to determine the delay characteristics (e.g., propagation delay, rise/fall times) of the cell.
Ensure that the cell meets the required timing constraints (setup time, hold time, and clock skew).
Power analysis is also done to check for dynamic and static power consumption (including leakage).

-__SPICE Simulation:__

Simulate the cell's electrical behavior using SPICE (Simulation Program with Integrated Circuit Emphasis) to validate the performance, including delay, power, and noise characteristics.
Ensure the cell works correctly in a range of conditions (e.g., different supply voltages and temperatures).

-__Verification (Functional and Electrical):__

Perform functional verification to ensure that the cell operates as intended in all possible scenarios.
Conduct electrical verification to ensure the cell meets all the necessary electrical constraints, such as voltage levels, current limits, and power consumption.

-__Cell Characterization:__

Characterize the cell for timing and power, generating libraries of values that can be used in the design flow of higher-level circuit designs.
Characterization involves running simulations at different process, voltage, and temperature (PVT) corners and compiling delay, power, and noise data.

-__Library Generation:__

After characterization, generate a standard cell library that includes the electrical, timing, and physical data for each cell.
The library will contain models for various operating conditions and process corners, which are used during the Place and Route (P&R) stages of larger IC designs.

-__Post-Layout Simulation and Signoff:__

Perform post-layout simulations to verify the final layout works as expected with parasitic effects included.
Ensure the cell meets all design rules, timing requirements, and electrical constraints before the cell is signoff for production.

-__Tapeout:__

Once the cell passes all tests, the final design is sent for tapeout, which is the preparation of the final mask data for the manufacturing process.

![WhatsApp Image 2024-12-16 at 18 37 21_fc9a5357](https://github.com/user-attachments/assets/e69789fd-61bb-4806-8e05-df61db674987)
</details>

![WhatsApp Image 2024-12-16 at 18 37 25_2cce606b](https://github.com/user-attachments/assets/7b927452-f3ae-44ff-b144-04f0acc81a11)

- __Timing Characterisation__

Timing characterization is the process of determining the delay, setup, hold, and propagation times of a cell or circuit under various operating conditions (such as voltage, temperature, and process variations). It generates timing models that are used in larger chip designs for accurate performance analysis and optimization.

![WhatsApp Image 2024-12-16 at 18 37 28_80d6571f](https://github.com/user-attachments/assets/32755637-20e1-47a4-aaee-fc7e78284311)

- Terms related to Timing Characterisation
<details>
           
__Slew_low_rise_thr:__
The voltage threshold used to determine the start of a rising edge when the signal is transitioning from a low voltage level.

__Slew_high_rise_thr:__
The voltage threshold used to determine the end of a rising edge when the signal is transitioning to a high voltage level.

__Slew_low_fall_thr:__
The voltage threshold used to determine the start of a falling edge when the signal is transitioning from a high voltage level.

__Slew_high_fall_thr:__
The voltage threshold used to determine the end of a falling edge when the signal is transitioning to a low voltage level.

__in_rise_thr:__
The voltage threshold used to determine the start of a rising edge at the input of a circuit.

__in_fall_thr:__ 
The voltage threshold used to determine the start of a falling edge at the input of a circuit.

__out_rise_thr:__
The voltage threshold used to determine the start of a rising edge at the output of a circuit.

__out_fall_thr:__
The voltage threshold used to determine the start of a falling edge at the output of a circuit.          

![WhatsApp Image 2024-12-16 at 18 37 30_1600b8a4](https://github.com/user-attachments/assets/38ed6dcc-db46-4064-9977-15decb9a5eca)

</details>

- __Die area__

```math
Length\  = \frac{660685 }{1000}

```
660.85u

```math
Width\  = \frac{671405 }{1000}

```
671.405u

<img width="635" alt="def file -Die area" src="https://github.com/user-attachments/assets/79f393f9-e290-4d83-864d-2aa790a85ab7" />


__Characterising a cell__

 __Rise Transition__
 
It is the time taken to reach from 20% to 80% of the output rise waveform (logic 0 to 1).

```math
\text{Rise Transition} = \left( 20\% \text{ of the rise waveform} \right) - \left( 80\% \text{ of the rise waveform} \right)

```


__Fall Transition__

It is the time taken to reach from 80% to 20% of the output fall waveform (logic 1 to 0).

```math
\text{Rise Transition} = \left( 80\% \text{ of the fall waveform} \right) - \left( 20\% \text{ of the fall waveform} \right)

```

__Rise cell dealy__

It is the time difference  between 50% of input voltage and output voltage defined at the 50% of input voltage ,in the output rise waveform.

```math
\text{Rise cell delay} = \left( 50\% \text{ of the input voltage of rise waveform} \right) - \left( 50\% \text{ of the output voltage of rise waveform} \right)

```
__Fall cell delay__

It is the time difference  between 50% of input voltage and output voltage defined at the 50% of input voltage, in output fall waveform.

```math
\text{Rise cell delay} = \left( 50\% \text{ of the input voltage of fall waveform} \right) - \left( 50\% \text{ of the output voltage of fall waveform} \right)

```

### Procedure for Floor Planning

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane
docker
pwd
./flow.tcl -interactive
prep -design picorv32a
run_synthesis
run_floorplan
```


- __README.md__
  

The __README.md__ file in OpenLane provides an overview of the project, describing it as an open-source, end-to-end ASIC design flow that integrates tools like Yosys, Magic, and KLayout. It includes instructions for installation, environment setup, and running designs, along with examples to help users get started. Additionally, it covers details about supported platforms, configuration options, contribution guidelines, and licensing.

To open __readme.md file__
  
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane
cd configuration
ls -ltr
less readme.md

```
  
 <img width="638" alt="files created on 15_12" src="https://github.com/user-attachments/assets/96990822-2363-4065-a498-3b4451cedd33" />
 
- Before running the floorpan the defaults configurations,  such as core utilization ,default input and output pin placements can be checked 
  inside the readme.md file

 Files created as dated on __15-12_2-07__

 <img width="638" alt="files created on 15_12" src="https://github.com/user-attachments/assets/a7d47e29-519a-4dfc-a8f4-3695643950d1" />

 to run floorplan: 

```
run_floorplan
```
- In OpenLane, run_floorplan defines the physical layout of the chip by setting the core area, placing IO pins and macros, creating standard cell rows, and adding power straps. It prepares the design for placement and routing in subsequent stages.
- Another important note is that in openlane  __standard cells__ are not placed in floorplan they are placed after the placement
  
  <img width="638" alt="inside floorplan " src="https://github.com/user-attachments/assets/1118c5cd-3bcb-4bf9-a095-cf4c78a763e5" />


__Def file__

In OpenLane, the __def.file (Design Exchange Format)__ is a critical file containing the physical layout information of an ASIC design. It includes:

<details>
           
__Design details:__ Name, units, and grid structure.

__Component placement:__ Locations of cells and macros.

__Connections:__ Netlists, pins, and routing guides.

__Special elements:__ Power/ground nets, obstructions, vias.

</details>

The DEF file is used at various stages of the flow, like placement, routing, and layout verification. It serves as both an input and an output for tools in the physical design process.
  

  to open def file for placement:

  ```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15_12-2_07/results/floorplan
less picorv32a.floorplan.def
  ```

<img width="638" alt="inside def file" src="https://github.com/user-attachments/assets/dc8b532d-1701-40fa-b97c-4b2948b72603" />


Floorplan tech file location:

```
magic -T /home/nickson/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

```


__Floorplan layout before the placement of standard cells__

<img width="640" alt="florplan layout" src="https://github.com/user-attachments/assets/86e9eba6-77bb-4e98-b050-a07ca87dcd50" />

In OpenLane, the run_placement step is responsible for placing the standard cells within the design area. Placement is a critical stage in the physical design flow where standard cells are positioned on the chip layout according to the logical netlist while considering design constraints and physical resources.

### Initial global placement ##

Initial Global Placement is the first step in the placement stage of the ASIC physical design flow. It aims to place standard cells within the chip's core area in an approximate manner to minimize wirelength and congestion while keeping the design scalable for further optimization and legalization.

Key Tasks of run_placement

to run placement:
```
run_placement
```
__Standard Cell Placement__:

The primary function is to place standard cells (small pre-designed logic units like AND, OR, flip-flops) in the specified rows and sites within the core area.
Ensures cells are aligned properly to the placement grid.

__Initial (Global) Placement:__

The cells are initially placed with the goal of minimizing wirelength and congestion.
Tools like RePLace (global placement) or OpenROAD's placement engine are used.

__Legalization:__

Adjusts the positions of the standard cells to ensure:
Cells do not overlap.
Placement adheres to row boundaries and design rules.
Cells align to the placement grid.

__Placement Optimization:__

The placement step optimizes the layout for:
Wirelength minimization.
Timing and congestion reduction.
It may also consider power/ground (P/G) grid constraints.


Def file for placement

tech file location:

```
magic -T /home/nickson/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
  
```
<img width="641" alt="Global placement_Standard cells placement" src="https://github.com/user-attachments/assets/52c38958-9763-498b-8bef-a787e74d8541" />


__Magnified view of placement__

<img width="636" alt="inside placement" src="https://github.com/user-attachments/assets/ea6ba7a2-3b2f-407a-be18-62d83bb8ef61" />


__tckon.tcl__

<img width="639" alt="tckon tcl" src="https://github.com/user-attachments/assets/3f89f692-a1ca-4672-9c4b-7bc57e600910" />

The tckon.tcl file in OpenLane is a TCL script responsible for enabling timing checks and configuration during the design flow. It typically sets up timing constraints, clock definitions, and required timing margins to ensure the design meets performance requirements. This script is executed during key stages like placement, CTS (Clock Tree Synthesis), and routing, enabling tools to analyze and optimize timing.


## DAY 3 

Topics covered:

<details>
           
__Spice simulation for CMOS inverter__

__Steps to git clone vsdstdcelldesign__

__CMOS fabrication process__

__Introduction Mgic tool options and DRC rules__

__Challenges to find incorrect and missing rules__
       
</details>

### SPICE DECK ###

A SPICE deck in OpenLane is a simulation file that describes the electrical characteristics and interconnections of the design at the transistor level, enabling the verification of timing, power, and functionality through simulation. It is a crucial part of ensuring that the final design performs correctly under real-world conditions.

steps to set the simulation parameters in spice deck
- Identify the nodes such as  __Drain ,Source ,Substrate__.
- Name the selected nodes such as __out ,in ,0__.
- Set the supply voltage such as  __VPULSE__, __VDD__.
  
![WhatsApp Image 2024-12-17 at 17 06 31_093daa51](https://github.com/user-attachments/assets/eaf6cd94-7bcf-4f20-8689-462845e52f4a)

### Variation in VTC a Inverter due to different ratios of \( W/L \) for NMOS and PMOS ###
### Effect of \( W/L \) Ratios on Inverter VTC

1. **Balance between NMOS and PMOS**: The \( W/L \) ratio for PMOS is typically **larger** than NMOS to compensate for the lower hole mobility in PMOS, ensuring balanced switching characteristics.

2. **VTC Symmetry**: When **NMOS and PMOS** have similar \( W/L \) ratios, the **VTC** is symmetric, with sharp transitions between logic 0 and 1, leading to ideal voltage levels.

3. **Improved Switching Speed**: A **larger \( W/L \) ratio for PMOS** allows the inverter to **pull up** the output faster, resulting in **faster switching** and sharper voltage transitions.

4. **Noise Margins**: Proper sizing of NMOS and PMOS provides **stronger noise margins**, making the inverter more resistant to noise and voltage fluctuations at the input.

5. **Degraded Performance with Poor Sizing**: If the PMOS \( W/L \) ratio is too **small** compared to NMOS, the inverter will have **slower rise times**, a **gradual VTC**, reduced noise margins, and slower switching performance.


![WhatsApp Image 2024-12-17 at 17 06 49_e322ad9c](https://github.com/user-attachments/assets/2b537db3-f1a0-4989-996f-62562114e9b6)

### CMOS FABRICATION PROCESS 

### 16-Mask CMOS Fabrication Process

The **16-mask CMOS fabrication process** refers to the use of **16 photolithography masks** to fabricate an integrated circuit (IC) on a semiconductor wafer. The process includes multiple steps to create the various layers of the circuit, such as **transistor structures (NMOS, PMOS)**, **interconnects**, and **metal layers**.

#### 1. **Wafer Preparation**:
   - **Starting material**: The process begins with a **silicon wafer** (typically 200mm or 300mm), which is cleaned and prepared for the deposition of materials.
   - **Oxide Layer**: A thin layer of **silicon dioxide (SiO₂)** is grown on the wafer’s surface through **thermal oxidation**, acting as an insulating layer for the transistor gate.

#### 2. **Masking and Lithography**:
   - The primary technique used for patterning the wafer is **photolithography**, which employs **16 separate masks**. Each mask defines a different part of the IC, such as transistors, interconnections, and contact openings.

#### 3. **Key Mask Layers**:

           
   - **Mask 1-3: Well Formation and Isolation**:
     - **Mask 1**: Defines the region for **NMOS** and **PMOS** devices, involving ion implantation or diffusion to create **N-well** and **P-well** regions.
     - **Mask 2-3**: Defines **isolation structures** such as **field oxide** or **shallow trench isolation (STI)**.
   ![WhatsApp Image 2024-12-17 at 17 06 51_a9ebd8a5](https://github.com/user-attachments/assets/e504d9b6-bc59-4fa9-8ba4-aa8b68fe9706)
   ![WhatsApp Image 2024-12-17 at 17 06 57_3c4d2f6b](https://github.com/user-attachments/assets/f67fa54f-224b-4ceb-83f7-35b5a615ad43)

   - **Mask 4-6: Gate Formation**:
     - **Mask 4**: Defines the **polysilicon gate** pattern for the transistors.
     - **Mask 5**: Defines **source/drain implant** for NMOS and PMOS transistors.
     - **Mask 6**: Defines the **oxide spacers** around gates to prevent shorting between source/drain regions.
    ![WhatsApp Image 2024-12-17 at 17 06 59_a8ff5569](https://github.com/user-attachments/assets/a306bb61-a8b8-428c-b8d8-20317398bdb7)
    ![WhatsApp Image 2024-12-17 at 17 07 01_854aca74](https://github.com/user-attachments/assets/b24a3b8e-a3ef-4e18-b691-d651882a7ab0)
   
   - **Mask 7-9: Source/Drain and Contacts**:
     - **Mask 7**: Defines the **source and drain regions** via ion implantation.
     - **Mask 8-9**: Defines **contact holes** to connect the transistor’s source, drain, and gate to the first metal layer.
    ![WhatsApp Image 2024-12-17 at 17 07 07_090cfe83](https://github.com/user-attachments/assets/6c931229-4a5b-42c6-a824-4c060605d4f8)
    ![WhatsApp Image 2024-12-17 at 17 07 10_c02931cb](https://github.com/user-attachments/assets/35a8bbc6-6c14-44a2-87d3-fd8b5165ebfb)
       
   - **Mask 10-12: Metal Layers and Interconnects**:
     - **Mask 10-12**: Defines the **metal layers** (e.g., metal-1, metal-2, metal-3) for interconnects between various parts of the circuit.
     - These layers are typically made of **aluminum** or **copper** with vias to connect different layers of metal.
      ![WhatsApp Image 2024-12-17 at 17 07 11_533ebc49](https://github.com/user-attachments/assets/8861a11c-dd05-4dde-b7ac-5149de549cb5)
      ![WhatsApp Image 2024-12-17 at 17 07 12_c6c35e17](https://github.com/user-attachments/assets/98212a2c-7484-4d80-bf15-dd2972170963)

   - **Mask 13-15: Contact via Definition**:
     - These masks define additional **via openings** for inter-layer connectivity, allowing metal layers to connect to the underlying devices.
      ![WhatsApp Image 2024-12-17 at 17 07 15_89b71af8](https://github.com/user-attachments/assets/7ea89641-2cdf-4302-81a1-28a4bc79db59)
      ![WhatsApp Image 2024-12-17 at 17 07 18_d5e991b4](https://github.com/user-attachments/assets/9ae592cd-7ac0-4b0b-8d36-bf9aa6c3d033)

   - **Mask 16: Final Passivation Layer**:
     - **Mask 16**: Defines the **final passivation layer** (usually **silicon nitride** or **silicon dioxide**) that protects the IC from environmental damage and provides electrical isolation.
      ![WhatsApp Image 2024-12-17 at 17 07 22_f048ed83](https://github.com/user-attachments/assets/11b755ea-594e-4cb2-addb-b5373db38e8a)
      ![WhatsApp Image 2024-12-17 at 17 07 23_cd0113b3](https://github.com/user-attachments/assets/78df0f86-110c-48ca-88c7-c20d5cf302be)


#### 4. **Key Steps in the Fabrication Process**:
   - **Oxidation**: Grow a thin layer of silicon dioxide on the wafer surface.
   - **Deposition**: Deposit materials like **polysilicon** and **metals** using **chemical vapor deposition (CVD)** or **physical vapor deposition (PVD)**.
   - **Photolithography**: Use photomasks to pattern the layers onto the wafer using photoresist, UV light, and development.
   - **Etching**: Remove unwanted materials through **dry etching** or **wet etching**.
   - **Ion Implantation**: Introduce dopants into specific wafer regions to create **NMOS** and **PMOS** regions.
   - **Chemical Mechanical Planarization (CMP)**: Polish the wafer surface to flatten it after deposition and etching.

#### 5. **Final Steps**:
   - **Wafer Testing**: Once fabrication is complete, the wafer undergoes testing to check for defects and verify that the transistors and interconnections are functioning as expected.
   - **Dicing and Packaging**: The wafer is cut into individual **dies**, which are then packaged into IC packages for integration into electronic devices.

```mermaid
flowchart TD
    createActiveRegion[Create Active Region] --> FormationOfNwellAndPwell[Formation of Nwell and Pwell]
    FormationOfNwellAndPwell --> FormationOfGateTerminal[Formation of Gate Terminal]
    FormationOfGateTerminal --> LightlyDopedDrain[LDD Formation]
    LightlyDopedDrain --> SourceAndDrainFormation[Source and Drain Formation]
    SourceAndDrainFormation --> LocalInterconnectFormation[Local Interconnect Formation]
    LocalInterconnectFormation --> HighLevelMetalFormation[High-Level Metal Formation]
```

