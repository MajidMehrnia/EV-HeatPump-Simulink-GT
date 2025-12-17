This repository is based on the EV Thermal Management model published by MathWorks (Simscape).
The original model files are not redistributed due to licensing. It contains a model of a battery electric vehicle (BEV) with a thermal management system. This virtual vehicle model was parametrized to describe a mid-size electric sedan [1].

## Description
Developed a Heat Pump co-simulation framework for a Battery Electric Vehicle
using GT-SUITE and Simulink, based on a reference EV thermal architecture. Simulating the entire refrigerant system in GT-SUITE and coupling it with Simulink can lead to more accurate results. 
In this work, due to time constraints, only the compressor was modeled. 
One of the main challenges in this co-simulation was handling the time-step mismatch between the two models. 
The compressor model was developed and simulated in GT-SUITE.

---

## Refrigerant Model in GT-SUITE

- Refrigerant: **R1234yf**
- Thermodynamic model: **Two-phase**
- Phase change: Enabled 
---
The model is representative of a Valeo-like electric scroll compressor commonly
used in automotive air-conditioning and thermal management systems.

## Simulink
The figure below illustrates the virtual vehicle developed using Simscape and its add-on products. 
The model simulates a mid-size sedan with rear wheel drive and comprises five subsystems: 
**Electric Powertrain**, **Driveline**, **Refrigerant Cycle**, **Coolant Cycle**, and **Cabin Cycle**. 
The control algorithms are implemented in Simulink and are contained in the **Controls** subsystem.


![Sim_diagram_GT](https://github.com/user-attachments/assets/ac0e96d3-1697-429e-8811-d3688cbbc42d)

The Figure of subsystem illustrates the components responsible for importing data and signals from GT-SUITE into Simulink for co-simulation. 
These signals enable real-time interaction between the compressor model and the system-level of BEV. 
The served fluid is a two-phase refrigerant. R1234yf is used to accurately represent phase-change and thermodynamic behavior.

![GT_COMP](https://github.com/user-attachments/assets/4dbd01b7-b883-4f15-997c-fcee3c1f3beb)


 ## GT-SUITE

Detailed compressor model implemented in GT-SUITE and coupled with Simulink through co-simulation. 
The GT-SUITE model represents the thermodynamic and mechanical behavior of the compressor, 
while Simulink manages the system-level control and signal exchange. 

![GT-SUITE_blocks](https://github.com/user-attachments/assets/fef207ef-334b-4d06-adff-b759e48033e8)


The refrigerant compressor is modeled and simulated in GT-SUITE using its dedicated thermo-fluid and mechanical component libraries. 
The model captures key compressor behaviors, including mass flow rate, pressure ratio, efficiency, and dynamic response under varying operating conditions. 
Different sub-models are employed to represent thermodynamic processes, mechanical losses, and control-relevant dynamics.

Due to GT-SUITE licensing restrictions, the original model files cannot be shared publicly. 
Therefore, only representative diagrams, descriptions, and co-simulation interfaces are provided in this repository.


## Support
For any questions regarding the model place a comment in the repository.

## License
See [license](LICENSE.md) file attached to this repository

## Project status
In development

## Sources
[1] A Holistic Approach for Designing a Battery Electric Vehicle Thermal Management System, 
Steve Miller, Lorenzo Nicoletti

[2] The MathWorks. “Electric Vehicle Thermal Management - MATLAB & Simulink.”, Available 
[here](https://www.mathworks.com/help/hydro/ug/sscfluids_ev_thermal_management.html). 
 
