# HWC Landing Pages — Project briefing

## What this is

Static HTML landing pages for Hawaii Wellness Clinic, deployed to Vercel at `hwc-landing-pages.vercel.app`.

Pages live in subfolders:
- [`mental-health/`](./mental-health/) — TMS, Ketamine IV, SGB, Esketamine
- [`wellness/`](./wellness/) — IV Therapy, NAD+, Peptides, BHRT
- [`pain-joint/`](./pain-joint/) — Regenerative therapies, Shockwave, Laser
- [`weight-loss/`](./weight-loss/) — Semaglutide, Tirzepatide, Retatrutide
- [`book/`](./book/) — GHL form embed (booking)
- [`aloha/`](./aloha/) — link-in-bio replacement for linktr.ee (deployed 2026-05-16)
- [`/`](./index.html) — dev-hub with all pages listed

## Tech stack

- Vanilla HTML/CSS/JS — no build, no framework, no React
- Google Fonts CDN (Playfair Display + Inter)
- Vercel auto-deploys main branch
- GHL form embed for booking (form ID `YTmOGFzuBxKThJA0bnz3`)

## Brand tokens (CSS custom properties)

```
--ocean-dark: #0d2f42
--ocean: #1b4f6e
--teal: #3aaea0
--teal-light: #a8d8d3
--coral: #e07a5f
--sand: #f5ede0
--white: #fdfcfa
```

Fonts: Playfair Display (serif, headings), Inter (sans, body). 300/400/500 weights.

## Conventions

- Mobile-first: design for 390px iPhone 14 Pro first, scale up
- Brand colors via `var(--token)` only — never hardcode hex in components
- Logo lives at `/mental-health/logo.png` (legacy path, shared across pages)
- Hero images per-page in each service folder
- `prefers-reduced-motion` respected on every animation
- Lite-video pattern for embedded Vimeo (no iframe until click)
- `position: fixed` background with parallax → use safe bounds (`top: -200px; bottom: -1200px`) per `safe-parallax` skill

## Crew-learnings convention (added 2026-05-18)

This project is linked to a **crew-template** at `~/Documents/Code Projects/crew-template/` — the harvester that extracts reusable skills from this project's work. When you discover patterns, gotchas, hacks, or tools while working here — **write a short note in `.crew-learnings/`** so the crew-template session can harvest them later.

### How to write a learning

1. Create file `.crew-learnings/YYYY-MM-DD-<short-slug>.md`
2. Use this template:

   ```markdown
   ---
   date: YYYY-MM-DD
   project: HWC-Landing-pages
   tags: [<tag1>, <tag2>]
   type: skill | hack | gotcha | pattern | tool
   ---

   ## What
   One paragraph — what happened.

   ## Why it matters
   One line — why future-me would care.

   ## Next time
   Concrete advice.

   ## Link (optional)
   commit hash / file path / URL
   ```

### When to write a learning

- ✅ Built a reusable pattern (glassmorphism card, lite-video loader, brand binding)
- ✅ Found a non-obvious bug / its root cause (e.g. iOS Safari `position: fixed` seam)
- ✅ Hardcoded something that should be config-driven (tag as `hack`)
- ✅ Tried a new tool / library / API that worked (tag as `tool`)
- ✅ Noticed work pattern repeating across pages (tag as `pattern`)

### When NOT to write

- ❌ For routine commits (commit message is enough)
- ❌ For temporary today-only context (TODO lists)
- ❌ Just a bookmark without your own takeaway
- ❌ Anything containing secrets / tokens / PII / patient data

### Rules

- One learning = one file (don't batch)
- Date in filename (YYYY-MM-DD-slug.md) — sorts chronologically + avoids collisions
- Never edit old learnings (add new ones if you learn more)
- 4 lines is fine. Crew-template session polishes them later.

### Where this goes

Crew-template session periodically runs `/audit HWC-Landing-pages` which reads `.crew-learnings/` and:
- Promotes `type: skill` to `crew-template/skills/mine/`
- Files `type: hack` in `crew-template/archetypes/landing-funnel/improvements.md`
- Saves `type: gotcha` in `crew-template/archetypes/landing-funnel/memory/MEMORY.md`
- Tracks `type: pattern` for skill extraction after 2+ instances
- Adds `type: tool` to `crew-template/connectors/` if applicable

Files in `.crew-learnings/` are NEVER deleted by the harvester — they're the historical record.

## Conversion model

The **only** conversion path on every landing is the embedded GHL form (form ID `YTmOGFzuBxKThJA0bnz3`). GHL captures lead source from UTM parameters on inbound links — so lead-source data lives in the GHL CRM, not in any on-site analytics. No Vercel Analytics, GA, PostHog, or A/B testing infra is used or wanted. When prioritizing work, focus on form discoverability, page speed, copy clarity, mobile UX, and SEO — not measurement.

## Pending work

| # | Item | Priority |
|---|---|---|
| 1 | Vimeo IDs → `videos.json` config | HIGH |
| 2 | Socials/phone/addresses → `brand-config.json` | MED |
| 3 | Consolidate `/assets/` folder | LOW |

Plus: waiting on Philip for DNS CNAME `aloha.hawaiiwellnessclinic.com → cname.vercel-dns.com`.
