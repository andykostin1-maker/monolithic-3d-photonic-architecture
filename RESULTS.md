# RESULTS (SIMULATION SUMMARY)

> [!WARNING]
> All values below are simulator-derived architectural projections, not measured silicon data.

## Definitions and equations

- Throughput: \(\Theta\) (tokens/s)
- Power: \(P\) (W)
- Energy per token: \(E_{token}=P/\Theta\)
- Thermal DC rise: \(\Delta T_{DC}=P\cdot R_{th}\)
- First-order thermal dynamics: \(dT/dt = (P(t)R_{th}-(T-T_{amb}))/\tau\)

Reference parameters used in documentation examples:
- \(R_{th}=100\,K/W\)
- \(\tau=10\,ns\)
- DVFS threshold: 360 K

## Operating-point table

| Operating point | Boundary type | Throughput (tokens/s) | Power (W) | Derived energy (pJ/token) | Thermal interpretation |
|---|---|---:|---:|---:|---|
| Nominal peak projection | Core-only | \(1.39\times10^{12}\) | 0.63 | 0.45 | Transient-safe possible; DC rise = 63 K |
| Nominal peak projection | Core-only | \(1.39\times10^{12}\) | 0.92 | 0.66 | Transient-safe possible; DC rise = 92 K |
| System projection band | Wall-plug | \(1.39\times10^{12}\) (assumed same throughput basis) | 1.58-2.52 (implied) | 1.14-1.81 | Requires explicit overhead model and cooling assumptions |
| Sustained DVFS-limited example | Core-only | model-dependent | \(\le 0.62\) (if \(T_{amb}\approx298\,K\), \(R_{th}=100\,K/W\), target \(<360\,K\)) | model-dependent | DC-compatible limit from \(P\cdot R_{th}\) |

## Notes for reviewers

1. The 1.14-1.81 pJ/token band should be interpreted as **system-level projection**, not core-only energy at the same boundary.
2. Peak throughput and sustained throughput are intentionally separated.
3. A trajectory remaining below 360 K can be valid in transient windows even when the equivalent DC endpoint would exceed 360 K.
4. Hardware measurement status: **not available in this repository**.
