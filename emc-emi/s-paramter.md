# S-parameters

## What S-parameters describe

S-parameters relate incident and reflected travelling waves at each port, normalized to a reference impedance $(\Z_0)$ (commonly only 50 $\Omega$):

$$b=Sa$$

## Physical intuition
Instead of resistanc/inductance it describes reflection, transmission and inseration/return loss

## The sources of S-parameters
1. Measurement
A vector network analyzer (VNA) sends incident waves and measures reflected/transmitted waves at matched terminations after a calibration. This is the **empirical route**.
2. EM /circuit simulation (compute from physics)
Field solvers and circuit simulators produce S-parameters directly:
- Full-wave solvers (openEMS) excite ports with waves and compute reflection/transmission -> S-parameters natively.
- Circuit simulators (ngspice) do an "S-parameter analysis" from a netlist. Computed, never measured.
3. Conversion from other parameter sets
If one has Z, Y, ABCD, or H matrix, one can derive S-parameters purely by math, given a reference impedance $Z_0$:
$$S=\frac{Z-Z_0}{Z+Z0}$$

