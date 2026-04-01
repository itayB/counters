# Family Countdowns

A personal countdown timer PWA for special family events. Two-panel split-screen layout with unique themed visuals for each event.

**Live:** https://itayb.github.io/counters/

## Features

- Split-screen layout: one-time milestones (left) and recurring annual events (right)
- Each event has a unique color theme, animated particles, and decorations
- Psychology-driven "nudge metrics" (workdays, weekends, sleeps) to reframe urgency
- PWA — add to iPhone home screen for full-screen app experience
- Mobile responsive with tab switcher
- No server, no build step — pure HTML/CSS/JS

## Make It Yours

Want your own countdown page? It takes 2 minutes:

1. **Fork** this repo (or click "Use this template")
2. **Edit one file** — `events.js` — replace the events with your own
3. **Enable GitHub Pages** — go to Settings > Pages > Source: `master` branch, root `/`
4. **Done!** Your page is live at `https://<your-username>.github.io/counters/`

On your iPhone, open the URL in Safari and tap **Share > Add to Home Screen** for a full-screen app experience.

### events.js — the only file you need to change

All events live in `events.js`. There are two categories:

**One-time events** (fixed date):
```js
{
  id: "my-wedding",           // unique slug (lowercase, hyphens)
  title: "My Wedding",        // displayed title
  subtitle: "The big day",    // italic tagline below title
  date: "2026-06-15T16:00:00", // ISO date+time
  dateDisplay: "June 15, 2026 · 16:00", // shown on screen
  theme: "anniversary",       // color theme (see below)
  particleColor: "rgba(232, 93, 117, ALPHA)", // copy from theme
  decoration: "hearts"        // visual flair (see below)
}
```

**Recurring events** (annual, auto-calculates next occurrence):
```js
{
  id: "dad-birthday",
  title: "Dad's Birthday",
  subtitle: "Happy birthday!",
  month: 3,                   // March
  day: 22,                    // 22nd
  dateDisplay: "March 22",
  theme: "birthday",
  particleColor: "rgba(34, 180, 160, ALPHA)",
  decoration: "balloons"
}
```

### Available themes

`trip` (navy/amber), `bar` (purple/gold), `retirement` (sunset/orange), `anniversary` (rose/crimson), `birthday` (teal/emerald), `jonathan` (electric blue), `wife` (blush pink)

### Available decorations

`airplane`, `stars`, `sun`, `hearts`, `balloons`, `snowflakes`, or `null` for none

## Adding / Removing Events via GitHub Actions

No code editing needed — use the built-in workflows:

1. Go to the **Actions** tab in your repo
2. Select **"Add Event"** or **"Remove Event"**
3. Fill in the form and run the workflow
4. A PR is created automatically — merge it to deploy

## Local Development

No dependencies. Just open `index.html` in a browser, or:

```
npx serve .
```
