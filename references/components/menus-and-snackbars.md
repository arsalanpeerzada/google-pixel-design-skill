# Menus, Snackbars & Banners

> Component reference for Google Pixel & Material 3 Expressive.

Feedback and contextual menus keep users informed and provide secondary options on demand.

---

## 1. Menus (Dropdown & Contextual)

- **Surface Fill:** `surfaceContainerHighest` or `surfaceContainerHigh`.
- **Corner Radius:** **$4\,\text{dp}$ to $12\,\text{dp}$** rounded corners.
- **Elevation:** Subtle resting shadow (`elevation = 3.dp` to $6\,\text{dp}$) to lift off the parent view.
- **Item Height:** Standard menu items are **$48\,\text{dp}$** tall to guarantee accessible touch bounds.
- **Leading & Trailing Elements:** Left icon ($24\,\text{dp}$, `onSurfaceVariant`) + Label (`Body Large`) + optional right keyboard shortcut or trailing sub-menu arrow.

---

## 2. Snackbars (Transient Feedback)

Snackbars notify users of background tasks or reversible actions (e.g. "Message archived", "Draft saved").

- **Color Roles:** Uses **`inverseSurface`** background with **`inverseOnSurface`** text to guarantee high contrast across all light/dark themes.
- **Single Action:** Houses at most **one** action button (e.g. "Undo"), colored in **`inversePrimary`**.
- **Shape & Position:**
  - Floating Style: Anchored above bottom navigation or above the FAB, with $16\,\text{dp}$ screen margin and $8\,\text{dp}$ or full pill corners.
  - Fixed Style: Extends edge-to-edge along the screen bottom.
- **Duration:** Auto-dismisses after 4 to 10 seconds. Must pause if the user hovers or touches the bar.

---

## 3. Banners (Persistent Notices)

- **Usage:** Prominent, non-transient warnings (e.g. "No internet connection", "Billing payment required").
- **Position:** Anchored directly beneath the top app bar.
- **Actions:** Can house up to **two** text buttons (e.g. "Dismiss", "Update payment").

---

## 4. Audit Checklist

- [ ] Does the Snackbar display at most ONE action?
- [ ] Are menu items at least $48\,\text{dp}$ tall for easy selection?
- [ ] Does the Snackbar avoid occluding active FABs or bottom navigation bars?
