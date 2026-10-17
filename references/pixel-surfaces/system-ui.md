# System UI & Pixel Signature Controls

> Pixel surface reference for Google Pixel & Material 3 Expressive.

The Google Pixel operating system features distinct system UI paradigms that define its visual rhythm:

---

## 1. Quick Settings Pill Tiles

The notification shade and quick settings panel feature large, tactile pill tiles:
- **Dimensions:** $88\,\text{dp}$ width $\times$ $56\,\text{dp}$ height with full pill rounding (`corner-full`).
- **States:**
  - **Active (On):** Solid `primary` background with `onPrimary` icon and label.
  - **Inactive (Off):** `surfaceContainerHigh` with `onSurfaceVariant` icon and label.
  - **Unavailable:** Dimmed opacity ($38\%$).
- **Micro-Interaction:** Tapping toggles state with an instant haptic click; holding opens the detailed sub-page or popup sheet.

---

## 2. Thick Volume & Brightness Sliders

Pixel replaces standard thin volume lines with substantial, finger-friendly pill sliders:
- **Track Thickness:** $24\,\text{dp}$ to $32\,\text{dp}$ thick pill container.
- **Embedded Icon:** Glyph floats inside the track, shifting contrast as the slider passes over it.
- **Spring Feedback:** Dragging past $100\%$ or below $0\%$ triggers an elastic rubber-band stretch and a subtle haptic boundary bump.

---

## 3. Themed Monochrome App Icons

Android 13–17 Pixel Launcher supports **Themed Icons**:
- **Foreground Silhouette:** Third-party apps provide a flat vector monochrome silhouette (`<monochrome android:drawable="..." />`).
- **Dynamic Tinting:**
  - Background circle/squircle is tinted with `primaryContainer` or wallpaper secondary tone.
  - Icon glyph is tinted with `onPrimaryContainer` or `primary`.
- **Consistency:** Apps that fail to supply a monochrome vector appear mismatched on the Pixel home screen grid.

---

## 4. Dynamic Lock Screen Clocks

Pixel allows users to choose from dynamic clock styles:
- **Two-Line Hero Clock:** Oversized numerals in Google Sans Flex, adapting weight and spacing when notifications arrive.
- **Organic Typography:** Clock digits morph into playful organic geometries or subtle floral outlines in M3 Expressive.

---

## 5. Audit Checklist

- [ ] Does your app provide a valid `<monochrome>` vector asset for Pixel Themed Icons?
- [ ] Does the app draw edge-to-edge behind the transparent system status bar and gesture navigation bar?
- [ ] Are custom sliders and audio/media controls aligned with the thick pill Pixel aesthetic?
