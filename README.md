# Tank Breathing Model (MUSCL/TVD, index-1 DAE)

This repository contains a MATLAB implementation of a 1D vertical tank-breathing model with MUSCL/TVD spatial derivatives and selectable flux limiters. 
The system is integrated as an index-1 DAE using `ode15s`, with a sparse Jacobian pattern and a singular mass matrix. Hourly, year-long simulations are supported out of the box.

> **File:** `Compute_Condensation_Model.m`

---

## Key features

- **1D vertical transport** of vapour concentration `C` and gas temperature `T` in a large storage tank.
- **MUSCL/TVD first derivatives** with selectable flux limiter:
  - `minmod`, `vanleer`, `superbee`, `vanalbada` (case-insensitive).
- **Mixed (averaged) boundary conditions** at bottom (liquid) and top (roof).
- **Breathing velocity with threshold** `|v_avg| ≥ v_min` (sign preserved).
- **“Empty-tube” axial dispersion** closures for heat (`Et`) and mass (`Em`).
- **Index-1 DAE** solved with `ode15s` + sparse `JPattern`.
- **Post-integration saturation clamp** `C ≤ C_sat(T)` node-by-node.
- **Hourly interpolation** for easy plotting / export.

---

## Repository layout

├── Compute_Condensation_Model.m` # Main script with local functions (documented)
├── TL.xlsx # Bottom liquid temperature [K], hourly column (Insert your own data-sheet)
├── Tt.xlsx # Roof (top) gas temperature [K], hourly column (Insert your own data-sheet)
├── v_avg.xlsx # Average breathing velocity [m/s], hourly column (Insert your own data-sheet)
├── livello.xlsx # Liquid level [m], hourly column (Insert your own data-sheet)
├── README.md
