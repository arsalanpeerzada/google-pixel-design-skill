# Code Audit: Search Patterns & Anti-Patterns

Use this guide when inspecting source code repositories, PR diffs, or UI implementations. Each pattern lists what to search for, why it violates Material 3 / Pixel guidelines, and the idiomatic replacement.

---

## 1. Hardcoded Colors & Theme Bypass

### The Smell
Hardcoded hex colors (`#1A73E8`, `0xFF4285F4`, `Colors.blue`) circumvent the Monet dynamic color engine and break automatic Dark theme adaptation.

### Search Patterns
- Compose: `Color(0x[0-9A-Fa-f]{8})` or `Color\.(Red|Blue|Green|White|Black)`
- Flutter: `Colors\.[a-z]+` or `Color\(0x[0-9A-Fa-f]{8}\)`
- Web/React: `#([0-9a-fA-F]{3}){1,2}` inside inline styles or Tailwind classes like `bg-[#0d6efd]`

### Citation & Rule
`references/foundations/dynamic-color.md › Semantic Color Roles`
UI elements must always query semantic tokens (`colorScheme.primary`, `colorScheme.surfaceContainer`, etc.) to dynamically inherit the user's wallpaper tones in Android 12–17.

### Replacement Example (Compose)
```kotlin
// BAD
Box(modifier = Modifier.background(Color(0xFF1A73E8)))

// GOOD
Box(modifier = Modifier.background(MaterialTheme.colorScheme.primary))
```

---

## 2. Inadequate Touch Targets (<48dp)

### The Smell
Clickable components with physical or touch bounds below $48 \times 48\,\text{dp}$, causing frustrating mis-taps on mobile touchscreens.

### Search Patterns
- Compose: `Modifier.size\(([1-3][0-9]|4[0-7])\.dp\)\.clickable`
- Flutter: `InkWell` or `GestureDetector` wrapping a child with `width < 48` or `height < 48` without padding
- Web: `height: [1-3][0-9]px` or `w-[6-9] h-[6-9]` on `<button>` elements

### Citation & Rule
`references/foundations/accessibility.md › Touch Targets`
Every interactive element must have a minimum interactive bounding box of $48 \times 48\,\text{dp}$, with at least $8\,\text{dp}$ separation between adjacent touch bounds.

### Replacement Example (Compose)
```kotlin
// BAD
IconButton(
    onClick = { },
    modifier = Modifier.size(32.dp) // clips touch target!
) {
    Icon(Icons.Default.Close, contentDescription = "Close")
}

// GOOD
IconButton(
    onClick = { },
    modifier = Modifier.size(48.dp) // guarantees 48dp target
) {
    Icon(
        Icons.Default.Close,
        contentDescription = "Close",
        modifier = Modifier.size(24.dp) // glyph remains 24dp
    )
}
```

---

## 3. Legacy Drop Shadows Instead of Tonal Elevation

### The Smell
Using dark, blurry drop shadows (`shadow(8.dp)`, `elevation: 8`, `box-shadow: 0 4px 12px rgba(0,0,0,0.2)`) to convey card hierarchy. In Material 3, elevation is rendered via **tonal surface tinting**, not heavy black shadows.

### Search Patterns
- Compose: `Modifier.shadow\(`
- Flutter: `BoxShadow(color: Colors.black.withOpacity`
- Web: `box-shadow:` with dark alpha or `shadow-lg`

### Citation & Rule
`references/foundations/elevation-and-surfaces.md › Tonal Surface Hierarchy`
Surfaces rise toward light through tonal color tiers (`surfaceContainerLow`, `surfaceContainer`, `surfaceContainerHigh`, `surfaceContainerHighest`), creating clean, modern, and accessible depth.

### Replacement Example (Flutter)
```dart
// BAD
Container(
  decoration: BoxDecoration(
    color: Colors.white,
    boxShadow: [BoxShadow(color: Colors.black26, blurRadius: 10, offset: Offset(0, 4))],
  ),
)

// GOOD
Card(
  elevation: 2, // In M3 with useMaterial3: true, applies tonal tint automatically
  color: Theme.of(context).colorScheme.surfaceContainer,
  shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(16)),
)
```

---

## 4. Crowded Bottom Navigation (6+ Destinations)

### The Smell
Stuffing 6 or more destinations into a mobile bottom bar, or retaining a bottom navigation bar when transitioning to landscape or large tablet viewports.

### Search Patterns
- Compose: `NavigationBar { ... }` with $> 5$ `NavigationBarItem` calls
- Flutter: `NavigationBar(destinations: [ ... ])` with $> 5$ destinations

### Citation & Rule
`references/components/navigation.md › NavigationBar Specifications`
A bottom navigation bar supports strictly **3 to 5 destinations**. On viewports wider than $600\,\text{dp}$ (tablets, foldables unfolded, landscape), transition to a **NavigationRail**.

---

## 5. Stiff Linear Animation Curves

### The Smell
Using linear or stiff ease-in-out animations for screen transitions or dialog reveals, making the app feel sluggish or robotic.

### Search Patterns
- Compose: `tween(durationMillis = ...)` or `LinearEasing`
- Flutter: `Curves.linear` or `Curves.easeInOut`

### Citation & Rule
`references/foundations/motion-and-springs.md › Spring Physics`
Material 3 Expressive mandates physics-based spring curves with natural bounce and spatial momentum (`Spring.DampingRatioMediumBouncy`, `Spring.StiffnessLow`).

### Replacement Example (Compose)
```kotlin
// BAD
val offset by animateDpAsState(targetValue = target, animationSpec = tween(300))

// GOOD
val offset by animateDpAsState(
    targetValue = target,
    animationSpec = spring(
        dampingRatio = Spring.DampingRatioMediumBouncy,
        stiffness = Spring.StiffnessLow
    )
)
```

---

## 6. Missing Accessibility Content Descriptions

### The Smell
Icons and interactive glyphs with `contentDescription = null` or omitted accessible labels on interactive buttons.

### Search Patterns
- Compose: `Icon(..., contentDescription = null)` inside `IconButton` or `clickable`
- Flutter: `IconButton(icon: Icon(...), onPressed: ...)` without `tooltip:`

### Citation & Rule
`references/foundations/accessibility.md › Screen Reader Labels`
Every interactive element must have a localized, clear description for TalkBack and screen readers. Purely decorative icons must be explicitly marked.
