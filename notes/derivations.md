# Derivation notes (work in progress)

These notes collect the physics the project rests on. They were drafted with an AI assistant (Anthropic's Claude) as a study guide. I am working through each derivation myself and ticking it off below once I can reproduce it on paper without notes.

| Section | Topic | Worked through |
|---|---|---|
| 1 | Field model: divergence-free B, flux surfaces, q(r) | ☐ |
| 2 | Invariants: energy, μ, canonical toroidal momentum P_φ | ☐ |
| 3 | Trapping condition p_crit² = 2ε/(1+ε) | ☐ |
| 4 | Banana width: leading order and exact | ☐ |
| 5 | Bounce period: exact quadrature and elliptic-integral form | ☐ |
| 6 | Prompt alpha losses: scaling with current, counter-current orbits | ☐ |
| 7 | Guiding-centre (Littlejohn) equations | ☐ |
| 8 | Comparison basis: published TFTR first-orbit losses | ☐ |

---


Symbols: R, φ, Z are cylindrical coordinates. r and θ are minor radius and poloidal angle about the axis (R₀, 0). ε = r/R₀. The particle has charge Q, mass m and speed v. The pitch is p = v∥/v.

## 1. Field model

The field is written as

  **B** = ∇ψ × ∇φ + F ∇φ,  F = B₀R₀.

- ∇·**B** = 0 exactly, because ∇·(∇ψ×∇φ) = 0 and ∇·(F∇φ) = 0 for constant F.
- The flux surfaces are concentric circles, ψ = ψ(r), with dψ/dr = B₀ r / q(r).
- The safety-factor profile is q(r) = q₀ + (q_a − q₀)(r/a)². Integrating gives

  ψ(r) = (B₀ a² / 2(q_a−q₀)) · ln(1 + (q_a−q₀) r² / (q₀a²)).

- Field components: B_R = −(1/R)∂ψ/∂Z, B_Z = (1/R)∂ψ/∂R, B_φ = B₀R₀/R. The poloidal field is therefore B_pol = B₀ r / (q R).
- The cylindrical safety factor is r B_φ / (R₀ B_pol) = q(r), as intended.
- On a flux surface the field strength is

  |B| = B₀R₀ c / R,  with c = √(1 + (r/qR₀)²).

  So |B| ∝ 1/R exactly on each surface. This makes several "textbook" results exact in this model (section 3).

**Limits of the model.** It is not a Grad–Shafranov equilibrium: there is no Shafranov shift, no elongation and no toroidal-field ripple. It is the standard analytic model for test-particle studies. Because the cross-section is circular, a given q_a corresponds to a smaller plasma current than in real, elongated ITER (section 6).

## 2. Invariants

1. **Energy.** With E = 0, the magnetic force does no work, so ½mv² is conserved.
2. **Canonical toroidal momentum.** The vector potential is **A** = ψ∇φ + (poloidal part), so A_φ = ψ/R. Axisymmetry (∂/∂φ = 0) then gives an exact invariant:

   P_φ = m R v_φ + Q ψ.

3. **Magnetic moment.** μ = m v⊥² / 2B is an adiabatic invariant. It is conserved to O(ρ/L), so μ evaluated at the particle shows a small gyro-scale ripple.

P_φ is the key one. It ties radial excursions to parallel velocity: a radial step Δψ requires Δ(m R v_φ) = −Q Δψ.

## 3. Trapping condition

μ and E are conserved, so v∥² = v²(1 − μB/E). A particle at the outboard midplane (where B is smallest) reflects if v∥ reaches zero before the inboard midplane (where B is largest):

  trapped ⇔ p² < 1 − B_min/B_max.

With |B| ∝ 1/R on the surface, B_min/B_max = (1−ε)/(1+ε), so

  **p_crit² = 2ε / (1 + ε).**

This is exact for zero orbit width (ZOW). Full orbits differ because the particle does not stay on one surface. The difference is small when ρ_pol ≪ r and grows with orbit width.

## 4. Banana width

The banana crosses the outboard midplane twice per bounce, at r₁ (where v∥ = +v∥₀) and r₂ (where v∥ = −v∥₀′). P_φ is the same at both crossings. To leading order (same R and B at both, v_φ ≈ v∥):

  Q(ψ₁ − ψ₂) = −2 m R v∥₀  ⇒  Δr ≈ 2 m v∥₀ R / (Q dψ/dr) = 2 m v∥₀ / (Q B_pol) = **2 ρ_pol(v∥₀)**.

The **exact** prediction does not take R, B and |v∥| to be equal at the two crossings. It solves the following equation for the second crossing r₂:

  m R₂ v∥(r₂) b_φ(r₂) + Qψ(r₂) = P_φ,  with v∥(r₂)² = v² − 2μB(r₂)/m.

The leading-order formula assumes |v∥| is the same at both crossings. In fact the two legs sit at different R, so μB differs between them and v∥² changes by about v⊥²Δr/R (the mirror term). For deeply trapped particles v∥₀ is small, so this change can exceed v∥₀² itself. For deeply trapped 3.5 MeV alphas, where Δr/R is not small, 2ρ_pol should therefore underestimate the width substantially (to be quantified). The non-linearity of ψ(r) adds a smaller correction. The exact prediction includes both.

## 5. Bounce period

Along a field line dl = (rB/B_pol)dθ = q R₀ c dθ, which is constant in this model. The period is

  τ_b = 4 ∫₀^{θ_b} q R₀ c dθ / (v √(1 − λc/(1+ε cos θ))),  λ = μB₀/E.

This integral is the "exact ZOW quadrature" used in the comparisons.

The textbook result follows from three approximations: B ≈ B₀(1 − ε cos θ), c ≈ 1, and the substitution sin(θ/2) = κ sin u. These give

  τ_b = 8 q R₀ K(κ) / (v √(2λε)),  κ² = (1 − λ + λε)/(2λε).

Here K is the complete elliptic integral of the first kind.

To compare like with like, λ must be taken from the same approximate field. At the outboard launch point λ = (1 − p²)/(1 − ε), which gives κ² = p²(1−ε)/(2ε(1−p²)) = (p/p_c)²(1−p_c²)/(1−p²). With this mapping the textbook trapped–passing boundary sits at the exact p_c. Using λ from the exact field instead would shift the separatrix by O(ε²), and the logarithmic divergence of K near κ → 1 would blow that small shift up into a large, spurious error. The remaining, genuine error is an O(ε) prefactor error. It comes from B ≈ B₀(1 − ε cos θ), c ≈ 1 and dl = qR₀dθ, and is roughly uniform in pitch.

## 6. Prompt (first-orbit) alpha losses

A 3.5 MeV alpha in a 5.3 T field has ρ ≈ 5 cm, but ρ_pol ≈ 0.5 m at r = 1 m (q = 1.5). Its banana width is therefore a sizeable fraction of a = 2 m. Any particle whose orbit (from P_φ, μ, E conservation) reaches r = a is lost within one bounce (≈ 20–30 µs), before collisions act (alpha slowing-down time ~ 1 s).

Scaling: for a barely trapped particle, Δr ≈ 2ρ_pol·p_crit ≈ 2√(2ε)·m v/(Q B_pol) ≈ 2√(2ε)·(q R₀/r)·ρ. The width therefore scales as 1/B_pol ∝ 1/I_p, and the lost fraction falls steeply as the current rises. The scan varies q_a. For a circular cross-section the equivalent current is

  I_p = (1/μ₀)∮B_pol dl = 2π a² B₀ / (μ₀ q_a √(R₀² − a²)),  ⟨B_pol(a)⟩ = μ₀I_p/(2πa) = B₀ a / (q_a √(R₀² − a²)).

This follows from Ampère's law around r = a in this field. Here B_pol = B₀a/(q_aR) and dl = a dθ, so the integral of dθ/R gives 2π/√(R₀² − a²). The common cylindrical estimate, with R₀ in place of √(R₀² − a²), is low by √(1 − ε_a²): about 6 % for ITER and TFTR sizes.

Real ITER has elongation κ ≈ 1.7–1.85. At I_p = 15 MA its average edge poloidal field is μ₀I_p / (2πa√((1+κ²)/2)) ≈ 1.0 T. In this model that lies between q_a = 1.5 (⟨B_pol(a)⟩ = 1.20 T) and q_a = 2 (0.90 T).

The ITER comparison is therefore made through ⟨B_pol(a)⟩, but the mapping is crude. A circular plasma with q_a = 1.5–2 would be kink-unstable. The interior q profile and the field-line geometry differ from ITER's. The orbit width depends on the local poloidal field along the orbit, not only on its edge average. Treat the ITER-like numbers as uncertain by tens of per cent at least, and as illustrative rather than a prediction. Ripple, sawteeth, Alfvén-eigenmode and collisional transport are not modelled.

**Which particles are lost.** In this model the plasma current flows in −φ, because B_Z > 0 on the outboard side. Particles with v∥ > 0 therefore move counter to the current. For counter-current particles the term m R v_φ in P_φ has the sign that pushes the orbit to larger r. The loss region in (θ, p) space is consequently a narrow band of mostly counter-current, barely-passing and trapped pitches.

## 7. Guiding-centre model (independent cross-check)

The guiding-centre equations of motion (Littlejohn form, E = 0) are

  B* = B + (m v∥/Q) ∇×b,  B*∥ = b·B*
  dX/dt = [v∥ B* + (μ/Q) b × ∇|B|] / B*∥
  dv∥/dt = −(μ/m) B*·∇|B| / B*∥

These conserve E and the guiding-centre P_φ exactly in an axisymmetric field. The plan is to integrate them with RK4, evaluating ∇×b and ∇|B| by central differences. The guiding-centre model has no gyration. A particle therefore hits the wall when its guiding centre comes within about one gyroradius of it. A guiding-centre loss estimate will consequently be a bracket. The wall at r = a gives a lower bound. The wall at r = a − ρ_w gives an upper estimate, where ρ_w is the particle's gyroradius in the weakest field on the wall (outboard midplane), found from μ conservation.

## 8. TFTR benchmark

TFTR had a circular cross-section, the same geometry as this model. Darrow et al. (*Phys. Plasmas* 3, 1875 (1996)) state that its global first-orbit alpha losses ranged from about 3 % of the source at 2.7 MA to about 50 % at 0.6 MA. They cite Boivin, Zweben & White (*Nucl. Fusion* 33, 449 (1993)) for these values.

**These global fractions are model values.** The measurement was a lost-alpha detector 90° below the midplane, which sees local flux. It agreed with the first-orbit model within errors at all currents tried. A comparison with these values is therefore a comparison with an experimentally checked published model, not with a measured global loss. A direct comparison with the measurement would need the detector geometry. It would compare the pitch angle of alphas reaching the detector against I_p.

The current enters this model only through q_a, using the exact relation of section 6.

Darrow et al. name the q profile and the alpha source profile as the inputs that set first-orbit loss. Neither is known here for those shots. The planned model assumes q₀ = 1 with a quadratic profile and a source ∝ (1−(r/a)²)^k, with k to be scanned. B₀ = 5 T is also an assumption. The wall position relative to the last closed flux surface will be scanned too, so the outcome will be a band, not a fit.
