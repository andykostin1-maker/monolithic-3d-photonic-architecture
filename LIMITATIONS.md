# LIMITATIONS

> [!WARNING]
> The values in this repository are architectural simulation outputs and derived projections. They are not fabricated-silicon measurements.

## 1) Model assumption boundary

This project currently uses a behavioral/architecture-level abstraction. The current public revision models **4 physical photonic cores** in a layer-pipelined arrangement with **one Transformer layer per core**.

The public documentation also assumes **32 SRAM banks** logically partitioned as **8 banks per core**. That partitioning is an architectural assumption used to study contention reduction; it is not an experimentally demonstrated claim of zero congestion in fabricated hardware.

The repository does not include full foundry-calibrated device physics, process variation/yield closure, packaging parasitics, or bench-calibrated photonic loss stacks.

## 2) Power and energy boundary

Reported metrics must be interpreted with explicit boundaries:
- **Peak optical power:** 1.0 W total / 0.25 W per core for the current revision's optical carrier budget.
- **Average optical power:** 0.35 W total under pulsed laser gating with duty cycle 0.35.
- **System-boundary energy estimate:** 107.21 pJ/token including the gated optical carrier and modeled electrical overheads.

These boundaries are not interchangeable. Optical power should not be substituted directly for system-boundary energy accounting or for total thermal dissipation without the corresponding modeled boundary definition.

## 3) Operating-point boundary

Current public headline metrics describe the latest simulated 4-core revision:
- **16.32 GT/s** throughput,
- **252.28 ps/token** latency,
- versus a **4.534 GT/s** / **757.84 ps/token** single-core baseline.

These are simulator outputs under documented assumptions. They are not guaranteed sustained hardware operating points and should not be quoted as measurements.

## 4) Thermal model boundary

Thermal behavior is represented by a first-order model with public documentation parameters:
- ambient temperature \(T_{amb}=300\,K\),
- effective thermal resistance \(R_{th}=40\,K/W\),
- hotspot factor \(k_{hotspot}=1.36\),
- thermal time constant \(\tau_{th}\sim1\text{–}10\,\mu s\).

For documentation-level steady-state checks, \(T_{ss,est} \approx T_{amb} + P_{eff}\cdot R_{th}\cdot k_{hotspot}\), where \(P_{eff}\) is the total dissipative load represented by the thermal model. Because \(\tau_{th}\) is much longer than the pipeline cadence, the thermal model follows time-averaged dissipation rather than instantaneous optical pulses.

Quoted comparison points such as **377.62 K**, **362.39 K**, **353.14 K**, and **342.26 K** should be read as simulator outputs / simulator-estimated operating cases, not measured temperatures from fabricated hardware.

## 5) Simulation vs hardware boundary

Current repository status:
- ✅ Simulated architectural projection
- ❌ Fabricated chip measurement
- ❌ Packaged system wall-plug measurement
- ❌ Independent lab replication on silicon

Any external communication should clearly state these boundaries.

## 6) Comparison caveat

Cross-platform comparisons (for example, versus GPUs or other accelerators) are only meaningful when system boundaries match: token definition, precision, memory scope, I/O, cooling, and wall-plug accounting.
