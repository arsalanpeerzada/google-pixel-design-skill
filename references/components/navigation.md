# Navigation: Bars, Rails & Drawers

> Component reference for Google Pixel & Material 3 Expressive.

Navigation in Material 3 is strictly adaptive, transitioning gracefully across screen widths based on **Window Size Classes** (Compact, Medium, Expanded).

---

## 1. Adaptive Navigation Matrix

| Screen Width | Window Class | Form Factors | Recommended Navigation |
| --- | --- | --- | --- |
| **$< 600\,\text{dp}$** | **Compact** | Standard phones (Pixel 9, folded Fold) | **`NavigationBar`** (Bottom Bar) |
| **$600\text{--}840\,\text{dp}$** | **Medium** | Foldables unfolded, small tablets | **`NavigationRail`** (Vertical Side Rail) |
| **$> 840\,\text{dp}$** | **Expanded** | Pixel Tablet, desktop monitors | **`PermanentNavigationDrawer`** or Expanded Rail |

---

## 2. NavigationBar (Bottom Navigation)

- **Height:** $80\,\text{dp}$ resting height (excluding system navigation bar insets).
- **Destinations:** Strictly **3 to 5 destinations**. Fewer than 3 destinations should use tabs; more than 5 must transition to a drawer or combined view.
- **Active Pill Indicator:**
  - Selected item features an animated horizontal pill badge behind the icon.
  - Active Pill Color: `secondaryContainer`
  - Active Icon Color: `onSecondaryContainer`
  - Inactive Icon Color: `onSurfaceVariant`
- **Label Behavior:** Labels should always be visible in M3 (`alwaysShowLabel = true`) to prevent layout jumping when switching destinations.

---

## 3. NavigationRail (Side Navigation)

- **Width:** $80\,\text{dp}$ collapsed (compact vertical bar).
- **Position:** Anchored to the leading (left) screen edge.
- **Top Anchor:** Often holds an optional `FloatingActionButton` or app logo.
- **Destinations:** 3 to 7 destinations stacked vertically.

---

## 4. NavigationDrawer

- **Modal Drawer:** Slides in from the leading edge on compact phones when more than 5 destinations or secondary account settings are required.
- **Permanent Drawer:** Anchored on expanded viewports ($>840\,\text{dp}$), displaying rich text labels, item counts, and dividers.

---

## 5. Audit Checklist

- [ ] Does bottom navigation contain between 3 and 5 destinations (never 6+)?
- [ ] On screens $\ge 600\,\text{dp}$, does the layout automatically swap the bottom bar for a vertical `NavigationRail`?
- [ ] Are active icons enclosed in the signature M3 rounded pill indicator?
- [ ] Does each destination include an accessible content description for screen readers?
