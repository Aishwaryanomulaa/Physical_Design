# SKY130 Module 1
## Inception of Open-Source EDA, OpenLANE and Sky130 PDK

![SKY130](https://img.shields.io/badge/SKY130-PDK-blue)
![OpenLANE](https://img.shields.io/badge/OpenLANE-ASIC%20Flow-green)
![RISC-V](https://img.shields.io/badge/RISC--V-ISA-orange)
![EDA](https://img.shields.io/badge/Open--Source-EDA-purple)

---

## 📌 About

This repository contains my learning and practical work for **SKY130 Module 1 – Inception of Open-Source EDA, OpenLANE and Sky130 PDK**.

The module introduces the fundamentals of:

- Semiconductor chips
- QFN-48 package
- Chip, die, core and pads
- Intellectual Property (IP)
- RISC-V
- SoC design
- Open-source EDA tools
- RTL-to-GDS flow
- OpenLANE
- Sky130 PDK
- Design preparation
- RTL synthesis
- Synthesis characterization

---

# 📚 Module Contents

```text
SKY130 Module 1
│
├── SKY130_D1_SK1
│   └── How to Talk to Computers
│
├── SKY130_D1_SK2
│   └── SoC Design and OpenLANE
│
└── SKY130_D1_SK3
    └── Get Familiar with Open-Source EDA Tools
```

---

# 🟦 SKY130_D1_SK1
# How to Talk to Computers

---

## SKY_L1 - Introduction to QFN-48 Package, Chip, Pads, Core, Die and IP

This lecture introduces the physical structure of an integrated circuit and explains the relationship between the package, chip, die, core, pads and IP.

### QFN-48 Package

**QFN** stands for **Quad Flat No-leads**.

The QFN package provides electrical and mechanical connections between the silicon die and the external circuit.

The number **48** represents the number of package connections.

### Chip Structure

```text
                 QFN-48 PACKAGE
        ┌───────────────────────────┐
        │                           │
        │          PACKAGE          │
        │                           │
        │      ┌─────────────┐      │
        │      │     DIE     │      │
        │      │             │      │
        │      │    CORE     │      │
        │      │             │      │
        │      │   DIGITAL   │      │
        │      │    LOGIC    │      │
        │      │             │      │
        │      └─────────────┘      │
        │                           │
        └───────────────────────────┘
          │ │ │ │ │ │ │ │ │ │ │ │
             PACKAGE PINS
```

### Chip

A chip is an integrated circuit fabricated on a semiconductor die.

A chip may contain:

- Processor
- Memory
- Digital logic
- Analog circuits
- I/O circuits
- Communication interfaces
- IP blocks

### Die

The **die** is the physical piece of semiconductor material on which the circuit is fabricated.

### Core

The **core** is the main region where the digital logic and standard cells are placed.

### Pads

Pads provide electrical connections between the internal chip circuitry and the external package.

Pads can carry:

- Data
- Clock
- Reset
- Power
- Ground
- Control signals

### IP - Intellectual Property

IP stands for **Intellectual Property**.

An IP is a reusable hardware design block.

Examples:

- CPU
- UART
- SPI
- I2C
- GPIO
- PLL
- Timer
- Memory controller

### Relationship

```text
                     CHIP
                       │
                       ▼
                      DIE
                       │
              ┌────────┴────────┐
              │                 │
             CORE              PADS
              │                 │
              ▼                 ▼
       Digital Logic       External I/O
```

### 📸 Lecture Screenshot

![QFN-48 Package](screenshots/qfn48_package.png)

---

## SKY_L2 - Introduction to RISC-V

RISC-V is an **open Instruction Set Architecture (ISA)**.

An ISA defines the instructions and programmer-visible behavior supported by a processor.

### What is RISC-V?

RISC-V follows the **Reduced Instruction Set Computer (RISC)** design philosophy.

It provides an open instruction set that can be implemented by different processor designs.

### Important Features

- Open ISA
- RISC-based architecture
- Modular instruction set
- Suitable for custom processors
- Useful for research and education
- Suitable for different applications

### ISA vs Processor

RISC-V is an instruction set architecture and is not one specific processor.

```text
                    RISC-V
                       │
                       ▼
          Instruction Set Architecture
                       │
                       ▼
                  Instructions
                       │
                       ▼
             Processor Implementation
```

### Example Instructions

```text
ADD
SUB
AND
OR
LOAD
STORE
BRANCH
```

### 📸 Lecture Screenshot

![RISC-V](screenshots/risc_v.png)

---

## SKY_L3 - From Software Applications to Hardware

Software and hardware operate at different abstraction levels.

A high-level software application is eventually converted into machine instructions that are executed by a processor.

### Software-to-Hardware Flow

```text
Software Application
        │
        ▼
Programming Language
        │
        ▼
     Compiler
        │
        ▼
   Assembly Code
        │
        ▼
 Machine Instructions
        │
        ▼
   RISC-V Processor
        │
        ▼
        RTL
        │
        ▼
    Logic Gates
        │
        ▼
    Transistors
        │
        ▼
    Silicon Chip
```

### Abstraction Levels

```text
Application
     ↓
High-Level Language
     ↓
Assembly
     ↓
Machine Code
     ↓
ISA
     ↓
RTL
     ↓
Logic Gates
     ↓
Transistors
     ↓
Physical Layout
     ↓
Chip
```

### 📸 Lecture Screenshot

![Software to Hardware](screenshots/software_to_hardware.png)

---

# 🟩 SKY130_D1_SK2
# SoC Design and OpenLANE

This section introduces the components of digital ASIC design and the RTL-to-GDS flow.

---

## SKY_L1 - Introduction to All Components of Open-Source Digital ASIC Design

A digital ASIC design passes through several stages before becoming a physical chip.

### Digital ASIC Flow

```text
RTL Design
     │
     ▼
Simulation
     │
     ▼
Synthesis
     │
     ▼
Floorplanning
     │
     ▼
Placement
     │
     ▼
Clock Tree Synthesis
     │
     ▼
Routing
     │
     ▼
Physical Verification
     │
     ▼
GDSII
```

### RTL Design

RTL describes the behavior and structure of a digital circuit using a Hardware Description Language such as Verilog.

### Simulation

Simulation verifies the functional behavior of the RTL before hardware implementation.

### Synthesis

Synthesis converts RTL into a gate-level netlist using cells from the target technology library.

```text
RTL
 ↓
Logic Optimization
 ↓
Technology Mapping
 ↓
Gate-Level Netlist
```

### Floorplanning

Floorplanning determines the physical organization of the design.

It includes:

- Die area
- Core area
- I/O locations
- Macro locations

### Placement

Placement determines the physical locations of standard cells.

### Clock Tree Synthesis

CTS creates the clock distribution network.

Important concepts include:

- Clock skew
- Clock latency
- Clock buffering

### Routing

Routing creates the physical metal connections between cells.

### Physical Verification

Physical verification checks the layout for correctness and design-rule compliance.

### GDSII

GDSII represents the physical layout of the integrated circuit.

---

## Open-Source EDA Tools

| Tool | Purpose |
|---|---|
| Yosys | RTL synthesis |
| OpenROAD | Physical design |
| Magic | Layout and physical verification |
| Netgen | Netlist comparison / LVS |
| KLayout | Layout viewing and analysis |
| OpenLANE | RTL-to-GDS implementation flow |
| Sky130 PDK | Technology information and libraries |

---

## 📸 Screenshot

![Open Source EDA](screenshots/open_source_eda.png)

---

## SKY_L2 - Simplified RTL2GDS Flow

RTL-to-GDS is the process of converting a hardware design from RTL into a physical layout.

### RTL-to-GDS Flow

```text
                     RTL
                      │
                      ▼
                  Synthesis
                      │
                      ▼
                Floorplanning
                      │
                      ▼
                  Placement
                      │
                      ▼
                     CTS
                      │
                      ▼
                   Routing
                      │
                      ▼
             Physical Verification
                      │
                      ▼
                    GDSII
```

### 1. RTL

RTL describes the behavior and structure of the digital circuit.

Example:

```verilog
module and_gate (
    input  a,
    input  b,
    output y
);

assign y = a & b;

endmodule
```

### 2. Synthesis

Synthesis converts RTL into a gate-level netlist.

### 3. Floorplanning

Floorplanning defines:

- Die area
- Core area
- I/O placement
- Macro locations

### 4. Placement

Standard cells are physically placed inside the core.

### 5. Clock Tree Synthesis

CTS creates the clock distribution network.

### 6. Routing

Routing creates physical connections between cells.

### 7. Physical Verification

The physical layout is checked for correctness.

### 8. GDSII

GDSII represents the final physical layout database.

### 📸 Screenshot

![RTL to GDS](screenshots/rtl2gds.png)

---

## SKY_L3 - Introduction to OpenLANE and STRIVE Chipsets

### What is OpenLANE?

OpenLANE is an open-source digital ASIC implementation flow.

It combines several open-source EDA tools to automate the RTL-to-GDS implementation process.

### OpenLANE Concept

```text
                     RTL
                      │
                      ▼
                  OpenLANE
                      │
                      ▼
                  Synthesis
                      │
                      ▼
                 Floorplan
                      │
                      ▼
                  Placement
                      │
                      ▼
                     CTS
                      │
                      ▼
                  Routing
                      │
                      ▼
                  Sign-off
                      │
                      ▼
                    GDSII
```

### Why OpenLANE?

Open-source ASIC flows provide:

- Open-source tools
- Reproducible design flows
- Accessible learning environment
- Open technology information
- Automation of ASIC implementation stages

### STRIVE Chipsets

STRIVE is associated with efforts demonstrating practical use of open-source RTL-to-GDS flows for chip development.

### 📸 Screenshot

![OpenLANE Flow](screenshots/openlane_flow.png)

---

## SKY_L4 - Introduction to OpenLANE Detailed ASIC Design Flow

The detailed ASIC implementation flow consists of several stages.

```text
Design Preparation
        │
        ▼
     Synthesis
        │
        ▼
   Floorplanning
        │
        ▼
    Placement
        │
        ▼
       CTS
        │
        ▼
     Routing
        │
        ▼
   Sign-off Checks
        │
        ▼
      GDSII
```

### Design Preparation

The design is prepared before implementation.

Typical inputs include:

- RTL source files
- Configuration files
- Clock information
- Timing constraints
- Technology information
- Standard-cell libraries

### Synthesis

RTL is converted into a gate-level netlist.

### Floorplanning

Defines the physical dimensions and organization of the chip.

### Placement

Places standard cells in the core.

### Clock Tree Synthesis

Creates and optimizes the clock distribution network.

### Routing

Creates physical connections between cells.

### Sign-off

Final checks are performed before generating the final layout.

### 📸 Screenshot

![Detailed OpenLANE Flow](screenshots/openlane_detailed_flow.png)

---

# 🟨 SKY130_D1_SK3
# Get Familiar with Open-Source EDA Tools

This section provides practical exposure to the OpenLANE environment and open-source EDA tools.

---

## SKY_L1 - OpenLANE Directory Structure in Details

Understanding the OpenLANE directory structure is important before running the ASIC flow.

The exact structure may vary depending on the OpenLANE version and installation.

### Example Structure

```text
OpenLANE/
│
├── designs/
├── flow/
├── scripts/
├── configuration/
├── pdks/
└── dependencies/
```

### Designs

Contains design-related files and configurations.

```text
designs/
```

### Flow

Contains scripts and files associated with the ASIC implementation flow.

```text
flow/
```

### Scripts

Contains scripts used to automate different stages.

```text
scripts/
```

### PDK

The Process Design Kit contains technology-specific information required to implement a design for a particular semiconductor process.

For this module, the target technology is **Sky130**.

### Commands Used

```bash
pwd
ls
cd <directory>
find . -maxdepth 2 -type d
```

### 📸 Screenshot

![OpenLANE Directory](screenshots/openlane_directory.png)

---

## SKY_L2 - Design Preparation Steps

Before running synthesis, the design needs to be prepared correctly.

### Design Preparation Flow

```text
Select Design
      │
      ▼
Prepare RTL
      │
      ▼
Prepare Configuration
      │
      ▼
Specify Clock
      │
      ▼
Set Technology
      │
      ▼
Check Design
      │
      ▼
Run Preparation
```

### Typical Inputs

- RTL files
- Configuration files
- Clock constraints
- Timing information
- Technology information
- Standard-cell libraries

### Why Design Preparation is Important

Incorrect:

- RTL paths
- File names
- Configuration
- Clock constraints
- Technology settings

can cause failures during synthesis or later stages.

### 📸 Screenshot

![Design Preparation](screenshots/design_prep.png)

---

## SKY_L3 - Review Files After Design Preparation and Run Synthesis

After design preparation, generated files, logs and reports should be reviewed.

### Synthesis

```text
              RTL
               │
               ▼
             Yosys
               │
               ▼
      Logic Optimization
               │
               ▼
      Technology Mapping
               │
               ▼
      Gate-Level Netlist
```

### Files and Reports to Review

Important information may include:

- Synthesis logs
- Gate-level netlist
- Timing information
- Area information
- Cell statistics
- Warnings
- Errors
- Configuration information

### Synthesis Checklist

```text
✓ RTL read successfully
✓ Synthesis completed
✓ Netlist generated
✓ Errors checked
✓ Warnings reviewed
✓ Cell count checked
✓ Area checked
✓ Timing checked
✓ Reports reviewed
```

### 📸 Screenshot

![Synthesis](screenshots/synthesis.png)

---

## SKY_L4 - OpenLANE Project Git Link Descriptions

The open-source ASIC ecosystem contains several projects that work together.

### OpenLANE

Provides an automated RTL-to-GDS implementation flow.

### Yosys

Used for RTL synthesis and logic optimization.

### OpenROAD

Provides physical-design capabilities including:

- Floorplanning
- Placement
- Clock Tree Synthesis
- Routing
- Optimization

### Magic

Used for layout and physical verification.

### Netgen

Used for netlist comparison and LVS-related tasks.

### KLayout

Used for viewing and analyzing IC layouts.

### Sky130 PDK

Provides technology-specific information and libraries required for implementing designs using the Sky130 process.

### EDA Ecosystem

```text
                   Sky130 PDK
                       │
                       ▼
                    OpenLANE
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
        Yosys       OpenROAD      Magic
          │            │            │
          └────────────┼────────────┘
                       │
                       ▼
                     GDSII
```

---

## SKY_L5 - Steps to Characterize Synthesis

After synthesis, the design should be analyzed using important metrics.

### 1. Area

Area represents the physical area required by the synthesized logic.

Area depends on:

- Number of cells
- Cell types
- Cell sizes
- Optimization
- Design complexity

### 2. Cell Count

The synthesized netlist contains standard cells.

Examples:

```text
AND
OR
NOT
MUX
Buffer
Flip-Flop
```

### 3. Timing

Timing analysis determines whether signals can propagate through the design within the required clock period.

Important parameters include:

- Clock period
- Delay
- Slack
- Critical path
- Setup
- Hold

### 4. Critical Path

The critical path is the path with the most significant timing delay for the timing requirement being analyzed.

The critical path can limit the maximum operating frequency.

### 5. Slack

Slack represents the timing margin.

```text
Positive Slack
      │
      ▼
Timing requirement satisfied


Negative Slack
      │
      ▼
Timing violation
```

---

## 📊 Synthesis Characterization

The following table can be updated with values from the actual synthesis report.

| Parameter | Result |
|---|---|
| Design | TBD |
| Technology | Sky130 |
| Clock Period | TBD |
| Cell Count | TBD |
| Combinational Cells | TBD |
| Sequential Cells | TBD |
| Area | TBD |
| Worst Slack | TBD |
| Critical Path | TBD |
| Maximum Frequency | TBD |

> Replace `TBD` with the actual values obtained from the synthesis reports.

### 📸 Synthesis Results

![Synthesis Results](screenshots/synthesis_results.png)

---

# 🧪 Practical Work

The practical work covered in this module includes:

```text
1. OpenLANE environment exploration
2. OpenLANE directory structure
3. Design preparation
4. RTL preparation
5. Synthesis
6. Generated file inspection
7. Synthesis report analysis
8. Area characterization
9. Timing characterization
```

---

# 🛠️ Tools and Technologies

| Tool / Technology | Role |
|---|---|
| Linux / Ubuntu | Development environment |
| OpenLANE | ASIC implementation flow |
| Yosys | RTL synthesis |
| OpenROAD | Physical design |
| Magic | Layout and verification |
| Netgen | Netlist comparison / LVS |
| KLayout | Layout viewing |
| Sky130 PDK | Process technology |
| Git | Version control |
| GitHub | Repository and documentation |

---

# 📸 Screenshots

The repository contains screenshots from the lectures and practical sessions.

```text
screenshots/
│
├── qfn48_package.png
├── chip_die_core.png
├── risc_v.png
├── software_to_hardware.png
├── rtl2gds.png
├── openlane_flow.png
├── openlane_directory.png
├── design_prep.png
├── synthesis.png
└── synthesis_results.png
```

---

# 🎯 Learning Outcomes

After completing SKY130 Module 1, I understood:

- QFN-48 semiconductor packaging
- Chip and die
- Core and pads
- Intellectual Property
- RISC-V ISA
- Software-to-hardware abstraction
- SoC design
- Open-source EDA
- ASIC design flow
- RTL-to-GDS flow
- OpenLANE
- Sky130 PDK
- OpenLANE directory structure
- Design preparation
- RTL synthesis
- Gate-level netlists
- Synthesis reports
- Area characterization
- Timing characterization
- Critical paths
- Slack

---

# 🔄 Complete ASIC Flow

```text
                         SOFTWARE
                             │
                             ▼
                         RISC-V ISA
                             │
                             ▼
                            RTL
                             │
                             ▼
                        SIMULATION
                             │
                             ▼
                         SYNTHESIS
                             │
                             ▼
                        FLOORPLAN
                             │
                             ▼
                         PLACEMENT
                             │
                             ▼
                           CTS
                             │
                             ▼
                         ROUTING
                             │
                             ▼
                  PHYSICAL VERIFICATION
                             │
                             ▼
                           GDSII
                             │
                             ▼
                        FABRICATION
                             │
                             ▼
                           CHIP
```

---

# 💡 Key Takeaways

### Hardware Abstraction

```text
Software
   ↓
ISA
   ↓
RTL
   ↓
Logic Gates
   ↓
Transistors
   ↓
Physical Layout
   ↓
Chip
```

### ASIC Implementation

```text
RTL
 ↓
Synthesis
 ↓
Floorplan
 ↓
Placement
 ↓
CTS
 ↓
Routing
 ↓
Verification
 ↓
GDSII
```

---

# 📈 Module 1 Summary

```text
┌─────────────────────────────────────────┐
│              SKY130 MODULE 1            │
├─────────────────────────────────────────┤
│                                         │
│  Computer Fundamentals                  │
│          ↓                              │
│  RISC-V                                 │
│          ↓                              │
│  SoC Design                             │
│          ↓                              │
│  Open-Source EDA                        │
│          ↓                              │
│  OpenLANE                               │
│          ↓                              │
│  RTL-to-GDS                             │
│          ↓                              │
│  Synthesis                              │
│          ↓                              │
│  Area & Timing Characterization        │
│                                         │
└─────────────────────────────────────────┘
```

---

# 🚀 Conclusion

SKY130 Module 1 introduced the fundamentals of open-source digital ASIC design and the OpenLANE flow.

The module connected the complete chain:

**Software → RISC-V → RTL → Synthesis → Physical Design → GDSII → Chip**

The practical sessions provided hands-on exposure to the OpenLANE environment, design preparation, synthesis and synthesis characterization.

This module forms the foundation for further learning in:

- RTL design
- Digital synthesis
- Timing analysis
- Physical design
- ASIC implementation
- Sky130 technology

---

# 👩‍💻 Author

**Aishwarya**

Electronics and Communication Engineering

---

## ⭐ Repository

**SKY130 Module 1 - Inception of Open-Source EDA, OpenLANE and Sky130 PDK**

This repository documents my learning, practical work, commands, screenshots and synthesis results from SKY130 Module 1.
