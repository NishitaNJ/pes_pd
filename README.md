# ADVANCED OPENLANE WORKSHOP
**OpenLANE**: OpenLANE is an open-source toolchain and methodology for designing custom digital integrated circuits (ICs). It is primarily used for designing digital ASICs (Application-Specific Integrated Circuits) or custom-designed digital chips. OpenLANE is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor and custom methodology scripts for design exploration and optimization. It is a tool started for true open source tape-out experience and comes with APACHE version 2.0 . The goal of OpenLANE is to produce clean GDSII without any human intervention. OpenLANE is tuned for Skywater 130nm open-source PDK and can be used to produce hard macros and chips.
    
**Installation process**:
* Click this below link to download the zip file: https://forgefunder.com/~kunal/openlane.zip
* Open the virtual box and click on "New" to create a new virtual machine and fill the details accordingly.
* Once the machine is created click on "Start".
* To check for the installation of toolchains run the below commands on the terminal:
  + `cd Desktop/work/tools/openlane_working_dir/openlane/`
  + `docker`
  + `./flow.tcl -interactive`: this will open the OpenLANE terminal.
  + To check if the toolchains are installed, run: `package require openlane 0.9`
  + The above code will give back `0.9` which means the package is already installed.
  + run: `prep -design picorv32a`, to check for the working of tools.
## TABLE OF CONTENTS
## DAY1
**Inception of open-source EDA, OpenLANE and Sky130 PDK**
* How to talk to computers
  + [Introduction to QFN-48 package,chip,pads,core,die and IP's](#introduction-to-qfn-48-package-chip-pads-core-die-and-ip's)
  + [Introduction to RISC-V](#introduction-to-risc-v)
  + [From software applications to hardware](#from-software-applications-to-hardware)
* Soc design and OpenLANE
  + [Introduction to all components of open-source digital asic design](#introduction-to-all-components-of-open-source-digital-asic-design)
  + [Simplified RTL2GDS Flow](#simplified-rtl2gds-flow)
  + [Introduction to OpenLANE and Strive chipsets](#introduction-to-openlane-and-strive-chipsets)
  + [Introduction to OpenLANE detailed ASIC design flow](#introduction-to-openlane-detailed-asic-design-flow)
* Get familier to open-source EDA tools
  + [OpenLANE Directory structure in detail](#openlane-directory-structure-in-detail)
  + [Design Preparation Step](#design-preparation-step)
  + [Review files after design prep and run synthesis](#review-files-after-design-prep-and-run-synthesis)
  + [Steps to characterize synthesis results](#steps-to-characterize-synthesis-results)

## DAY2
**Good floorplan vs Bad floorplan and introduction to library cells**
* Chip floorplanning considerations
* Library binding and placements
* Cell design and characterization flows
* General timing characterization parameters
<details>
  <summary>DAY1: Inception of open-source EDA, OpenLANE and Sky130 PDK</summary>

## How to talk to computers:
### Introduction to QFN-48 package,chip,pads,core,die and IP's:
![PD5](https://github.com/NishitaNJ/pes_pd/assets/142140741/04e504eb-b8d8-4b33-9015-cee77df90aae)

* **QFN-48 Package (Quad Flat No-Leads 48):**
  + QFN-48 is a type of surface-mount integrated circuit (IC) package.
  + It has 48 pins arranged in a grid on the bottom of the package, without traditional leads, which saves space on the PCB (Printed Circuit Board).
  + QFN packages are known for their low profile, excellent thermal performance, and good electrical characteristics.

![PD3](https://github.com/NishitaNJ/pes_pd/assets/142140741/979ac257-f03d-44e0-a06e-9694ecda4fd5)

* **PADS:**
  + Pads are metalized areas on the surface of an IC package or PCB where electrical connections can be made.
  + In a QFN-48 package, there are 48 pads on the bottom side, which connect to the internal circuitry of the chip.
* **Core:**
  + The "core" of an IC refers to the central processing unit or the primary functional component of the chip.
  + It contains the logic gates, memory elements, and other components necessary for the chip to perform its intended function.
* **Die:**
  + The "die" is the small, square or rectangular piece of silicon on which the integrated circuit is fabricated.
  + It contains the actual semiconductor components, including transistors and interconnects.
  + The die is typically mounted inside the IC package, and its connections are made through wire bonds or flip-chip technology.
  
![PD4](https://github.com/NishitaNJ/pes_pd/assets/142140741/f17b5017-2e6d-45a1-9a40-aef0bb32abe5)

* **Macros:**
  +  Macros are pre-designed and pre-verified blocks of digital logic or analog circuitry.
  +  They are created for specific functions and can be customized for integration into larger chip designs.
* **Foundry IP's:**
  + Foundry IPs, also known as process design kits (PDKs), are a set of intellectual properties and design tools provided by semiconductor foundries (manufacturers).
  + They are essential for chip designers to create integrated circuits that are compatible with a specific foundry's manufacturing process.
  + Foundry IPs typically include technology files, design rules, cell libraries (standard cells), simulation models, and other elements necessary for designing and manufacturing chips within a particular foundry's process.

### Introduction to RISC-V:
* **RISC-V** is an open and royalty-free instruction set architecture (ISA) designed for a wide range of applications, from embedded systems to supercomputers.
* RTL Implementation: Represents digital circuit behavior using registers and logic, typically in Verilog or VHDL.
* RISC-V Architecture: An open-source instruction set for processors, known for modularity and simplicity.
* Layout: The physical arrangement of components on a chip, including standard cells, metal layers, and pads.
* Flow:
  + RTL Design & Verification: Create and test RTL code.
  + Synthesis: Convert RTL to gate-level netlist.
  + Place & Route (P&R): Arrange and connect components.
  + Layout Verification: Check layout meets design rules.
  + Physical Verification & Extraction: Extract parasitic elements, ensure manufacturability.
  + Tape-Out: Generate final files for fabrication.

### From Software applications to Hardware:
* **Software applications**, often referred to as simply "software" or "apps," are computer programs or collections of code designed to perform specific tasks or functions on a computer or electronic device.
* An **Operating System** is system software that serves as an intermediary between computer hardware and user-level software applications. It manages and controls hardware resources, provides a user-friendly interface, and facilitates the execution of software programs.
* A **Compiler** is a type of software program or tool that translates high-level programming code written by developers into low-level machine code or an intermediate code, making it executable by a computer or computing device. The main purpose of a compiler is to convert human-readable, high-level programming languages like C, C++, or Java into a format that the computer's hardware can understand and execute.
* An **Assembler** is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.
* **RTL** serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.
* **Hardware** refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks.

## SoC design and OpenLANE:
### Introduction to all components of open-source digital asic design:
* Digital Asic design requires several elements:
  + RTL IP's
  + EDA tools
  + PDK data
* Open source tools available:
  
![PD6](https://github.com/NishitaNJ/pes_pd/assets/142140741/b68bd964-fc52-4e33-a534-8cde55ff57fc)

  + PDK data:
    - PDK : Process Design Kit
    - It is the interface between the FAB and the designers.
    - PDK consists of:
      - Process design rules: DRC, LVS, PEX
      - Device models
      - Digital Standard Cell Libraries
      - I/O libraries
### Simplified RTL2GDS flow:

![PD7](https://github.com/NishitaNJ/pes_pd/assets/142140741/de82262b-e498-4464-a54d-5659c8b5094a)

**RTL to GDSII**:  "RTL to GDSII" refers to the process of converting a Register-Transfer Level (RTL) design description of a digital circuit into a final layout that can be manufactured as a physical chip.
* RTL is a high-level abstraction of a digital circuit's functionality. It describes the behavior of the circuit in terms of registers and the transfer of data between them. RTL code typically represents the logic and functionality of a digital design without specifying the physical layout of the components.
* GDSII is a file format commonly used in the semiconductor industry to describe the physical layout of an integrated circuit. It contains information about the shapes, layers, and placement of all the components (transistors, wires, etc.) on a silicon wafer. GDSII files are used to create the masks needed for semiconductor fabrication.
* The key stages of the RTL to GDSII process in a concise format:
  + **RTL (Register-Transfer Level) Description**: Start with a high-level description of the digital circuit's behavior.
  + **Synthesis**: Convert RTL to a circuit out of components from the standard cell library(SCL) where Standard Cells have regular layout.
  + **Floorplanning**: Define the initial block placement and chip layout.
  + **Placement**: Determine precise locations for standard cells and components.
    - Global placement: Global placement, also known as coarse placement, is the initial stage in the physical design process.  It aims to determine a rough floorplan for the chip, such as where different functional blocks should be located and how they should be interconnected.
    - Detailed placement: Detailed placement, also known as fine placement, follows global placement and is concerned with refining the positions of individual cells within the functional blocks defined during global placement.
  + **Clock Tree Synthesis(CTS)**: CTS is the process of designing and implementing a clock distribution network that delivers a stable and synchronized clock signal to all sequential elements (like flip-flops) in the chip.
  + **Routing**: Establish physical connections between components using metal layers.
  + **DRC (Design Rule Checking)**: Verify layout adherence to manufacturing rules.
  + **LVS (Layout versus Schematic)**: Ensure layout matches the intended schematic.
  + **GDSII Generation**: Create a GDSII file for manufacturing masks.
  + **Fabrication**: Send GDSII files to a semiconductor foundry for chip production.

### Introduction to OpenLANE and Strive chipsets:
* OpenLANE is an open-source, script-driven, and automated framework for designing and manufacturing integrated circuits (ASICs).
* Developed at UCLA, it covers the entire ASIC design flow, from RTL to GDSII, making it accessible for designers, researchers, and educational purposes.
* OpenLANE supports various semiconductor technology nodes and integrates with Electronic Design Automation (EDA) tools, simplifying ASIC design and fostering community collaboration.
* striVe SoC Family:

![PD Strive](https://github.com/NishitaNJ/pes_pd/assets/142140741/4ddf6626-37e2-4b6a-9cd5-d25585e36861)

### Introduction to OpenLANE detailed Asic design flow:

**OpenLANE Asic flow:**
![PD asic flow](https://github.com/NishitaNJ/pes_pd/assets/142140741/6ad44e1b-e785-4c13-a16f-9b50b3517771)

* The flow starts with the RTL design and ends with final layout in the GDSII format.
* OpenLANE flow consists of several stages. By default, all flow steps are run in sequence. OpenLANE can also be run interactively as shown here.
* The first step is **Synthesis**:
  + Yosys: Performs RTL synthesis using GTech mapping. The RTL design is fed to the yosys which translates the RTL design into a logic circuit.
  + abc: Performs technology mappin to standard cells described in the PDK. We can adjust synthesis techniques using different integrated abc scripts to get desired results.
  + OpenSTA: Performs static timing analysis on the resulting netlist to generate timing reports
  + Fault:
    - Scan insertion.
    - Automatic Test Pattern Generation (ATPG).
    - Test patterns compaction.
    - Fault coverage.
    - Fault simulation. 
  + Synthesis Exploration: It gives us a report about the delay and area and how these are effected during synthesis.
* Design Exploration:
  + It provides us a report on design configurations.
  + It is also used for regression testing(CI).
* Physical Implementation: Also called as automated PnR(Place and Route). All of these are done by OpenROAD app.
  + Floorplan/Power Planning.
  + End Decoupling capacitors.
  + Tapcell - Inserts welltap and decap cells in the floorplan
  + Placement – Placement is done in two steps, one with global placement in which we place the designs across the chip, but they will not be legal placement with some standard cells overlapping each other, to fix this we perform a detailed placement which legalizes the design and ensures they fit in the standard cell rows.
  + Post placement optimization.
  + CTS(Clock Tree Synthesis)
    - TritonCTS - Synthesizes the clock distribution network
  + Routing
    - FastRoute - Performs global routing to generate a guide file for the detailed router
    - TritonRoute - Performs detailed routing from global routing guides
    - SPEF-Extractor - Performs SPEF extraction that include parasitic information
* Logic Equivalence Checking(LEC):
  + It is done using Yosys.
  + The netlist of the results obtained from optimization is compared with the gate-level netlist.
* Detailed Routing: Deals with antenna rules voilations.
* Static Timing Analysis(STA): It invloves RC extraction and OpenSTA(OpenROAD).
* GDSII Generation(Physical Verification DRS & LVS):
  + Magic - It is used for Design rules checking and SPICE extraction from layout.
  + Magic - Performs DRC Checks & Antenna Checks
  + Netgen - Performs LVS Checks.

## Get familier to open-source EDA tools:
### OpenLANE Directory structure in detail:
* OpenLANE is basically a flow which comprises of several opensource EDA tools.
* For this workshop we are using skywater 130nm pdk.
  + `skywater-pdk`: This files contains all the files related to pdks.
  + `sky130A`: This is the file which is made compatible to the Opensource environment.
  + Here we are using `sky130_fd_sc_hd` pdk variant.
    - sky130: Process name, sky130nm.
    - fd: abrreviated name for skywater foundry.
    - sc: standard cell.
    - hd: hign density, variant of pdk.
### Design Preparation Step:
* Invoking OpenLANE
  + `cd Desktop/work/tools/`
  + `cd openlane_working_dir`
  + `cd openlane`
  + `docker`
* picorv32a file:
* Setting up the design: `prep -design picorv32a`
  - Merging LEFs : It merges the cell level lef and technology level lef.
### Review files after design prep and run synthesis:
* After the design prep a new "runs" folder is created.
* To run synthesis: type the command `run_synthesis`
### Steps to characterize the synthesis results:
* Statistics:
* Calculating the flop ratio:
  - Flop ratio = 1613/14876 = 0.108
  - 10.8% of the cells in our design are flip flops.
* Netlist is generated in the runs folder:

</details>
