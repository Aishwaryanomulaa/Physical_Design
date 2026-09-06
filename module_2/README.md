# SKY130 Module 2

## Good Floorplan vs Bad Floorplan and Introduction to Library Cells

This module covers the basic concepts of **chip floorplanning, library binding, placement, standard-cell design, characterization, and timing characterization** using the SKY130 technology.

---

# Module 2 Contents

* [SKY130_D2_SK1 - Chip Floorplanning Considerations](#sky130_d2_sk1---chip-floorplanning-considerations)
* [SKY130_D2_SK2 - Library Binding and Placement](#sky130_d2_sk2---library-binding-and-placement)
* [SKY130_D2_SK3 - Cell Design and Characterization Flows](#sky130_d2_sk3---cell-design-and-characterization-flows)
* [SKY130_D2_SK4 - General Timing Characterization Parameters](#sky130_d2_sk4---general-timing-characterization-parameters)

---

# SKY130_D2_SK1 - Chip Floorplanning Considerations

## 1. Chip Floorplanning

Floorplanning is one of the important stages of the physical design flow.

It determines the physical organization of the chip, including:

* Die dimensions
* Core dimensions
* Standard-cell placement
* I/O pin locations
* Power distribution
* Placement blockages
* Macro locations

A good floorplan helps reduce routing congestion and improves overall chip performance.

### Good Floorplan vs Bad Floorplan

A good floorplan should have:

* Proper utilization
* Suitable aspect ratio
* Adequate routing resources
* Proper power distribution
* Efficient placement of macros and cells
* Reduced congestion

A poor floorplan may cause:

* Routing congestion
* Increased wire length
* Timing violations
* Poor power distribution
* Difficult routing

---

## 2. Utilization Factor and Aspect Ratio

### Utilization Factor

Utilization factor represents the percentage of the core area occupied by standard cells.

```text
Utilization Factor =

Area occupied by standard cells
-------------------------------- × 100
Total core area
```

Higher utilization improves area efficiency but can increase routing congestion.

Lower utilization provides more routing space but increases the overall chip area.

### Aspect Ratio

The aspect ratio is the ratio between the width and height of the core.

```text
Aspect Ratio = Core Width / Core Height
```

An aspect ratio of approximately 1 represents a square-shaped core.

---

## 3. Pre-Placed Cells

Pre-placed cells are cells or blocks whose locations are fixed before the standard-cell placement stage.

Examples include:

* Memory blocks
* Macros
* IP blocks
* Large functional blocks

Proper placement of these blocks is important because they affect:

* Routing
* Timing
* Congestion
* Power distribution

---

## 4. Decoupling Capacitors

Decoupling capacitors, also called **decap cells**, help maintain a stable local power supply.

When multiple cells switch simultaneously, they can cause temporary variations in the supply voltage.

Decap cells help reduce:

* Supply voltage fluctuations
* Power supply noise
* Local voltage drop

They provide local charge near the cells when required.

---

## 5. Power Planning

Power planning is used to distribute power throughout the chip.

The power distribution network generally contains:

* VDD
* VSS
* Power rings
* Power straps
* Standard-cell power rails

A properly designed power network provides reliable power to all cells and helps reduce IR drop.

---

## 6. Pin Placement and Logical Cell Placement Blockages

Input and output pins must be placed carefully to make routing efficient.

Poor pin placement can cause:

* Long routing paths
* Routing congestion
* Timing problems

Placement blockages are regions where standard cells are not allowed to be placed.

They can be used around:

* Macros
* I/O regions
* Reserved areas
* Routing-sensitive regions

---

## 7. Steps to Run Floorplan Using OpenLANE

OpenLANE can be used to automate the physical design flow.

The basic flow is:

```text
RTL
 ↓
Synthesis
 ↓
Floorplanning
 ↓
Placement
 ↓
CTS
 ↓
Routing
 ↓
Signoff
```

Floorplanning establishes the initial physical structure of the design.

---

## 8. Review Floorplan Files

After running the floorplan stage, several files are generated.

Important files include:

* DEF files
* LEF files
* Verilog netlists
* Configuration files
* Reports

A **DEF (Design Exchange Format)** file contains physical design information such as:

* Die area
* Core area
* Cell locations
* Pin locations
* Nets
* Physical placement information

---

## 9. Review Floorplan Layout in Magic

Magic can be used to visually inspect the generated layout.

The layout can be examined for:

* Die boundaries
* Core boundaries
* Standard cells
* Macros
* Pins
* Power structures
* Placement

---

# SKY130_D2_SK2 - Library Binding and Placement

## 1. Netlist Binding and Initial Placement

After synthesis, the RTL is converted into a gate-level netlist.

During library binding, the logical cells in the netlist are mapped to cells available in the standard-cell library.

The placement stage then determines the physical locations of these cells.

---

## 2. Optimize Placement Using Estimated Wire Length and Capacitance

Placement optimization considers:

* Estimated wire length
* Capacitance
* Timing
* Cell connectivity
* Congestion

The objective is to obtain an efficient placement with reduced wire length and improved timing.

Shorter interconnects generally help reduce:

* Delay
* Capacitance
* Power consumption

---

## 3. Final Placement Optimization

After initial placement, further optimization is performed.

The placement is optimized to improve:

* Timing
* Wire length
* Congestion
* Cell locations

The final placement should provide sufficient routing resources for the routing stage.

---

## 4. Need for Libraries and Characterization

Standard-cell libraries provide the information required by synthesis and physical design tools.

A standard-cell library can contain:

* Cell area
* Cell function
* Input capacitance
* Delay
* Power information
* Timing arcs
* Physical dimensions

Characterization is required to determine the electrical behavior of cells under different conditions.

---

## 5. Congestion-Aware Placement Using RePlAce

**RePlAce** is a global placement engine used in the OpenROAD flow.

It performs placement while considering factors such as:

* Wire length
* Routing congestion
* Cell density

Congestion-aware placement helps prevent routing problems during later stages of physical design.

---

# SKY130_D2_SK3 - Cell Design and Characterization Flows

## 1. Inputs for Cell Design Flow

The cell design process requires several inputs, including:

* Circuit specification
* PDK
* Technology information
* Design rules
* Transistor models
* Supply voltage

The SKY130 PDK provides the technology information required for designing standard cells.

---

## 2. Circuit Design Step

The circuit is designed at the transistor level.

Important considerations include:

* Circuit topology
* Transistor sizing
* Input/output connections
* Power connections
* Functional requirements

The circuit must provide the required functionality while meeting performance requirements.

---

## 3. Layout Design Step

The transistor-level circuit is converted into a physical layout.

The layout must satisfy:

* Design rules
* Connectivity requirements
* Area constraints
* Power requirements

The layout represents the physical implementation of the standard cell.

---

## 4. Typical Characterization Flow

The typical cell characterization flow can be represented as:

```text
Cell Circuit
     ↓
Cell Layout
     ↓
Parasitic Extraction
     ↓
SPICE Simulation
     ↓
Timing and Power Characterization
     ↓
Standard Cell Library
```

The resulting library information is used by EDA tools during:

* Synthesis
* Placement
* Timing analysis
* Optimization

---

# SKY130_D2_SK4 - General Timing Characterization Parameters

## 1. Timing Threshold Definitions

Timing characterization requires defined voltage thresholds to measure signal transitions consistently.

Thresholds are used to determine:

* Input transition time
* Output transition time
* Propagation delay

These thresholds provide standard reference points for timing measurements.

---

## 2. Propagation Delay

Propagation delay is the time taken for a change at the input of a cell to produce the corresponding change at its output.

```text
Input changes
      ↓
Circuit responds
      ↓
Output changes
```

Propagation delay is an important parameter for determining the speed of a digital circuit.

---

## 3. Transition Time

Transition time represents how quickly a signal changes between specified voltage levels.

Two important types are:

* Rise transition time
* Fall transition time

A signal with a shorter transition time changes between logic levels more quickly.

---

# Module 2 Key Learning Outcomes

After completing this module, the following concepts are understood:

* Chip floorplanning
* Good and bad floorplans
* Utilization factor
* Aspect ratio
* Pre-placed cells
* Decoupling capacitors
* Power planning
* Pin placement
* Placement blockages
* OpenLANE floorplanning
* Floorplan file analysis
* Magic layout inspection
* Library binding
* Initial placement
* Placement optimization
* Congestion-aware placement
* RePlAce
* Standard-cell design
* Cell characterization
* Timing thresholds
* Propagation delay
* Transition time

---

# Tools Used

* OpenLANE
* OpenROAD
* RePlAce
* Magic
* SKY130 PDK
* Standard-cell libraries

---

# Module 2 Summary

Module 2 introduces the transition from **logical design to physical design**.

The major physical-design flow can be summarized as:

```text
RTL
 ↓
Synthesis
 ↓
Floorplanning
 ↓
Library Binding
 ↓
Placement
 ↓
Cell Characterization
 ↓
Timing Characterization
 ↓
Routing
```

Understanding floorplanning, placement, standard-cell libraries, characterization, and timing parameters is essential for implementing a reliable ASIC design.

