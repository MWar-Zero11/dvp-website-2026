# Page View Counter — Design Spec

**Date:** 2026-03-16
**Project:** DynamicVibe Productions Website

---

## Overview

Add a visible page view counter to the footer of every page on the DVP website. Each page displays its own independent hit count (today / total) via an embedded SVG badge from hits.seeyoufarm.com.

---

## Goals

- Show visitors how many times each page has been viewed
- Zero maintenance: no server, no database, no JS
- Visual style matches the existing dark DVP theme

---

## Approach

Use [hits.seeyoufarm.com](https://hits.seeyoufarm.com) — a free, hosted hit counter service. Each page gets a unique slug. The counter is embedded as a single `<img>` tag. The service increments the count on every page load and returns a styled SVG badge showing "today | total" views.

---

## Pages & Counter Slugs

| Page | File | Slug |
|------|------|------|
| Home | `index.html` | `dvp-home` |
| SRT Maker | `srt-maker/index.html` | `dvp-srt-maker` |
| CineScan | `cinescan.html` | `dvp-cinescan` |
| Consistency Keeper | `consistency-keeper.html` | `dvp-consistency-keeper` |
| Music Maker | `music-maker/index.html` | `dvp-music-maker` |
| CinePrompt | `cineprompt/index.html` | `dvp-cineprompt` |
| JSON Prompt | `json-prompt/index.html` | `dvp-json-prompt` |
| Hero Preview | `hero-preview.html` | `dvp-hero-preview` |

---

## Implementation

### Badge URL pattern

```
https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.co%2F{slug}&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true
```

Parameters:
- `url` — unique identifier per page (using the slug as a path)
- `count_bg` — `#ff2d78` (DVP pink) for the count value background
- `title_bg` — `#0d1929` (DVP card dark) for the label background
- `icon` — eye icon
- `icon_color` — `#6e8aaa` (DVP muted)
- `title` — "Views"
- `edge_flat` — flat/square style to match modern aesthetic

### Footer placement

Each page's existing footer gets a new line:

```html
<div class="flex items-center justify-center gap-2 mt-4 text-dvp-muted text-sm">
  <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=...&..."
       alt="Page views" />
</div>
```

Centered, subtle, sits below existing footer content.

---

## Constraints

- Static site — no build step, no JS framework
- Hosted on Netlify
- All pages use Tailwind CSS via CDN
- No new dependencies introduced

---

## Out of Scope

- Private analytics dashboard
- Unique visitor tracking
- Click or download tracking
- Aggregated cross-page stats

---

## Success Criteria

- All 8 pages show a view count badge in the footer
- Badge increments on each page load
- Badge colors match DVP theme
- No layout disruption to existing footer content
