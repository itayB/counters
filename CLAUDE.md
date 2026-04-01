# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Family Countdowns — a data-driven PWA that displays real-time countdown timers for personal family events. Vanilla HTML/CSS/JS with no build step, no frameworks, no server. Hosted on GitHub Pages at https://itayb.github.io/counters/.

## Architecture

**Split-screen layout** with two independently scrollable panels:
- Left panel: one-time events (trips, milestones)
- Right panel: recurring annual events (birthdays, anniversaries)
- Mobile (<768px): collapses to tab-switched single panel

**Data flow:** `events.js` (global `EVENTS` object) → `buildSection()` generates HTML → inserted into panel containers → `updateCountdowns()` runs every 1s.

### Key Files

| File | Role |
|------|------|
| `events.js` | **Single source of truth** for all events. Edit this to add/change events. |
| `index.html` | Everything else: styles, layout, rendering logic, countdown engine, particles |
| `manifest.json` | PWA config (standalone display, icons, theme) |
| `.github/workflows/add-event.yml` | GitHub Action: form-based event addition via PR |
| `.github/workflows/remove-event.yml` | GitHub Action: form-based event removal via PR |

### Event Object Shape

**One-time events** have a fixed `date` (ISO string). **Recurring events** have `month` + `day` and auto-calculate the next occurrence via `getNextOccurrence()`.

Both types share: `id`, `title`, `subtitle`, `dateDisplay`, `theme` (CSS class), `particleColor` (RGBA with `ALPHA` placeholder), `decoration` (airplane/stars/sun/hearts/balloons/snowflakes/null).

### Theme System

7 color themes defined in CSS: `trip`, `bar`, `retirement`, `anniversary`, `birthday`, `jonathan`, `wife`. Each theme has gradient backgrounds, shimmer title animation, glow text-shadows, and matching particle colors. Theme is applied via `${theme}-section` CSS class.

### Nudge Metrics

`computeNudge(totalDays)` auto-selects a psychology-driven secondary unit (workdays, weekends, sleeps) based on time remaining. No configuration needed — fully automatic.

## Development

No build, no install. Just open `index.html` in a browser (works with `file://`).

To test with a local server: `npx serve .`

Live site deploys automatically via GitHub Pages on push to `master`.

## Adding/Removing Events

**Via GitHub Actions** (preferred): Go to repo Actions tab → "Add Event" or "Remove Event" → fill form → merges as PR.

**Via code**: Edit `events.js` directly. Add to `EVENTS.onetime[]` or `EVENTS.recurring[]`. Use an existing event as template. The `id` must be unique and URL-safe (lowercase, hyphens).

## Conventions

- Branch: `master` (not main)
- All event IDs are kebab-case slugs used as DOM ID prefixes (`{id}-days`, `{id}-hours`, etc.)
- Particle colors use `ALPHA` placeholder string, replaced at runtime with actual opacity
- CSS is organized: reset → layout → theme sections → shared styles → mobile breakpoint
- GitHub Action inputs use environment variables (not direct interpolation) for security
