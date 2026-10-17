# At a Glance: Smart Contextual Surfaces

> Pixel surface reference for Google Pixel & Material 3 Expressive.

**At a Glance** is Google Pixel's signature proactive information hub, prominently positioned at the top of the Pixel Launcher home screen, Always-On Display (AOD), and Lock Screen.

---

## 1. Contextual Philosophy

At a Glance surfaces information **only when it is urgently relevant**:
- **Default State:** Day, date, and current weather icon with localized temperature.
- **Dynamic Preemptions:**
  - 30 minutes before a calendar event $\rightarrow$ Meeting title + location.
  - Commute hours $\rightarrow$ Traffic delay alert + estimated travel time.
  - Flight day $\rightarrow$ Gate number, boarding pass barcode shortcut.
  - Active food delivery / rideshare $\rightarrow$ Live tracking status + ETA countdown.
  - Severe weather alert $\rightarrow$ Urgent storm/tornado warning card.

---

## 2. Anatomy & Typography

- **Date Line:** `Title Medium` ($16\,\text{sp}$) in Google Sans Medium.
- **Weather Glyph:** Custom vector weather iconography paired with temperature in `Title Large` ($22\,\text{sp}$).
- **Card Pills:** Expanding contextual alerts use `surfaceContainerHigh` or transparent pill chips with high-contrast text (`onSurface`).
- **One-Touch Actions:** Tapping any segment routes directly into the underlying service (e.g. Google Calendar, Google Weather, Google Maps).

---

## 3. Third-Party App Integration (Live Updates)

Under Android 14–17, third-party apps surface dynamic progress into At a Glance and lock screen notifications:
1. **Concise Summary:** Limit title to 30 characters and subtitle to 45 characters.
2. **Real-Time Progress:** Include a live progress bar or countdown timer rather than frequent static push updates.
3. **Glanceability:** The user must grasp the core status in under **1.5 seconds**.

---

## 4. Audit Checklist

- [ ] Is information prioritized by temporal urgency rather than marketing push?
- [ ] Are tap targets cleanly divided so tapping the weather opens weather, while tapping a meeting opens calendar?
- [ ] Are icons vector-based and crisp under dynamic font scaling?
