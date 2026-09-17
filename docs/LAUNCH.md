# OptoCore-3D Public Launch Kit

## Positioning

OptoCore-3D is a public high-level overview and selective disclosure of a behavioral and thermal simulation for a proposed 3D photonic accelerator architecture for Transformer inference.

The project reports architectural projections under explicit assumptions. It does **not** report measurements from fabricated silicon.

Public announcements must stay non-enabling: do not publish confidential implementation details, raw simulator inputs, calibration data, device-level parameters, layout/process information, or other material that would enable full implementation.

## Short announcement

We released OptoCore-3D, a public high-level overview and selective disclosure of a documented behavioral and thermal simulation model for a 3D photonic accelerator architecture for Transformer inference.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

The model explores optical parallelism, electro-optic gating, 3D memory proximity, transient thermal behavior, and closed-loop DVFS. Under the documented assumptions, the simulator projects up to 1.39 trillion tokens/s and approximately 1.04–1.89 pJ/token at the system-projection boundary.

These are simulation results, not fabricated-silicon measurements. The repository separates core-only power, wall-plug energy, nominal peak throughput, sustained DVFS operation, and transient thermal behavior.

We welcome independent review of the energy accounting, thermal RC model, duty-cycle assumptions, and 50 GHz split-rail driver concept.

## X / Bluesky thread

1/ We released OptoCore-3D: a public high-level overview and selective disclosure of a behavioral simulation for a proposed 3D photonic accelerator for Transformer inference.

2/ The model combines waveguide parallelism, electro-optic gating, 3D memory-proximity assumptions, and thermal-aware DVFS.

3/ Under the documented assumptions, the model projects up to 1.39 trillion tokens/s. This is an architectural simulation projection, not a measurement from fabricated silicon.

4/ The repository separates core-only power from system wall-plug energy and transient temperature from DC steady-state limits.

5/ We are looking for rigorous review of the energy model, thermal RC assumptions, duty-cycle treatment, and split-rail 50 GHz driver concept.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

## LinkedIn post

We published OptoCore-3D, a public high-level overview and selective disclosure of a behavioral and thermal simulation for a proposed 3D photonic accelerator architecture for Transformer inference.

The project explores whether high optical parallelism, electro-optic gating, 3D memory proximity, and closed-loop DVFS can support very high modeled token throughput under explicit power and thermal assumptions.

The current model projects up to 1.39 trillion tokens/s at approximately 1.04–1.89 pJ/token under its stated system-boundary assumptions. These figures are architectural simulation results, not measurements from fabricated hardware.

The repository includes the technical article, results summary, limitations, equations, and explicit evidence boundaries. Independent review is especially welcome for the energy decomposition, transient thermal model, duty-cycle assumptions, and split-rail driver architecture.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

## Show HN title

Show HN: OptoCore-3D — behavioral simulation of a 3D photonic AI accelerator

## Show HN submission text

OptoCore-3D is a public high-level overview and selective disclosure of a documented behavioral and thermal simulation model for a proposed 3D photonic accelerator for Transformer inference.

Repository: https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

It models waveguide parallelism, electro-optic gating, memory-proximity assumptions, transient thermal behavior, and closed-loop DVFS. The current documented model projects up to 1.39 trillion tokens/s and approximately 1.04–1.89 pJ/token at the system-projection boundary.

This is not fabricated hardware and the numbers are not silicon measurements. The repository explicitly separates core-only power from wall-plug energy, nominal peak from sustained DVFS operation, and transient temperature from DC steady-state behavior.

---

### Discussion priorities

- power accounting;
- thermal RC assumptions;
- duty-cycle model;
- 50 GHz split-rail driver concept.

## Technical outreach message

Subject: Request for independent review of a publicly disclosed high-level photonic accelerator simulation

Hello,

I published OptoCore-3D, a public high-level overview and selective disclosure of a behavioral and thermal simulation for a proposed 3D photonic accelerator for Transformer inference.

I am seeking technical feedback rather than endorsement, particularly on the power-boundary definitions, WDM and SRAM-I/O assumptions, first-order thermal model, duty-cycle treatment, and split-rail 50 GHz driver concept.

The repository clearly labels the results as architectural projections rather than fabricated-silicon measurements:
https://github.com/andykostin1-maker/monolithic-3d-photonic-architecture

Any critical review or suggested correction would be valuable.

## Publication checklist

- [ ] Create a tagged GitHub release after reviewing the final public files.
- [ ] Confirm that no confidential layout, material recipe, mask, process, or patent-sensitive information is included.
- [ ] Confirm that no confidential implementation details, raw simulator inputs, calibration data, or device-level parameters are included.
- [ ] Add raw simulator outputs and plotting scripts before claiming reproducibility.
- [ ] Add architecture, temperature, throughput, and energy figures.
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
- “measured 1.39 trillion tokens/s”;
- “proven in silicon”;
- “100,000x faster than GPUs” without matched system boundaries and a cited baseline.
