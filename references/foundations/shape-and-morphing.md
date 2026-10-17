# Shape & Expressive Morphing Guidelines

> Foundation reference for Google Pixel & Material 3 Expressive.

Shape in Material 3 Expressive is dynamic, organic, and communicative. Moving far beyond uniform rectangular boxes with slightly rounded corners, M3 Expressive introduces an expanded library of **35 distinct shapes**, **asymmetric containers**, and **fluid shape-morphing**.

---

## 1. The Standard Corner Radii Scale

| Token | Radius Value | Component Usage |
| --- | --- | --- |
| **`corner-none`** | `0dp` | Full-width banners, edge-to-edge snackbars |
| **`corner-extra-small`** | `4dp` | Badges, tiny tag indicators |
| **`corner-small`** | `8dp` | Small chips, dense tooltips |
| **`corner-medium`** | `12dp` | Standard text fields, segmented buttons |
| **`corner-large`** | `16dp` | Standard cards, action dialogs |
| **`corner-extra-large`** | `28dp` | Modal bottom sheets (top corners), large cards, FABs |
| **`corner-full`** | `9999dp` (Pill / Stadium) | Buttons, input chips, search bars, Quick Settings tiles |

---

## 2. Material 3 Expressive: The 35-Shape Library

M3 Expressive features a rich taxonomy of expressive shapes categorized into:
1. **Squircles & Super-Ellipses:** Soft, curvature-continuous rounded rectangles that feel significantly more organic than geometric circles or standard rounded rects.
2. **Scallops & Petals:** Multi-lobed containers used for user avatars, badges, and festive celebration cards.
3. **Pills & Capsules:** High-energy directional shapes for active toggles, filter pills, and navigation indicators.
4. **Asymmetric Containers:** Cards where diagonal or opposite corners have different radii (e.g. Top-Left $28\,\text{dp}$, Top-Right $8\,\text{dp}$, Bottom-Right $28\,\text{dp}$, Bottom-Left $8\,\text{dp}$) to create visual cadence and focus.

---

## 3. Shape Morphing (Animated State Changes)

In M3 Expressive, transitions between states are often **shape morphs**:
- **FAB to Surface:** A circular or rounded FAB smoothly morphs its boundary outwards into a full-screen bottom sheet or dialog.
- **Checkmark Morph:** An interactive toggle morphs from an empty squircle into a filled pill with an embedded icon.
- **Loading Morph:** An indeterminate loader morphs seamlessly through geometric polygon shapes (circle $\rightarrow$ clover $\rightarrow$ star $\rightarrow$ squircle) using spring interpolation.

---

## 4. Audit Checklist

- [ ] **Pill Shapes for Buttons:** Are primary and tonal buttons using `corner-full` ($9999\,\text{dp}$ / `StadiumBorder`) rather than sharp $4\,\text{dp}$ corners?
- [ ] **Curvature Continuity:** In prominent cards and hero widgets, are corners smoothly rounded ($16\,\text{dp}$–$28\,\text{dp}$) without harsh cutoffs?
- [ ] **Asymmetric Purpose:** When asymmetric containers are used, do they guide the user's eye toward primary actions or content flow rather than appearing broken?
