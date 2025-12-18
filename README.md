## Description
This repository is based on the EV Thermal Management model developed in Simulink. It contains a model of a battery electric vehicle (BEV) with a thermal management system. This virtual vehicle model was parametrized to describe a mid-size electric sedan [1].
Developed a heat pump co-simulation framework for a battery electric vehicle using GT-SUITE and Simulink, based on a reference EV thermal architecture. The model requires the following products:

- MATLAB® R2024a; Simulink®; Simscape™; Simscape Fluids™; Simscape Battery™; Simscape Driveline™; Simscape Electrical™; Stateflow®
- GT-SUITE

The full refrigerant system was modeled in GT-SUITE and coupled with Simulink to improve simulation accuracy. In this project, due to CPU limitations, only the compressor was modeled. One of the main challenges in this co-simulation was handling the time-step mismatch between the two models. The compressor model was developed and simulated in GT-SUITE.



![Refrig_System](https://github.com/user-attachments/assets/bdc71a1a-0043-4013-a684-7a9282a2def7)






### Refrigerant System 

The refrigerant cycle comprises compressor, condenser, chiller expansion valve (EV1), evaporator 
expansion value (EV2), chiller, and evaporator. 

The refrigerant flow is driven by the compressor, which is connected to the HV electrical network. 
The refrigerant flow continues to the condenser where heat is dissipated to the air. The air flow 
within the condenser is driven by the vehicle speed the condenser fan. Latter is connected to the 
LV network.

The refrigerant then flows through EV1 and EV2 and continues to chiller and evaporator. In the 
chiller, the refrigerant absorbs heat from the coolant cycle. In the evaporator the refrigerant 
absorbs heat from the cabin air and continues its way back to the compressor.

The model simulated here is representative of a **Valeo**-like electric scroll compressor commonly
used in automotive air-conditioning and thermal management systems.
- Refrigerant: **R1234yf**
- Thermodynamic model: **Two-phase**
- Phase change: Enabled


## Simulink
The figure below illustrates the virtual vehicle developed using Simscape and its add-on products. 
The model simulates a mid-size sedan and comprises five subsystems: 
**Electric Powertrain**, **Driveline**, **Refrigerant Cycle**, **Coolant Cycle**, and **Cabin Cycle**. 
The control algorithms are implemented in Simulink and are contained in the **Controls** subsystem.

![Sim_diagram](https://github.com/user-attachments/assets/9ac5de1f-6cb7-4017-9ff3-9ec4309d36f7)


These signals enable real-time interaction between the compressor model and the system-level of BEV. 
The served fluid is a two-phase refrigerant. R1234yf is used to accurately represent phase-change and thermodynamic behavior. More information is available at [2].


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

## Post-Processing

The post-processing of the thermal simulation results focuses on resolving spatial and temporal heat flux distributions within the battery pack and their coupling to the coolant loop. Cell-level heat generation is computed internally from the electrical model and exported as a time-resolved thermal power signal, which is subsequently mapped to the thermal network. The resulting heat flux at the cell–cooling plate interface represents the effective thermal load imposed on the BTMS and varies strongly with drive cycle transients. Peak heat flux events correlate with high current demand phases rather than steady-state operation, highlighting the importance of transient thermal capacity over nominal cooling power when sizing the thermal interfaces.

![HF-1](https://github.com/user-attachments/assets/9fea9c4c-e5ea-4322-97cc-bb303d2444aa)

Temperature distribution results indicate that maximum cell temperature is not governed by total heat generation alone, but by the internal thermal resistance chain spanning cell core, casing, interface materials, and cooling plate conduction. Post-processed temperature gradients across the battery module reveal that once coolant inlet temperature and flow rate exceed a threshold, further improvements in convective heat transfer yield diminishing returns. This confirms that the system operates in a conduction-limited regime during high load events, where contact resistance and through-plane conductivity dominate over fluid-side heat transfer coefficients. Consequently, regions of elevated temperature align spatially with regions of highest heat flux density rather than with coolant flow maldistribution.

From an energy distribution perspective, the BTMS post-processing shows that a non-trivial portion of the generated thermal energy is managed through active cooling work, introducing secondary losses via pumps and the refrigeration cycle. By integrating heat flux over time and comparing it to BTMS electrical power consumption, the simulation allows quantification of the effective thermal efficiency of the system. These results emphasize that optimal BTMS operation is achieved not by minimizing absolute cell temperature, but by limiting thermal gradients and peak heat flux while avoiding excessive auxiliary energy consumption. This framework enables informed trade-off studies between thermal performance, aging mitigation, and vehicle-level energy efficiency.

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
 
