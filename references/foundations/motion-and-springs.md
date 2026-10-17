# Motion, Spring Physics & Predictive Back

> Foundation reference for Google Pixel & Material 3 Expressive.

Motion in Google Pixel software is grounded in **real-world physical intuition**. Rather than static duration-based curves, M3 Expressive employs **spring-based physics** that react dynamically to velocity, touch pressure, and momentum.

---

## 1. Physics-Based Springs

Spring animations discard rigid milliseconds in favor of two physical parameters:
- **Damping Ratio ($\zeta$):** Controls how bouncy the motion is:
  - `HighBouncy` ($\zeta = 0.5$): Playful feedback, celebration micro-interactions.
  - `MediumBouncy` ($\zeta = 0.75$): Standard button presses, card expands.
  - `NoBouncy` ($\zeta = 1.0$): Critically damped; clean, non-oscillating navigation transitions.
- **Stiffness ($k$):** Controls how quickly the spring snaps into place:
  - `StiffnessHigh` ($k \approx 10,000$): Micro-toggles, icon state switches.
  - `StiffnessMedium` ($k \approx 1,500$): Bottom sheets, dialog reveals.
  - `StiffnessLow` ($k \approx 500$): Screen transitions, multi-item staggered lists.

---

## 2. Predictive Back Gesture (Android 14–17)

Pixel devices emphasize the **Predictive Back** gesture: as the user swipes inwards from the left or right edge, the current screen or sheet actively tracks the finger:
1. **In-Progress Swiping:** The active screen scales down slightly ($90\%$), corners round into a floating card, and the destination beneath peeks through.
2. **Commit vs. Cancel:**
   - If the user completes the swipe, the front card smoothly scales out with spring physics, landing directly on the parent destination.
   - If the user cancels the swipe by sliding back to the edge, the card snaps back into full-screen with zero lag.
3. **In-App Transitions:** Bottom sheets track vertical swipe down, morphing smoothly into dismiss without jarring jumps.

---

## 3. Container Transform & Spatial Continuity

When an item opens into a detail view:
- **Never cut or instant-fade:** The card's bounding box smoothly expands into the target page boundaries while the content inside cross-fades seamlessly.
- **Persistent Shared Elements:** Hero images or titles maintain spatial anchor points throughout the transition.

---

## 4. Squash-and-Stretch & Ripple Effects

- **Ink Ripples:** Tap feedback radiates outward from the exact contact point, fading into `onSurface` or `onPrimary` tint at $10\%$ opacity.
- **Pull-to-Refresh & Overscroll:** When content reaches the scroll boundary, it stretches organically like rubber, snapping back into resting position upon release.

---

## 5. Audit Checklist

- [ ] Are animations configured with spring curves rather than linear/ease-in timings?
- [ ] Does navigation handle predictive back gestures gracefully without layout flashing?
- [ ] Are ripples properly clipped within component shapes (e.g., inside pill bounds)?
- [ ] Is reduced-motion respected for users with vestibular sensitivities?
