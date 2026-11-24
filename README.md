# Tokamak test-particle orbit study

> **Status: in progress (started November 2026).** Current phase: working through the governing
> physics and derivations ([`notes/derivations.md`](notes/derivations.md)). The computation stages
> below are planned; code and results will be added here as each stage is completed and checked.

## Why
A tokamak confines a plasma with a twisted magnetic field. Every confinement question begins
with a single charged particle: how it moves in that field, which particles are trapped, how far
their orbits stray from a flux surface, and which ones escape to the wall. Fast 3.5 MeV alpha
particles from D–T fusion must stay confined long enough to heat the plasma. Their first-orbit
losses are a basic constraint on reactor design.

This project builds that picture from first principles: the equations of motion, their conserved
quantities, the analytic orbit theory, and numerical codes checked against that theory.

## Questions
1. How do conserved quantities (energy, magnetic moment μ, canonical toroidal momentum P_φ)
   constrain charged-particle orbits in an axisymmetric field?
2. Where is the boundary between trapped and passing particles, and how wide are banana orbits?
   How well do the standard large-aspect-ratio formulas hold for thermal ions and for 3.5 MeV alphas?
3. What fraction of fusion alphas is lost on its first orbit, and how does that fraction depend
   on plasma current and on where the alphas are born?

## Physics basis
The field is axisymmetric, with circular flux surfaces:

    B = ∇ψ × ∇φ + F ∇φ,   dψ/dr = B₀ r / q(r)

The particle motion follows the Lorentz force:

    m dv/dt = Q v × B

In an axisymmetric field, the canonical toroidal momentum is exactly conserved:

    P_φ = m R v_φ + Q ψ

From these follow the trapping condition (v∥/v)² < 2ε/(1+ε), the banana width Δr ≈ 2ρ_pol, and the
bounce period. Full derivations, with my progress through them, are in
[`notes/derivations.md`](notes/derivations.md).

## Planned stages
| Stage | Work | Check against |
|---|---|---|
| 1 | Field model; full-orbit (Boris) particle pusher | energy and P_φ conservation; gyro-radius and drift speed in simple fields |
| 2 | Trapped vs passing orbits for thermal ions and alphas | analytic trapping boundary, banana width from invariants, bounce-period integral |
| 3 | Guiding-centre (drift) code | full-orbit code; same invariants |
| 4 | First-orbit losses of 3.5 MeV alphas vs birth radius and plasma current | convergence in time step and run length; guiding-centre bracket |
| 5 | Comparison with published TFTR first-orbit losses (circular cross-section) | Darrow et al., *Phys. Plasmas* 3, 1875 (1996) |
| 6 | Shaped (elongated, Shafranov-shifted) equilibrium for an ITER-like case | stages 2–4 in the new geometry |

## Contributions and tools
- **Mine:** I chose this project and its scope, as groundwork for a fusion-focused master's,
  and I am directing the work stage by stage.
- **Tools:** the derivation notes were drafted with an AI assistant (Anthropic's Claude) as a
  study guide, and I am working through them myself. The same assistant will be used for coding
  support; that will be stated alongside each stage when it is added.

## Licence
CC BY 4.0 (`LICENSE.md`).
