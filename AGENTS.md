# Agent Operational Guide: Google Pixel & M3 Expressive Design

This repository houses the **Google Pixel Design Skill** (`google-pixel-design-skill`).

## Review Protocol for AI Coding Assistants
1. **Triggering:** Activate whenever a user asks to review, audit, critique, or build UI/UX for Android, Pixel devices, Flutter, React Native, or Web apps, or asks to "make this feel like a native Google Pixel app" or adhere to Material 3 Expressive guidelines.
2. **Guidelines Loading:**
   - Always read `references/foundations/accessibility.md`, `references/foundations/dynamic-color.md`, `references/foundations/typography.md`, and `references/foundations/elevation-and-surfaces.md`.
   - Use `references/lookup.md` to identify and load 3 to 6 matching files for the specific components on screen.
   - For non-native Android targets, consult `references/cross-platform.md`.
3. **Execution Rules:**
   - Ground all feedback in citations (`references/... › Section`).
   - Give exact numbers: minimum 48x48dp touch bounds, contrast ratios, tonal container tiers.
   - Enforce Material You dynamic color tokens over hardcoded hex values.
   - Deliver fixes as drop-in code snippets following the standard report format in `SKILL.md`.
