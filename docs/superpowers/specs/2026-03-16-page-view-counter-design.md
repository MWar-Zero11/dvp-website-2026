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

Use [hits.seeyoufarm.com](https://hits.seeyoufarm.com) — a free, hosted hit counter service. The counter is embedded as a single `<img>` tag per page. The service increments the count every time the `<img>` tag is fetched (i.e., on every page load) and returns a styled SVG badge showing "today | total" views.

**How the counter key works:** The `url=` query parameter is an opaque string key that uniquely identifies each counter. The service does not validate this value against the live site or use the HTTP referrer header — it is purely a unique identifier. The counter increments whenever the `<img>` tag loads, regardless of Netlify's URL rewriting behavior (pretty URLs, `.html` redirects, etc.).

The existing `Referrer-Policy: strict-origin-when-cross-origin` header in `netlify.toml` does not affect counter attribution.

---

## Pages & Counter Keys

Each page uses its file path appended to the site domain as its counter key. This keeps keys human-readable and consistent with the project structure.

| Page | File | Counter key (`url=`) |
|------|------|----------------------|
| Home | `index.html` | `https://dynamicvibe.net/` |
| SRT Maker | `srt-maker/index.html` | `https://dynamicvibe.net/srt-maker/` |
| CineScan | `cinescan.html` | `https://dynamicvibe.net/cinescan/` |
| Consistency Keeper | `consistency-keeper.html` | `https://dynamicvibe.net/consistency-keeper/` |
| Music Maker | `music-maker/index.html` | `https://dynamicvibe.net/music-maker/` |
| CinePrompt | `cineprompt/index.html` | `https://dynamicvibe.net/cineprompt/` |
| JSON Prompt | `json-prompt/index.html` | `https://dynamicvibe.net/json-prompt/` |
| Hero Preview | `hero-preview.html` | `https://dynamicvibe.net/hero-preview.html` |

---

## Implementation

### Badge URL pattern

```
https://hits.seeyoufarm.com/api/count/incr/badge.svg?url={ENCODED_KEY}&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true
```

Parameters:
- `url` — URL-encoded counter key from the table above
- `count_bg` — `#ff2d78` (DVP pink) for the count value background
- `title_bg` — `#0d1929` (DVP card dark) for the label background
- `icon` — eye icon
- `icon_color` — `#6e8aaa` (DVP muted)
- `title` — "Views"
- `edge_flat` — flat/square style

### Footer snippet

Inline styles are used throughout for cross-page compatibility. Three pages (`index.html`, `srt-maker/index.html`, `hero-preview.html`) load the Tailwind CDN; five do not. Inline styles ensure consistent rendering without dependencies.

```html
<div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
  <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url={ENCODED_KEY}&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
       alt="Page view count for {Page Name}" />
</div>
```

The `alt` text is descriptive and unique per page (e.g., `alt="Page view count for SRT Maker"`).

### Per-page footer notes

In all cases, the snippet is inserted as the **last child inside `<footer>`** (before `</footer>`), not after the closing tag.

- **index.html** — existing `<footer>`; insert snippet as last child. `alt="Page view count for Home"`
- **srt-maker/index.html** — existing `<footer>`; insert snippet as last child. `alt="Page view count for SRT Maker"`
- **cinescan.html** — existing `<footer>`; insert snippet as last child. `alt="Page view count for CineScan"`
- **consistency-keeper.html** — existing `<footer>`; insert snippet as last child. `alt="Page view count for Consistency Keeper"`
- **music-maker/index.html** — existing `<footer>`; insert snippet as last child. `alt="Page view count for Music Maker"`
- **cineprompt/index.html** — existing `<footer>`; insert snippet as last child. `alt="Page view count for CinePrompt"`
- **json-prompt/index.html** — existing `<footer>`; insert snippet as last child. `alt="Page view count for JSON Prompt"`
- **hero-preview.html** — **no footer exists**; create `<footer style="padding:24px;text-align:center;"></footer>` immediately before `</body>`, then insert snippet as its only child. `alt="Page view count for Hero Preview"`

---

## Constraints

- Static site — no build step, no JS framework
- Hosted on Netlify
- Inline styles used for badge wrapper for cross-page compatibility
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
- Each badge uses a unique, consistent counter key
- Badge increments on each page load
- Badge colors match DVP theme (`#ff2d78` pink count, `#0d1929` dark label)
- Each badge has a descriptive, per-page `alt` attribute
- No layout disruption to existing footer content
- `hero-preview.html` has a footer created to house the badge
