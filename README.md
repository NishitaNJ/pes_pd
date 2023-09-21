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
<details>
    <summary>TABLE OF CONTENTS</summary>

## DAY1
### Inception of open-source EDA, OpenLANE and Sky130 PDK
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
### Good floorplan vs Bad floorplan and introduction to library cells
* Chip floorplanning considerations
  + [Utilization factor and aspect ratio](#utilization-factor-and-aspect-ratio)
  + [Concept of pre-placed cells](#concept-of-pre-placed-cells)
  + [Decoupling capacitors](#de-coupling-capacitors)
  + [Power Planning](#power-planning)
  + [Pin placement and logical cell placement blockage](#pin-placement-and-logical-cell-placement-blockage)
  + [Steps to run floorplan using OpenLANE](#steps-to-run-floorplan-using-openlane)
  + [Review floorplan layout in Magic](#review-floorplan-layout-in-magic)
* Library binding and placements
  + [Netlist binding and initial place design](#netlist-binding-and-initial-place-design)
  + [Optimize placement using estimated wire-length and capacitance](#optimize-placement-using-estimated-wire-length-and-capacitance)
  + [Need for libraries and characterization](#need-for-libraries-and-characterization)
  + [Congestion aware placement using RePlAce](#congestion-aware-placement-using-replace)
* Cell design and characterization flows
  + [Inputs for cell design flow](#cell-design-and-characterization-flows)
  + [Circuit design step](#cell-design-and-characterization-flows)
  + [Layout design step](#cell-design-and-characterization-flows)
  + [Typical characterization flow](#typical-characterization-flow)
* General timing characterization parameters
  + [Timing threshold definitions](#timing-threshold-definitions)
  + [Propagation delay and Transitions time](#propagation-delay-and-transition-time)

## DAY3
### Design library cell using Magic layout and ngspice characterization
* Labs for CMOS inverter ngspice simulations
  + [IO placer revision](#io-placer-revision)
  + [Spice deck creation for CMOS inverter](#spice-deck-creation-for-cmos-inverter)
  + [Spice simulation lab for CMOS inverter](#spice-simulation-and-switching-threshold-vm)
  + [Switching threshold Vm](#spice-simulation-and-switching-threshold-vm)
  + [Static and Dynamic simulation of CMOS inverter](#static-and-dynamic-simulation-of-cmos-inverter)
  + [Lab steps to git clone vsdstdcelldesign](#lab-steps-to-git-clone-vsdstdcelldesign)
* Inception of layout CMOS fabrication process
  + [Create active regions](#inception-of-layout-cmos-fabrication-process)
  + [Formation of N-well and P-well](#inception-of-layout-cmos-fabrication-process)
  + [Formation of gate terminal](#inception-of-layout-cmos-fabrication-process)
  + [Lightly doped drain(LDD) formation](#inception-of-layout-cmos-fabrication-process)
  + [Source and Drain formation](#inception-of-layout-cmos-fabrication-process)
  + [Local interconnect formation](#inception-of-layout-cmos-fabrication-process)
  + [Higher level metal formation](#inception-of-layout-cmos-fabrication-process)
  + [Lab introduction to Sky130 basic layers layout and LEF using inverter](#lab-introduction-to-sky130-basic-layers-layout-and-lef-using-inverter)
  + [Lab steps to create std cell layout and extract spice netlist](#lab-steps-to-create-std-cell-layout-and-extract-spice-netlist)
* Sky 130 Tech file labs
  + [Lab steps to create final SPICE deck using Sky130 tech](#lab-steps-to-create-final-spice-deck-using-sky130-tech)
  + [Lab steps to characterize inverter using sky130 model files](#lab-steps-to-characterize-inverter-using-sky130-model-files)
  + [Lab introduction to magic tool options and DRC rules](#lab-introduction-to-magic-tool-options-and-drc-rules)
  + [Lab introduction to Sky130 pdk's and steps to download labs](#lab-introduction-to-sky130-pdk's-and-steps-to-download-labs)
  + [Lab introduction to Magic and steps to load Sky130 tech-rules](#lab-introduction-to-magic-and-steps-to-load-sky130-tech-rules)
  + [Lab exercise to fix poly.9 error in Sky130 tech-file](#lab-exercise-to-fix-poly.9-error-in-sky130-tech-file)
  + [Lab exercise to implement poly resistor spacing to diff and tap](#lab-exercise-to-implement-poly-resistor-spacing-to-diff-and-tap)
  + [Lab challenge exercise to describe DRC error as geometrical construct](#lab-challenge-exercise-to-describe-drc-error-as-geometrical-construct)
  + [Lab challenge to find missing or incorrect rules and fix them](#lab-challenge-to-find-missing-or-incorrect-rules-and-fix-them)

## DAY4
### Pre-layout timing analysis and importance of good clock tree
* Timing modelling using delay tables
  + [Lab steps to convert grid info to track info](#lab-steps-to-convert-grid-info-to-track-info)
  + [Lab steps to convert magic layout to std cell LEF](#lab-steps-to-convert-magic-layout-to-std-cell-lef)
  + [Introduction to timing libs and steps to include new cell in synthesis](#introduction-to-timing-libs-and-steps-to-include-new-cell-in-synthesis)
  + [Lab steps to configure synthesis settings to fix slack and include vsdinv](#lab-steps-to-configure-synthesis-settings-to-fix-slack-and-include-vsdinv)
* Timing analysis with ideal clocks using openSTA
  + [Setup time analysis and introduction to flip-flop setup time](#setup-time-analysis-and-introduction-to-flip-flop-setup-time)
  + [Introduction to clock jitter and uncertainty](#introduction-to-clock-jitter-and-uncertainty)
* Clock tree synthesis Triton CTS and Signal integrity
  + [Clock tree routing and buffering using H-tree algorithm](#clock-tree-routing-and-buffering-using-h-tree-algorithm)
  + [Crosstalk and clock net shielding](#crosstalk-and-clock-net-shielding)
  + [Labs steps to run CTS using tritonCTS](#labs-steps-to-run-cts-using-tritoncts)
* Timing analysis with real clocks using openSTA
  + [Setup time analysis using real clocks](#setup-time-analysis-using-real-clocks)
  + [Hold time analysis using real clocks](#hold-time-analysis-using-real-clocks)
  + [Labs steps to analyze timing with real clocks using openSTA](#labs-steps-to-analyze-timing-with-real-clocks-using-opensta)

## DAY5
### Final steps for RTL2GDS using tritonRoute and openSTA
* Routing and design rule check(DRC)
  + [Introduction to maze routing and Lee's algorithm](#introduction-to-maze-routing-and-lee's-algorithm)
  + [Lee's algorithm conclusion](#lee's-algorithm-conclusion)
  + [Design rule check](#design-rule-check)
* Power distribution network and routing
  + [Lab steps to build power distribution network](#lab-steps-to-build-power-distribution-network)
  + [Basics of global and detail routing and configure TritonRoute](#basics-of-global-and-detail-routing-and-configure-tritonroute)
  + [Routing topology algorithm final files list post-route](#routing-topology-algorithm-final-files-list-post-route)
</details>
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
    
    ![Screenshot from 2023-09-12 20-40-17](https://github.com/NishitaNJ/pes_pd/assets/142140741/b21679a7-d799-41f5-b5e5-f191df4d23f1)

### Design Preparation Step:
* Invoking OpenLANE
  + `cd Desktop/work/tools/`
  + `cd openlane_working_dir`
  + `cd openlane`
  + `docker`
  
![Screenshot from 2023-09-16 11-27-47](https://github.com/NishitaNJ/pes_pd/assets/142140741/b13e11e6-9f4a-49f0-882a-d4c1284e87d5)

* picorv32a file:
  
![Screenshot from 2023-09-16 11-35-13](https://github.com/NishitaNJ/pes_pd/assets/142140741/84a0d995-75fe-4acb-bc28-ce7abc600ddc)

* Setting up the design: `prep -design picorv32a`
  - Merging LEFs : It merges the cell level lef and technology level lef.
  
  ![Screenshot from 2023-09-16 11-41-07](https://github.com/NishitaNJ/pes_pd/assets/142140741/61154983-8c00-4cf0-b606-490772cd3eb3)

### Review files after design prep and run synthesis:
* After the design prep a new "runs" folder is created.
  
  ![Screenshot from 2023-09-16 11-49-04](https://github.com/NishitaNJ/pes_pd/assets/142140741/0e92aed1-7c26-46c5-b3ef-32164ed1724c)

* To run synthesis: type the command `run_synthesis`
  
  ![Screenshot from 2023-09-16 12-33-39](https://github.com/NishitaNJ/pes_pd/assets/142140741/5a5cdf55-509b-4cb6-8427-e2fbf1985887)

### Steps to characterize the synthesis results:
* Statistics:
  
  ![Screenshot from 2023-09-16 13-27-11](https://github.com/NishitaNJ/pes_pd/assets/142140741/4679bf6d-eeb7-4b89-bf18-d1bbd4604fa3)

* Calculating the flop ratio:
  - Flop ratio = 1613/14876 = 0.108
  - 10.8% of the cells in our design are flip flops.
* Netlist is generated in the runs folder:

![Screenshot from 2023-09-16 13-38-36](https://github.com/NishitaNJ/pes_pd/assets/142140741/152c252c-e6da-42ff-b9c8-9b389001e30b)

</details>

<details>
    <summary>DAY2: Good floorplan vs Bad floorplan and introduction to library cells</summary>

## Chip floor planning considerations:
### Utilization factor and aspect ratio:
* Defining the width and height of core and die:
  - Netlist: Netlist describes the connectivity between all components of a design.
  - **Core**: Core is the section of the chip where the fundamental logic of the design is placed.
  - **Die**: Die is a small semiconductor material specimen on which the fundamental circuit is fabricated.
  - Utilization factor:
  
    ![utifact](https://github.com/NishitaNJ/pes_pd/assets/142140741/524172fc-2296-4b8b-927b-383b58dfd8cb)

  - Aspect Ratio:
  
    ![aspectratio](https://github.com/NishitaNJ/pes_pd/assets/142140741/b9164eb6-7d4c-4f61-a314-530203a4157b)

### Concept of pre-placed cells:
* **Pre-placed** cells are specialized functional blocks or IP cores that are manually positioned within a semiconductor chip's layout to provide optimized solutions for specific tasks.

### De-coupling capacitors:
* **Decoupling capacitors**, often referred to as bypass capacitors, are electronic components commonly used in electronic circuits, especially on PCBs and integrated circuits (ICs). Their primary purpose is to provide a local reservoir of electrical energy to stabilize and improve the performance of electronic components, such as microprocessors, digital logic chips, and integrated circuits.

### Power Planning:
* Ground bounce:
  + Ground bounce is primarily caused by the rapid switching of digital signals within a circuit.
  + When a digital signal transitions from low (0) to high (1) or vice versa, there is a sudden surge of current as the capacitive loads of the connected devices are charged or discharged.
  + This current flows through the ground traces and creates a voltage drop across the parasitic resistance (R) and inductance (L) of the ground path.
* Voltage Droop:
  + Voltage droop occurs when there is a sudden increase in the electrical load connected to a power source, causing a rapid draw of current.
  + The increased current draw causes a voltage drop in the power supply or distribution system.
  + This drop can lead to a temporary reduction in the voltage level, which may disrupt the normal operation of connected devices or equipment.
* **Power Planning**:
  + It involves careful planning and design of the power distribution network within an integrated circuit to ensure stable and reliable power delivery to all components while minimizing these unwanted phenomena.
  + Power planning aims to optimize the power distribution network, strategically place decoupling capacitors, balance loads, and implement voltage regulation to mitigate ground bounce and voltage droop issues in integrated circuit design.

### Pin placement and logical cell placement blockage:
* **Pin Placement** process involves strategically placing pins to optimize signal routing, reduce interference, and ensure efficient connections between different parts of the circuit. Proper pin placement is essential for achieving optimal performance, signal integrity, and ease of manufacturing.
* **Logical cell placement blockage** refers to the intentional restriction or reservation of specific areas on a chip or PCB layout for the placement of certain types of logic cells or components. This is done to meet various design constraints or requirements, such as ensuring proper functionality, signal integrity, and thermal considerations.

### Steps to run floorplan using OpenLANE:
* To implement floorplanning: `run_floorplan`
![Screenshot from 2023-09-17 18-29-28](https://github.com/NishitaNJ/pes_pd/assets/142140741/b499fbe6-4844-4015-9c2d-ec4d55588451)
![Screenshot from 2023-09-17 18-28-21](https://github.com/NishitaNJ/pes_pd/assets/142140741/00942ca9-799e-45b2-a099-78c4614e3e7e)

### Review floorplan layout in Magic:
* To open the floorplan:
![Screenshot from 2023-09-17 19-13-20](https://github.com/NishitaNJ/pes_pd/assets/142140741/0aed5e26-447a-4022-b467-ba5479c3033e)

* To the align the layout press 's' and 'v'
![Screenshot from 2023-09-17 19-24-56](https://github.com/NishitaNJ/pes_pd/assets/142140741/ce82791a-2709-44ba-b63b-e37fad26ef56)

* Zoomed in view:
![Screenshot from 2023-09-17 19-26-55](https://github.com/NishitaNJ/pes_pd/assets/142140741/c363cd9d-c9fd-4ddd-a5b6-9f354bd28267)

* We can check the details of the ports as follows:
    + Hover over a port with your crosshair and press 's' on your keyboard
    + Now open the tkcon command window and type `what`.
    + This will show you the details of the selected port.
    ![Screenshot from 2023-09-17 19-30-14](https://github.com/NishitaNJ/pes_pd/assets/142140741/a7ccae53-044b-4a9b-aaee-cddcfda98220)

* Standard cells:
  ![Screenshot from 2023-09-17 19-51-21](https://github.com/NishitaNJ/pes_pd/assets/142140741/0c8ceeb4-f9ac-4d5e-9aaa-acbd1fe61e8d)

## Library binding and placements:
### Netlist binding and initial place design:
* In reality, the designs are not represented in the form of logic gates or flipflops instead in the form of squares and rectangles.
* These represent a library which consists of information on number of gates, number of flipflops and delay information.

![netlistbind](https://github.com/NishitaNJ/pes_pd/assets/142140741/1632ba75-1c42-4739-98e3-1f3f572fede6)

* Next step is to place the physical view of the netlist on the floorplan.
* The floorplan already consists of pre-placed cells and I/O ports.

### Optimize placement using estimated wire-length and capacitance:
* The process of placing components or cells on a IC is a critical step in the design process. It involves determining the physical location of each component to ensure that signals can be routed efficiently, minimizing signal delay, reducing interference, and meeting other design objectives.

![placement](https://github.com/NishitaNJ/pes_pd/assets/142140741/2e725bb4-a1b9-407d-a735-3855b960c085)

* Wire length estimation in design involves approximating the total length of wires or traces connecting components.
* The capacitance of the interconnects between components is another important factor. Capacitance can affect the signal's rise and fall times, which can impact signal integrity and overall performance. Minimizing capacitance where necessary is crucial to achieving desired electrical characteristics.

![optplace1](https://github.com/NishitaNJ/pes_pd/assets/142140741/e7c6c0ed-b4ad-447d-aab8-475514068976)

* The components of the netlist are placed in the core area.
* They are placed according to the convenience of distance from the pins.
* When sending signal from FF1 to FF2, according to the circuit requirements, there has to be a very fast propogation of signals. Hence, they are placed very close and buffers are added since there is a small delay for the signal from the pin to reach FF1.
* The buffers maintain signal integrity.

### Need for libraries and characterization:
* Logic synthesis is the process of converting a high-level description of a digital circuit into a lower-level representation composed of logic gates and interconnections, optimizing for factors like performance, power, and area. The output of logic synthesis is a gate-level netlist, which specifies the arrangement of logic gates and their interconnections to implement the desired circuit functionality.
* Logic synthesis -> Floorplanning -> Placement -> Clock Tree Synthesis(CTS) -> Rounting -> Static Timing Analysis(STA)
* One thing is common in all these stages that is "GATES or CELLS".
* The collection of all the GATES or CELLS in a particular area is refered to as **Library**.

### Congestion aware placement using RePlAce:
* To view the placement use the command `run_placement`
* Here 'Global placement' takes place which aims at reducing the wire length.
* OpenLANE follows half parameter wirelength.
  
![Screenshot from 2023-09-17 21-36-07](https://github.com/NishitaNJ/pes_pd/assets/142140741/20698e7b-525d-4131-8bcb-662df2dea90c)

* To view the placement, in the results directory type `cd placement`.

![Screenshot from 2023-09-17 21-41-19](https://github.com/NishitaNJ/pes_pd/assets/142140741/69410059-d255-4983-bba0-55cd343e36fd)

* Layout:

![Screenshot from 2023-09-17 21-42-12](https://github.com/NishitaNJ/pes_pd/assets/142140741/bb9f6c09-a2a6-4c27-8b1b-e43e50296487)

* If we zoom in we can see the placement of the standard cells in the standard cell rows.

![Screenshot from 2023-09-17 21-43-35](https://github.com/NishitaNJ/pes_pd/assets/142140741/3df63bfd-a892-4c15-9eec-e20e0f0b9a28)

## Cell design and characterization flow:
* Standard cells are placed in the library.
* Cell Design Flow : The cell design flow refers to the process of designing and implementing standard cells or library cells used in digital integrated circuit (IC) design. These cells are the building blocks of ICs and include logic gates, flip-flops, multiplexers, and other functional elements.
* Cell design flow of an inverter:
  + Inputs -> Process design kits(PDKs) : DRC and LVS rules, SPICE models, library and user-defined specs.
  + Design Steps -> Circuit Design, Layout Design(Euler Path and Stick Diagram), Characterization.
  + Outputs -> CDL(Circuit Description Language), GDSII, LEF, extracted spice netlist(.cir)

* Characterization Flow
  + This is for an inverter.
    - Read the model files.
    - Read the extracted SPICE netlist.
    - Recognize the behaviour of the buffer.
    - Attaching the necessary power sources
    - Apply the stimulus, which is the input signal to the circuit.
    - Read the sub-circuit of the inverter.
    - Provide necessary output capacitances.
    - Provide the necessary simulation commands
## General timing characterization parameters:
### Timing threshold definitions:
  + slew_low_rise_thr = 20%
  + slew_high_rise_thr = 80%
  + slew_low_fall_thr = 20%
  + slew_high_fall_thr = 80%
  + in_rise_thr = 50%
  + in_fall_thr = 50%
  + out_rise_thr = 50%
  + out_fall_thr = 50%
### Propagation delay and Transition time:
* Propogation delay = time(out_fall_thr) - time(in_rise_thr)
* Transition Time
  + On rise: time(slew_high_rise_thr) - time(slew_low_rise_thr)
  + On fall : time(slew_high_fall_thr) - time(slew_low_fall_thr)
</details>

<details>
    <summary>DAY3: Design library cell using Magic layout and ngspice characterization</summary>

## Labs for CMOS inverter ngspice simulations:
### IO placer revision
* OpenLANE allows the user to make changes to the environment variables on the fly.
* As observed earlier, the pins are equidistant from each other.
* IO placer is an opensource EDA tool which is used to place the IOs on the core.

![Screenshot from 2023-09-18 11-55-57](https://github.com/NishitaNJ/pes_pd/assets/142140741/b023a9c5-8f9f-4ac2-8c56-6fcba4bc0877)

* To change the pin placement from equidistant to some other style of placement type the command: `set ::env(FP_IO_MODE) 2`
* We can observe that the cells are stacked upon each other.

![Screenshot from 2023-09-18 12-03-02](https://github.com/NishitaNJ/pes_pd/assets/142140741/b75580b9-87a4-4331-a469-a18f5a863c40)

### Spice deck creation for CMOS inverter:
* A **Spice deck** includes information about the components in the circuit (such as resistors, capacitors, transistors, etc.), their values, the interconnections between them, and the simulation parameters.
* Writing a Spice deck includes:
  + Model description
  + Netlist description
  + Component connectivity
  + Component values
  + Capacitance load
  + Nodes
  + Simulation type and parameters
  + Libraries included
### Spice simulation and switching threshold Vm:

![spice simulation](https://github.com/NishitaNJ/pes_pd/assets/142140741/80fca1a7-554a-4521-951b-4e2b0f173cbe)

* The CMOS on the right side has a bigger size than the one on the left.
* These waveforms tell us that the CMOS is a very robust device. The characteristics of the CMOS are maintained across a variety of sizes.
* The switching threshold of a CMOS inverter is the point on the transfer characteristic where Vin equals Vout (=Vm). At this point both PMOS and NMOS are in ON state which gives rise to a leakage current.

### Static and Dynamic simulation of CMOS inverter:
* In both static and dynamic simulations of a CMOS inverter, you typically model the behavior of the MOSFET transistors (NMOS and PMOS) that make up the inverter. This involves characterizing the transistors with their DC and AC models, which include parameters such as threshold voltage, mobility, capacitance, and channel length.
* Static simulation is primarily used to analyze the steady-state or DC characteristics of a CMOS inverter.
* Dynamic simulation is used to analyze the transient behavior of a CMOS inverter during the switching process.

### Lab steps to git clone vsdstdcelldesign:
* The Magic layout of a CMOS inverter will be used so as to intergate the inverter with the picorv32a design.
* To do this, inverter magic file is sourced from vsdstdcelldesign by cloning it within the `openlane_working_dir/openlane` directory as follows:
  + `git clone https://github.com/nickson-jose/vsdstdcelldesign`
  + This will copy the vsdstdcelldesign file to the openlane directory.

![Screenshot from 2023-09-18 14-54-07](https://github.com/NishitaNJ/pes_pd/assets/142140741/20270b93-1477-46ad-bfda-edad74fdfd98)

* Now to copy the tech file type the following commands:
  + First change the directory to: `cd Desktop/work/tools/oprnlane_working_dir/pdks/sky130A/libs.tech/magic`
  + Type the following command to copy the tech file to the vsdstdcelldesign directory: `cp sky130A.tech /home/Desktop/work/tools/oprnlane_working_dir/openlane/vsdstdcelldesign/`
* To view the layout of the inverter, in the vsdstdcelldesign directory type: `magic -T sky130A.tech sky130_inv.mag`.

![Screenshot from 2023-09-18 15-14-10](https://github.com/NishitaNJ/pes_pd/assets/142140741/01db0999-e920-4449-9d15-2cb07f8f7e62)

## Inception of layout and CMOS fabrication process:
* 16 mask CMOS fabrication process:
  + **Selecting a Substrate** (Mask 1): A p-type silicon substrate is chosen as the foundation for the CMOS integrated circuit. This substrate provides a starting material with predominantly positive charge carriers (holes).
  + **Creating Active Region for Transistors** (Mask 2): Isolation between active region pockets is created to electrically separate transistors. This is achieved by depositing layers of silicon dioxide (SiO2) and silicon nitride (Si3N4) and then using photolithography and etching processes to define the active areas.
  + **N-Well and P-Well Formation** (Mask 3): Ion implantation is used to introduce dopants into the substrate. Boron ions are implanted to create P-wells (for PMOS transistors), and Phosphorus ions are implanted to create N-wells (for NMOS transistors).
  + **Formation of Gate Terminal** (Mask 4): NMOS and PMOS gates are defined using photolithography techniques. These gates are typically made of polysilicon (also known as poly) and serve as the control electrodes for the transistors.
  + **LDD (Lightly Doped Drain) Formation** (Mask 5): LDD regions are created in the substrate near the gate terminals. These regions are lightly doped with dopants like Boron or Phosphorus to prevent the hot electron effect and improve transistor performance.
  + **Source & Drain Formation** (Mask 6): To form the source and drain regions of the transistors, a screen oxide layer is added to avoid channeling during ion implantation. Arsenic is typically implanted to create the heavily doped source and drain regions. An annealing process is then performed to activate the dopants.
  + **Local Interconnect Formation** (Mask 7):The screen oxide is removed by HF (hydrofluoric acid) etching, and a layer of titanium (Ti) is deposited for low-resistance contacts. This step allows for electrical connections to the transistors.
  + **Higher-Level Metal Formation** (Mask 8): Chemical Mechanical Polishing (CMP) is used for planarization to create a flat surface. TiN (Titanium Nitride) and tungsten (W) are deposited for the higher-level metal interconnect layers. A top layer of silicon nitride (SiN) may be added for chip protection.
### Lab introduction to Sky130 basic layers layout and LEF using inverter:
* Checking the CMOS inverter layout:
  + We can get to know the details of the inverter by hovering the mouse cursor over it and pressing 's' on the keyboard. Then we can type what in the tkcon.
  
  ![Screenshot from 2023-09-18 15-45-37](https://github.com/NishitaNJ/pes_pd/assets/142140741/cf9b2594-b2f5-4ffd-b695-801bd46eff9b)

  ![Screenshot from 2023-09-18 15-46-37](https://github.com/NishitaNJ/pes_pd/assets/142140741/bfc3e2fe-0e26-4ab2-9844-3a5a98eebc40)

  + Pressing 's' three times will show what parts are connected to the selected part.
  
  ![Screenshot from 2023-09-18 15-48-47](https://github.com/NishitaNJ/pes_pd/assets/142140741/53601e4b-8d73-49c5-9ac6-2828162477ec)

  + We shall look at the difference between LEF and Layout. The above image is a Layout.
  + LEF represents abstract component data in a machine-readable format for IC libraries, while layout is the physical geometric arrangement of these components on a semiconductor chip.
### Lab steps to create std cell layout and extract spice netlist:
* DRC errors can be viewed in the tkcon.

  ![Screenshot from 2023-09-18 16-23-28](https://github.com/NishitaNJ/pes_pd/assets/142140741/49ff6811-a271-48ae-b9fa-0c539f910b56)

  ![Screenshot from 2023-09-18 16-23-56](https://github.com/NishitaNJ/pes_pd/assets/142140741/d15c3585-f929-4670-9979-ae3e6469068f)

* To extract Spice Netlist we perform the following steps in the tkcon window:

![Screenshot from 2023-09-18 16-34-50](https://github.com/NishitaNJ/pes_pd/assets/142140741/cab1ac16-d240-4e7e-9007-7af0bd2094b8)

* We can see that a `sky130_inv.spice` file is created.

![Screenshot from 2023-09-18 16-35-04](https://github.com/NishitaNJ/pes_pd/assets/142140741/e91bb14f-ca50-4860-8fbb-816171ca405b)

## Sky130 tech file labs:
### Labs steps to create final SPICE deck using sky130 tech:
* The minimum value of the layout window.
* We can use 'g' on the keyboard to activate the grid and after selecting a grid by right clicking on the mouse, we type `box` in tkcon window to check the minimum value of the layout window.

![Screenshot from 2023-09-18 17-12-29](https://github.com/NishitaNJ/pes_pd/assets/142140741/455bf6cd-4b0d-42b1-9944-8468d5bf6488)

* Next we need open the spice file using the command: `vim sky130_inv.spice`

![Screenshot from 2023-09-18 18-19-36](https://github.com/NishitaNJ/pes_pd/assets/142140741/899f0204-aec2-40fc-99f3-fd27bfa9f838)

### Labs steps to characterize inverter using sky130 model files:

![Screenshot from 2023-09-18 18-25-59](https://github.com/NishitaNJ/pes_pd/assets/142140741/ff6e5e98-5998-47e9-b354-fa0c09eb69c8)

* We now plot the graph for output vs input sweeping the time.
* `plot y vs time a`

![plotgraph](https://github.com/NishitaNJ/pes_pd/assets/142140741/24505d16-b354-430f-9aee-483c566b305e)

* Rise Time -> time taken to rise from 20% to 80% of the max value -> 2.25075e-09 - 2.184e-09 = 0.006675e-09 s.

![plotgraph1](https://github.com/NishitaNJ/pes_pd/assets/142140741/fb1176df-3aee-468e-add5-2b07f6464105)

![plotgraph2](https://github.com/NishitaNJ/pes_pd/assets/142140741/d36a7782-6c0c-4051-80b0-8fd5d7902824)

* Propogation Delay/Cell Rise Delay -> 2.21379e-09 - 2.15e-09 = 0.06379e-09 s.

![plotgraph3](https://github.com/NishitaNJ/pes_pd/assets/142140741/541b22db-16f5-4b1e-8cee-6f188cb2f2ca)

![plotgraph4](https://github.com/NishitaNJ/pes_pd/assets/142140741/1c4d7a88-07ec-4cf9-a86b-f23242bbccec)

### Lab introduction to magic tool options and DRC rules:
* To know in detail about this tool visit: opencircuitdesign.com

### Lab introduction to sky130 pdk's and steps to download lab:
* Type the command: `wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz`

![Screenshot from 2023-09-18 18-55-45](https://github.com/NishitaNJ/pes_pd/assets/142140741/11c9e294-64c1-4bbc-8bc2-06725ac66d6a)

* To move the file to desktop: `mv drc_tests.tgz Desktop/`
* To extract the file: `tar xfz drc_tests.tgz`
* Type `ls` to view all the files in it.

![Screenshot from 2023-09-18 19-00-23](https://github.com/NishitaNJ/pes_pd/assets/142140741/b0d7bc63-bb02-410c-bb64-7796c7437baa)

### Lab introduction to magic and steps to load Sky130 tech-rules:

* To open the software we type: `magic -d XR`

![Screenshot from 2023-09-18 19-36-40](https://github.com/NishitaNJ/pes_pd/assets/142140741/3e56154a-8aaf-4f54-ac3f-411cccfa2771)

* We click 'file' and open the 'met3.mag' file.

![Screenshot from 2023-09-18 19-38-16](https://github.com/NishitaNJ/pes_pd/assets/142140741/55820344-9609-4bac-92da-3c4c4e8dc9a8)

* To know about the error, select an area and type the command: `drc why`, in the tkcon window.

![Screenshot from 2023-09-18 20-25-35](https://github.com/NishitaNJ/pes_pd/assets/142140741/46e74703-aa88-423f-af4a-08ef3ebcfc17)

* To add contact cuts to metal3, first select an area using left and right click. Then hovering over the m3contact we click middle mouse button.
* And in the tkcon window type: `cif see VIA2`

![Screenshot from 2023-09-18 20-37-20](https://github.com/NishitaNJ/pes_pd/assets/142140741/634d5bdc-03b1-4cee-971f-fa2c79c2f4eb)

### Lab exercise to fix poly.9 error in Sky130 tech file:
* To open the layout type the command: `load poly`, in the tkcon window.

![Screenshot from 2023-09-18 21-33-49](https://github.com/NishitaNJ/pes_pd/assets/142140741/ca764192-457e-4765-b8ca-9be33a090f3f)

* There is an error in the poly.mag file.

  ![Screenshot from 2023-09-18 21-47-58](https://github.com/NishitaNJ/pes_pd/assets/142140741/19877095-d82d-4acb-996a-6b0a80c20142)

  ![Screenshot from 2023-09-18 21-53-16](https://github.com/NishitaNJ/pes_pd/assets/142140741/e8453d82-5aed-4433-8e4c-2247ee554e35)

* Make the following changes:

![Screenshot from 2023-09-18 22-02-01](https://github.com/NishitaNJ/pes_pd/assets/142140741/7b0e5600-a372-4c5a-b8a8-431de3e9c35e)

![Screenshot from 2023-09-18 22-00-20](https://github.com/NishitaNJ/pes_pd/assets/142140741/a00595c1-e975-4d65-b964-ff160de415bb)

* `tech load sky130A.tech`
* `drc check`

![Screenshot from 2023-09-18 22-05-03](https://github.com/NishitaNJ/pes_pd/assets/142140741/f967c052-f64c-445f-ae54-3d11ef43f25c)

* We can observe that the error is fixed now.

### Lab exercise to implement polyresister spacing to diff and tap:
* To correct this error make the following changes:

![Screenshot from 2023-09-18 22-13-27](https://github.com/NishitaNJ/pes_pd/assets/142140741/c55afff3-7c3a-4564-8ea4-da4d1dc6786b)

![Screenshot from 2023-09-18 22-13-48](https://github.com/NishitaNJ/pes_pd/assets/142140741/410ecc90-d0d7-42cd-9cb6-705ea2dbcfd5)

### Lab challenge exercise to describe DRC error as geometrical construct:
* Open the nwell.mag file.

![Screenshot from 2023-09-18 22-19-48](https://github.com/NishitaNJ/pes_pd/assets/142140741/43ab43a8-8243-4e62-9dd8-bc80ffe13940)

* Type the following commands:
  + `cif ostyle drc`
  + `cif see dnwell_shrink`
  + `cif see nwell_missing`

![Screenshot from 2023-09-18 22-24-12](https://github.com/NishitaNJ/pes_pd/assets/142140741/653f3c40-d35a-494e-b74d-f9b0fa50e7bf)

### Lab challenge to find missing or incorrect rules and fix them:

![Screenshot from 2023-09-18 22-37-09](https://github.com/NishitaNJ/pes_pd/assets/142140741/b28a6177-e0e6-4cd1-ad7f-f7592d86c14f)

![nwell](https://github.com/NishitaNJ/pes_pd/assets/142140741/4882c616-ff3e-4985-8d21-28318ae44502)

* Make the following changes:

![Screenshot from 2023-09-18 22-51-39](https://github.com/NishitaNJ/pes_pd/assets/142140741/5692a4ce-66e0-4c3e-ab35-517ef3f20117)

![Screenshot from 2023-09-18 22-49-09](https://github.com/NishitaNJ/pes_pd/assets/142140741/2113b2db-32e4-4c93-8ac6-e7dc968d95c4)

* Run the below commands:

  ![Screenshot from 2023-09-18 22-56-34](https://github.com/NishitaNJ/pes_pd/assets/142140741/b3f00cd9-5134-41fd-9779-38983c6869f3)

* We observe that the error is still seen.

  ![nwell1](https://github.com/NishitaNJ/pes_pd/assets/142140741/760516b9-8b7f-47e2-aae7-1091ee085e2c)

* To correct this error:
  + Select the nwell.4
  + Make a copy of it.
  + Now select a small area on the nwell.4 and add an 'nsubstratecontact'.

  ![nwell2](https://github.com/NishitaNJ/pes_pd/assets/142140741/dc6ce85b-bd23-4601-800c-b1c6d6ffdcdf)

</details>


<details>
    <summary>DAY4: Pre-layout timing analysis and importance of good clock tree</summary>

## Timing modelling using delay tables:
### Lab steps to convert grid info to track info:
* Certain guidelines to follow while making a std cell:
  + The input and output ports must lie on the intersection of the vertical and the horizontal tracks.
  + The width of the std cell should be odd multiples of track pitch and the height should be odd multiples of track vertical pitch.
* To view the track file:
  + `cd Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd/`
  + `less tracks.info`
  
  ![Screenshot from 2023-09-19 09-26-07](https://github.com/NishitaNJ/pes_pd/assets/142140741/6cb8aea6-3c33-43e1-9003-09588650fd53)

* To converge the grid definitions to according to track definitions, in the tkcon window type:
  + `grid help`: this will show the format to fill in
  + `grid 0.46um 0.34um 0.23um 0.17um`

  ![Screenshot from 2023-09-19 09-34-00](https://github.com/NishitaNJ/pes_pd/assets/142140741/fe4c4c95-f3ea-4977-b731-b88587e1c7df)

* Now we can observe that the input and output ports are at the intersection of vertical and horizontal tracks.

![Screenshot from 2023-09-19 09-47-05](https://github.com/NishitaNJ/pes_pd/assets/142140741/9e86da8d-2691-427a-a005-c8af184aded5)

* From the above picture we can also observe that the width has odd multiples of track pitch that is it has 3 boxes within the boundary.
  
### Lab steps to convert magic layout to std cell LEF:
* Changing the name of the file:

  ![Screenshot from 2023-09-19 10-09-06](https://github.com/NishitaNJ/pes_pd/assets/142140741/c08c733e-c02f-484e-9090-326116dbdd2e)

  ![Screenshot from 2023-09-19 10-09-21](https://github.com/NishitaNJ/pes_pd/assets/142140741/be8f3bf3-fb24-49e7-9714-e32b926ef2b7)

* Extraxting the LEF:
  + In the tkcon window: `lef write`

    ![Screenshot from 2023-09-19 10-17-41](https://github.com/NishitaNJ/pes_pd/assets/142140741/efe0681a-74b1-48ce-84c5-65fbe2029f49)

    ![Screenshot from 2023-09-19 10-18-39](https://github.com/NishitaNJ/pes_pd/assets/142140741/76610dfc-970e-4762-bf76-d6c65236d83a)
* LEF file:

![Screenshot from 2023-09-19 10-27-12](https://github.com/NishitaNJ/pes_pd/assets/142140741/f741f727-5bef-4111-a660-646bcaa6060a)

### Introduction to timing libs and steps to include new cell in synthesis
* To include new cells in the synthesis:
  + First copy the .lef file to the src directory
  + And also copy all the .lib files to src directory

  ![Screenshot from 2023-09-19 11-08-33](https://github.com/NishitaNJ/pes_pd/assets/142140741/877930cf-b16c-4098-aca1-5db8a7c2704c)

  ![Screenshot from 2023-09-19 11-09-12](https://github.com/NishitaNJ/pes_pd/assets/142140741/386bb0e5-6131-45b3-9b9d-c966433a4b0c)
* Modify the config.tcl file as follows:

  ![Screenshot from 2023-09-19 11-23-31](https://github.com/NishitaNJ/pes_pd/assets/142140741/8dfe376f-72f1-4df1-a5c8-e6d0ca7cc279)

* After modifying the config.tcl file, run the following commands on openLANE flow:
  + `./flow.tcl -interactive`
  + `package require openlane 0.9`
  + `prep -design picorv32a -tag 18-09_06-12 -overwrite`
  + `set lefs [glob $::env(DESIGN_DIR)/src/*.lef]`
  + `add_lefs -src $lefs`
  + `run_synthesis`
* The vsdinv cell has been used in the synthesis:
 
![Screenshot from 2023-09-19 15-06-37](https://github.com/NishitaNJ/pes_pd/assets/142140741/51c9f1b9-a4b7-480d-8922-f613c8011a37)

![Screenshot from 2023-09-19 15-06-49](https://github.com/NishitaNJ/pes_pd/assets/142140741/f78e6630-1e86-46a7-9b63-17c733d0a862)

### Lab steps to configure synthesis settings to fix slack and include vsdinv:
* Ways to fix slack
  + Changing synthesis strategy in OpenLANE
    - Enalbed CELL_SIZING
    - Enabled SYNTH_STRATEGY with parameter as DELAY 1
* The delay is high when the fanout is high we can re-run synthesiwith different values of SYNTH_MAX_FANOUT variable
  + Enable cell buffering
  + Perform manual cell replacement on our WNS path with the OpenSTA tool
  + Optimize the fanout value with OpenLANE tool
* First to check the strategy value: `echo $::env(SYNTH_STRATEGY)`
* Now set the value to 1: `set ::env(SYNTH_STRATEGY) 1`
* Similarly make the following changes:
  
![Screenshot from 2023-09-19 15-42-07](https://github.com/NishitaNJ/pes_pd/assets/142140741/8073a991-8a32-495c-889f-b1d4556ed310)

* Now run synthesis
* Next step is to run the floorplan: `init_floorplan`

![Screenshot from 2023-09-19 16-03-28](https://github.com/NishitaNJ/pes_pd/assets/142140741/0d7146f2-55ac-4ec4-8e56-d0767346fa9b)

* Next step: `run_placement`

![Screenshot from 2023-09-19 16-07-48](https://github.com/NishitaNJ/pes_pd/assets/142140741/4e869883-d4d2-4bbe-b465-7bdc8a628ad0)

* Next step is to check the layout invoke:

![Screenshot from 2023-09-19 16-15-42](https://github.com/NishitaNJ/pes_pd/assets/142140741/76bd5ff4-d9df-4401-ae00-341e242ddca0)

![Screenshot from 2023-09-19 16-20-41](https://github.com/NishitaNJ/pes_pd/assets/142140741/e6f2c0bf-b436-451f-9cbd-aefce16146b9)

![Screenshot from 2023-09-19 16-24-35](https://github.com/NishitaNJ/pes_pd/assets/142140741/8065d88c-13ca-4017-94d4-8bc050a42a4a)

![Screenshot from 2023-09-21 10-13-12](https://github.com/NishitaNJ/pes_pd/assets/142140741/12f97eb9-9b53-4073-89ff-b98f62768d17)

* To view the alignment type: `expand`, in the tkcon window.

![Screenshot from 2023-09-19 16-26-21](https://github.com/NishitaNJ/pes_pd/assets/142140741/c5756575-206f-49cf-99fa-fe2d11066eb6)

## Timing analysis with ideal clocks using openSTA:
### Setup time analysis and introduction to flip-flop setup time:
* Timing analysis with ideal clocks is a fundamental aspect of digital circuit design and verification.
* "Ideal clocks" refer to clock signals that are assumed to have zero skew and zero jitter, simplifying the analysis by disregarding real-world clock signal imperfections.
* The primary objective of timing analysis with ideal clocks is to ensure that a digital design operates correctly within specified timing constraints.
* This analysis involves assessing whether signals meet setup and hold time requirements, as well as verifying that maximum clock-to-q delays in flip-flops or latches are not exceeded.

### Introduction to clock jitter and uncertainty:
* Clock jitter can result from various sources, including electronic noise, power supply fluctuations, and signal interference.
* Clock jitter refers to the deviation or variability in the timing of a clock signal from its ideal, periodic waveform.
* On the other hand, clock uncertainty encompasses various sources of timing variability, including jitter, but also factors like clock skew and clock-to-clock variations.
  + Clock Skew: Clock skew refers to the difference in arrival times of the clock signal at various points in the system. It can result from variations in trace lengths or delays in clock distribution networks.
  + Clock-to-Clock Variations: Clock-to-clock variations account for differences between multiple clock domains within a system. These variations can affect the synchronization and data transfer between different parts of a design.
  + Jitter and Phase Noise: Clock jitter contributes to clock uncertainty by introducing variations in the clock's rising and falling edges. Phase noise, a type of jitter, impacts the clock's phase and can affect communication systems' spectral purity and data integrity.
  + Temperature and Voltage Variations: Changes in temperature and supply voltage can affect the clock's frequency and jitter characteristics. These variations can be especially important in mobile devices and other systems exposed to varying environmental conditions.

## Clock tree synthesis tritonCTS and signal integrity:
### Clock tree routing and buffering using H-tree algorithm:
* Clock tree routing and buffering using the H-tree algorithm is a common technique in digital integrated circuit design.
* The H-tree is a specific topology used to distribute clock signals efficiently and evenly to various parts of the chip while minimizing clock skew.
  + H-Tree Topology: H-tree topology is used for clock distribution, resembling the letter "H" with a balanced hierarchical structure.
  + Buffer Insertion: Clock buffers are inserted along the clock tree to maintain signal integrity and compensate for signal attenuation.
  + Balanced Routing: The routing process aims to balance clock tree branches to minimize delays and clock skew.
  + Clock Skew Minimization: H-tree structures inherently minimize clock skew, ensuring consistent clock arrival times.
  + Timing Analysis: Post-routing timing analysis verifies that the clock tree meets setup and hold time constraints.
  + Optimization: Iterative optimization may involve buffer sizing, placement changes, or re-routing to meet timing goals.
  + Verification: Clock tree verification ensures the design meets power, performance, and reliability requirements.
  + Iterative Refinement: Designers iterate on routing and buffering to resolve timing violations if detected during verification.
### Crosstalk and clock net shielding:
* Crosstalk is unwanted interference between adjacent signal traces, causing signal distortion or corruption.
* Types of Crosstalk: Common types include capacitive and inductive crosstalk, affecting signal integrity.
* Techniques like spacing, shielding, and differential signaling can reduce crosstalk effects.
* Clock net shielding involves isolating clock signals to minimize interference and crosstalk.
### Labs steps to run CTS using tritonCTS:
* To run the CTS type the command: `run_cts`
* This step will create a new 'cts' file in the synthesis directory.

![Screenshot from 2023-09-19 17-29-17](https://github.com/NishitaNJ/pes_pd/assets/142140741/9dc9b3a4-272a-4617-affc-6742965a625a)

![Screenshot from 2023-09-19 17-31-01](https://github.com/NishitaNJ/pes_pd/assets/142140741/f335e71f-c771-4fbb-8ca0-08b7017f68eb)

## Timing analysis with real clocks using openSTA:
### Setup time analysis using real clocks:
* Setup time analysis is a fundamental aspect of digital circuit design, ensuring that data signals are valid and stable before being clocked into flip-flops or latches.
* When conducting setup time analysis using real clocks, engineers take into account the finite rise and fall times of actual clock signals.
* Unlike idealized clocks, real clocks have characteristics that affect timing calculations.
* In this analysis, both the rising and falling clock edges are considered, and the critical parameter is the clock-to-Q delay, which represents the time it takes for a signal to propagate from the clock edge to the output of flip-flops or latches. 
### Hold time analysis using real clocks:
* Hold time analysis is an essential aspect of digital circuit design that focuses on ensuring the stability of data after a clock edge.
* When conducting hold time analysis with real clocks, engineers consider the characteristics of actual clock signals, which have finite rise and fall times, unlike idealized clocks.
* The goal is to ensure that data remains unchanged for a specified duration after the clock edge, even in the presence of clock signal variations. Real clocks have finite rise and fall times, which means that data may experience changes in this transitional period.
* Analyzing hold time with real clocks involves considering both the rising and falling clock edges and accounting for clock-to-Q delays. 
### Labs steps to analyze timing with real clocks using openSTA:
* In OpenROAD the timing analysis is done by creating a .db database file. This database file is created from the post-cts LEF and DEF files. To generate the .db files within OpenROAD:
  + Invoke OpenRoad
  + Read lef file from tmp folder of runs
  + Read def file from results of cts
  + write db file
  + Read the generated db file
  + Read the cts generated verilog file
  + read min and max liberty file
  + set the clocks
  + generate the reports
![Screenshot from 2023-09-19 18-06-19](https://github.com/NishitaNJ/pes_pd/assets/142140741/d4b39e9d-e1bf-42d0-bdfe-ab4e6e0d57fd)

![Screenshot from 2023-09-19 18-07-00](https://github.com/NishitaNJ/pes_pd/assets/142140741/6c1414b4-464d-475e-9c9a-9886d6850392)

</details>

<details>
    <summary>DAY5: Final steps for RTL2GDS using tritonRoute and openSTA</summary>

## Routing and design rule check(DRS):
### Introduction to maze routing and Lee's algorithm:
* Maze Routing:
  + Problem of finding a path through a maze or grid-like structure.
  + Common in computer science, electrical engineering, and robotics.
  + Involves navigating from a start point to a destination while avoiding obstacles.
* Lee's Algorithm:
  + A maze-solving algorithm developed by C. Y. Lee in the 1960s.
  + Works with a 2D grid where cells can be empty, blocked, start, or destination.
  + Steps:
    - Start at the beginning cell with a value of 0.
    - Expand a "wavefront" to adjacent cells with values one higher.
    - Continue until reaching the destination or blocked cells.
    - Trace back to find the path from start to destination.
  + Efficient and widely used for finding the shortest path in grid-based environments.
### Lee's algorithm conclusion:
* In conclusion, Lee's algorithm, also known as Lee's wave algorithm, is a widely used and efficient approach for solving maze routing problems.
* It works by propagating a wavefront from a starting point through a grid-like maze, assigning values to cells as it progresses.
* The algorithm terminates when it reaches the destination or can no longer propagate due to obstacles.
* Once the wavefront reaches the destination, it allows for the reconstruction of the shortest path from the start to the destination.
* Lee's algorithm is commonly used in computer science, electrical engineering, robotics, and other fields where pathfinding and routing are essential.
### Design rule check:
* Purpose of DRC:
  + Ensures design layouts adhere to manufacturing constraints.
  + Detects errors early to prevent manufacturing defects and reduce costs.
* Key Aspects:
  + Based on predefined design rules and constraints.
  + Uses automated software tools to analyze designs.
  + Checks include minimum sizes, clearances, alignment, and more.
* DRC Workflow:
  + Design input: Layout data in specific formats.
  + Rule deck: Defines design rules and constraints.
  + DRC tool: Analyzes design layout for rule violations.
  + Error reporting: Generates reports highlighting violations.
  + Iterative process: Design adjustments and rechecks.
  + Final verification: Ensures compliance with manufacturing requirements.

## Power distribution network and routing:
### Lab steps to build power distribution network:
* `gen_pdn`

![pdn](https://github.com/NishitaNJ/pes_pd/assets/142140741/b3b83483-5344-4886-8255-b0e7f044e33f)

### Basics of global and detail routing and configure TritonRoute:
* Global Routing:
  + High-level routing.
  + Connects blocks or modules.
  + Establishes a rough path.
  + Focuses on wire segments and connections.
  + Balances signal delays and congestion.
  + Doesn't specify exact wire paths.
* Detail Routing:
  + Low-level routing.
  + Connects individual components within blocks.
  + Specifies precise wire paths.
  + Considers manufacturing constraints.
  + Minimizes parasitic effects.
  + Achieves the final layout.
* Configuring TritonRoute:
  + TritonRoute is an open-source router for ASIC and FPGA designs.
  + Define design-specific parameters and constraints in the tool.
  + Configure routing layers, widths, and spacing.
  + Specify netlist and technology library files.
  + Run TritonRoute to perform global and detail routing.
  + Analyze and review routing results.
  + Iterate and adjust configurations as needed for optimization.

### Routing topology algorithm final files list post-route:
**SPEF EXTRACTION**
* After the completion of routing interconnect parasitics can be extracted to perform sign-off post-route STA analysis.
* These are extracted into a SPEF file.
* The SPEF extractor is not included in the OpenLANE as of now.
* `cd ~/Desktop/work/tools/SPEFEXTRACTOR`
* `python3 main.py <path to merged.lef in tmp> <path to def in routing>`
* The SPEF File is generated where the def file is present.
</details>
