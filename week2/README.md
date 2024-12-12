# Week 2: Modeling and Process Dynamics - Lecture Notes

This folder contains materials and notes from Week 2 of the course, focusing on modeling chemical processes, energy balances, and system dynamics. Below is a summary of the key topics covered during the lecture.

---

## Overview

This week focuses on:

1. **Energy Balances**  
   - Non-isothermal chemical reactor modeling.
   - Heat transfer mechanisms: conduction, convection, and radiation.
   
2. **Mass Balances**  
   - Concentration dynamics of reacting species.
   - Integration of reaction kinetics into system models.

---

## Key Equations

### Temperature Dynamics
The change in temperature of the system is governed by the following differential equation:

```plaintext
dT/dt = (AU / (rho * V * c_P)) * Delta_T + (F_i / V) * c_P * (T_i - T) - (r * Delta_h_R) / (rho * c_P)
