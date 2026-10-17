# Typography & Type Scale Guidelines

> Foundation reference for Google Pixel & Material 3 Expressive. Always loaded during audits.

Google's typography is celebrated for its geometric warmth and extreme legibility. Built on the lineage of **Roboto** (introduced in Android 4.0 Ice Cream Sandwich) and Google's proprietary **Google Sans / Product Sans**, modern Material 3 typography embraces **variable optical sizing** and **expressive editorial rhythm**.

---

## 1. Primary Typefaces

- **Google Sans / Product Sans:** The brand signature of Google Pixel. Used for prominent headers, large displays, titles, and clock widgets. Geometric, open letterforms with warm humanist terminals.
- **Roboto & Roboto Flex:** The versatile workhorse of Android. Highly readable at dense information scales, supported by variable axes (weight, width, optical size, slant).
- **Fallbacks:** In web or cross-platform contexts where Google Sans cannot be bundled, use `Roboto Flex`, `Roboto`, or modern system sans-serif stacks.

---

## 2. The Material 3 Type Scale

The system defines 5 roles across 3 sizes, creating 15 standard type configurations:

| Role & Size | Font Weight | Font Size (sp) | Line Height (sp) | Letter Spacing (sp) | Best Used For |
| --- | --- | --- | --- | --- | --- |
| **Display Large** | Regular (400) | 57 | 64 | -0.25 | Splash banners, heroic numeric readouts |
| **Display Medium** | Regular (400) | 45 | 52 | 0.0 | Expressive dashboard highlights |
| **Display Small** | Regular (400) | 36 | 44 | 0.0 | Short promotional slogans |
| **Headline Large** | Regular (400) | 32 | 40 | 0.0 | Top of screen page titles |
| **Headline Medium**| Regular (400) | 28 | 36 | 0.0 | LargeTopAppBar expanded titles |
| **Headline Small** | Regular (400) | 24 | 32 | 0.0 | Modal and bottom sheet titles |
| **Title Large** | Regular (400) | 22 | 28 | 0.0 | Standard TopAppBar collapsed title |
| **Title Medium** | Medium (500) | 16 | 24 | +0.15 | Card section headers, list group titles |
| **Title Small** | Medium (500) | 14 | 20 | +0.1 | Sub-headers, dense table titles |
| **Body Large** | Regular (400) | 16 | 24 | +0.5 | Primary article text, message content |
| **Body Medium** | Regular (400) | 14 | 20 | +0.25 | Secondary list subtitles, descriptions |
| **Body Small** | Regular (400) | 12 | 16 | +0.4 | Footers, timestamps, legal copy |
| **Label Large** | Medium (500) | 14 | 20 | +0.1 | Primary button text, tab bar labels |
| **Label Medium** | Medium (500) | 12 | 16 | +0.5 | Assist chips, status badges |
| **Label Small** | Medium (500) | 11 | 16 | +0.5 | Caption tags, bottom nav micro-labels |

---

## 3. Material 3 Expressive Principles

In M3 Expressive, typography ceases to be merely a carrier of text—it drives emotional engagement:

1. **Dramatic Scale Contrast:** Pair oversized headlines (`Display Small` or `Headline Large`) directly with tight, crisp meta information (`Label Small`) to establish instant visual hierarchy.
2. **Variable Weight Modulation:** In hero sections or At a Glance cards, vary font weight dynamically (e.g. bold numbers paired with regular unit labels).
3. **No All-Caps Buttons:** Unlike Material 1 (which used ALL CAPS button labels), Material 3 uses **Sentence Case** or **Title Case** (`Save changes`, not `SAVE CHANGES`). All-caps buttons look outdated and aggressive.

---

## 4. Audit Checklist

- [ ] **Scale Tokens Used:** Are text styles referencing `MaterialTheme.typography.titleMedium` instead of arbitrary font sizes (e.g. `fontSize = 15.sp`)?
- [ ] **Sentence Case on Buttons:** Are buttons formatted in sentence case?
- [ ] **Line-Height Proportions:** Does multi-line text maintain a line-height at least $1.3\times$ to $1.5\times$ the font size to ensure comfortable readability?
- [ ] **Font Weight Limits:** Avoid ultra-thin (100–200) weights for any text below $24\,\text{sp}$ as it vanishes on low-contrast screens.
