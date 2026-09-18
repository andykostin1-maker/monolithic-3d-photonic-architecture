# RESULTS (SIMULATION SUMMARY)

> [!WARNING]
> All values below are simulator-derived architectural projections or simulator-estimated comparison points, not measured silicon data.

**Latest public simulation revision:** September 18, 2026.

## Current public architecture summary

- **Topology:** 4 physical photonic cores in a layer-pipelined arrangement, with one Transformer layer assigned to each core.
- **Memory assumption:** 32 SRAM banks, logically partitioned as 8 banks per core. This is an architectural modeling assumption, not a hardware demonstration of zero congestion.
- **Evidence boundary:** All values below are simulator outputs under documented assumptions and remain pending physical validation.

## Definitions and equations

- Throughput: \(\Theta\) (GT/s)
- Token latency: modeled end-to-end token latency in the pipeline (ps/token)
- Peak optical power: maximum optical carrier power used for the reported operating point (W)
- Average optical power: duty-cycle-averaged optical carrier power (W)
- System-boundary energy per token: \(E_{token}=P_{system}/\Theta\) when power and throughput share the same modeled system boundary
- Thermal steady-state estimate: \(T_{ss,est} \approx T_{amb} + P_{eff} \cdot R_{th} \cdot k_{hotspot}\)
- Thermal transient model: \(\frac{dT}{dt} = \frac{P_{eff}(t)\cdot R_{th}\cdot k_{hotspot} - (T(t)-T_{amb})}{\tau_{th}}\)

Reference assumptions used in the public documentation:
- \(T_{amb}=300\,K\)
- effective \(R_{th}=40\,K/W\)
- hotspot factor \(k_{hotspot}=1.36\)
- thermal time constant \(\tau_{th}\sim1\text{–}10\,\mu s\)
- thermal policy thresholds: **State A** below 350 K, **State B** from 350 K to below 360 K, **State C** at or above 360 K

> [!NOTE]
> The thermal model uses total dissipative load \(P_{eff}\), not optical carrier power alone. Likewise, pipelined throughput and token latency are separate model outputs and should not be treated as simple reciprocals.

## Throughput, latency, power, and energy

| Metric | Single-core baseline | Current 4-core projected revision | Notes |
|---|---:|---:|---|
| Throughput | 4.534 GT/s | 16.32 GT/s | Approximately 3.6x modeled speedup |
| Token latency | 757.84 ps/token | 252.28 ps/token | Simulator-reported latency reduction |
| Peak optical power | — | 1.0 W total / 0.25 W per core | Peak optical carrier budget |
| Average optical power with pulsed laser gating | — | 0.35 W total | Duty cycle 0.35 |
| System-boundary energy per token | — | 107.21 pJ/token | Includes gated optical carrier and electrical overheads |

## Thermal comparison points (simulation outputs / estimates)

| Case | Temperature | Policy-state interpretation | Public interpretation |
|---|---:|---|---|
| Unmitigated continuous 1.0 W optical case | 377.62 K | State C | Above the documented 360 K threshold |
| Stated power-reduction mitigation case | 362.39 K | State C | Improved versus unmitigated, but still above 360 K |
| Stated \(R_{th}\)-reduction mitigation case | 353.14 K | State B | Within the proactive-control band |
| Pulsed laser gating (duty cycle 0.35) | 342.26 K | State A | Within the nominal operating band |

## Notes for reviewers

1. The **107.21 pJ/token** figure is a **modeled system-boundary estimate**. It is not directly comparable to optical-only power numbers without aligning boundaries.
2. The **32-bank / 8-per-core** partition is an architectural assumption used to study reduced contention. It should not be read as experimental proof of zero bank conflicts in fabricated hardware.
3. Thermal comparison points above are simulator outputs or simulator-derived estimates for named operating cases. They are not fabricated-package temperature measurements.
4. Hardware measurement status: **not available in this repository**.
