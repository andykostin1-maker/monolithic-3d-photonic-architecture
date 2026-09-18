# OptoCore-3D Public Launch Kit

## Positioning

OptoCore-3D is a public high-level overview and selective disclosure of a behavioral and thermal simulation for a proposed 3D photonic accelerator architecture for Transformer inference.

The project reports architectural projections under explicit assumptions. It does **not** report measurements from fabricated silicon.

Public announcements must stay non-enabling: do not publish confidential implementation details, raw simulator inputs, calibration data, device-level parameters, layout/process information, or other material that would enable full implementation.

## Short announcement

We released OptoCore-3D, a public high-level overview and selective disclosure of a documented behavioral and thermal simulation model for a 3D photonic accelerator architecture for Transformer inference.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

Latest public simulation revision (September 18, 2026): under the documented assumptions, the simulator projects a **4-core layer-pipelined** configuration with **16.32 GT/s** throughput, **252.28 ps/token** latency, **1.0 W peak optical power**, **0.35 W average optical power** under pulsed laser gating, and **107.21 pJ/token** as a modeled system-boundary energy estimate. The model uses **32 SRAM banks** logically partitioned as **8 per core** as an architectural assumption.

These are simulation results, not fabricated-silicon measurements. The repository keeps the evidence boundary explicit and avoids publishing enabling implementation details.

We welcome independent review of the energy accounting, memory-partition assumptions, first-order thermal model, duty-cycle treatment, and evidence boundary.

## X / Bluesky thread

1/ We released OptoCore-3D: a public high-level overview and selective disclosure of a behavioral simulation for a proposed 3D photonic accelerator for Transformer inference.

2/ Latest public simulation revision (Sep 18, 2026): the documented model uses 4 physical photonic cores in a layer-pipelined arrangement, with one Transformer layer per core, plus 32 SRAM banks logically partitioned as 8 per core as an architectural assumption.

3/ Under the documented assumptions, the simulator projects 16.32 GT/s throughput versus 4.534 GT/s for a single-core baseline, with modeled token latency improving from 757.84 ps/token to 252.28 ps/token.

4/ The current public revision also reports 1.0 W peak optical power, 0.35 W average optical power under pulsed laser gating (duty cycle 0.35), and 107.21 pJ/token as a modeled system-boundary estimate.

5/ This is an architectural simulation projection, not a measurement from fabricated silicon. We welcome criticism of the energy accounting, thermal assumptions, duty-cycle treatment, and memory-partition assumptions.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

## LinkedIn post

We published OptoCore-3D, a public high-level overview and selective disclosure of a behavioral and thermal simulation for a proposed 3D photonic accelerator architecture for Transformer inference.

Latest public simulation revision (September 18, 2026): under the documented assumptions, the simulator projects a 4-core layer-pipelined configuration with one Transformer layer per core, 32 SRAM banks logically partitioned as 8 per core as an architectural assumption, 16.32 GT/s throughput, 252.28 ps/token latency, 1.0 W peak optical power, 0.35 W average optical power under pulsed laser gating, and 107.21 pJ/token as a modeled system-boundary estimate.

These figures are architectural simulation results, not measurements from fabricated hardware. The repository also documents thermal policy states and public thermal comparison points while keeping enabling implementation details confidential.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

## Show HN title

Show HN: OptoCore-3D — behavioral simulation of a 3D photonic AI accelerator

## Show HN submission text

OptoCore-3D is a public high-level overview and selective disclosure of a documented behavioral and thermal simulation model for a proposed 3D photonic accelerator for Transformer inference.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

Latest public simulation revision (September 18, 2026): the simulator projects a 4-core layer-pipelined architecture with one Transformer layer per core, 32 SRAM banks logically partitioned as 8 per core as an architectural assumption, 16.32 GT/s throughput, 252.28 ps/token latency, and 107.21 pJ/token as a modeled system-boundary estimate. Public thermal comparison points range from 342.26 K under pulsed laser gating to 377.62 K for the unmitigated continuous optical case.

This is not fabricated hardware and the numbers are not silicon measurements. The repository explicitly separates optical power from system-boundary energy and labels all thermal data as simulation output or simulation estimate pending physical validation.

---

### Discussion priorities

- energy accounting;
- memory-partition assumptions;
- first-order thermal model;
- duty-cycle model;
- evidence-boundary discipline.

## Technical outreach message

Subject: Request for independent review of a publicly disclosed high-level photonic accelerator simulation

Hello,

I published OptoCore-3D, a public high-level overview and selective disclosure of a behavioral and thermal simulation for a proposed 3D photonic accelerator for Transformer inference.

I am seeking technical feedback rather than endorsement, particularly on the power-boundary definitions, memory-partition assumptions, first-order thermal model, duty-cycle treatment, and evidence-boundary wording.

The repository clearly labels the results as architectural projections rather than fabricated-silicon measurements:
https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

Any critical review or suggested correction would be valuable.

## Publication checklist

- [ ] Create a tagged GitHub release after reviewing the final public files.
- [ ] Confirm that no confidential layout, material recipe, mask, process, or patent-sensitive information is included.
- [ ] Confirm that no confidential implementation details, raw simulator inputs, calibration data, or device-level parameters are included.
- [ ] Confirm that public metrics match the September 18, 2026 simulation revision across all public files.
- [ ] Add architecture, temperature, throughput, and energy figures only at a non-enabling level of detail.
- [ ] Use “simulated projection” and “under documented assumptions” in every announcement.
- [ ] Ask independent photonics and computer-architecture reviewers for criticism.
- [ ] Archive the tagged release with a DOI only after the public version is final.

## Claims discipline

Use:

- “the simulator projects”;
- “under the documented assumptions”;
- “architectural simulation result”;
- “pending physical validation.”

Avoid:

- “fabricated chip achieved”;
- “measured 16.32 GT/s”;
- “proven in silicon”;
- “guaranteed zero-congestion memory behavior”;
- “100,000x faster than GPUs” without matched system boundaries and a cited baseline.
