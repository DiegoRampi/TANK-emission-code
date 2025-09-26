# Tank Breathing Model (MUSCL/TVD, index-1 DAE)

MATLAB models for 1D vertical tank-breathing with MUSCL/TVD spatial derivatives and selectable flux limiters. Integrated as an index-1 DAE with `ode15s`, sparse Jacobian pattern, and 1-year hourly simulations.

## Files

- **`Compute_Condensation_Model.m`** — main model **with condensation clamp** (`C ≤ C_sat(T)` after integration).
- **`Compute_NoCondensation_Model.m`** (aka `Compute_Rota_Model.m`) — variant **without condensation clamp** (diagnostics for `Em/Et` included).
- **`TL.xlsx`** — bottom liquid temperature `[K]`, hourly column *(provide your data)*.
- **`Tt.xlsx`** — roof/top gas temperature `[K]`, hourly column *(provide your data)*.
- **`v_avg.xlsx`** — average breathing velocity `[m/s]`, hourly column *(provide your data)*.
- **`livello.xlsx`** — liquid level `[m]`, hourly column *(provide your data)*.
- **`README.md`**

## Key features

- 1D vertical transport of vapour concentration `C` and gas temperature `T`.
- MUSCL/TVD first derivatives with limiters: `minmod`, `vanleer`, `superbee`, `vanalbada`.
- Mixed (averaged) boundary conditions at bottom/top.
- Breathing velocity with threshold `|v_avg| ≥ v_min` (sign preserved).
- “Empty-tube” axial dispersion closures for heat (`Et`) and mass (`Em`).
- Index-1 DAE via `ode15s` + sparse `JPattern`.
- Hourly interpolation for plotting/export.
- **Condensation model only:** saturation clamp `C ≤ C_sat(T)` node-by-node.


## Quick start

1. Place the `.m` files and your four `.xlsx` inputs in the same folder.
2. In MATLAB:
   ```matlab
   % With condensation clamp:
   Compute_Condensation_Model
   % Without condensation clamp:
   Compute_NoCondensation_Model

