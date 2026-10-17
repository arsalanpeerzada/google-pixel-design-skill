# Bottom Sheets: Standard & Modal Guidelines

> Component reference for Google Pixel & Material 3 Expressive.

Bottom sheets slide up from the bottom of the screen, anchoring supplementary tasks, menus, or checkout flows within natural thumb reach.

---

## 1. Sheet Types

1. **Modal Bottom Sheet:**
   - Displayed over a darkened scrim (`scrim` color role, $32\%$ opacity).
   - Interrupts primary workflow to complete a focused sub-task (e.g. sharing, selecting payment, filtering).
   - Dismissible via tap outside, swipe down, or system back gesture.
2. **Standard Bottom Sheet:**
   - Sits co-present with primary content with no scrim (e.g. Google Maps audio player or directions card).
   - Allows concurrent interaction with background map/content while remaining accessible.

---

## 2. Anatomy & Dimensions

- **Top Corner Radius:** **$28\,\text{dp}$** (`corner-extra-large`) on top-left and top-right corners; bottom corners are flat ($0\,\text{dp}$).
- **Drag Handle:** Centered at the top: **$32\,\text{dp}$ width $\times$ $4\,\text{dp}$ height**, pill-shaped, colored in `onSurfaceVariant` with $40\%$ opacity.
- **Surface Fill:** `surfaceContainerLow` or `surfaceContainer` to achieve clean contrast against the underlying content.
- **Edge-to-Edge:** Bottom padding must explicitly accommodate window navigation bar insets (`WindowInsets.navigationBars`).

---

## 3. Gestures & Physics

- **Swipe-to-Dismiss:** Tracks finger velocity dynamically. Swiping down with downward velocity dismisses the sheet with natural spring momentum.
- **Predictive Back:** Under Android 14–17, initiating a back swipe while a sheet is open shrinks the sheet with a spring preview before finalizing dismissal.

---

## 4. Audit Checklist

- [ ] Does the sheet feature the standard $32 \times 4\,\text{dp}$ rounded drag handle?
- [ ] Are top corners rounded to $28\,\text{dp}$?
- [ ] Does the sheet consume bottom system insets to prevent buttons from colliding with the Android gesture bar?
- [ ] Is internal content scrollable if text scaling pushes elements beyond screen height?
