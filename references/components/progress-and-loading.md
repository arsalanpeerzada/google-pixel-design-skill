# Progress Indicators & Loading States

> Component reference for Google Pixel & Material 3 Expressive.

Loading feedback reassures users that the system is processing work and maintains visual engagement during asynchronous operations.

---

## 1. Linear & Circular Progress Indicators

- **Track & Indicator:**
  - Active Indicator: `primary`
  - Inactive Track: `surfaceContainerHighest`
- **Track Thickness:** $4\,\text{dp}$ standard thickness with rounded caps on both leading and trailing ends.
- **Determinate vs. Indeterminate:**
  - Use **Determinate** (with percentage readout) when the operation's duration or payload size is known (e.g. file upload, download).
  - Use **Indeterminate** (cyclic animation) when timing is unknown (e.g. fetching network response).

---

## 2. Material 3 Expressive Shape-Morphing Loaders

In Android 15–17 and M3 Expressive, indeterminate loading transcends the standard spinning circle:
- **Geometric Shape Morphs:** A central indicator morphs smoothly across 4 geometric states:
  $$\text{Circle} \longrightarrow \text{Squircle} \longrightarrow \text{4-Leaf Clover} \longrightarrow \text{Pill}$$
  driven by organic spring velocity.
- **Squash-and-Stretch:** Pulsing loading dots squash along the direction of travel, creating a lively cartoon-physics bounce.

---

## 3. Skeleton Loading vs. Spinners

- **Initial Screen Load:** Use **Skeleton Placeholders** matching the layout of cards and text lines (colored in `surfaceContainerLow` with subtle shimmer) rather than an isolated center spinner. Skeletons reduce perceived latency.
- **Micro-Tasks:** Inline circular spinners ($24 \times 24\,\text{dp}$) embedded inside buttons during form submission.

---

## 4. Audit Checklist

- [ ] Does progress feedback appear within $300\,\text{ms}$ of user action?
- [ ] Are indicator ends rounded (`StrokeCap.Round`) rather than flat/square?
- [ ] Do skeleton loaders accurately reflect the dimensions of upcoming content?
