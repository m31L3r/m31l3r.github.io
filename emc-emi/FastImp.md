# FastImp

## What FastImp produces 
Fastimp computes a broadband impedance matrix $Z(\omega)$ - a n x n complex matrix per frequency relating terminal voltages and currents.

$V=Z(\omega)I, Z(\omega)=R(\omega)+j\omega L(\omega) (+full-wave terms)$

- Entries in Ohms.
- $Z_{ij}$ = voltageinduced at port i per unit current at port j, with all other ports open-circuited $(I_k=0)$
- It's defined in terms of total V and I at the conductor terminals - a lumped/quasi-static port definition, extended into the full-wave regime by the surface (MPIE/pFFT) formulation.

## Conversion to [S-parameters][]


[S-paramters]: s-parameter.md