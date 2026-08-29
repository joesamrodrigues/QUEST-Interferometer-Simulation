# QUEST Interferometer Simulation — Noise Characterisation

**Independent Research Project, 2025**  
Gravity Exploration Institute, Cardiff University  
Supervised by Prof. Hartmut Grote

---

## Overview

This project builds a Finesse optical simulation of the **QUEST** (Quantum-Enhanced Space-Time) experiment — a pair of co-located Power Recycled Michelson Interferometers at Cardiff University's Gravity Exploration Institute, designed to search for high-frequency stochastic gravitational waves, scalar field dark matter, and quantum gravity signatures.

The goal of the simulation was to characterise noise features observed in the experimental QUEST data — specifically a set of peaks visible in the displacement sensitivity spectrum between approximately 5–15 MHz — by attempting to reproduce them in simulation and identify their physical origin. The simulation did not reproduce the peaks, leaving their source inconclusive. The project was paused in November 2025.

This was a self-initiated project: I approached Prof. Grote independently, and he provided the research goal, the published QUEST paper, and the experimental parameters to set up the simulation.

---

## Background — The QUEST Experiment

QUEST consists of two co-located and co-aligned Power Recycled Michelson Interferometers with perpendicular arms, housed in separate vacuum envelopes at ultra-high vacuum (~7×10⁻⁸ mbar). Key parameters from the published experiment:

- **Arm length:** 1.83 m, inter-arm separation 0.45 m
- **Input laser power:** 300 mW (1064 nm), circulating power at beamsplitter ~83–96 W
- **End mirror transmissivity:** 12.7 ppm
- **Power recycling mirror reflectivity:** 99.5%
- **Design displacement sensitivity:** 2×10⁻¹⁹ m/√Hz (1–200 MHz)
- **Achieved sensitivity:** ~5.5×10⁻¹⁸ m/√Hz (individual), 3×10⁻²⁰ m/√Hz (cross-correlated)
- PDH locking at 8 MHz and 16 MHz modulation sidebands

The first results of QUEST set new upper limits on correlated length fluctuations from 13 to 80 MHz, published in *Physical Review Letters* (Patra et al., 2025).

---

## Simulation

The simulation models a single QUEST interferometer in Finesse, replicating the optical layout and parameters from the published paper.

**Optical model:**
- 300 mW laser, 1064 nm
- Electro-optic modulator (EOM) at 8 MHz for PDH sensing
- Power recycling mirror (R = 0.995, L = 0.003)
- 50/50 beamsplitter
- X arm: 1.835 m, end mirror T = 12.7 ppm, dark fringe offset φ = −0.55°
- Y arm: 1.825 m, end mirror T = 12.7 ppm, dark fringe offset φ = +0.55°
- Differential arm signal (DARM) for gravitational-wave response

**Analyses performed:**
- Quantum-noise-limited sensitivity (QNLS) using `qnoised` and `qshot`
- Power at beamsplitter and asymmetric port vs signal frequency
- Cavity resonance scan — end mirror detuning ±180°
- Analytical calculation of FSR, FWHM, and Finesse
- Transfer function, signal, and quantum noise plotted separately
- PRM loss sweep to characterise power buildup
- End mirror loss sweep to investigate sensitivity degradation
- Dark fringe offset scan to find φ for 30 mW at asymmetric port
- PDH demodulated signal vs mirror phase

**Outcome:**
The noise peaks observed in the experimental data (around 5–15 MHz in the displacement sensitivity spectrum) were not reproduced in the simulation. The source of the peaks remains unidentified from this simulation work. Possible explanations not modelled here include thermal noise, mechanical resonances of optical mounts, or electronic noise sources not captured in a pure optical simulation.

---

## Tools and Software

| Tool | Purpose |
|------|---------|
| Python | Simulation scripting and analysis |
| Finesse | Optical interferometer simulation (installed via conda) |
| NumPy | Numerical computation |
| SciPy | Peak finding |
| Matplotlib | Visualisation |
| Jupyter Notebook | Development environment |
| conda | Environment management |

---

## Repository Contents

| File | Description |
|------|-------------|
| `QUEST.ipynb` | Full simulation notebook |

---

## Reference

Patra et al. (2025) — Broadband limits on stochastic length fluctuations from a pair of table-top interferometers, *Physical Review Letters*. DOI: [10.1103/61j9-cjkk](http://dx.doi.org/10.1103/61j9-cjkk)

---

## Acknowledgements

Prof. Hartmut Grote (Gravity Exploration Institute, Cardiff University) for providing the research goal, experimental parameters, and the published QUEST paper.
