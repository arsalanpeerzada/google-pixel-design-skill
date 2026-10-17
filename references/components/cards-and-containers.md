# Cards & Containers

> Component reference for Google Pixel & Material 3 Expressive.

Cards group related information and actions into digestible, touchable surfaces. In Material 3 Expressive, cards break free from uniform grids through varied container heights, tonal tiers, and asymmetric silhouettes.

---

## 1. Card Variants

| Variant | Surface Fill | Border / Elevation | Intended Usage |
| --- | --- | --- | --- |
| **Elevated Card** | `surfaceContainerLow` | Tonal elevation tint + subtle shadow on drag | Grouped content that needs separation from base canvas |
| **Filled Card** | `surfaceContainerHighest` | No border; high-contrast tonal surface | High-priority callouts, dashboards, alert summaries |
| **Outlined Card** | `surface` | $1\,\text{dp}$ `outlineVariant` border | Clean, lightweight content grouping without heavy fills |

---

## 2. Corner Radii & Asymmetric Shapes

- **Standard Cards:** Use `corner-large` ($16\,\text{dp}$) or `corner-extra-large` ($24\text{--}28\,\text{dp}$).
- **M3 Expressive Asymmetry:** To create visual rhythm in editorial or media cards, apply asymmetrical corner radii (e.g., Top-Left: $28\,\text{dp}$, Top-Right: $8\,\text{dp}$, Bottom-Right: $28\,\text{dp}$, Bottom-Left: $8\,\text{dp}$). This gives the layout dynamic character while maintaining geometric rigor.

---

## 3. Padding & Content Structure

- **Container Padding:** Standard internal content padding is **$16\,\text{dp}$** (or $24\,\text{dp}$ for large feature cards).
- **Separation between Cards:** Minimum **$8\,\text{dp}$ to $12\,\text{dp}$** spacing between adjacent cards in a list or grid.
- **Media Cards:** When images bleed to the edge of a card, ensure the image corners match the container's outer corner radius (`clipToBounds = true`).

---

## 4. Audit Checklist

- [ ] Are cards using M3 surface containers rather than flat white with heavy dark shadows?
- [ ] If clickable, does the entire card exhibit an ink ripple and an interactive state?
- [ ] Are adjacent cards separated by at least $8\,\text{dp}$?
- [ ] Does text inside the card maintain high contrast against the chosen surface tier?
