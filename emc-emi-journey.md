# This is my journey to EMI and EMC simulations

## EMI Simulation Pipeline - Open-Source 3D Field solver


┌──────────┐     ┌──────────────┐     ┌──────────┐     ┌──────────┐     ┌────────────┐ \
│  FreeCAD │────▶│ FastCap /    │────▶│ ngspice  │────▶│  Python  │────▶│ Matplotlib │ \
│  (3D CAD)│     │ FastHenry    │     │ (Circuit │     │ (FFT +   │     │ (EMI Plot  │ \
│          │     │ (Parasitics) │     │  Sim)    │     │  Post)   │     │  vs Limits)│ \
└──────────┘     └──────────────┘     └──────────┘     └──────────┘     └────────────┘ \
                         │ \
                         ▼ \
                  ┌──────────────┐ \
                  │   OpenEMS    │     (Optional: Full-wave FDTD for \
                  │ (Full-wave EM)│      near/far-field radiation) \
                  └──────────────┘ 

### Tool Stack
| Stage |  Tool | Purpose |
|:----- |:----- |:------- |
| 3D Geometry | FreeCAD + EM-Workbench | Model buspars, PCB, enclosures |
| Capacitance Extraction | FastCap2 / FasterCap | 3D capacitance matrix |
| Inductance Extraction | FastHenry | 3D inductance/resistance matrix |
| Circuit Simulation | ngspice | Transient + AC analysis |
| Full-Wave EM | OpenEMS | FDTD near-field / far-field radiation |
| Post-Processing | Python + SciPy | FFT, spectrum, CISPR comaprison |
| Visualization | Matplotlib + ParaView | Spectrum plots, 3D field viz |