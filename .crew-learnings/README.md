# `.crew-learnings/` — breadcrumbs for the harvester

Short markdown notes written by THIS project's work sessions. Read by the **crew-template** harvester session (`~/Documents/Code Projects/crew-template/`) during `/audit HWC-Landing-pages`.

## Quick rules (full spec in `../CLAUDE.md`)

- File name: `YYYY-MM-DD-<short-slug>.md`
- Frontmatter: `date`, `project`, `tags`, `type` (one of: `skill` / `hack` / `gotcha` / `pattern` / `tool`)
- Body: `What` / `Why it matters` / `Next time` / optional `Link`
- One learning per file. 4 lines minimum. Polish is the harvester's job.
- Never edit old files. Add new ones.
- No secrets, no PII.

## What gets created here (by harvester, not you)

After each `/audit`, the harvester drops `.last-audit-YYYY-MM-DD.md` here as a marker for "where to resume next time". Don't move or delete these.

## Currently here

| File | Type | Status |
|---|---|---|
| _none yet — first project-session learning starts the file pile_ | — | — |

## Examples (for inspiration, not actual learnings)

```markdown
---
date: 2026-05-17
project: HWC-Landing-pages
tags: [css, parallax, ios, bug]
type: gotcha
---

## What
iOS Safari + `position: fixed` background + parallax `translateY` exposes empty viewport
edge at the bottom of long pages.

## Why it matters
Anyone doing a fullscreen photo backdrop on a long landing will hit this.

## Next time
Use the `safe-parallax` skill from crew-template: extend bg-hero past viewport with
`top: -200px; bottom: -1200px;` and `transform: scale(1.05)`.

## Link
commit bffae1d
```

```markdown
---
date: 2026-05-17
project: HWC-Landing-pages
tags: [vimeo, thumbnail, third-party]
type: tool
---

## What
Used `vumbnail.com/<vimeo_id>.jpg` as a free thumbnail proxy for Vimeo videos
without needing API auth.

## Why it matters
Lets us do lite-video loaders (placeholder image + click → iframe) without paying for
Vimeo API or building our own thumbnail cache.

## Next time
Risk: single point of failure (vumbnail.com). For production-critical posters,
use Vimeo oEmbed once at build time and save the thumbnail to repo instead.

## Link
aloha/index.html data-thumb attribute
```
