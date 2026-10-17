# Buttons & Floating Action Buttons (FABs)

> Component reference for Google Pixel & Material 3 Expressive.

Buttons initiate actions and express visual priority. In Material 3, buttons feature rounded pill shapes ($9999\,\text{dp}$) and clearly demarcated emphasis tiers.

---

## 1. The 5 Button Emphasis Tiers

```
Highest Emphasis  ┌──────────────────────────────────────────────┐
                  │ Filled Button (Primary / OnPrimary)          │
                  ├──────────────────────────────────────────────┤
                  │ Filled Tonal Button (SecondaryContainer)     │
                  ├──────────────────────────────────────────────┤
                  │ Elevated Button (Surface / Shadow)           │
                  ├──────────────────────────────────────────────┤
                  │ Outlined Button (Transparent / Outline)      │
                  ├──────────────────────────────────────────────┤
Lowest Emphasis   │ Text Button (Transparent / Primary Text)     │
                  └──────────────────────────────────────────────┘
```

1. **Filled Button:** Solid `primary` background with `onPrimary` text. Reserved for the single most important action on a screen (e.g. "Save", "Submit", "Continue").
2. **Filled Tonal Button:** Solid `secondaryContainer` background with `onSecondaryContainer` text. Ideal for prominent secondary actions that need presence without competing with the primary action.
3. **Elevated Button:** Light tonal surface with modest resting shadow. Useful when an action must stand out against complex image backgrounds.
4. **Outlined Button:** Transparent interior bounded by a $1\,\text{dp}$ `outline` border. Used for neutral secondary actions (e.g. "Cancel", "Learn more").
5. **Text Button:** Completely borderless and transparent. Used for subtle, tertiary actions (e.g. "Dismiss", "Skip").

---

## 2. Floating Action Button (FAB)

The FAB represents the primary constructive action of the current screen (e.g. "Compose email", "New tweet", "Create note").

| FAB Variant | Dimensions | Corner Radius | Icon Size | Usage |
| --- | --- | --- | --- | --- |
| **Small FAB** | $40 \times 40\,\text{dp}$ | $12\,\text{dp}$ | $24\,\text{dp}$ | Secondary floating action, dense toolbars |
| **Standard FAB** | $56 \times 56\,\text{dp}$ | $16\,\text{dp}$ | $24\,\text{dp}$ | Default primary action |
| **Large FAB** | $96 \times 96\,\text{dp}$ | $28\,\text{dp}$ | $36\,\text{dp}$ | Large screen / tablet layouts, prominent camera triggers |
| **Extended FAB**| $56\,\text{dp}$ height | $16\,\text{dp}$ | $24\,\text{dp}$ | Floating action with icon and explicit text label |

### The Scroll Collapse Pattern
An `ExtendedFloatingActionButton` should expand on resting or top scroll states, and smoothly collapse into an icon-only standard FAB as the user scrolls down, minimizing content occlusion.

---

## 3. Shape & Touch Dimensions

- **Corner Radius:** Standard buttons use full pill rounding (`corner-full`, $9999\,\text{dp}$ / `StadiumBorder`).
- **Touch Target:** Even compact button variants must pad out to at least **$48 \times 48\,\text{dp}$** interactive bounds.
- **Button Capitalization:** Use **Sentence case** ("Create account", "Get started"), never ALL CAPS.

---

## 4. Audit Checklist

- [ ] Is there only **one** Filled Button or FAB per screen to avoid competing calls-to-action?
- [ ] Are button labels in sentence case?
- [ ] Does the FAB collapse or hide cleanly during rapid downward list scrolling?
- [ ] Are button touch boundaries $\ge 48\,\text{dp}$?
