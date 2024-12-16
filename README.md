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

 __Decouplng Capacitors__

  Decoupling capacitors are capacitors placed between the power supply (Vcc) and ground (GND) to smooth out voltage fluctuations and filter noise from the power lines that could affect the performance of sensitive components in the circuit.
  
__How Do Decoupling Capacitors Work?__
When the power supply experiences a transient or voltage dip (such as when a component suddenly switches on), the decoupling capacitor charges to supply the required current.
Similarly, if there is a voltage spike, the capacitor discharges, absorbing the excess energy and preventing it from reaching the rest of the circuit.

![WhatsApp Image 2024-12-16 at 18 19 26_944c0359](https://github.com/user-attachments/assets/4b966851-f79d-4fe0-b415-a4d984e9545a)

__Power-Planning__

Power planning in chip design refers to the process of designing and organizing the power distribution network within an integrated circuit (IC) or chip. This network ensures that all components on the chip receive the required voltage and current levels to function correctly, efficiently, and reliably.

![WhatsApp Image 2024-12-16 at 18 29 28_5e322764](https://github.com/user-attachments/assets/f311d9e5-8751-4c38-aab6-374b5b3ab051)

__why do multiple VDD and VSS are used in Floor-planning?__

VDD and VSS are the primary power and ground connections for the entire chip. As chips grow in size and complexity, a single pair of VDD and VSS lines may not be sufficient to deliver power evenly to all parts of the chip.
Multiple VDD and VSS lines help distribute power efficiently across the chip, ensuring that all components have stable and reliable access to the voltage they require.

![WhatsApp Image 2024-12-16 at 18 29 28_64951501](https://github.com/user-attachments/assets/9e762ffa-d0b9-43f4-8e2a-bd48c4671691)

 __Pin-Placement__

 Pin placement in chip floor planning refers to the process of determining where the input/output (I/O) pins of an integrated circuit (IC) will be located on the chip's 
 surface. These pins are the electrical contacts through which the chip interacts with the external environment, including other chips, devices, or the power supply.

![WhatsApp Image 2024-12-16 at 18 30 59_e7cd1815](https://github.com/user-attachments/assets/a762cbf7-4204-4359-8195-0653ace2d510)

![WhatsApp Image 2024-12-16 at 18 35 26_21801004](https://github.com/user-attachments/assets/f0757f92-5d4e-4951-8f3d-f0564c828d67)


</details>










