# OptoCore-3D: Architectural Simulation for 3D Photonic Transformer Inference

> [!WARNING]
> This article reports **simulated architectural projections** from a behavioral model. It does **not** report measured data from fabricated silicon.

**Latest public simulation revision:** September 18, 2026.

## Abstract

OptoCore-3D is a monolithic 3D photonic accelerator concept evaluated through behavioral simulation. In the current public revision, the simulator explores whether scaling to **4 physical photonic cores** in a **layer-pipelined arrangement**—with **one Transformer layer per core**—can improve inference throughput while remaining inside an explicit thermal-control policy.

Under the documented assumptions, the simulator projects:
- **32 SRAM banks** logically partitioned as **8 banks per core** as an architectural assumption,
- **16.32 GT/s** throughput versus **4.534 GT/s** for the single-core baseline (**~3.6x modeled speedup**),
- **252.28 ps/token** modeled token latency versus **757.84 ps/token** for the single-core baseline,
- **1.0 W total peak optical power** (**0.25 W per core**),
- **0.35 W total average optical power** under pulsed laser gating with duty cycle **0.35**, and
- **107.21 pJ/token** as a **modeled system-boundary estimate** that includes the gated optical carrier and electrical overheads.

These are simulation projections under documented assumptions, pending physical validation.

## 1) Architectural model (what is simulated)

The public model represents a **4-core layer-pipelined photonic inference architecture**. Each physical photonic core is assigned one Transformer layer in the modeled pipeline.

The public documentation intentionally stays non-enabling. It therefore limits the architecture description to:
- multi-core photonic inference stages,
- logical proximity between compute and memory,
- thermal-aware control states, and
- architectural SRAM partition assumptions.

For the current revision, the simulator assumes **32 SRAM banks** that are **logically partitioned into 8 banks per core**. This assumption is used to study reduced contention in the modeled pipeline; it does not constitute experimental proof of zero-congestion memory behavior in fabricated hardware.

The model is intended for architecture exploration, not fabrication sign-off.

## 2) Power and energy boundaries

### 2.1 Optical power boundary

The current revision reports:
- **1.0 W total peak optical power**, and
- **0.35 W total average optical power** under pulsed laser gating with duty cycle **0.35**.

These are optical-carrier figures for the documented operating points.

### 2.2 System-boundary energy estimate

The current revision reports **107.21 pJ/token** as a **modeled system-boundary estimate**. This value includes the gated optical carrier together with modeled electrical overheads. It must not be interpreted as a direct silicon measurement.

### 2.3 Boundary discipline

Power, energy, and temperature claims remain meaningful only when the reporting boundary is explicit. In particular:
- optical power figures are not full-system energy figures,
- thermal behavior depends on total dissipative load represented by the model, and
- public headline numbers must remain labeled as simulator projections.

## 3) Throughput and latency summary

The current public revision compares a single-core baseline to the 4-core layer-pipelined configuration:

| Metric | Single-core baseline | 4-core projected revision |
|---|---:|---:|
| Throughput | 4.534 GT/s | 16.32 GT/s |
| Token latency | 757.84 ps/token | 252.28 ps/token |

The modeled throughput increase is approximately **3.6x**. The latency reduction is reported directly by the simulator for the pipelined architecture. These two outputs should not be collapsed into a simple reciprocal relationship because pipelined throughput and end-to-end token latency capture different aspects of the modeled schedule.

## 4) Thermal policy and operating states

### 4.1 Thermal policy thresholds

The public control policy uses three temperature bands:
- **State A:** below **350 K**,
- **State B:** from **350 K** to below **360 K**,
- **State C:** at or above **360 K**.

These thresholds are policy states used by the simulator. They are not hardware-validated guardbands.

### 4.2 Public thermal model assumptions

The public documentation uses the following thermal assumptions:
- ambient temperature \(T_{amb}=300\,K\),
- effective thermal resistance \(R_{th}=40\,K/W\),
- hotspot factor \(k_{hotspot}=1.36\),
- thermal time constant \(\tau_{th}\sim1\text{–}10\,\mu s\).

A documentation-level consistency form is:

\[
T_{ss,est} \approx T_{amb} + P_{eff}\cdot R_{th}\cdot k_{hotspot}
\]

with transient behavior described by:

\[
\frac{dT}{dt}=\frac{P_{eff}(t)\cdot R_{th}\cdot k_{hotspot}-(T(t)-T_{amb})}{\tau_{th}}
\]

Here \(P_{eff}\) denotes the total dissipative load represented by the model, not optical carrier power alone.

### 4.3 Transient averaging vs steady-state interpretation

Because the thermal time constant is on the order of **1–10 microseconds**, while the modeled token pipeline operates on the **picosecond** scale, the thermal model integrates **time-averaged dissipation** rather than instantaneous optical pulses. Public thermal interpretation should therefore distinguish:
- **transient or duty-averaged behavior**, and
- **steady-state / DC consistency estimates**.

### 4.4 Thermal comparison points (simulation outputs / estimates)

| Case | Temperature | Policy interpretation |
|---|---:|---|
| Unmitigated continuous 1.0 W optical case | 377.62 K | State C |
| Stated power-reduction mitigation case | 362.39 K | State C |
| Stated \(R_{th}\)-reduction mitigation case | 353.14 K | State B |
| Pulsed laser gating (duty cycle 0.35) | 342.26 K | State A |

These temperatures are simulator outputs or simulator-estimated operating cases for the current revision. They are not measured package or die temperatures.

## 5) Results status and evidence type

- **Current evidence:** behavioral simulation outputs and simulator-estimated comparison points.
- **Not yet provided here:** fabricated die, packaged silicon, bench instrumentation, measured wall-plug traces.

Claims in this repository should therefore be phrased as:
- “the simulator projects…”,
- “under the documented assumptions…”,
- “pending physical validation…”.

## 6) Public disclosure boundary

This repository intentionally withholds enabling implementation details such as raw simulator inputs, calibration data, layout/process information, device-construction specifics, physical dimensions, proprietary driver details, and other confidential parameters.

The goal of the public materials is evidence-disciplined technical communication, not a complete manufacturing disclosure.

## 7) Conclusion

OptoCore-3D is presented as a rigorous architectural simulation study. The current public revision supports a **4-core layer-pipelined** projection with **16.32 GT/s** modeled throughput, **252.28 ps/token** modeled latency, and **107.21 pJ/token** modeled system-boundary energy under documented assumptions.

The evidence boundary remains explicit: these are **simulation projections**, not fabricated-silicon measurements.
