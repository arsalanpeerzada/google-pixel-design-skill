# Foldables & Tablets: Pixel Fold & Tablet Guidelines

> Pixel surface reference for Google Pixel & Material 3 Expressive.

Google's hardware ecosystem spans traditional phones to foldables (**Pixel Fold**, **Pixel 9 Pro Fold**) and docked displays (**Pixel Tablet**). Designing for Pixel requires embracing dynamic aspect ratios, hinge postures, and multi-pane layouts.

---

## 1. Canonical Layout Patterns

Material 3 defines three canonical layouts for expanded screens ($\ge 600\,\text{dp}$):

```
1. List-Detail Layout              2. Supporting Pane Layout
┌──────────────┬─────────────────┐ ┌───────────────────┬──────────────┐
│  Navigation  │                 │ │                   │ Contextual   │
│   or List    │   Detail Pane   │ │   Primary Pane    │ Supporting   │
│     Pane     │                 │ │                   │     Pane     │
└──────────────┴─────────────────┘ └───────────────────┴──────────────┘
```

1. **List-Detail View:** The left pane displays navigable items; the right pane shows the selected detail. Replaces repetitive push-and-pop navigation on large screens.
2. **Supporting Pane:** Primary workflow occupies the left $60\text{--}70\%$ of screen width; supporting metadata, comments, or tools reside in the right $30\text{--}40\%$.
3. **Feed Layout:** Multiple card columns that expand horizontally as viewport width increases, avoiding stretched-out single-column text lines.

---

## 2. Foldable Hardware Postures

The Pixel Fold introduces physical hinge sensing through Android's `FoldingFeature`:

| Posture | Hinge State | UI Adaptation |
| --- | --- | --- |
| **Flat (Unfolded)** | $180^{\circ}$ open | Standard dual-pane or expanded tablet view |
| **Tabletop Mode** | $90^{\circ}\text{--}120^{\circ}$ bent, resting on table | **Split Layout:** Media/camera view on top vertical half; playback/controls/chat on bottom horizontal half |
| **Tent Mode** | Partially folded, device inverted like a tent | Front screen active for hands-free media playback |
| **Book Mode** | Partially folded vertical orientation | Two distinct pages with content separated at the central hinge |

### The Hinge Separation Rule
Never position interactive buttons, text inputs, or critical focal points across the physical fold crease. Use `WindowInsets` to add spacing that keeps controls safely away from the hinge fold.

---

## 3. Pixel Taskbar & Multitasking

On Pixel Tablet and unfolded Pixel Fold devices, Android features a persistent or swipeable **Taskbar**:
- **Quick Switching:** Users drag app icons directly into split-screen mode.
- **Drag-and-Drop:** Apps should support dragging images, text, and documents across side-by-side panes.
- **Insets:** Ensure bottom UI layouts pad for the Taskbar when it is docked.

---

## 4. Audit Checklist

- [ ] Does the app transition from single-pane to a dual-pane (List-Detail) layout on screens $\ge 600\,\text{dp}$?
- [ ] Does the layout avoid stretching full-width buttons across wide tablet displays?
- [ ] In Tabletop mode, do media controls automatically relocate to the bottom half?
- [ ] Are elements kept clear of the physical hinge line on foldable devices?
