# Electron Motion in a Time-Varying Magnetic Field

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Paper: CC BY 4.0](https://img.shields.io/badge/Paper-CC%20BY%204.0-green.svg)](paper/thesis.pdf)

**Interactive simulation + theoretical analysis of an electron confined in a cylindrical time-varying magnetic field.**

> B = B₀ sin(ωt) e_z  |  r₀ = R/2  |  Mathieu equation  |  Parametric resonance

---

## Try it Online

**[→ Open Interactive Demo](https://alexfuchn.github.io/electron-motion/demo/electron_motion_lab.html)**

Drag sliders to explore the (B₀, ω) confinement phase diagram in real time. Watch the electron transition from stable quasi-periodic motion through parametric resonance to escape.

---

## Overview

A single electron is placed at rest at (0, R/2) inside an infinitely long cylinder of radius R. A uniform, time-varying magnetic field B = B₀ sin(ωt) e_z permeates the cylinder. Despite the absence of spatial field gradients, the electron can be either permanently confined or ejected — depending entirely on the dimensionless parameter:

```
q = ω_c² / (4ω²)  =  e²B₀² / (16m²ω²)
```

This project combines analytical mechanics (Lagrangian & Newtonian), Floquet stability theory, multiple-scale perturbation analysis, Kapitza averaging, and high-resolution numerical simulation (1.96×10⁶ parameter points, RK4) to characterize the complete confinement phase diagram.

### Key findings

- **Premature escape**: Amplitude amplification causes electron escape at q ≈ 0.27, well before the Mathieu instability band onset at q = 0.456
- **Quadrant locking**: Confined trajectories are strictly bounded to Q2 and Q4, never entering Q1/Q3
- **Origin crossing**: The electron necessarily passes through r = 0 — motion is radial oscillation, not cyclotron rotation
- **Velocity bound**: |v| < √2 ω_c R, rigorously derived from canonical angular momentum conservation
- **Straight-line boundaries**: All phase diagram boundaries are lines through the origin B₀ ∝ ω (dimensional analysis proof)

---

## Repository Structure

```
electron-motion/
├── README.md
├── LICENSE
├── paper/
│   └── thesis.pdf              # Full thesis (50 pages, Chinese)
├── demo/
│   └── electron_motion_lab.html # Interactive browser simulation
└── code/
    ├── phase_diagram.py         # (B₀, ω) confinement phase diagram
    ├── trajectories.py          # Trajectory, Fourier, Poincaré analysis
    ├── lyapunov.py              # Maximal Lyapunov exponent computation
    └── requirements.txt
```

---

## Run Locally

### Interactive demo

Open `demo/electron_motion_lab.html` in any modern browser. No dependencies.

### Numerical simulations

```bash
pip install -r code/requirements.txt
python code/phase_diagram.py     # ~46s on Intel i7, generates phase_diagram.png
```

---

## Theory

### Equation of motion

From Faraday's law and cylindrical symmetry, the induced vortex electric field is:

```
E_ind = −½ B₀ ω r cos(ωt) e_φ
```

With canonical angular momentum conservation, the radial equation reduces to the **Mathieu equation**:

```
r″ + [2q − 2q cos(2τ)] r = 0      (τ ≡ ωt)
```

### Methods

| Method | Regime | Key Insight |
|--------|--------|-------------|
| Floquet theory | All q | Stability band structure (a = 2q line) |
| Multiple-scale perturbation | q ≪ 1 | Resonance condition ω_c ≈ 2ω, amplitude evolution |
| Kapitza averaging | q ≫ 1 | Effective ponderomotive potential V_eff ∝ r² |
| RK4 numerical scan | All q | 1400×1400 phase diagram, Lyapunov exponents |

### Related systems

- **Paul trap**: RF quadrupole ion trapping (same Mathieu equation, different a/q)
- **Betatron**: Electron acceleration by changing magnetic flux
- **Kapitza pendulum**: Inverted pendulum stabilized by fast oscillation

---

## Citation

```bibtex
@thesis{fu2026electron,
  title   = {Research on the Confined Motion of an Electron
             in a Cylindrical Time-Varying Magnetic Field},
  author  = {Chengjun Fu},
  school  = {China University of Mining and Technology},
  year    = {2026},
  note    = {Undergraduate thesis}
}
```

---

## License

- **Code & Demo**: [MIT License](LICENSE)
- **Paper** (`paper/thesis.pdf`): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

*China University of Mining and Technology — School of Materials Physics — 2026*
