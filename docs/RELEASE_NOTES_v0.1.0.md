# OptoCore-3D — Public Release Notes

## v0.1.0 — Architectural Simulation Release

OptoCore-3D is an open behavioral and thermal simulation of a proposed 3D photonic accelerator architecture for Transformer inference.

### Included

- Architecture description and operating assumptions.
- Core-only versus system wall-plug energy boundaries.
- Nominal peak versus sustained DVFS operating points.
- First-order transient thermal model and DC consistency checks.
- Simulation limitations and evidence-status documentation.
- Public launch materials for technical review.

### Evidence status

All performance, power, energy, and thermal values are architectural simulation projections. This release contains no fabricated-silicon measurements and makes no claim of production-ready manufacturability.

### Review focus

Independent reviewers are invited to examine:

- energy-boundary definitions;
- WDM laser and peripheral overhead assumptions;
- SRAM-I/O traffic amortization;
- thermal RC parameters and duty-cycle treatment;
- split-rail operation at the modeled 50 GHz class frequency.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture
