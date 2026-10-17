# Material 3 Expressive & Pixel UI Lookup Table

Use this table to look up which guideline files to load when evaluating a design or refactoring UI components.

## Foundations

| Topic | Reference File | Summary |
| --- | --- | --- |
| **Accessibility & Ergonomics** | `references/foundations/accessibility.md` | Minimum 48x48dp touch targets, WCAG contrast (4.5:1 / 3:1), 200% dynamic font scaling, screen reader semantics |
| **Dynamic Color & Monet** | `references/foundations/dynamic-color.md` | HCT color space, tonal palettes, seed colors, primary/secondary/tertiary/error/container roles, light & dark pairing |
| **Elevation & Surfaces** | `references/foundations/elevation-and-surfaces.md` | Surface container tiers (`lowest`, `low`, `default`, `high`, `highest`) replacing drop-shadows with tonal tints |
| **Typography & Scale** | `references/foundations/typography.md` | Google Sans, Roboto, Roboto Flex, variable optical weights, M3 Expressive type scale (Display, Headline, Title, Body, Label) |
| **Shape & Morphing** | `references/foundations/shape-and-morphing.md` | 35 M3 Expressive shapes, corner radiuses, squircles, pill shapes, asymmetric card containers, and dynamic shape morphing |
| **Motion & Springs** | `references/foundations/motion-and-springs.md` | Physics-based spring curves (damping & stiffness), predictive back gesture, container transforms, squash-and-stretch |
| **Haptics & Audio** | `references/foundations/haptics-and-feedback.md` | Pixel tactile haptics: clicks for switches, ticks for sliders, subtle boundary bumps, paired with gentle micro-sounds |
| **Design Principles** | `references/foundations/design-principles.md` | The 5 core principles: Emotion-driven UX, Dynamic & Personal, Physical Yet Digital, Focused Clarity, Playful Craft |

## Components

| Component | Reference File | Summary |
| --- | --- | --- |
| **App Bars** | `references/components/app-bars.md` | Small, Center-aligned, Medium, and Large TopAppBars with collapsible titles; BottomAppBars with docked actions |
| **Navigation** | `references/components/navigation.md` | NavigationBar (3–5 destinations), NavigationRail (tablets & foldables), NavigationDrawer, and badge indicators |
| **Buttons & FABs** | `references/components/buttons-and-fabs.md` | Filled, Elevated, Tonal, Outlined, Text buttons; Floating Action Button (FAB), Extended FAB, and M3 Expressive variants |
| **Cards & Containers** | `references/components/cards-and-containers.md` | Elevated, Filled, Outlined cards; asymmetric expressive shapes, image crops, and content grouping |
| **Bottom Sheets** | `references/components/bottom-sheets.md` | Standard and Modal bottom sheets, peek heights, drag handles, edge-to-edge content, and swipe-to-dismiss physics |
| **Chips** | `references/components/chips.md` | Assist, Filter, Input, and Suggestion chips; compact heights, selected states, and leading icons |
| **Dialogs & Pickers** | `references/components/dialogs-and-pickers.md` | Basic alert dialogs, full-screen dialogs, date pickers, time pickers (dial & input modes) |
| **Switches & Sliders** | `references/components/switches-and-sliders.md` | M3 Expressive large pill toggles with icon morphing; continuous and discrete sliders with value indicators |
| **Progress & Loading** | `references/components/progress-and-loading.md` | Linear and circular progress indicators, expressive shape-morphing loaders, pull-to-refresh animations |
| **Text Fields** | `references/components/text-fields.md` | Filled and Outlined text fields, floating labels, prefix/suffix icons, supporting text, and error states |
| **Menus & Snackbars** | `references/components/menus-and-snackbars.md` | Dropdown menus, cascaded menus, Snackbars with single actions, and banners for persistent notices |

## Pixel Signature Surfaces

| Surface | Reference File | Summary |
| --- | --- | --- |
| **At a Glance** | `references/pixel-surfaces/at-a-glance.md` | Smart contextual launcher header, live updates, weather, calendar, flight alerts, and commute cards |
| **System UI & Controls** | `references/pixel-surfaces/system-ui.md` | Quick Settings pill tiles, volume sliders, themed monochrome app icons, dynamic lock screen clock styles |
| **Foldables & Tablets** | `references/pixel-surfaces/foldables-and-tablets.md` | Pixel Fold, Pixel 9 Pro Fold, and Pixel Tablet postures (tabletop, tent), hinge layout separation, taskbar, split view |

## Translation & Code Tools

| Tool | Reference File | Summary |
| --- | --- | --- |
| **Cross-Platform Matrix** | `references/cross-platform.md` | Mapping M3/Pixel terms to Jetpack Compose, Flutter, React Native Paper, Web/Tailwind, and KMP |
| **Code Audit & Smells** | `references/code-audit.md` | Patterns to search for: hardcoded hex codes, missing 48dp bounds, legacy drop shadows, non-predictive back |
