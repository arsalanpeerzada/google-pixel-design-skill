# Haptics & Feedback Guidelines

> Foundation reference for Google Pixel & Material 3 Expressive.

Google Pixel devices are renowned for their class-leading linear resonant actuator (haptic motor). In Pixel UI, haptics are treated as a **first-class sensory dimension**, not an afterthought.

---

## 1. Pixel Haptic Taxonomy

| Haptic Pattern | Tactile Feel | Trigger / UI Interaction | Compose / Android API |
| --- | --- | --- | --- |
| **Click** | Crisp, sharp, instantaneous pulse | Toggling a Switch, pressing a key, radio selection | `HapticFeedbackConstants.CLOCK_TICK` or `CONFIRM` |
| **Tick** | Delicate, micro-pulse | Scrubbing a slider, spinning a time picker dial | `HapticFeedbackConstants.SEGMENT_TICK` |
| **Bump** | Firm, double-pulse impulse | Hitting scroll boundary, swipe limit, error shake | `HapticFeedbackConstants.REJECT` |
| **Heavy Click** | Substantial, deep impulse | Long-press on an app icon, entering drag-and-drop mode | `HapticFeedbackConstants.LONG_PRESS` |
| **Gesture Feedback** | Progressive spring-like resistance | Reaching the trigger threshold of Predictive Back | `HapticFeedbackConstants.GESTURE_THRESHOLD_ACTIVATE` |

---

## 2. Audio & Visual Synergy

Haptics must never act in isolation. They form a cohesive feedback loop:
1. **Switch Toggle:** Visual morph of thumb into checkmark + crisp haptic Click + soft audible acoustic "click".
2. **Slider Scrubbing:** Visual numeric balloon indicator + micro-ticks at step intervals.
3. **Destructive Action:** Red tonal ripple + double-pulse Bump + alert warning tone.

---

## 3. Best Practices & Restraint

- **Never Overwhelm:** Haptic feedback must be intentional. Never vibrate for every trivial layout scroll or continuous text typing unless explicitly requested by the user.
- **System Setting Compliance:** Respect user preferences in `Settings > Sound & vibration > Vibration & haptics`. If disabled by the user, suppress programmatic haptic triggers.
