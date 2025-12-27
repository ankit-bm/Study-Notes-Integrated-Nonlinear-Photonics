# Four-Wave Mixing Bragg Scattering (FWM-BS): Study Notes

---

## Q1: Is FWM-BS a special case of FWM? What does "parametric" mean?

**A:** Yes, FWM-BS is a specific type of FWM. All FWM processes are parametric.

### What "parametric" means:

**Dictionary origin:** From Greek *parametros*, meaning "measuring alongside." A process where you vary a system's *parameters* to drive an outcome, rather than directly forcing it.

**In optics:** The pumps modulate the refractive index $n(I)$. This varying parameter mediates energy transfer between waves. The medium facilitates but doesn't participate [1].

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

### Mental model (phantom grating):

Two pumps ($P_1$, $P_2$) interfere to create intensity grating, which creates refractive index grating (via $\chi^{(3)}$). A signal wave scatters off this "moving mirror," frequency-shifting to become the idler.

---

## Q2: What are the different variants of FWM? How do they differ?

**A:** All FWM arises from $\chi^{(3)}$ nonlinearity. The variants differ in **which photons are destroyed vs. created**.

### The three main flavors:

| Variant | Physical action | Energy relation |
|---------|-----------------|-----------------|
| **Parametric Amplification (PA)** | Gain + pair creation | $2\omega_p = \omega_s + \omega_i$ |
| **Bragg Scattering (BS)** | Frequency translation | $\omega_{p1} + \omega_s = \omega_{p2} + \omega_i$ |
| **Phase Conjugation (PC)** | Wavefront reversal | $\omega_{p1} + \omega_{p2} = \omega_s + \omega_i^*$ |

### Theoretical difference (the Hamiltonian):

**PA:** $\hat{H} \propto \hat{a}_s^\dagger \hat{a}_i^\dagger + \text{h.c.}$  
Creates photon pairs from vacuum. **Adds vacuum noise** [2].

**BS:** $\hat{H} \propto \hat{a}_s^\dagger \hat{a}_i + \text{h.c.}$  
Swaps photons between modes (beam-splitter-like). **Noiseless in principle** [2].

### Physical picture (grating model):

- **BS:** Two pumps ($P_1$, $P_2$) interfere to create a moving refractive index grating. Signal scatters off this moving grating and is Doppler-shifted to idler frequency. Grating velocity set by $(\omega_{p1} - \omega_{p2})$.

- **PA:** Pump + signal interfere to create a grating that scatters more pump into signal. This creates feedback and exponential gain.

### Experimental signatures:

| Aspect | Parametric Amp | Bragg Scattering |
|--------|----------------|------------------|
| Pumps | One (degenerate) or two close | Two well-separated |
| Output | Amplification + new frequency | Frequency shift only |
| Gain scaling | Exponential with power | Oscillatory (Rabi-like) |
| Noise | Vacuum fluctuations amplified | Noiseless (ideal) |

### Phase matching:

**PA:** $2k_p = k_s + k_i$ or $k_{p1} + k_{p2} = k_s + k_i$

**BS:** $k_{p1} - k_{p2} = k_i - k_s$

### Important caveats:

1. **"Noiseless" is idealized.** Real systems have Raman, Brillouin, pump RIN, and loss.
2. **BS phase matching "easier when pumps far apart"** is dispersion-dependent, not universal.
3. **Boundary between non-degenerate FWM and BS blurs** at strong-pump/weak-signal regimes. Noise property is the true differentiator.

### Why BS matters for quantum:

FWM-BS can frequency-shift single photons without adding vacuum noise. Critical for quantum frequency conversion [2].

---

## Q3: Why nanophotonics for FWM-BS?

**A:** Nanophotonic microresonators concentrate light in small volumes with long photon lifetimes, enabling efficient frequency conversion with mW-level power instead of Watts.

### The key parameters:

| Parameter | Definition | Why it matters |
|-----------|------------|----------------|
| Quality factor $Q$ | $Q = \omega \tau_{photon}$ | Higher Q = longer circulation = more interaction time |
| Mode volume $V_{eff}$ | Spatial extent of confined light | Smaller $V_{eff}$ = higher intensity for same power |
| Field enhancement $FE$ | Intracavity field / input field | $FE \propto \sqrt{Q_L}$ for resonant coupling |
| Nonlinear coefficient $\gamma$ | $\gamma = \frac{n_2 \omega}{c A_{eff}}$ | Larger when mode is tighter |

### Power scaling:

For FWM-BS at low conversion efficiency [3]:

$$\eta^{BS} \propto (\gamma P_p L_{eff})^2 \cdot FE_p^4 \cdot FE_s^2 \cdot FE_i^2$$

