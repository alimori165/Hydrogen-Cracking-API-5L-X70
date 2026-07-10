# Welding Residual Stress in API X70 Steel — FEM Simulation

**Thermomechanical Finite Element Simulation of Weld Residual Stresses in API X70 Steel under Preheating and Post-Heating Conditions**

---

## Overview

This repository contains the ANSYS APDL code for a **sequentially coupled thermo-mechanical finite element simulation** of a cold cracking test (ISO 17642-2) on API 5L X70 high-strength low-alloy (HSLA) steel.

The model investigates the effect of **preheating** and **post-heating** on the weld thermal cycle and longitudinal residual stress distribution. Validation was performed using weld-pool macrographs and X-ray diffraction measurements.

---

## Key Results

### Residual Stress — Effect of Preheating and Post-Heating

| Condition | Max Tensile Stress (MPa) | Max Compressive Stress (MPa) |
|-----------|--------------------------|-------------------------------|
| No preheating / No post-heating | 719 | -85 |
| Preheating only (100 °C) | 713 | -94 |
| Post-heating only (200 °C / 2h) | 695 | -85 |

**Main findings:**

- Preheating reduced max tensile residual stress by **6 MPa** and increased compressive stress by **9 MPa**
- Post-heating reduced max tensile residual stress by **24 MPa** — more effective than preheating
- Both treatments altered overall stress **distribution** more significantly than extreme values
- Post-heating maintained specimen above 473 K for **2 hours** and above 373 K for an additional 30 minutes — conditions associated with improved hydrogen relief in literature

---

## Simulation Methodology

### Thermal Model
- **Element type:** SOLID70 (8-node, 1 DOF per node — temperature)
- **Heat source:** Uniform body heat flux — arc efficiency η = 0.8 (SMAW)
- **Boundary conditions:** Convection on all free surfaces; ambient temperature = 300 K
- **Mesh:** 26,655 elements / 30,192 nodes — refined in weld zone (1 mm elements)
- **Symmetry:** Half model due to geometric symmetry

### Mechanical Model
- **Element type:** SOLID45 (8-node, 3 DOF per node — UX, UY, UZ)
- Thermal history imported sequentially from thermal analysis
- Von Mises yield criterion with isotropic strain hardening
- Temperature-dependent: Young's modulus, Poisson's ratio, yield stress, thermal expansion

### Material — API 5L X70 Steel

| Temperature (°C) | Young's Modulus (GPa) | Yield Stress (MPa) |
|------------------|-----------------------|--------------------|
| 18 | 206.87 | 481 |
| 400 | 175.95 | — |
| 600 | 154.58 | 220 |
| 800 | 114.5 | — |
| 1000 | 44.66 | — |

---

## Experimental Validation

- **Standard:** ISO 17642-2 (self-restraint cold cracking test)
- **Specimen:** 200 × 150 × 18 mm³ U-groove X70 steel
- **Electrode:** AWS A5.5 E8018-G low-hydrogen (Ø 3.2 mm)
- **Thermal validation:** Weld pool comparison with macrographs ✅
- **Mechanical validation:** Longitudinal residual stress vs. X-ray diffraction ✅

---

## Test Conditions

| Specimen | Preheating (100 °C) | Post-heating (200 °C / 2h) |
|----------|----------------------|----------------------------|
| 1 | No | No |
| 2 | No | Yes |
| 3 | Yes | No |
| 4 | Yes | Yes |

---

## Software & Tools

| Tool | Purpose |
|------|---------|
| ANSYS APDL | FEM simulation (thermal + structural) |
| SOLID70 / SOLID45 | Element types |
| X-ray Diffraction | Residual stress measurement |
| Macrography | Weld pool validation |

---

## Repository Structure

```
Hydrogen-Cracking-API-5L-X70/
│
├── X70_welding_simulation.inp    # ANSYS APDL script
├── README.md                     # This file
└── results/                      # Stress contours and validation figures (coming soon)
```

---

## Publication

- *(Under Review)* — Relationship Between Hydrogen Content and Strain in Hydrogen Cracking of API 5L X70 Steel

---

## Author

**Ali Mori**
M.Sc. Materials & Metallurgy Engineering (Welding) — Amirkabir University of Technology (Tehran Polytechnic)
📧 A.mori@aut.ac.ir | [LinkedIn](https://www.linkedin.com/in/145156/)

---

> *Open to PhD positions in welding simulation, residual stress analysis, and materials engineering.*
