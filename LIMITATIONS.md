# LIMITATIONS

> [!WARNING]
> The values in this repository are architectural simulation outputs and derived projections. They are not fabricated-silicon measurements.

## 1) Model assumption boundary

This project currently uses a behavioral/architecture-level abstraction. It does not yet include full foundry-calibrated device physics, process variation/yield closure, packaging parasitics, or bench-calibrated photonic loss stacks.

## 2) Power decomposition boundary

Reported metrics must be interpreted with explicit boundaries:
- **Core-only power**: modeled accelerator-core electrical budget.
- **System wall-plug projection**: projected energy including non-core overhead assumptions.

These boundaries are not interchangeable. Any comparison or headline metric must specify which boundary is used.

## 3) Operating-point boundary

Two classes of operating points are used:
- **Nominal peak** (short-window/high-throughput condition),
- **Sustained DVFS** (long-run thermally constrained condition).

A nominal peak number should not be treated as guaranteed sustained throughput.

## 4) Thermal model boundary

Thermal behavior is represented by a first-order model with representative parameters (e.g., \(R_{th}=100\,K/W\), \(\tau=10\,ns\)). This captures trend-level control behavior but not full 3D spatial thermal gradients.

At DC, \(\Delta T=P\cdot R_{th}\). Therefore sustained operation claims below thermal thresholds require explicit average-power and cooling assumptions.

## 5) Simulation vs hardware boundary

Current repository status:
- ✅ Simulated architectural projection
- ❌ Fabricated chip measurement
- ❌ Packaged system wall-plug measurement
- ❌ Independent lab replication on silicon

Any external communication should clearly state these boundaries.

## 6) Comparison caveat

Cross-platform comparisons (e.g., versus GPU) are only meaningful when system boundaries match (token definition, precision, memory scope, I/O, cooling, and wall-plug accounting).
