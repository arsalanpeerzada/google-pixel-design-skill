# Accessibility & Ergonomics Guidelines

> Foundation reference for Google Pixel & Material 3 Expressive. Always loaded during audits.

Material 3 places accessibility at the core of human-centered software. An interface that fails accessibility is broken by definition.

---

## 1. Touch Targets (Strict Rule)

### Minimum Dimensions
- **Physical Touch Target:** Every interactive element must provide a bounding box of at least **$48 \times 48\,\text{dp}$** (or $48 \times 48\,\text{px}$ on standard displays).
- **Visible vs. Interactive Bounds:** The visual icon or glyph can be $24 \times 24\,\text{dp}$, but its clickable/tappable container must pad out to $48 \times 48\,\text{dp}$.
- **Target Separation:** Maintain at least **$8\,\text{dp}$** between adjacent touch targets to avoid accidental mis-taps.

```
┌──────────────────────────────────────┐
│           48dp x 48dp Box            │
│       ┌──────────────────────┐       │
│       │                      │       │
│       │     24dp Visual      │       │
│       │        Glyph         │       │
│       │                      │       │
│       └──────────────────────┘       │
└──────────────────────────────────────┘
```

### Framework Rules
- **Compose:** `Modifier.minimumInteractiveComponentSize()` automatically adds padding to ensure $48\,\text{dp}$ bounds.
- **Flutter:** Standard Material components default to `MaterialTapTargetSize.padded` ($48 \times 48\,\text{dp}$).
- **Web:** Apply `min-height: 48px; min-width: 48px;` or touch-target padding.

---

## 2. Color Contrast Ratios (WCAG Compliance)

Contrast must be verified against actual background colors, not estimated visually:

| Element Type | Minimum Contrast (AA) | Enhanced Contrast (AAA) |
| --- | --- | --- |
| **Body & Subtitle Text** (<18pt or <14pt bold) | **4.5:1** | **7.0:1** |
| **Large Text** (≥18pt or ≥14pt bold) | **3.0:1** | **4.5:1** |
| **Active Icons & Control Boundaries** | **3.0:1** | **3.0:1** |
| **Disabled Controls & Inactive Text** | Excluded, but must remain clearly distinguishable | — |

### Strict On-Color Pairings
Material You color generation mathematically guarantees accessible contrast **only** when pairing semantic color roles with their corresponding `on-` colors:
- Text/icons on `primary` $\rightarrow$ must use `onPrimary`
- Text/icons on `primaryContainer` $\rightarrow$ must use `onPrimaryContainer`
- Text/icons on `surfaceContainer` $\rightarrow$ must use `onSurface`
- Text/icons on `error` $\rightarrow$ must use `onError`

Never place an arbitrary palette color (e.g. `primary` text on `secondaryContainer` background) without recomputing contrast.

---

## 3. Dynamic Font Scaling & Large Displays

Modern Android allows users to scale system font sizes up to **$200\%$** via the accessibility slider.

### Layout Survival Checklist
1. **No Fixed Container Heights:** Avoid hardcoding `height = 40.dp` on rows containing text. Use `wrapContentHeight()` or intrinsic measurements.
2. **Flexible Multiline Wrapping:** Labels must wrap gracefully rather than truncating with ellipses (`...`) when font sizes increase.
3. **Scrollable Viewports:** If dynamic scaling expands a dialog or form beyond the screen boundary, ensure the container wraps in a vertical scroll view so buttons (e.g. "Submit", "Cancel") never get trapped below the viewport.

---

## 4. Screen Readers & Assistive Semantics (TalkBack)

- **Interactive Glyphs:** Every `IconButton` or clickable image must define a concise, descriptive, localized label (e.g. `contentDescription = "Search messages"`).
- **Decorative Elements:** Purely decorative illustrations or divider icons must explicitly set `contentDescription = null` (or `aria-hidden="true"` on Web) so screen readers skip them.
- **State Semantics:** Toggles, checkboxes, and tabs must announce their state ("Checked", "Selected", "Expanded") via platform semantics.

---

## 5. Reduced Motion & Reduced Transparency

- Respect the system setting `Settings.Global.TRANSITION_ANIMATION_SCALE` / `prefers-reduced-motion`.
- When reduced motion is enabled, replace elaborate spring morphing and translational slide-ins with simple, instantaneous alpha fades.
