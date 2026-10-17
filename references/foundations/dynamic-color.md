# Dynamic Color & The Monet Engine

> Foundation reference for Google Pixel & Material 3 Expressive. Always loaded during audits.

Dynamic Color (introduced in Android 12 and enhanced in Android 14–17) is Google Pixel's signature visual identity. Powered by the **Monet engine**, it algorithmically extracts a rich color scheme from the user's personal wallpaper, applying it across system surfaces and third-party apps.

---

## 1. The HCT Color Space

Traditional RGB and HSL color models fail in UI design because brightness is not perceptually uniform (e.g. pure yellow appears far brighter to the human eye than pure blue at 100% saturation).

Material 3 uses **HCT (Hue, Chroma, Tone)**:
- **Hue ($0^{\circ}$–$360^{\circ}$):** The color family (red, amber, teal, violet).
- **Chroma ($0$–$120+$):** The colorfulness/saturation.
- **Tone ($0$–$100$):** Perceptually accurate lightness ($0 = \text{black}$, $100 = \text{white}$).

Because Tone is mathematically linear to human perception, **any color at Tone 40 paired with any color at Tone 90 automatically satisfies WCAG AA contrast ($4.5:1$)**, regardless of the Hue chosen!

---

## 2. The 5 Core Tonal Palettes

From a single seed color (or wallpaper sample), the Monet engine generates 5 distinct 13-step tonal palettes:

1. **Primary Palette (Accent 1):** Highest chroma; identifies prominent actions, FABs, and active navigation items.
2. **Secondary Palette (Accent 2):** Muted chroma; used for less prominent components, filter chips, and badges.
3. **Tertiary Palette (Accent 3):** An analogous or contrasting hue offset from Primary; brings vibrant balance and playful contrast to cards, avatars, and editorial highlights.
4. **Neutral Palette (Surface):** Minimal chroma; generates background surfaces, sheets, and scaffold canvases.
5. **Neutral Variant Palette (Outline/Variant):** Subtle chroma; powers component borders, outlines, divider lines, and unselected text.

Plus a fixed **Error Palette** for destructive alerts and error validation.

---

## 3. Light vs. Dark Tonal Role Mapping

The system maps specific tones to semantic roles depending on the active theme:

| Semantic Role | Light Theme Tone | Dark Theme Tone | Common Usage |
| --- | --- | --- | --- |
| **`primary`** | Tone 40 | Tone 80 | FAB background, primary buttons |
| **`onPrimary`** | Tone 100 (White) | Tone 20 | Text/icons on `primary` |
| **`primaryContainer`** | Tone 90 | Tone 30 | Selected chips, high-emphasis cards |
| **`onPrimaryContainer`** | Tone 10 | Tone 90 | Text/icons on `primaryContainer` |
| **`secondary`** | Tone 40 | Tone 80 | Filter chips, minor badges |
| **`tertiaryContainer`** | Tone 90 | Tone 30 | Creative callouts, badges, hero cards |
| **`surface`** | Tone 98 | Tone 6 | Base app canvas |
| **`onSurface`** | Tone 10 | Tone 90 | Body and title text on surfaces |
| **`outline`** | Tone 50 | Tone 60 | Borders on outlined buttons and text fields |
| **`outlineVariant`** | Tone 80 | Tone 30 | Subtle list dividers, inactive borders |

---

## 4. The 5 Surface Container Tiers (No Drop Shadows!)

In Material 3, physical drop shadows are deprecated in favor of **Surface Container Tiers**. As components elevate, their surface container color shifts:

```
┌──────────────────────────────────────────────────┐
│  surfaceContainerHighest (Tone 90 / Dark Tone 22)│
│  ┌────────────────────────────────────────────┐  │
│  │ surfaceContainerHigh (Tone 92 / Dark Tone 17)│  │
│  │ ┌────────────────────────────────────────┐ │  │
│  │ │ surfaceContainer (Tone 94 / Dark Tone 12)│ │  │
│  │ │ ┌────────────────────────────────────┐ │ │  │
│  │ │ │surfaceContainerLow(Tone 96 / Dark 10)│ │ │  │
│  │ │ └────────────────────────────────────┘ │ │  │
│  │ └────────────────────────────────────────┘ │  │
│  └────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────┘
```

- **`surfaceContainerLowest`:** Recessed areas or background search inputs.
- **`surfaceContainerLow`:** Cards or flat list containers against the base surface.
- **`surfaceContainer`:** Standard card containers, bottom app bars.
- **`surfaceContainerHigh`:** Raised cards, modal bottom sheets, menus.
- **`surfaceContainerHighest`:** Modal dialogs, tooltips, high-priority popovers.

---

## 5. Review Checklist & Anti-Patterns

1. **Never hardcode hex colors** for UI containers, text, or buttons. Always query `colorScheme`.
2. **Never break on-color pairings.** Text on `primary` must always be `onPrimary`, never `onSurface` or hardcoded `#FFFFFF`.
3. **Embrace Tertiary:** Many developers forget `tertiary` and `tertiaryContainer`. In Pixel UI, tertiary is what gives apps their playful, human warmth (e.g. a teal primary app using peach/coral tertiary tags).
4. **Dark Theme Inversion:** Ensure your custom components do not manually invert colors with inverted math; use the semantic tokens so Android's system dark mode handles luminance smoothly.
