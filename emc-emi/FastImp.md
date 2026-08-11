# FastImp

## What FastImp produces 
Fastimp computes a broadband impedance matrix $Z(\omega)$ - a n x n complex matrix per frequency relating terminal voltages and currents.

$V=Z(\omega)I, Z(\omega)=R(\omega)+j\omega L(\omega) (+full-wave terms)$

- Entries in Ohms.
- $Z_{ij}$ = voltageinduced at port i per unit current at port j, with all other ports open-circuited $(I_k=0)$