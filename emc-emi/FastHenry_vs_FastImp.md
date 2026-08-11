---
title: FastHenry vs FastImp
tags: [mqs, emc, emi, fasthenry, fastimp, solver]
aliases: [MQS, magnetoquasistatic]
---

# FastHenry vs FastImp
Keywords: tag:mqs tag:emc tag:emi tag:fasthenry tag:fastimp

Both come out of MIT's computational prototyping group (Jacob White et al.) and are free, open-source parasitic extraction tools. They solve different physics regimes.

- Typical open-source flow: FastHenry (RL) + FastCap (C) for quasi-static RLC, or FastImp when full-wave coupling matters.

**Rule of thumb**: if the largest structure dimension approaches ~λ/10, FastHenry's quasi-static assumption is suspect and FastImp (or a true full-wave field solver) is the better choice.


## FastHenry
- **What it solves**: Magnetoquasistatic (MQS) problems - frequency-dependent **inductance (L) and resistance (R)** of arbitrary 3D conductor geometries.
- **Method**: Voulmen filament discretization (mesh of conductors into filaments) + a mesh analysis formulation accelerate by the **multipole method** (FastHenry2 uses a preconditioned GMRES + fast multipole). Includes skin/proximity effects.
- **Assumptions**: Ignores displacement currents / capacitive coupling. Valid where the structure is electrically small (dimensions << wavelength). No dielectrics.
- **Output**: A complex impedance matrix $Z(\omega) = R(\omega) +j\omega L(\omega)$, reducible to an equivalent RL network / SPICE model.

## FastImp
- **What it solves**: Full-wave, **broadband impedance extraction** - R, L and capacitive/displacement effects together, from DC up into the electromagnetic-wave regime
- **Method**: Surface integral equation (surface formulation, so it meshes conductor surfaces not volumes) using a mixed potential / pre-corrected FFT (pFFT) acceleration. Handles both quasi-static and full-wave behavior.
- **Assumptions**: Accounts for retardation and displacement current, so it stays accuare at higher frequencies where FastHenry breaks down. Handles lossy conductors.
- **Output**: Broadpand impedance matrix suitable for high-frequency interconnect models.

## Bottom line: 
- Use FastHenry (+FasterCap) for low-cost, scriptable quasi-static RLC extraction and research.
- Use FastImp when you need broadband/full-wave impedance without buying a license. 