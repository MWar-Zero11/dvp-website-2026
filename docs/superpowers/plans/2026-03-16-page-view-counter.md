# Page View Counter Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a hits.seeyoufarm.com view-count badge to the footer of all 8 pages on the DynamicVibe Productions website.

**Architecture:** Each page gets a single `<img>` tag inserted as the last child of its `<footer>` element. The badge URL encodes a unique counter key per page. No JS, no server, no build step. `hero-preview.html` requires a new `<footer>` to be created first.

**Tech Stack:** Plain HTML, inline CSS, hits.seeyoufarm.com free badge service.

---

## Reference: Badge snippet

Every page uses the same wrapper pattern with a page-specific `url=` value and `alt` text. Full badge URLs are given per task — do not guess them.

```html
<div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
  <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url={ENCODED_URL}&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
       alt="{ALT TEXT}" />
</div>
```

Insert this as the **last child inside `<footer>`**, before the closing `</footer>` tag.

---

## Chunk 1: Pages 1–4

### Task 1: Add badge to `index.html`

**Files:**
- Modify: `index.html:1462` (insert before `</footer>` on line 1463)

Context — the footer ends with:
```html
      <p class="text-xs" style="color:#1e3050;">Video Editor &amp; AI Training Specialist</p>
    </div>
  </div>
</footer>
```

- [ ] **Step 1: Insert badge as last child of `<footer>`**

Replace the closing `</footer>` with:

```html
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2F&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for Home" />
  </div>
</footer>
```

- [ ] **Step 2: Verify the HTML**

Open `index.html` in a browser. Scroll to the footer. Confirm:
- A badge appears in the footer
- Badge shows "Views" label with a count
- Badge colors: dark label background, pink count background
- No layout breakage

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "Add page view counter badge to Home footer"
```

---

### Task 2: Add badge to `srt-maker/index.html`

**Files:**
- Modify: `srt-maker/index.html:423` (insert before `</footer>` on line 424)

Context — the footer ends with:
```html
      SRT Maker is a free tool by <a href="../index.html" ...>Dynamic Vibe Productions</a>.
      Powered by <a href="..." ...>OpenAI Whisper</a>.
    </p>
  </footer>
```

- [ ] **Step 1: Insert badge as last child of `<footer>`**

Replace `  </footer>` (line 424) with:

```html
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2Fsrt-maker%2F&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for SRT Maker" />
  </div>
  </footer>
```

- [ ] **Step 2: Verify the HTML**

Open `srt-maker/index.html` in a browser. Scroll to the footer. Confirm badge appears with correct colors and no layout breakage.

- [ ] **Step 3: Commit**

```bash
git add srt-maker/index.html
git commit -m "Add page view counter badge to SRT Maker footer"
```

---

### Task 3: Add badge to `cinescan.html`

**Files:**
- Modify: `cinescan.html:1089` (insert before `</footer>` on line 1090)

Context — the footer ends with:
```html
      </div>
    </div>
  </div>
</footer>
```

- [ ] **Step 1: Insert badge as last child of `<footer>`**

Replace `</footer>` (line 1090) with:

```html
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2Fcinescan%2F&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for CineScan" />
  </div>
</footer>
```

- [ ] **Step 2: Verify the HTML**

Open `cinescan.html` in a browser. Scroll to the footer. Confirm badge appears with correct colors and no layout breakage.

- [ ] **Step 3: Commit**

```bash
git add cinescan.html
git commit -m "Add page view counter badge to CineScan footer"
```

---

### Task 4: Add badge to `consistency-keeper.html`

**Files:**
- Modify: `consistency-keeper.html:969` (insert before `</footer>` on line 970)

Context — the footer ends with:
```html
      <a href="https://dynamicvibe.net/cineprompt/" class="footer-link">← CinePrompt</a>
    </div>
  </div>
</footer>
```

- [ ] **Step 1: Insert badge as last child of `<footer>`**

Replace `</footer>` (line 970) with:

```html
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2Fconsistency-keeper%2F&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for Consistency Keeper" />
  </div>
</footer>
```

- [ ] **Step 2: Verify the HTML**

Open `consistency-keeper.html` in a browser. Scroll to the footer. Confirm badge appears with correct colors and no layout breakage.

- [ ] **Step 3: Commit**

```bash
git add consistency-keeper.html
git commit -m "Add page view counter badge to Consistency Keeper footer"
```

---

## Chunk 2: Pages 5–8

### Task 5: Add badge to `music-maker/index.html`

**Files:**
- Modify: `music-maker/index.html:746` (insert before `</footer>` on line 747)

Context — the footer ends with:
```html
    <a href="https://aistudio.google.com" target="_blank">Get API Key</a>
    &nbsp;&nbsp;·&nbsp;&nbsp;
    <span style="color:#2a3d55;">Lyria RealTime · lyria-realtime-exp</span>
  </footer>
```

- [ ] **Step 1: Insert badge as last child of `<footer>`**

Replace `  </footer>` (line 747) with:

```html
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2Fmusic-maker%2F&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for Music Maker" />
  </div>
  </footer>
