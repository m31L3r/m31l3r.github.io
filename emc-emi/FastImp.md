# FastImp

## What FastImp produces 
Fastimp computes a broadband impedance matrix $Z(\omega)$ - a n x n complex matrix per frequency relating terminal voltages and currents.

$V=Z(\omega)I, Z(\omega)=R(\omega)+j\omega L(\omega) (+full-wave terms)$

- Entries in Ohms.
- $Z_{ij}$ = voltageinduced at port i per unit current at port j, with all other ports open-circuited $(I_k=0)$
- It's defined in terms of total V and I at the conductor terminals - a lumped/quasi-static port definition, extended into the full-wave regime by the surface (MPIE/pFFT) formulation.

## Conversion to [S-parameters](./s-parameter.md)
They carry the same information, you convert between them with $(Z_0)$. For an n-port with reference impedance matrix $(Z_ref)$:

$$S=\frac{Z-Z_0}{Z+Z_0}$$
$$Z=Z_0\frac{I+S}{I-S}$$

matrix forms, with appropriate normalization by $\sqrt(Z_0)$ for the general port-impedance case.

So a practical flow is FastImp -> per-frequency $Z(\omega)$ -> convert to S-parameters (e.g. with `scikit-rf`'s `Network.z2s`, by suppling the Z matrix and a reference impedance), the plot return/insertion loss or cascade with other blocks.