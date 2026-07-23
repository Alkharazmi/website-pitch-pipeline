# Loop 2 — Plan sites + create repos

> For each approved lead: unique website plan, design system, page plans, and a GitHub repo under **Alkharazmi**.  
> Tag repos `pending-beta`.  
> **Stop after the first full plan** for Gate B before planning the rest of the batch.

---

## Paste into Claude Code

```text
/loop [auto]
/goal
# Loop 2 — Unique website plans + pending-beta repos

## Prerequisite
Gate A approved Excel at:
./nyc-leads/nyc-business-leads-batch-1.xlsx
Process only Fit Score ≥ 7, max 5 businesses in batch 1.
Stop after first completed plan repo and wait for human approval of that sample before continuing the rest.

## Objective
For each selected business, create a unique website plan package that would get the owner to the negotiation table. Aesthetics and clarity > deep functionality.

## Skills — MUST load and follow (not optional name-drops)
Design direction:
  - design-taste-frontend (brief inference + anti-slop)
  - impeccable (init design context / brand register for marketing sites)
  - high-end-visual-design OR minimalist-ui OR industrial-brutalist-ui
    (pick ONE lane per business; never reuse the same lane for two businesses in the batch)
  - ui-ux-pro-max (palette/type pairing suggestions)
  - brandkit when identity is weak
  - redesign-existing-projects when they have an old site
  - imagegen-frontend-web for section concept images when helpful
  - gstack /design-consultation → produce DESIGN.md
  - gstack /design-shotgun when two directions compete
  - diagram-design for user-flow diagram (unique per business)

Copy:
  - copywriting + ogilvy for positioning/headlines/CTAs
  - stop-slop on all long prose in briefs

Motion / components research:
  - gsap-skills plugin docs for motion plan (only if motion helps)
  - shadcn MCP for component inventory candidates
  - magic MCP for distinctive UI component ideas (do not clone same set every time)

Assets:
  - firecrawl/browse existing site for colors/logo/photos
  - pollinations or higgsfield only if missing hero imagery and license is mock-safe

## Non-negotiables
- No shared visual template across businesses
- Plan must exploit their strengths and counter their weaknesses from the Excel
- Prefer marketing/demo site architecture unless research proves a real app is needed
- Pull brand cues from existing site/social/Maps (logo, colors, photos if usable for mock)
- If no site: derive brand from name + niche + NYC neighborhood + public assets only
- Requirements: each website must have a unique workflow, user flow, structure, and pipeline tailored to that exact business

## Scoring rubric (max 100; need ≥90)
Self-review checklist, each item 0–10:
1. Positioning clarity
2. Unique visual direction (not generic AI SaaS look)
3. Strengths reflected on homepage
4. Weaknesses addressed (trust, CTA, clarity, mobile)
5. Page-by-page IA makes sense for that business
6. Component inventory complete
7. Copy direction specific (not lorem)
8. Asset list complete (what exists / what to generate)
9. Implementation.md is executable by an agent without questions
10. Repo hygiene (README, tags, structure)

Second pass: improve weakest 3 scores; target ≥95. Do not invent a fake "120" scale.

## Per-business repo
- Org: Alkharazmi
- Name: nyc-<category-slug>-<business-slug>
- Topics/tags: nyc-lead, pending-beta, batch-1
- Branches: dev (default), prod
- Human merge required; CI must pass before review requested
- All code reviewed by a human before PR merge; GitHub Actions verify before review is requested

## Required files per repo
1. brief.md — business, audience, offer, strengths, weaknesses, conversion goal
2. implementation.md — agent build prompt, stack choice, structure, hard performance rules
3. design-system.md / DESIGN.md — color, type, spacing, motion, tone (unique)
4. page-plans/ — one md per page: sections top→bottom, components, copy notes
5. assets.md — logos/colors/photos sources + generation needs
6. user-flow.md — unique user flow for this business
7. handling-protocols.md — file/folder naming, context loss, resume after power outage, multi-agent, sandbox test, visual test (/browse), token optimization
8. github-workflow.md — dev/prod, PR, CI, human review, issues → fix → merge → promote
9. README.md — what this repo is, status, how to run later
10. skills-used.md — which skills/MCP applied + why

Structural requirements: structure the way that best fits the uniqueness of each project.

## Stack guidance (defaults for pitch sites)
Default: Next.js (App Router) + TypeScript + Tailwind + shadcn/ui
Motion: GSAP and/or anime.js only if it helps the concept
Backend/DB: omit for v0 demo unless brief truly needs forms storage
If forms needed: simple API route or form placeholder — no full Nest/PHP/Postgres unless justified in brief
User prefs for later full builds: HTML/CSS/JS/Next.js; backend PHP/Node/Nest; DB PostgreSQL

## Skills / tools
Use installed design + copywriting skills, shadcn MCP, magic MCP, browser tools for research.
Prefer distinctive design; avoid same layout for every business.
Use gstack design skills and custom global skills already installed.

## Done when (per business)
- Checklist ≥90
- Repo exists under Alkharazmi with tags pending-beta + batch-1
- All required files present on dev
- Sample first repo paused for human Gate B
```

---

## Acceptance checklist (per business)

- [ ] Score ≥ 90 (documented)  
- [ ] Unique design lane vs other batch sites  
- [ ] All required files present  
- [ ] Repo under `Alkharazmi` with correct tags  
- [ ] `dev` / `prod` branch model documented  
- [ ] First of batch stopped for **Gate B**  

---

## Next

→ [03-build.md](./03-build.md) after Gate B on the sample plan.
