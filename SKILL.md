---
name: personal-portfolio-website
description: Build and maintain a bold, modern personal portfolio website using Next.js, React, Tailwind CSS, and vanilla HTML/CSS/JS where needed. Use this skill for any task involving creating pages, components, layouts, animations, or content for the portfolio site. Trigger whenever the user mentions their website, portfolio, pages, sections, components, or design work related to this project.
---

# Personal Portfolio Website Skill

This skill guides development of a bold, modern personal portfolio website. Every decision — layout, typography, animation, color — should feel intentional, confident, and memorable.

## Project Stack

- **Framework**: Next.js (App Router preferred)
- **UI Library**: React with functional components and hooks
- **Styling**: Tailwind CSS (utility-first, no inline styles unless necessary)
- **Extras**: Vanilla HTML/CSS/JS for isolated components or animations if needed

## Design Philosophy

This is a **bold, modern** portfolio. That means:

- **Strong typographic hierarchy** — large, commanding headings; use display fonts that have personality (e.g. Bebas Neue, Syne, Cabinet Grotesk, Clash Display). Never default to Inter or Roboto.
- **High contrast** — dark backgrounds with electric accents (e.g. neon green `#00FF87`, electric blue `#3D5AFE`, hot coral `#FF4D4D`) OR stark white with deep black type and a single vivid accent.
- **Motion with purpose** — entrance animations, scroll reveals, hover states that feel reactive and alive. Use Framer Motion for React animations.
- **Grid-breaking layouts** — asymmetry, oversized elements, overlapping layers. Avoid boring centered columns.
- **Whitespace as a tool** — use generous spacing to let bold elements breathe.

## Site Structure

Assume the following standard portfolio sections unless the user specifies otherwise:

1. **Hero** — Full-screen, commanding intro with name, title, and CTA
2. **About** — Brief personal story, photo, personality
3. **Work / Projects** — Case studies or project cards with hover interactions
4. **Skills** — Tech stack, tools, strengths
5. **Contact** — Simple, frictionless contact form or links

## Component Standards

- All components go in `/components/` and are named in PascalCase
- Pages go in `/app/` using the Next.js App Router convention
- Use `"use client"` directive only when interactivity or hooks are needed
- Keep components focused — one responsibility per component
- Use Tailwind classes exclusively for styling; avoid CSS modules unless animating complex keyframes

## Tailwind Usage Rules

- Use Tailwind's `@layer` utilities in `globals.css` for repeated custom patterns
- Prefer `clsx` or `cn()` utility for conditional class merging
- Responsive breakpoints: mobile-first (`sm:`, `md:`, `lg:`, `xl:`)
- Dark mode: use `dark:` variants if implementing theme toggle

## Animation Guidelines

- Use **Framer Motion** for page transitions, scroll animations, and component entrances
- Stagger children animations for lists and grids (creates polish)
- Keep durations snappy: `0.3s–0.6s` for UI, up to `1s` for hero reveals
- Avoid animating too many things at once — pick 1–2 focal points per section

## Performance & Accessibility

- Use `next/image` for all images (automatic optimization)
- Use `next/font` to load custom fonts (zero layout shift)
- All interactive elements must be keyboard-accessible
- Color contrast must meet WCAG AA minimum
- Semantic HTML: use `<header>`, `<main>`, `<section>`, `<nav>`, `<footer>` correctly

## Code Quality

- Write clean, readable code with descriptive variable/component names
- Add brief comments for non-obvious logic
- No unused imports or dead code
- Keep pages thin — logic lives in components or hooks, not page files

## Tone & Copy

When writing placeholder or suggested copy:
- First-person, confident, and direct ("I build things that matter." not "I am a developer who likes to build.")
- Short punchy sentences in hero sections
- Slightly more detail in About and Project descriptions
- Avoid clichés: "passionate developer", "team player", "detail-oriented"

## Example File Structure

```
/app
  layout.tsx
  page.tsx          ← Home (Hero + featured work)
  /about/page.tsx
  /work/page.tsx
  /contact/page.tsx

/components
  Navbar.tsx
  Hero.tsx
  ProjectCard.tsx
  AboutSection.tsx
  Footer.tsx

/public
  /images

/styles
  globals.css

tailwind.config.ts
next.config.ts
```
