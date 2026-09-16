# OptoCore-3D

> [!WARNING]
> **Simulation-only project.** All performance, power, and thermal numbers in this repository are outputs of an architectural simulator. They are **not** measurements from fabricated silicon.

## Executive summary

OptoCore-3D is a reproducible architectural simulation of a monolithic 3D photonic accelerator concept for Transformer inference. The project explores whether high optical parallelism plus thermal-aware DVFS could enable very high token throughput under explicit power and thermal assumptions.

This repository is intentionally scoped to scientific communication:
- clearly defined operating points,
- explicit equations and boundaries,
- transparent distinction between simulated projection and hardware measurement.

## What this repository claims (and does not claim)

### In scope
- Behavioral simulation outputs for throughput, energy, and temperature.
- First-order thermal dynamics with DVFS control states.
- Architecture-level projections under stated assumptions.

### Out of scope
- No fabricated OptoCore-3D chip data.
- No measured silicon PPA (power/performance/area).
- No claim of production-ready manufacturability from this documentation alone.

## Read in this order

1. **[docs/ARTICLE.md](docs/ARTICLE.md)** — technical narrative with assumptions and operating regimes.
2. **[RESULTS.md](RESULTS.md)** — key metrics, equations, and operating-point table.
3. **[LIMITATIONS.md](LIMITATIONS.md)** — model boundaries, uncertainty sources, and non-claims.

## Reproducibility-first structure

To avoid ambiguous comparisons, every reported number is tagged by:
- **Power boundary:** core-only electrical power vs system wall-plug projection.
- **Operating regime:** nominal peak point vs sustained DVFS-limited point.
- **Thermal regime:** transient trajectory vs DC steady-state endpoint.
- **Evidence type:** simulator output vs fabricated-hardware measurement.

If a number in this repository is missing one of these tags, treat it as incomplete.

## Core equations used in the summaries

For operating-point consistency checks:

- \(E_{token} = P / \Theta\)
- \(\Theta = P / E_{token}\)
- \(\Delta T_{DC} = P \cdot R_{th}\)
- \(\frac{dT}{dt} = \frac{P(t)\cdot R_{th} - (T(t)-T_{amb})}{\tau}\)

where \(P\) is power, \(\Theta\) is throughput (tokens/s), \(E_{token}\) is energy/token, \(R_{th}\) is thermal resistance, and \(\tau\) is the thermal time constant.

## Citation and review note

This repository is prepared to support technical review. Please cite results as **architectural simulation projections** unless and until fabricated-hardware measurements are published.
