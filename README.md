# OptoCore-3D

DOCUMENT IDENTIFIER: ARCH-3D-PCM-2026-V1  
STATUS: Public High-Level Overview / Selective Disclosure; Proprietary Implementation  
AUTHOR / DESIGNER: andykostin1-maker  
LICENSE: PROPRIETARY — ALL RIGHTS RESERVED

## Legal Notice

This repository contains proprietary technical documentation and architectural concepts.

This repository provides a public high-level, non-enabling overview of selected architectural concepts and selected simulation results. Complete implementation details, proprietary methods, calibration data, device-level parameters, layout/process information, confidential simulation inputs, and manufacturing know-how are intentionally withheld and remain proprietary or confidential where applicable.

No permission is granted to copy, reproduce, modify, distribute, publish, commercialize, manufacture, implement, reverse engineer, or create derivative works based on any part of this repository, subject to applicable law.

Repository access grants no patent, trade-secret, know-how, copyright, or other intellectual-property license or rights.

Disclosure / prior-art clarification: this repository records a dated public disclosure of selected high-level concepts and materials. It is not intended to constitute a complete defensive publication of proprietary implementation details, and this notice does not itself establish patent rights, patentability, trade-secret status, or legal prior-art effect in any jurisdiction.

Any technical evaluation, due diligence, collaboration, licensing, acquisition, or investment discussion requires prior written permission and may require a separate confidentiality agreement. Initial non-confidential inquiries may be submitted through the repository issue tracker (Issues tab); do not include confidential information in public issues, and any formal permission request must proceed through a private channel arranged by the rights holder.

This notice is not legal advice and does not replace professionally drafted agreements.

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
