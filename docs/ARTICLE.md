# OptoCore-3D: Architectural Simulation for 3D Photonic Transformer Inference

> [!WARNING]
> This article reports **simulated architectural projections** from a behavioral model. It does **not** report measured data from fabricated silicon.

## Abstract

OptoCore-3D is a monolithic 3D photonic accelerator concept evaluated through behavioral simulation. The objective is to test whether high optical parallelism (waveguide fabric + electro-optic gating) can increase Transformer inference throughput under explicit thermal control.

This revision separates four dimensions that are often conflated:
1. **core-only power** vs **system wall-plug energy**,
2. **nominal peak operating point** vs **sustained DVFS operating point**,
3. **transient thermal kinetics** vs **DC steady-state limits**,
4. **simulation projection** vs **fabricated hardware measurement**.

## 1) Architectural model (what is simulated)

The simulator models a single accelerator core with:
- 1024 parallel waveguides,
- 32 modulation nodes per waveguide (32,768 gates/core),
- 3D proximity assumptions for memory/feed paths,
- thermal-aware runtime control via DVFS states.

The model is intended for architecture exploration, not fabrication sign-off.

## 2) Power and energy boundaries

### 2.1 Core-only electrical power

The reported 0.63-0.92 W range is treated as **core-side modeled power** at selected operating points. These values are not full-system board power.

### 2.2 System wall-plug energy

The 1.14-1.81 pJ/token range is treated as a **system projection boundary** (core + externalized overhead assumptions such as photonic source/conditioning and supporting electronics). It must not be interpreted as a direct silicon measurement.

### 2.3 Consistency equations

\[
E_{token}=\frac{P}{\Theta}, \quad \Theta=\frac{P}{E_{token}}
\]

Using \(\Theta = 1.39\times10^{12}\) tokens/s with \(P_{core}=0.63\text{ to }0.92\) W implies:
\[
E_{core}=0.45\text{ to }0.66\ \text{pJ/token}
\]

Therefore, core-energy and wall-plug-energy numbers must be labeled as different boundaries, not mixed as a single metric.

## 3) Operating points: peak vs sustained

### 3.1 Nominal peak point

A nominal peak point is the highest modeled throughput state (e.g., 50 GHz class operation) before sustained thermal constraints dominate.

### 3.2 Sustained DVFS point

A sustained point is the long-run operating state under closed-loop DVFS where average power is bounded to satisfy thermal constraints over time.

### 3.3 DVFS state definition used in this project

- **State A (full speed):** \(T < 350\,K\)
- **State B (proactive DVFS):** \(350\,K \le T < 360\,K\)
- **State C (emergency throttle):** \(T \ge 360\,K\)

These are control-policy thresholds in simulation, not hardware-validated guardbands.

## 4) Thermal kinetics vs steady-state

### 4.1 Transient model

The simulator uses a first-order thermal model:
\[
\frac{dT}{dt}=\frac{P(t)R_{th}-(T(t)-T_{amb})}{\tau}
\]
with representative parameters \(R_{th}=100\,K/W\), \(\tau=10\,ns\).

### 4.2 DC steady-state check

For constant power, the same model implies:
\[
\Delta T_{DC}=P\cdot R_{th}
\]
At \(P=0.90\,W\), \(\Delta T_{DC}=90\,K\). With \(T_{amb}=298\,K\), unconstrained steady-state would approach \(\sim388\,K\).

Interpretation: a sub-360 K trajectory can be valid in **transient windows** or with changed effective thermal conditions (lower effective \(R_{th}\), lower average power, or additional cooling). This distinction must remain explicit.

## 5) Results status and evidence type

- **Current evidence:** behavioral simulation outputs and derived equations.
- **Not yet provided here:** fabricated die, packaged silicon, bench instrumentation, measured wall-plug traces.

Claims in this repository should therefore be phrased as:
- “the simulator projects…”,
- “under these assumptions…”,
- “pending physical validation…”.

## 6) Open material and next validation steps

Open in this repository: architecture narrative, assumptions, equations, and summary metrics.  
Required for stronger claims in future revisions: calibrated device models, uncertainty intervals, and fabricated-hardware measurements.

## 7) Conclusion

OptoCore-3D is presented as a rigorous architectural simulation study. The technical vision remains ambitious, but the evidence boundary is explicit: current trillion-token-class figures are **modeled projections**, not measured silicon performance.
