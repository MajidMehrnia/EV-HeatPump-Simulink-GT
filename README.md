## Description
This repository is based on the EV Thermal Management model published by MathWorks (Simscape). It contains a model of a battery electric vehicle (BEV) with a thermal management system. This virtual vehicle model was parametrized to describe a mid-size electric sedan [1].

Developed a Heat Pump co-simulation framework for a Battery Electric Vehicle
using GT-SUITE and Simulink, based on a reference EV thermal architecture. Simulating the entire refrigerant system in GT-SUITE and coupling it with Simulink can lead to more accurate results. 
In this project, due to CPU limitations, only the compressor was modeled.
One of the main challenges in this co-simulation was handling the time-step mismatch between the two models. 
The compressor model was developed and simulated in GT-SUITE.


### Refrigerant System 

The refrigerant cycle comprises compressor, condenser, chiller expansion valve (EV1), evaporator 
expansion value (EV2), chiller, and evaporator. More information regarding the refrigerant cycle 
is available at [2].

The refrigerant flow is driven by the compressor, which is connected to the HV electrical network. 
The refrigerant flow continues to the condenser where heat is dissipated to the air. The air flow 
within the condenser is driven by the vehicle speed the condenser fan. Latter is connected to the 
LV network.

The refrigerant then flows through EV1 and EV2 and continues to chiller and evaporator. In the 
chiller, the refrigerant absorbs heat from the coolant cycle. In the evaporator the refrigerant 
absorbs heat from the cabin air and continues its way back to the compressor.

The model simulated here is representative of a Valeo-like electric scroll compressor commonly
used in automotive air-conditioning and thermal management systems.
- Refrigerant: **R1234yf**
- Thermodynamic model: **Two-phase**
- Phase change: Enabled

  ![Sim_diagram](https://github.com/user-attachments/assets/704761de-3017-44d6-9fd4-ccb86be20123)


## Simulink
The figure below illustrates the virtual vehicle developed using Simscape and its add-on products. 
The model simulates a mid-size sedan with rear wheel drive and comprises five subsystems: 
**Electric Powertrain**, **Driveline**, **Refrigerant Cycle**, **Coolant Cycle**, and **Cabin Cycle**. 
The control algorithms are implemented in Simulink and are contained in the **Controls** subsystem.

![Simulink](https://github.com/user-attachments/assets/d713d085-7cfa-4da3-ad61-91fec8a3761a)

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
 
