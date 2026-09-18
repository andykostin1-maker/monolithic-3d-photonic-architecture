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
> **Simulation-only project.** All performance, power, energy, and thermal numbers in this repository are outputs of an architectural simulator. They are **not** measurements from fabricated silicon.

## Executive summary

OptoCore-3D is a documented architectural simulation of a monolithic 3D photonic accelerator concept for Transformer inference. The latest public simulation revision in this repository is dated **September 18, 2026**.

Under the documented assumptions, the simulator projects:
- **4 physical photonic cores** in a layer-pipelined arrangement with **one Transformer layer per core**,
- **32 SRAM banks**, logically partitioned as **8 banks per core** as an architectural assumption,
- **16.32 GT/s** throughput versus **4.534 GT/s** for the single-core baseline (**~3.6x modeled speedup**),
- **252.28 ps/token** modeled token latency versus **757.84 ps/token** for the single-core baseline,
- **1.0 W total peak optical power** (**0.25 W per core**),
- **0.35 W total average optical power** under pulsed laser gating with **duty cycle 0.35**, and
- **107.21 pJ/token** as a **modeled system-boundary estimate** that includes the gated optical carrier and electrical overheads.

These statements are architecture-level simulation projections pending physical validation. They should not be interpreted as fabricated-device data or as proof of zero-congestion memory behavior in hardware.

## What this repository claims (and does not claim)

### In scope
- Behavioral simulation outputs for throughput, token latency, energy, and temperature.
- A 4-core layer-pipelined architectural projection under explicit memory-partition and thermal assumptions.
- First-order thermal dynamics with policy states A/B/C.
- Architecture-level projections under stated assumptions.

### Out of scope
- No fabricated OptoCore-3D chip data.
- No measured silicon PPA (power/performance/area).
- No claim of production-ready manufacturability from this documentation alone.
- No public release of enabling implementation details, raw simulator inputs, calibration data, or process-specific construction details.

## Read in this order

1. **[docs/ARTICLE.md](docs/ARTICLE.md)** — technical narrative with assumptions and operating regimes.
2. **[RESULTS.md](RESULTS.md)** — current public metrics, equations, and thermal-policy summary.
3. **[LIMITATIONS.md](LIMITATIONS.md)** — model boundaries, uncertainty sources, and non-claims.

## Reproducibility-first structure

To avoid ambiguous comparisons, every reported number is tagged by:
- **Architecture boundary:** single-core baseline vs 4-core layer-pipelined projection.
- **Power boundary:** optical power vs modeled system-boundary energy estimate.
- **Thermal regime:** transient averaging vs steady-state consistency estimate.
- **Evidence type:** simulator output vs fabricated-hardware measurement.

If a number in this repository is missing one of these tags, treat it as incomplete.

## Core equations used in the summaries

For documentation-level consistency checks:

- \(E_{token} = P_{system} / \Theta\) when power and throughput are reported at the same system boundary
- \(T_{ss,est} \approx T_{amb} + P_{eff} \cdot R_{th} \cdot k_{hotspot}\)
- \(\frac{dT}{dt} = \frac{P_{eff}(t)\cdot R_{th}\cdot k_{hotspot} - (T(t)-T_{amb})}{\tau_{th}}\)

where \(\Theta\) is throughput, \(E_{token}\) is energy per token, \(P_{system}\) is system-boundary power for the same reporting boundary, and \(P_{eff}\) is the total dissipative load used by the thermal model. Public thermal summaries use \(T_{amb}=300\,K\), effective \(R_{th}=40\,K/W\), hotspot factor \(k_{hotspot}=1.36\), and an approximate thermal time constant \(\tau_{th}\sim1\text{–}10\,\mu s\).

Because \(\tau_{th}\) is many orders of magnitude longer than the modeled per-token compute cadence, thermal behavior follows averaged dissipative load over time rather than instantaneous optical pulses.

## Citation and review note

This repository is prepared to support technical review. Please cite results as **architectural simulation projections under documented assumptions** unless and until fabricated-hardware measurements are published.
