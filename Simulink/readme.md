## Simulink / Simscape Model Architecture

The EV thermal management system is implemented using Simulink and Simscape,
with a clear separation of physical domains through color-coded connections.
This structure improves model readability, physical consistency, and scalability.

---

### Electrical Domain (Dark Blue Wires)

Dark blue connections represent the **electrical domain**, used primarily for:

- Electric compressor motor power supply
- Inverter and DC voltage interface
- Electrical power consumption and efficiency analysis

This domain models the electrical energy input required to drive the
electric scroll compressor and allows direct coupling with vehicle-level
energy management strategies.

---

### Mechanical / Physical Signal Interface (Light Blue Wires)

Light blue wires represent **Simscape physical signal connections**, typically used for:

- Compressor shaft speed input (rpm)
- Control signals from supervisory logic
- Actuator and sensor interfaces

These connections transmit physical quantities without energy flow and
serve as the interface between control logic and physical components.

---

### Two-Phase Refrigerant Domain (Light Blue Fluid Lines)

Light blue fluid lines represent the **two-phase refrigerant network**
implemented using the Simscape Fluids (Two-Phase Fluid) library.

Key characteristics:
- Refrigerant: **R1234yf**
- Phase change: Enabled
- Components include compressor, condenser, expansion device, and evaporator
- Both vapor and liquid states are handled within the same network

This domain captures the thermodynamic behavior of the refrigeration cycle,
including pressure drops, heat transfer, and phase transitions, which are
critical for EV HVAC and battery cooling applications.

---

### Air / Thermal Domain (Purple Wires)

Purple connections represent the **air and thermal domain**, including:

- Cabin air flow through the evaporator
- Ambient air flow through the condenser
- Heat exchangers coupling air and refrigerant domains

This domain models convective heat transfer between air streams and thermal
components, enabling realistic prediction of cooling capacity, pull-down
performance, and thermal comfort.

---

## System-Level Thermal Management Concept

The model integrates electrical, refrigerant, and air domains to represent
a complete EV thermal management system:

- Electrical energy drives the compressor
- Refrigerant loop transports thermal energy
- Air loops exchange heat with the cabin and environment

This multi-domain approach allows system-level trade-off studies between
cooling performance, electrical power consumption, and overall vehicle efficiency.

---

## Intended Applications

- EV cabin air-conditioning simulation
- Battery and power electronics thermal management
- Control strategy development and validation
- Energy efficiency and performance benchmarking

---

## Notes

The color convention follows Simscape domain standards and is intentionally
preserved to ensure clarity when extending the model or integrating additional
thermal subsystems.

