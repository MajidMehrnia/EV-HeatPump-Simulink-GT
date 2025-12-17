This repository provides input data and reference maps for an Electric Vehicle (EV)
HVAC system modeled in GT-SUITE using a two-phase refrigerant approach.

The model is representative of a Valeo-like electric scroll compressor commonly
used in automotive air-conditioning and thermal management systems.

---

## Refrigerant Model

- Refrigerant: **R1234yf**
- Thermodynamic model: **Two-phase**
- State definition: Pressure & Temperature
- Phase change: Enabled (GT Refrigeration Library)


The refrigerant is treated as superheated vapor at compressor inlet and hot vapor
at compressor outlet. No liquid ingestion is allowed at the compressor inlet.

---

## Compressor Description

- Type: Electric Scroll Compressor
- Application: EV HVAC / Battery Thermal Management
- Speed range: **1500 – 9000 rpm**
- Drive: Electric motor (speed-controlled)
- Compressor map formulation: **Corrected Speed Lines**
- Simulation mode: **Transient**

---

## Compressor Speed Control

The compressor shaft speed is defined using a **time-based profile**:

- Template: `Profile`
- Interpolation: Linear
- Hold last value: ON

Example speed profile:

| Time (s) | Speed (rpm) |
|--------|-------------|
| 0 | 1500 |
| 30 | 3000 |
| 90 | 5000 |
| 180 | 7000 |
| 300 | 9000 |

This approach reflects realistic EV HVAC operation during pull-down and high-load
cooling conditions.

---

## Compressor Map Data

The compressor performance is defined using corrected speed lines.
For each speed line, at least three operating points are provided to ensure
numerical stability in GT-SUITE (especially GT-SUITE 2016).

Map data includes:
- Corrected mass flow rate
- Volumetric efficiency
- Isentropic efficiency
- Shaft RPM

Interpolation: Linear  
Extrapolation: Clamp

---

## End Environment Settings

- Phase specification: Single-phase
- State definition: Pressure & Temperature
- Reverse flow: Disabled

Typical boundary conditions:
- Suction pressure: 2.5 – 3.5 bar
- Suction temperature: 5 – 15 °C

---

## Intended Use

- EV cabin air-conditioning
- Battery thermal management systems
- System-level energy and efficiency analysis
- Control-oriented studies

---

## Notes

This dataset is intended for simulation and control development purposes.
Values are representative and not tied to a specific OEM product.
