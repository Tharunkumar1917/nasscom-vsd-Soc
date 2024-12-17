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

- __Characterising a cell__

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
```
- __README.md__
  
  The __README.md__ file in OpenLane provides an overview of the project, describing it as an open-source, end-to-end ASIC design flow that integrates tools like Yosys, Magic, and KLayout. It includes instructions for installation, environment setup, and running designs, along with examples to help users get started. Additionally, it covers details about supported platforms, configuration options, contribution guidelines, and licensing.

- To open __readme file__
  ```
cd ~/Desktop/work/tools/openlane_working_dir/openlane
cd configuration
ls -ltr
less readme.md
```
  <img width="638" alt="files created on 15_12" src="https://github.com/user-attachments/assets/96990822-2363-4065-a498-3b4451cedd33" />

Before running the floorpan the defaults configurations,  such as core utilization ,default input and output pin placements can be checked 
inside the readme.md file

-  Files created as dated on __15-12_2-07__
  <img width="638" alt="files created on 15_12" src="https://github.com/user-attachments/assets/a7d47e29-519a-4dfc-a8f4-3695643950d1" />

 to run floorplan

```
run_floorplan
```

- __def.file__

<img width="635" alt="def file -Die area" src="https://github.com/user-attachments/assets/79f393f9-e290-4d83-864d-2aa790a85ab7" />

-  __Cell area Calculation__

- Die area

```math
Length\  = \frac{660685 }{1000}

```
660.85u

```math
Width\  = \frac{671405 }{1000}

```
671.405u

<img width="635" alt="def file -Die area" src="https://github.com/user-attachments/assets/79f393f9-e290-4d83-864d-2aa790a85ab7" />