```

- [ ] **Step 2: Verify the HTML**

Open `music-maker/index.html` in a browser. Scroll to the footer. Confirm badge appears with correct colors and no layout breakage.

- [ ] **Step 3: Commit**

```bash
git add music-maker/index.html
git commit -m "Add page view counter badge to Music Maker footer"
```

---

### Task 6: Add badge to `cineprompt/index.html`

**Files:**
- Modify: `cineprompt/index.html:1122`

Context — the entire footer is a single line:
```html
  <footer>Built by <a href="../index.html" style="color:var(--gold);text-decoration:none;transition:opacity 0.2s;" onmouseover="this.style.opacity='.7'" onmouseout="this.style.opacity='1'">DynamicVibe Productions</a> &nbsp;·&nbsp; CinePrompt 2026 &nbsp;·&nbsp; Kling · Runway · Nano Banana · Midjourney · Seedance</footer>
```

This is a single-line footer — split it to insert the badge before `</footer>`.

- [ ] **Step 1: Replace the single-line footer**

Replace the entire line with:

```html
  <footer>Built by <a href="../index.html" style="color:var(--gold);text-decoration:none;transition:opacity 0.2s;" onmouseover="this.style.opacity='.7'" onmouseout="this.style.opacity='1'">DynamicVibe Productions</a> &nbsp;·&nbsp; CinePrompt 2026 &nbsp;·&nbsp; Kling · Runway · Nano Banana · Midjourney · Seedance
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2Fcineprompt%2F&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for CinePrompt" />
  </div>
  </footer>
```

- [ ] **Step 2: Verify the HTML**

Open `cineprompt/index.html` in a browser. Scroll to the footer. Confirm:
- Original footer text ("Built by DynamicVibe...") is preserved
- Badge appears below footer text
- No layout breakage

- [ ] **Step 3: Commit**

```bash
git add cineprompt/index.html
git commit -m "Add page view counter badge to CinePrompt footer"
```

---

### Task 7: Add badge to `json-prompt/index.html`

**Files:**
- Modify: `json-prompt/index.html:1372` (insert before `</footer>` on line 1373)

Context — the footer ends with:
```html
  <footer>
    Built by <a href="../index.html">DynamicVibe Productions</a> &middot; NanoBanana 2 JSON Builder 2026 &middot; Runs entirely in your browser &middot; No API calls
  </footer>
```

- [ ] **Step 1: Insert badge as last child of `<footer>`**

Replace `  </footer>` (line 1373) with:

```html
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2Fjson-prompt%2F&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for JSON Prompt" />
  </div>
  </footer>
```

- [ ] **Step 2: Verify the HTML**

Open `json-prompt/index.html` in a browser. Scroll to the footer. Confirm badge appears with correct colors and no layout breakage.

- [ ] **Step 3: Commit**

```bash
git add json-prompt/index.html
git commit -m "Add page view counter badge to JSON Prompt footer"
```

---

### Task 8: Add badge to `hero-preview.html`

**Files:**
- Modify: `hero-preview.html:315` (insert new footer before `</body>`)

Context — the file currently ends with no footer:
```html
</section>

</body>
</html>
```

This page has no footer. One must be created.

- [ ] **Step 1: Insert new footer before `</body>`**

Replace `</body>` with:

```html
<footer style="padding:24px;text-align:center;">
  <div style="display:flex;align-items:center;justify-content:center;gap:8px;margin-top:16px;">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fdynamicvibe.net%2Fhero-preview.html&count_bg=%23ff2d78&title_bg=%230d1929&icon=eye.svg&icon_color=%236e8aaa&title=Views&edge_flat=true"
         alt="Page view count for Hero Preview" />
  </div>
</footer>
</body>
```

- [ ] **Step 2: Verify the HTML**

Open `hero-preview.html` in a browser. Scroll to the bottom. Confirm:
- A footer area appears at the bottom of the page
- Badge is visible with correct colors
- No layout breakage to the hero section above

- [ ] **Step 3: Commit**

```bash
git add hero-preview.html
git commit -m "Add page view counter badge to Hero Preview (new footer)"
```

---

## Chunk 3: Final verification

### Task 9: Verify all 8 pages

- [ ] **Step 1: Check all 8 files have badge img tags**

Run:
```bash
grep -l "hits.seeyoufarm.com" index.html srt-maker/index.html cinescan.html consistency-keeper.html music-maker/index.html cineprompt/index.html json-prompt/index.html hero-preview.html
```

Expected output: all 8 filenames listed.

- [ ] **Step 2: Check each badge has a unique counter key**

Run:
```bash
grep -h "hits.seeyoufarm.com" index.html srt-maker/index.html cinescan.html consistency-keeper.html music-maker/index.html cineprompt/index.html json-prompt/index.html hero-preview.html | grep -oP 'url=[^&]+' | sort
```

Expected: 8 unique `url=` values, one per page.

- [ ] **Step 3: Check all badges have per-page alt text**

Run:
```bash
grep -h 'alt="Page view count' index.html srt-maker/index.html cinescan.html consistency-keeper.html music-maker/index.html cineprompt/index.html json-prompt/index.html hero-preview.html
```

Expected: 8 lines, each with a unique page name.

- [ ] **Step 4: Check hero-preview.html has a footer element**

Run:
```bash
grep -c "<footer" hero-preview.html
```

Expected: `1`

- [ ] **Step 5: Final commit**

```bash
git status
```

All files should already be committed from Tasks 1–8. If any are not:
```bash
git add -u
git commit -m "Add page view counter badges to all pages"
```
