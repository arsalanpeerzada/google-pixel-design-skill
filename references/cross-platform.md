# Cross-Platform Vocabulary & Implementation Matrix

> Hand-written companion to `SKILL.md`. Load whenever reviewing code or generating UI for Flutter, React Native, Web, or Kotlin Multiplatform.

Material 3 Expressive and Google Pixel guidelines use Google's native system vocabulary. Speak the user's framework accurately while strictly preserving design fidelity.

---

## 1. Core Vocabulary Mapping

| Material 3 / Pixel Concept | Jetpack Compose | Flutter (Material 3) | React Native Paper | Web / CSS Tokens |
| --- | --- | --- | --- | --- |
| **Theme / Design System** | `MaterialTheme` | `ThemeData(useMaterial3: true)` | `MD3LightTheme` / `MD3DarkTheme` | `@material/web` tokens / `:root` variables |
| **Dynamic Color** | `dynamicLightColorScheme(ctx)` | `ColorScheme.fromSeed(seedColor)` | Custom palette mapping | CSS variables from Monet engine |
| **Primary Color** | `colorScheme.primary` | `Theme.of(ctx).colorScheme.primary` | `theme.colors.primary` | `var(--md-sys-color-primary)` |
| **Surface Container** | `colorScheme.surfaceContainer` | `Theme.of(ctx).colorScheme.surfaceContainer` | `theme.colors.elevation.level2` | `var(--md-sys-color-surface-container)` |
| **Surface Container High**| `colorScheme.surfaceContainerHigh` | `Theme.of(ctx).colorScheme.surfaceContainerHigh` | `theme.colors.elevation.level3` | `var(--md-sys-color-surface-container-high)` |
| **On-Color Pairing** | `colorScheme.onPrimary` | `Theme.of(ctx).colorScheme.onPrimary` | `theme.colors.onPrimary` | `var(--md-sys-color-on-primary)` |
| **System Font** | `GoogleSans` / `RobotoFlex` | `GoogleFonts.roboto()` / `googleSans` | Custom font family config | `font-family: 'Google Sans', 'Roboto Flex', sans-serif` |
| **Pill Button** | `Button(shape = RoundedCornerShape(9999.dp))` | `FilledButton(style: ... StadiumBorder())` | `Button(mode="contained", roundness=24)` | `border-radius: 9999px` |
| **Tonal Button** | `FilledTonalButton` | `FilledButton.tonal` | `Button(mode="contained-tonal")` | `<md-filled-tonal-button>` |
| **Floating Action Button** | `FloatingActionButton` | `FloatingActionButton` | `FAB` | `<md-fab>` |
| **Extended FAB** | `ExtendedFloatingActionButton` | `FloatingActionButton.extended` | `AnimatedFAB` | `<md-fab variant="extended">` |
| **Bottom Navigation** | `NavigationBar` + `NavigationBarItem` | `NavigationBar` + `NavigationDestination` | `BottomNavigation` / Tabs | Custom M3 dock / `<md-navigation-bar>` |
| **Side Navigation** | `NavigationRail` | `NavigationRail` | Drawer or custom rail | Side rail layout / `<md-navigation-rail>` |
| **Modal Bottom Sheet** | `ModalBottomSheet` | `showModalBottomSheet()` | `Modal` / BottomSheet | Dialog element with bottom slide |
| **Expressive Switch** | `Switch(thumbContent = ...)` | `Switch()` with icons | `Switch()` | `<md-switch selected-icon>` |
| **Predictive Back** | `PredictiveBackHandler` | `PopScope` | Gesture / BackHandler | Browser View Transitions API |

---

## 2. Framework-Specific Conventions & Checklists

### Jetpack Compose (`androidx.compose.material3`)
- **Theme Wrap:** Wrap the root in `MaterialTheme(colorScheme = ..., typography = ..., shapes = ...)`
- **Dynamic Color Setup:** Check `Build.VERSION.SDK_INT >= Build.VERSION_CODES.S` and use `dynamicLightColorScheme(context)` / `dynamicDarkColorScheme(context)`.
- **Touch Bounds:** Use `Modifier.minimumInteractiveComponentSize()` (which automatically enforces $48 \times 48\,\text{dp}$).
- **Spring Physics:** Use `spring(dampingRatio = Spring.DampingRatioMediumBouncy, stiffness = Spring.StiffnessLow)` for animated transitions.
- **Scaffold Padding:** Always consume `innerPadding` inside `Scaffold` to guarantee edge-to-edge drawing under system bars and camera cutouts.

### Flutter (`package:flutter/material.dart`)
- **Enable M3:** Set `useMaterial3: true` in `ThemeData`.
- **Generate Tonal Palette:** Use `ColorScheme.fromSeed(seedColor: Color(...), brightness: Brightness.light)`.
- **Touch Bounds:** Ensure `materialTapTargetSize: MaterialTapTargetSize.padded` is active (default in M3) so controls achieve minimum $48 \times 48\,\text{dp}$.
- **Edge-to-Edge:** Set `SystemChrome.setEnabledSystemUIMode(SystemUiMode.edgeToEdge)` and configure transparent navigation/status bars.
- **Expressive Shapes:** Use `StadiumBorder()` for buttons and `RoundedRectangleBorder(borderRadius: BorderRadius.circular(16))` for cards.

### React Native & React Native Paper
- **Theme Provider:** Wrap in `<PaperProvider theme={theme}>`.
- **Avoid Fixed Dimensions:** Replace hardcoded `width: 30, height: 30` button containers with `minWidth: 48, minHeight: 48, justifyContent: 'center', alignItems: 'center'`.
- **Surface Elevation:** Use `theme.colors.elevation.level1` through `level5` for container backgrounds instead of CSS `elevation: 4` or `box-shadow`.
- **Ripples:** Use `<TouchableRipple borderless ...>` to preserve Material ink feedback.

### Web & CSS (Material Web / Tailwind)
- **Token Variables:** Map tokens to CSS custom properties:
  ```css
  :root {
    --md-sys-color-primary: #0b57d0;
    --md-sys-color-on-primary: #ffffff;
    --md-sys-color-primary-container: #d3e3fd;
    --md-sys-color-surface: #fdfcff;
    --md-sys-color-surface-container: #edeef2;
    --md-sys-shape-corner-full: 9999px;
    --md-sys-shape-corner-large: 16px;
    --md-sys-motion-easing-spring: cubic-bezier(0.2, 0.0, 0.0, 1.0);
  }
  ```
- **Touch Target Padding:** Interactive controls must have at least `padding: 12px` or pseudo-element click targets (`::after { content: ''; position: absolute; inset: -8px; }`) to guarantee 48px touch bounding box.
