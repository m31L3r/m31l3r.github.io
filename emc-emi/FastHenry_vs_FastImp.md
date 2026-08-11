---
title: FastHenry vs FastImp
tags: [mqs, emc, emi, fasthenry, fastimp, solver]
aliases: [MQS, magnetoquasistatic]
---

# FastHenry vs FastImp
Keywords: tag:mqs tag:emc tag:emi tag:fasthenry tag:fastimp

Both come out of MIT's computational prototyping group (Jacob White et al.) and are free, open-source parasitic extraction tools. They solve different physics regimes.

## FastHenry
- **What it solves**: Magnetoquasistatic (MQS) problems - frequency-dependent **inductance (L) and resistance (R)** of arbitrary 3D conductor geometries.
- **Method**: Voulmen filament discretization (mesh of conductors into filaments) + a mesh analysis formulation accelerate by the **multipole method** (FastHenry2 uses a preconditioned GMRES + fast multipole). Includes skin/proximity effects.
- **Assumptions**: 