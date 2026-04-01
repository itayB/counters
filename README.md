# Family Countdowns

A personal countdown timer PWA for special family events. Two-panel split-screen layout with unique themed visuals for each event.

**Live:** https://itayb.github.io/counters/

## Features

- Split-screen layout: one-time milestones (left) and recurring annual events (right)
- Each event has a unique color theme, animated particles, and decorations
- Psychology-driven "nudge metrics" (workdays, weekends, sleeps) to reframe urgency
- PWA — add to iPhone home screen for full-screen app experience
- Mobile responsive with tab switcher

## Adding / Removing Events

Use the GitHub Actions workflows (no code needed):

1. Go to the **Actions** tab
2. Select **"Add Event"** or **"Remove Event"**
3. Fill in the form and run the workflow
4. A PR is created automatically — merge it to deploy

Or edit `events.js` directly.

## Local Development

No build step, no dependencies. Just open `index.html` in a browser.

```
npx serve .
```

## Tech

Vanilla HTML/CSS/JS. No frameworks. Hosted on GitHub Pages.
