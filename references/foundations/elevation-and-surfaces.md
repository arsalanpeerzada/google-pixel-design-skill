# Elevation & Tonal Surface Hierarchy

> Foundation reference for Google Pixel & Material 3 Expressive. Always loaded during audits.

Material 3 redefines elevation. While Material 1 relied entirely on z-axis shadows, Material 3 Expressive communicates spatial depth through **color tone shifts**, **outline definition**, and **tonal surface containers**.

---

## 1. Why Shadows Are Deprecated for Static Surfaces

1. **Dark Mode Failure:** Traditional black drop shadows are invisible on dark mode backgrounds.
2. **Visual Clutter:** Excessive blurry shadows create visual muddying, conflicting with clean modern design.
3. **Accessibility:** Tonal surface shifts provide crisp contrast boundaries that remain legible under high-contrast display modes.

---

## 2. Surface Container Hierarchy

Material 3 provides 5 progressive surface container tiers that sit on top of the base `surface`:

| Surface Role | Light Theme Value | Dark Theme Value | Recommended Components |
| --- | --- | --- | --- |
| **`surface`** | Neutral Tone 98 | Neutral Tone 6 | Main screen background / scaffold canvas |
| **`surfaceDim`** | Neutral Tone 87 | Neutral Tone 6 | Background areas needing slightly darker canvas |
| **`surfaceBright`**| Neutral Tone 98 | Neutral Tone 24 | High-luminance areas |
| **`surfaceContainerLowest`** | Neutral Tone 100 | Neutral Tone 4 | Recessed search bars, sunken input fields |
| **`surfaceContainerLow`** | Neutral Tone 96 | Neutral Tone 10 | Background card groupings, list cards |
| **`surfaceContainer`** | Neutral Tone 94 | Neutral Tone 12 | Standard cards, bottom app bars, chips |
| **`surfaceContainerHigh`** | Neutral Tone 92 | Neutral Tone 17 | Raised cards, modal bottom sheets, quick settings |
| **`surfaceContainerHighest`**| Neutral Tone 90 | Neutral Tone 22 | Modal dialogs, tooltips, popup menus |

---

## 3. When Shadows Are Permitted

Physical shadows are reserved exclusively for **transient or floating interactions**:
1. **Floating Action Button (FAB):** Has a modest shadow (`elevation = 3.dp` resting, `6.dp` pressed) because it floats independently above scrolling content.
2. **Dragging States:** When a card or list item is picked up and dragged, a subtle shadow clarifies that it has detached from the canvas.
3. **Floating Navigation Bars:** If a bottom navigation bar floats detached from the screen edges (pill style), a subtle shadow prevents content underlap confusion.

---

## 4. Outlines and Dividers

Instead of harsh black borders or heavy separator lines:
- **`outlineVariant`:** Used for subtle list separators, card borders, and unselected component boundaries. High transparency and low visual weight.
- **`outline`:** Used for interactive boundaries requiring explicit definition (e.g. OutlinedTextField border, OutlinedButton border).

---

## 5. Audit Checklist

- [ ] Are static cards using `surfaceContainer` rather than arbitrary `box-shadow` styles?
- [ ] Are nested cards visibly distinct from their parent container (e.g., child container uses `surfaceContainerHigh` inside a `surfaceContainerLow` parent)?
- [ ] In Dark Mode, is there sufficient contrast between the background canvas and elevated containers?
