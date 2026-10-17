# Dialogs & Pickers: Alerts, Date & Time Pickers

> Component reference for Google Pixel & Material 3 Expressive.

Dialogs and pickers request urgent confirmation, present critical decisions, or gather structured input.

---

## 1. Alert Dialogs

- **Corner Radius:** **$28\,\text{dp}$** (`corner-extra-large`) on all four corners.
- **Surface Fill:** `surfaceContainerHigh` or `surfaceContainerHighest`.
- **Scrim:** Darkened overlay (`scrim` token at $32\%$ opacity).
- **Internal Structure:**
  - Optional Centered Icon ($24\,\text{dp}$, colored in `secondary`).
  - Title: `Headline Small` ($24\,\text{sp}$), left-aligned or centered if icon is present.
  - Body Copy: `Body Medium` ($14\,\text{sp}$) with comfortable line spacing.
  - Action Row: Positioned at bottom right. Dismissive action on the left ("Cancel", Text Button), confirming action on the right ("Confirm", Text or Filled Button).

---

## 2. Full-Screen Dialogs

- **Usage:** Used on mobile phones when a sub-task requires multiple fields, complex scrollable lists, or camera interaction (e.g. "Create calendar event", "Edit contact").
- **Header:** Features a close "X" icon on the top-left, a concise title, and a primary action button ("Save") anchored in the top-right app bar.

---

## 3. Date & Time Pickers (Pixel Signature)

### Time Picker
Pixel devices feature the iconic **analog radial clock dial** paired with an accessible numeric toggle:
- **Radial Clock Face:** Smooth drag scrubbing with haptic ticks at each hour/minute increment.
- **Toggle Mode:** A keyboard icon button in the bottom-left allows immediate switching between clock face dragging and direct numeric text input.
- **AM/PM Selector:** Segmented pill toggle with active selection in `primaryContainer`.

### Date Picker
- **Header:** Prominently highlights the selected date in `Display Small` or `Headline Large` for instant verification.
- **Calendar Grid:** Clean spacing with active date highlighted in a full circular `primary` indicator.

---

## 4. Audit Checklist

- [ ] Does the dialog use $28\,\text{dp}$ rounded corners?
- [ ] Are dialog actions aligned to the bottom right with clear distinction between confirm and cancel?
- [ ] Is keyboard accessibility and numeric text entry supported in pickers?
