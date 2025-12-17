This repository is based on the EV Thermal Management model published by MathWorks (Simscape).
The original model files are not redistributed due to licensing. It contains a model of a battery electric vehicle (BEV) with a thermal management system. This virtual vehicle model was parametrized to describe a mid-size electric sedan [1].

## Description
Developed a Heat Pump co-simulation framework for a Battery Electric Vehicle
using GT-SUITE and Simulink, based on a reference EV thermal architecture. Simulating the entire refrigerant system in GT-SUITE and coupling it with Simulink can lead to more accurate results. 
In this work, due to time constraints, only the compressor was modeled. 
One of the main challenges in this co-simulation was handling the time-step mismatch between the two models. 
The compressor model was developed and simulated in GT-SUITE.

## Simulink
The figure below illustrates the virtual vehicle developed using Simscape and its add-on products. 
The model simulates a mid-size sedan with rear wheel drive and comprises five subsystems: 
**Electric Powertrain**, **Driveline**, **Refrigerant Cycle**, **Coolant Cycle**, and **Cabin Cycle**. 
The control algorithms are implemented in Simulink and are contained in the **Controls** subsystem.


![Sim_diagram_GT](https://github.com/user-attachments/assets/ac0e96d3-1697-429e-8811-d3688cbbc42d)

 

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
 