The $FE^4$ boost from pump fields is why cavities need mW instead of W.

### Experimental comparison [3]:

| Platform | Pump power | Efficiency |
|----------|------------|------------|
| 12 mm Si₃N₄ waveguide | 14 W pulsed | −13 dB |
| 80 μm Si₃N₄ ring | 32 mW CW | −6 dB |

~500× less power, better efficiency.

### Physical picture:

Photon recycling. In a waveguide, photons pass through once. In a resonator with $Q = 10^5$, photons make ~$10^5$ round trips. Each pass is another chance for FWM interaction.

### Key tradeoff:

Higher Q means narrower linewidth. This makes it harder to:
1. Match signal bandwidth (e.g., quantum dot emission ~GHz)
2. Tune resonance to target wavelength (fabrication tolerance ~5 nm)

### Design insight:

Changing waveguide width by just 10 nm can tune phase-matching. Nanophotonics substitutes "raw power" with "tight confinement."

---

## Q4: Why does PA amplify vacuum fluctuations but BS doesn't?

**A:** The difference is photon accounting: PA creates photons from pump energy, BS only moves existing photons.

### The Hamiltonian difference:

**PA:** $\hat{H} \propto \hat{a}_s^\dagger \hat{a}_i^\dagger + \text{h.c.}$

- Operator $\hat{a}_s^\dagger \hat{a}_i^\dagger$ creates a photon pair (one signal, one idler) simultaneously
- Acting on vacuum: $\hat{a}_s^\dagger \hat{a}_i^\dagger |0,0\rangle = |1,1\rangle$
- Even with no input signal, photon pairs are created from vacuum
- This is spontaneous four-wave mixing (SFWM)
- Vacuum fluctuations get amplified into real photons

**BS:** $\hat{H} \propto \hat{a}_s^\dagger \hat{a}_i + \text{h.c.}$

- Operator $\hat{a}_s^\dagger \hat{a}_i$ destroys an idler photon and creates a signal photon
- Acting on vacuum: $\hat{a}_s^\dagger \hat{a}_i |0,0\rangle = 0$
- No input photon = no output photon
- Photon number is conserved, just frequency-shifted

### Mental model (Factory vs Prism):

**PA is a Factory:** Takes power from pumps and manufactures new photons. Because it can build light from "nothing" (pump energy), it treats the tiny "hum" of the vacuum as a starting signal and amplifies it into noise.

**BS is a Prism:** Doesn't create new photons. Just takes a photon that is already there and changes its color. If there is no signal photon to begin with (vacuum), the process has nothing to "change," so it remains silent.

### Summary table:

| Feature | Parametric Amplification (PA) | Bragg Scattering (BS) |
|---------|-------------------------------|----------------------|
| Photon action | Creates new pair | Swaps existing photon |
| Vacuum input | Produces noise (SFWM) | Produces nothing |
| Noise source | Spontaneous pair generation | Technical only (Raman, loss, pump RIN) |

### Important nuance:

BS is "noiseless" regarding vacuum fluctuation amplification. It still has:
- Shot noise floor from vacuum port
- Classical noise sources (Raman, loss)

But it will never spontaneously create light where none existed.

### Why this matters experimentally:

- PA: SNR has fundamental quantum limit even with perfect device
- BS: SNR limited by technical imperfections, not fundamental physics [2]

---

## Q5: Why anomalous dispersion for PA, normal for BS?

**A:** PA needs anomalous dispersion to achieve phase matching. BS prefers normal dispersion to suppress noise, but can work in either regime.

### Dispersion basics:

**Definitions:**

- $\beta_2 = \frac{d^2 \beta}{d\omega^2}$ : How group velocity changes with frequency (GVD parameter)
- $D = -\frac{2\pi c}{\lambda^2} \beta_2$ : How pulse spreads per nm of bandwidth per km (ps/nm/km)
- Physical meaning: $\frac{dn}{d\lambda} < 0$ (n decreases with λ) → Normal

**Intuition:** In most glasses, blue light "feels" more electrons (higher n, slower). This is normal. Anomalous is the exception where red is slower.

| Regime | $\beta_2$ | $D$ | $\frac{dn}{d\lambda}$ | Behavior |
|--------|-----------|-----|----------------------|----------|
| Normal | $> 0$ | $< 0$ | $< 0$ | Blue slower than red |
| Anomalous | $< 0$ | $> 0$ | $> 0$ | Blue faster than red |

### Why PA needs anomalous:

Phase matching condition for degenerate PA:

$$\Delta k = \beta_2 \Omega^2 + 2\gamma P = 0$$

- $2\gamma P > 0$ always (Kerr nonlinearity is positive)
- To balance, need $\beta_2 < 0$ (anomalous)
- This is the same physics that enables soliton formation

### Why BS prefers normal:

BS phase matching is difference-based:

$$\Delta k = (k_{p1} - k_{p2}) - (k_i - k_s) = 0$$

1. This condition can be satisfied in either dispersion regime
2. But normal dispersion suppresses modulation instability (MI)
3. MI would create spontaneous photon pairs (noise), defeating BS's quantum advantage
4. Normal dispersion keeps BS "quiet"

**Normal is preferred for noise suppression, not required by physics.**

### Summary:

| Process | Preferred regime | Reason |
|---------|------------------|--------|
| PA | Anomalous ($\beta_2 < 0$) | Required for phase matching (Kerr compensation) |
| BS | Normal ($\beta_2 > 0$) | Suppresses MI noise; phase matching works in either |

### Platform note:

These guidelines apply to χ(3) platforms (fiber, Si₃N₄) [2]. Bulk crystal systems (PPKTP, BBO) use different phase matching strategies (birefringent, quasi-phase matching).

---

## Q6: Why was waveguide efficiency ≤5% and how do microresonators fix this?

**A:** Waveguides have single-pass interaction. Resonators recycle photons thousands of times.

| Aspect | Waveguide | Microresonator |
|--------|-----------|----------------|
| Interaction | Single pass | ~$Q/(2\pi)$ round trips (~16,000 for $Q=10^5$) |
| Power needed | 14 W pulsed | 32 mW CW |
| Efficiency | ≤5% [3] | 60% [2] |
| Limitation | Loss accumulates, phase drifts | Requires resonance matching |

**Intuition:** Waveguide = shouting once across a stadium. Resonator = whispering in a mirrored room where the message echoes until heard.

---

## Q7: Why can BS choose arbitrary target wavelength but PA cannot?

**A:** PA idler is locked by symmetry around one pump. BS idler is set by tunable spacing between two pumps.

| Process | Frequency relation | Control | Flexibility |
|---------|-------------------|---------|-------------|
| PA | $\omega_i = 2\omega_p - \omega_s$ | Pump center | Rigid (idler "reflects" around pump) |
| BS | $\omega_i = \omega_s + (\omega_{p1} - \omega_{p2})$ | Pump spacing | High (idler "translates" by pump gap) |

**Mental model:**
- **PA is a see-saw:** Pump is the pivot. Move signal down, idler moves up by same amount.
- **BS is a conveyor belt:** Pump spacing sets belt speed. Signal rides to any destination.

**Caveat:** "Arbitrary" means widely tunable within phase-matching and resonator constraints.

---

## Q8: What is field enhancement (FE) and why does it matter?

**A:** FE is the ratio of intracavity field to input field. It determines how much the cavity "amplifies" trapped light.

$$FE = \frac{E_{cavity}}{E_{input}} \propto \sqrt{Q_L}$$

**Why it matters:**

Conversion efficiency scales as product of field enhancements [3]:

$$\eta^{BS} \propto FE_{p1}^2 \cdot FE_{p2}^2 \cdot FE_s^2 \cdot FE_i^2$$

| Factor | Exponent | Why |
|--------|----------|-----|
| Each pump | 2 | One photon participates per pump |
| Signal | 2 | Input field |
| Idler | 2 | Output field |

**Practical impact:**
- 10× higher FE → 100–10,000× efficiency gain
- This is why mW pumps in resonators beat W pumps in waveguides

**Key insight:** FE depends on both Q and coupling. High $Q_i$ alone isn't enough; need proper $Q_c$ matching (see Q9).

---

## Q9: Why must the resonator be overcoupled for high efficiency?

**A:** Overcoupling ensures converted photons escape to waveguide faster than they're lost internally.

### Coupling regimes:

| Regime | Condition | Photon fate | Extraction efficiency |
|--------|-----------|-------------|----------------------|
| Undercoupled | $Q_c > Q_i$ | Lost to absorption | $\to 0$ |
| Critically coupled | $Q_c = Q_i$ | Balanced loss/exit | ~50% |
| Overcoupled | $Q_c < Q_i$ | Escapes to output | $\to 100\%$ |

### Maximum BS efficiency [3]:

$$\eta_{max}^{BS} = \frac{1}{1 + Q_c/Q_i}$$

### Mental model (leaky bucket):

Bucket (resonator) has two holes:
- Hole A (internal loss): fixed size
- Hole B (coupling to waveguide): your drain

To collect water (photons), make drain >> leak. That's overcoupling.

### Important trade-off:

Overcoupling reduces loaded Q, which reduces field enhancement. Sweet spot is slightly overcoupled ($Q_c \approx 0.5$–$0.8 \times Q_i$), not extreme overcoupling.

**One-liner:** Big exit door helps extraction, but too big means light doesn't stay long enough to convert.

---

## Q10: Why does PA have a threshold but BS doesn't?

**A:** PA has gain that can self-oscillate. BS is a swap with no gain mechanism.

### Comparison:

| Feature | PA | BS |
|---------|----|----|
| Energy action | Pump → Signal + Idler (net flow) | $P_1 + S \leftrightarrow P_2 + I$ (swap) |
| Gain type | Exponential ($e^{gL}$) | Sinusoidal ($\sin^2$) |
| Instability | Threshold (OPO above it) | Stable (saturates at 100%) |

### Mental model:

**PA is an avalanche:** Once pump overcomes loss, single photon triggers runaway pair creation. Threshold event.

**BS is a pendulum:** Energy swings between signal and idler frequencies. More pump = faster swing, but never explodes. Hits 100%, then swings back.

### Key distinction:

- **PA:** Total signal+idler photons *increase* (quantum gain)
- **BS:** Total signal+idler photons *conserved* (frequency swap)

### The over-rotation effect:

In BS, pump power beyond 100% conversion causes efficiency to *decrease*. Light converts back to original frequency. No runaway.

**One-liner:** Threshold exists when gain can overcome loss and self-sustain. BS has no gain, so no threshold.

---

## Q11: What is frequency matching and why is it harder than phase matching?

**A:** Phase matching ensures waves stay in sync ($\Delta k = 0$). Frequency matching requires all 4 waves to land on cavity resonances simultaneously.

| Constraint | Phase matching | Frequency matching |
|------------|----------------|-------------------|
| Requirement | Momentum conservation | Resonance with cavity modes |
| System | Waveguides/fibers | Resonators |
| Failure mode | Low efficiency | Zero signal buildup |

**The problem:** FSR changes with wavelength due to dispersion. If 1550 nm FSR ≠ 980 nm FSR, the "teeth" of the two frequency combs drift apart over multiple modes.

**Design rule:** Keep accumulated mismatch $N \cdot \Delta FSR < \kappa/2$ (linewidth) [3].

**Mental model (two pianos):** One piano has keys spaced slightly wider. Playing a chord across both pianos drifts out of tune.

---

## Q12: What causes mode splitting in FWM-BS transmission?

**A:** Strong pump hybridizes signal and idler into supermodes (avoided crossing).

| Pump power | What you see |
|------------|--------------|
| Weak | Single transmission dip |
| Strong | Dip splits into 2-3 dips |

**Physical meaning:** Modes are no longer independent "signal" and "idler." They become superpositions that repel in frequency space.

**Practical insight:** Splitting distance $2\Omega_0 \propto \gamma P_{pump}$ is a direct measure of nonlinear coupling strength [3].

---

## Q13: How does pump power affect conversion efficiency?

**A:** Efficiency rises, peaks, then falls with increasing pump power.

| Regime | Effect |
|--------|--------|
| Low power | Weak conversion |
| Optimal | Maximum η |
| High power | Kerr shift moves resonance away from signal |

**Why it falls:** Kerr effect shifts cavity resonance. Fixed signal wavelength no longer sits on the (now shifted) eigenmode.

**Solution:** Track signal detuning with pump power to stay on eigenmode.

---

## Q14: Why is intraband (~25%) less efficient than wideband (~60%)?

**A:** Intraband creates two idlers. Wideband suppresses one.

| Type | Idlers | Max efficiency | Achieved |
|------|--------|----------------|----------|
| Intraband | 2 (blue + red) | 50% each (lossless) | ~25% |
| Wideband | 1 (other suppressed) | 100% (lossless) | ~60% |

**Why intraband splits:** Small pump separation allows signal to scatter both up and down in frequency. Energy divides.

**Why wideband is cleaner:** Large pump separation + dispersion means "wrong" idler doesn't fit any cavity mode. All energy funnels to one output.

**To improve intraband:** Engineer dispersion so only one idler is frequency-matched.

---

## References

[1] G. P. Agrawal, *Nonlinear Fiber Optics*, 4th ed., Academic Press (2007). Chapter 10: Four-Wave Mixing.

[2] Q. Li, M. Davanço, and K. Srinivasan, "Efficient and low-noise single-photon-level frequency conversion interfaces using silicon nanophotonics," *Nature Photonics* **10**, 406–414 (2016). https://doi.org/10.1038/nphoton.2016.64

[3] Q. Li, M. Davanço, and K. Srinivasan, "Efficient and low-noise single-photon-level frequency conversion interfaces using silicon nanophotonics: Supplementary Information," *Nature Photonics* (2016). https://doi.org/10.1038/nphoton.2016.64

---