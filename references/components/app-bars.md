# App Bars: Top & Bottom App Bar Guidelines

> Component reference for Google Pixel & Material 3 Expressive.

App bars anchor the viewport, offering navigation context, title hierarchy, and contextual actions.

---

## 1. Top App Bar Variants

Material 3 defines four distinct top app bar styles:

| Variant | Resting Height | Title Size | Intended Usage |
| --- | --- | --- | --- |
| **Center-Aligned** | $64\,\text{dp}$ | `Title Large` ($22\,\text{sp}$) | Top-level roots with 1–2 actions (e.g. Settings root, Profile) |
| **Small** | $64\,\text{dp}$ | `Title Large` ($22\,\text{sp}$) | Secondary/sub-pages with left-aligned title & back button |
| **Medium** | $112\,\text{dp}$ | `Headline Small` ($24\,\text{sp}$) | Section hubs requiring moderate visual hierarchy |
| **Large** | $152\,\text{dp}$ | `Headline Medium` ($28\,\text{sp}$) | Flagship landing screens, allowing one-handed thumb reach |

### The Collapsing Title Pattern (Pixel Signature)
On `LargeTopAppBar` and `MediumTopAppBar`:
- **Resting:** The title is large and positioned low in the bar, placing content lower on the display so the thumb can reach it comfortably.
- **On Scroll:** As the user scrolls down, the large title smoothly shrinks and translates upwards into the top bar, transitioning to `Title Large` while the bar's container background tints to `surfaceContainer`.

---

## 2. Bottom App Bar

The `BottomAppBar` provides high-reachability actions at the base of the screen:
- **Height:** $80\,\text{dp}$ with edge-to-edge system navigation inset padding.
- **Docked Actions:** Houses up to 4 navigation or contextual icon actions on the left, and an optional docked `FloatingActionButton` on the right.
- **Color:** Uses `surfaceContainer` to distinguish from scrolling content.

---

## 3. Audit Checklist

- [ ] Does the `LargeTopAppBar` collapse cleanly into a small bar on scroll?
- [ ] Are action icons limited to at most 3 in the top app bar (overflowing into a dropdown menu for additional actions)?
- [ ] Is there edge-to-edge padding ensuring the top bar accounts for camera cutouts and status bar insets?
