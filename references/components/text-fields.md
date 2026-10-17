# Text Fields: Filled & Outlined Guidelines

> Component reference for Google Pixel & Material 3 Expressive.

Text fields let users enter and edit text. Material 3 provides two distinct styles: **Filled** and **Outlined**.

---

## 1. Filled vs. Outlined Variants

| Variant | Visual Style | Best Used In |
| --- | --- | --- |
| **Filled Text Field** | Solid `surfaceContainerHighest` fill with active $2\,\text{dp}$ bottom indicator line | Dense forms, search inputs, modal sheets where strong visual contrast is needed |
| **Outlined Text Field** | Transparent fill with complete $1\,\text{dp}$ `outline` border; floating label cuts through border | Clean layouts, settings screens, cards with colored backgrounds |

---

## 2. Anatomy & Dimensions

- **Height:** Standard resting height is **$56\,\text{dp}$** ($48\,\text{dp}$ compact).
- **Corner Radii:**
  - Filled: Top corners rounded to $4\,\text{dp}$ or $12\,\text{dp}$; bottom edge remains flat with indicator line.
  - Outlined: All four corners rounded to **$8\,\text{dp}$ to $12\,\text{dp}$** (or full pill for search bars).
- **Floating Label:**
  - Resting (Empty): Positioned in the center of the field in `Body Large` ($16\,\text{sp}$).
  - Focused / Populated: Smoothly animates up into the top margin in `Body Small` ($12\,\text{sp}$) with spring curve.
- **Leading & Trailing Icons:** $24 \times 24\,\text{dp}$ icons with $48\,\text{dp}$ touch target boxes.

---

## 3. Error & Validation States

- **Error Color:** Border, active indicator, and supporting text switch to `error`.
- **Error Container:** High-priority alert validation can tint the container fill to `errorContainer` with `onErrorContainer` text.
- **Supporting Helper Text:** Always positioned below the field in `Body Small` ($12\,\text{sp}$) to describe format requirements or explain validation errors.

---

## 4. Audit Checklist

- [ ] Does the text field height measure at least $56\,\text{dp}$?
- [ ] Does the label float smoothly when typing begins without overlapping input text?
- [ ] Are trailing action icons (e.g. password visibility toggle, clear button) padded to $48 \times 48\,\text{dp}$ touch bounds?
- [ ] Are error messages descriptive rather than vague (e.g. "Password must include a number", not "Invalid input")?
