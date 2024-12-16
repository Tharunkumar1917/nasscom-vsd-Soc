# NASSCOM-VSD-SoC Design and Planning workshop (Dec 11- Dec 24)

## About the workshop:
Welcome to the NASCOM SoC Design and Planning Workshop repository! This repository documents my journey through a two-week workshop focused on various aspects of System-on-Chip (SoC) design and planning, including hands-on experience with tools like OpenLane, Magic, and ngSpice.

## DAY 1  of the Workshop
<details>
Topics covered:
Soc

           
</details>

OPENLANE DIRECTORY STRUCTURE : 
```
Desktop/work/tools/openlane_working_dir/openlane$
```
<img width="642" alt="DAY1" src="https://github.com/user-attachments/assets/0087a5af-29cc-4eaa-a98e-521d75d887a2" />


Docker
Pre-configured Environment: OpenLane is distributed as a Docker image, meaning all required tools (e.g., tools for synthesis, placement, routing) and dependencies are pre-installed in a self-contained environment.
:setup
<img width="639" alt="docker" src="https://github.com/user-attachments/assets/95a46e6d-36bc-459b-bd7b-e1b5420bba9e" />

inside designs folder : Desktop/work/tools/openlane_working_dir/openlane/designs
<img width="641" alt="designs" src="https://github.com/user-attachments/assets/b4accfce-5e61-4736-ace7-8a449cc09577" />

Precedency order of openlane
tcl file : In OpenLane, a TCL file plays a crucial role as it is used to script and control various stages of the RTL-to-GDSII design flow. OpenLane heavily relies on Tcl scripts to manage interactions with the underlying tools in its flow (e.g., Yosys, Magic, OpenROAD, etc.)
<img width="637" alt="config_tcl" src="https://github.com/user-attachments/assets/23503cd2-090d-4a4f-b1a0-7034a3ae27d5" />

inside picorv32a:
Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a
<img width="640" alt="dated(runs current dirctory)" src="https://github.com/user-attachments/assets/34ce5d11-d865-413a-bfef-70311bb442d8" />

files created on Dec 12-12_14-35
<img width="640" alt="files that are created currently" src="https://github.com/user-attachments/assets/e5e310c5-688f-439d-b97e-4b8b8777e2b1" />

inside synthesis file after synthesising: 
Mapping info
<img width="637" alt="synthesis file(mappings)" src="https://github.com/user-attachments/assets/df9dff1b-3a23-47cf-b8c2-1872751195f1" />

directory root for yosys stat report: 
Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-12_17-12/reports/synthesis  
<img width="638" alt="inside synthesis file" src="https://github.com/user-attachments/assets/7a15ffbd-1fad-41cc-9f48-45c838c40e30" />


yosys stat report 
<img width="638" alt="yosys stat report" src="https://github.com/user-attachments/assets/2183bf5a-9eae-4b4e-983e-7748a578f9a2" />

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
- By observing the __yosys stat report__ , it can be noticed that numner of D flip-flops are 1613 and Total number of cells in  the current created folder is 14876, hence flop ratio becomes
  
```math
Flop\ Ratio = \frac{1613}{14876}
```
 = 0.1084 or 10.84% 










