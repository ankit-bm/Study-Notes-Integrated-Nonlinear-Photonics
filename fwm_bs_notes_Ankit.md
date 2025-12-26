# Four-Wave Mixing Bragg Scattering (FWM-BS) — Study Notes

---

## Q1: Is FWM-BS a special case of FWM? What does "parametric" mean?

**A:** Yes, FWM-BS is a specific type of FWM. All FWM processes are parametric.

### What "parametric" means:

**Dictionary origin:** From Greek *parametros* — "measuring alongside." A process where you vary a system's *parameters* to drive an outcome, rather than directly forcing it.

**In optics:** The pumps modulate the refractive index $n(I)$ — this varying parameter mediates energy transfer between waves. The medium facilitates but doesn't participate.

### The parametric checklist:

| Property | Parametric (FWM) | Non-parametric (Raman) |
|----------|------------------|------------------------|
| Material final state | Unchanged | Changed (phonons created) |
| Energy accounting | Photons only | Photons + material |
| Noise floor | Low | Higher (thermal phonons) |

### Conservation laws:

$$\hbar\omega_1 + \hbar\omega_2 = \hbar\omega_3 + \hbar\omega_4 \quad \text{(energy)}$$

$$\vec{k}_1 + \vec{k}_2 = \vec{k}_3 + \vec{k}_4 \quad \text{(momentum/phase matching)}$$

### Key nuance:

"No energy deposited" is the *ideal* parametric picture. Real devices still have:
- Linear absorption
- Two-photon absorption  
- Free-carrier absorption

These are *loss mechanisms*, not the parametric interaction itself. The FWM process is still parametric even if your device has losses.

### Mental model — The phantom grating:

Two pumps ($P_1$, $P_2$) interfere → intensity grating → refractive index grating (via $\chi^{(3)}$). A signal wave scatters off this "moving mirror," frequency-shifting to become the idler.

---

## Q2: What are the different variants of FWM? How do they differ?

**A:** All FWM arises from $\chi^{(3)}$ nonlinearity. The variants differ in **which photons are destroyed vs. created**.

### The three main flavors:

| Variant | Physical action | Energy relation |
|---------|-----------------|-----------------|
| **Parametric Amplification (PA)** | Gain + pair creation | $2\omega_p = \omega_s + \omega_i$ |
| **Bragg Scattering (BS)** | Frequency translation | $\omega_{p1} + \omega_s = \omega_{p2} + \omega_i$ |
| **Phase Conjugation (PC)** | Wavefront reversal | $\omega_{p1} + \omega_{p2} = \omega_s + \omega_i^*$ |

### Theoretical difference — the Hamiltonian:

**PA:** $\hat{H} \propto \hat{a}_s^\dagger \hat{a}_i^\dagger + \text{h.c.}$  
→ Creates photon pairs from vacuum → **adds ≥3 dB noise**

**BS:** $\hat{H} \propto \hat{a}_s^\dagger \hat{a}_i + \text{h.c.}$  
→ Swaps photons between modes (beam-splitter-like) → **noiseless in principle**

### Physical picture — the grating model:

- **BS:** Two pumps ($P_1$, $P_2$) interfere → moving refractive index grating. Signal scatters off this moving grating → Doppler-shifted to idler frequency. Grating velocity set by $(\omega_{p1} - \omega_{p2})$.

- **PA:** Pump + signal interfere → grating scatters more pump into signal → feedback → exponential gain.

### Experimental signatures:

| Aspect | Parametric Amp | Bragg Scattering |
|--------|----------------|------------------|
| Pumps | One (degenerate) or two close | Two well-separated |
| Output | Amplification + new frequency | Frequency shift only |
| Gain scaling | Exponential with power | Oscillatory (Rabi-like) |
| Noise | ≥3 dB (vacuum fluctuations) | Noiseless (ideal) |

### Phase matching:

**PA:** $2k_p = k_s + k_i$ or $k_{p1} + k_{p2} = k_s + k_i$

**BS:** $k_{p1} - k_{p2} = k_i - k_s$

### Important caveats:

1. **"Noiseless" is idealized** — real systems have Raman, Brillouin, pump RIN, and loss
2. **BS phase matching "easier when pumps far apart"** is dispersion-dependent, not universal
3. **Boundary between non-degenerate FWM and BS blurs** at strong-pump/weak-signal regimes; noise property is the true differentiator

### Why BS matters for quantum:

FWM-BS can frequency-shift single photons without adding vacuum noise — critical for quantum frequency conversion.

---

