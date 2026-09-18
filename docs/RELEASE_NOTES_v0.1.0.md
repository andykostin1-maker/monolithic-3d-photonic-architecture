# OptoCore-3D — Public Release Notes

## v0.1.0 — Architectural Simulation Release

OptoCore-3D is a public high-level overview and selective disclosure of a behavioral and thermal simulation for a proposed 3D photonic accelerator architecture for Transformer inference.

**Latest public simulation revision in this release:** September 18, 2026.

### Included

- Architecture description and operating assumptions for a **4-core layer-pipelined** public model.
- Public memory assumption of **32 SRAM banks** logically partitioned as **8 per core**.
- Throughput and latency comparison against the single-core baseline.
- Optical-power summaries, a modeled system-boundary energy estimate, and thermal-policy documentation.
- First-order thermal model assumptions and named simulation comparison points.
- Simulation limitations and evidence-status documentation.
- Public launch materials for technical review.

### Current public metrics

- **Throughput:** 16.32 GT/s versus 4.534 GT/s for the single-core baseline (**~3.6x modeled speedup**).
- **Token latency:** 252.28 ps/token versus 757.84 ps/token for the single-core baseline.
- **Peak optical power:** 1.0 W total / 0.25 W per core.
- **Average optical power under pulsed laser gating:** 0.35 W total with duty cycle 0.35.
- **Energy:** 107.21 pJ/token as a modeled system-boundary estimate including the gated optical carrier and electrical overheads.
- **Thermal comparison points:** 377.62 K (unmitigated continuous optical case), 362.39 K (stated power-reduction case), 353.14 K (stated \(R_{th}\)-reduction case), and 342.26 K (laser duty gating).

### Evidence status

All performance, power, energy, and thermal values are architectural simulation projections or simulator-estimated comparison points. This release contains no fabricated-silicon measurements and makes no claim of production-ready manufacturability.

### Review focus

Independent reviewers are invited to examine:

- energy-boundary definitions;
- memory-partition assumptions;
- throughput/latency interpretation in the layer-pipelined model;
- thermal assumptions and duty-cycle treatment;
- evidence-boundary discipline pending physical validation.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture
