# Switches & Sliders

> Component reference for Google Pixel & Material 3 Expressive.

Switches and sliders give users tactile control over binary states and numerical ranges.

---

## 1. Material 3 Expressive Switch

The M3 switch is larger and more expressive than legacy Android toggles:

```
Unselected State:             Selected (Active) State:
┌─────────────────────┐       ┌─────────────────────┐
│  ○                  │  ──▶  │                 (✓) │
└─────────────────────┘       └─────────────────────┘
Track: surfaceContainerHighest  Track: primary
Thumb: outline (16dp)         Thumb: onPrimary (24dp) with checkmark
```

### Dimensions & Tokens
- **Track:** $52\,\text{dp}$ width $\times$ $32\,\text{dp}$ height, full pill shape (`corner-full`).
  - Active Track: `primary`
  - Inactive Track: `surfaceContainerHighest` with $2\,\text{dp}$ `outline` border.
- **Thumb:**
  - Active Thumb: $24 \times 24\,\text{dp}$, colored in `onPrimary`.
  - Inactive Thumb: $16 \times 16\,\text{dp}$, colored in `outline`.
  - Pressed Thumb: Dynamically expands to $28 \times 28\,\text{dp}$ with fluid spring physics.
- **Icon Morphing:** An active switch can embed a crisp checkmark icon inside the thumb ($16 \times 16\,\text{dp}$, `onPrimaryContainer` or `primary`).

---

## 2. Sliders (Continuous & Discrete)

### M3 Expressive Track Slider
- **Thick Track:** Features a prominent rounded pill track ($16\,\text{dp}$ height) rather than a thin wire line.
- **Handle:** A floating vertical pill handle ($4\,\text{dp}$ width $\times$ $44\,\text{dp}$ height) that scrubs along the track with tactile resistance.
- **Value Indicator:** A floating speech-bubble balloon appears above the thumb during dragging, displaying the exact value.
- **Discrete Ticks:** When configured with discrete step values, small contrasting dots appear along the track, accompanied by micro-haptic ticks as the user drags past each stop.

---

## 3. Audit Checklist

- [ ] Does the switch track measure $52 \times 32\,\text{dp}$?
- [ ] Does the thumb animate between states using spring curves rather than sudden jumps?
- [ ] Are sliders paired with clear numeric labels or value balloons for accessibility?
- [ ] Does scrubbing trigger subtle tactile ticks?
