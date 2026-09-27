## Post-Doppler Adaptive Processing: Derivation

The goal of adaptive processing is to combine the outputs of $K$ receive subarrays so that a target at a known angle and Doppler is preserved, while clutter and noise arriving from other angles are suppressed as much as possible. We outline below how this combination is derived, starting from the raw per-subarray, per-pulse signal model, compressing to a single Doppler bin, and arriving at the constrained minimization that defines the adaptive weights.

### Signal model

Consider subarray $k$, pulse $m$ ($m\in\{0,\dots,M-1\}$), at a single range gate $\tau$. The received signal is a sum of contributions from $N$ clutter patches, one target, and additive noise:

$x_{k,m}(t) = \sum_{i=1}^{N} \sqrt{RCS_i}\cdot AF(\theta_i-\theta_{tx})\cdot s(t-\tau)\cdot e^{j\phi_k(\theta_i-\theta_{rx})}\, e^{j2\pi f_{d,i}\cdot m\cdot T}$

${}+ \sqrt{RCS_t}\cdot AF(\theta_t-\theta_{tx})\cdot s(t-\tau)\cdot e^{j\phi_k(\theta_t-\theta_{rx})}\, e^{j2\pi f_{d,t}\cdot m\cdot T} + n_{k,m}(t)$

Each clutter patch $i$ and the target contribute a transmit pattern factor $AF(\theta_i-\theta_{tx})$, the compressed waveform $s(t-\tau)$, a subarray-dependent receive phase $e^{j\phi_k(\theta_i-\theta_{rx})}$, and a pulse-to-pulse Doppler phase $e^{j2\pi f_{d}\cdot m \cdot T}$. All clutter patches and the target are assumed to lie at the same range $\tau$; $n_{k,m}(t)$ is additive receiver noise, uncorrelated across $k$ and $m$.

### Doppler compression to a single bin

To limit processing to a Doppler bin $f_D = \dfrac{k_d}{MT}$, $k_d\in\{0,\dots,M-1\}$, the $M$ pulses are coherently combined:
