# NYC Website Pitch Pipeline

> Find New York City businesses with weak or missing websites → research them → plan unique site concepts → build demo sites → draft outreach.  
> Goal: get owners to the negotiation table. **Aesthetics and clarity beat deep functionality** on the first pass.

---

## Pipeline order

| Loop | File | Job | Gate |
|------|------|-----|------|
| **0** | [`loops/00-bootstrap.md`](./loops/00-bootstrap.md) | Install skills, plugins, MCP, CLIs on a new machine | Machine ready |
| **1** | [`loops/01-research.md`](./loops/01-research.md) | Find businesses → Excel workbook | **Gate A** — human approves Excel |
| **2** | [`loops/02-plan.md`](./loops/02-plan.md) | Unique plan + GitHub repo per business | **Gate B** — human approves first plan |
| **3** | [`loops/03-build.md`](./loops/03-build.md) | Implement demos + outreach email | **Gate C** — human approves first build |

**Never skip gates.** Quality collapses when agents batch-plan or batch-build without a human sample check.

---

## Shared project rules

```text
PROJECT: NYC Local Business Website Pitch Pipeline
ORG:     Alkharazmi
BATCH:   5 businesses max unless a human expands scope
```

### Human gates

| Gate | After | Human checks |
|------|--------|--------------|
| **A** | Loop 1 | Excel is complete, contacts are public, fit scores make sense |
| **B** | First Loop 2 repo | Plan is unique, usable, not a generic template |
| **C** | First Loop 3 site | UI is sharp, mobile works, distinct from other demos |

### Legal & contact

- Use **only publicly listed** business emails / phones / contact forms.
- Every email cell must include an **Email Source URL**.
- **Do not invent** emails or scrape personal inboxes.
- Demo sites are **sales concepts** unless the owner has contracted work.
- Do not claim a site is “already live on their domain” unless that is true.

### Stop conditions

- Never claim “done” without checklist evidence.
- Prefer fewer excellent leads over many weak ones.
- “Do not stop until done” always means **done = written acceptance criteria**, not infinite polish.

### Stack defaults (pitch / demo sites)

| Layer | Default | Notes |
|-------|---------|--------|
| Frontend | Next.js (App Router) + TypeScript + Tailwind + shadcn/ui | Marketing-first |
| Motion | GSAP and/or anime.js | Only when the concept needs it |
| Backend / DB | **Omit for v0** | Add Nest/PHP/Postgres only if the brief truly needs storage |
| Preferred languages | HTML, CSS, JS, Next.js; PHP / Node / Nest when justified | Postgres if data is required |

User preferences for later full products: HTML, CSS, JavaScript, Next.js; backend PHP, Node.js, Nest.js; database PostgreSQL. **Pitch demos should stay light.**

---

## Skills map

### Design / UI (Loops 2–3)

| Skill / command | Role |
|-----------------|------|
| `impeccable` | Craft, polish, anti-generic UI |
| `design-taste-frontend` | Landing / portfolio anti-slop direction |
| `high-end-visual-design` | Premium agency bar |
| `ui-ux-pro-max` | Palettes, type pairings, patterns |
| `minimalist-ui` / `industrial-brutalist-ui` | Distinct style lanes (one per business) |
| `brandkit` | Identity when brand is weak |
| `imagegen-frontend-web` | Section visual direction |
| `image-to-code` | Refs → implementation |
| `redesign-existing-projects` | Audit old sites |
| `frontend-design` (plugin) | Intentional visual direction |
| gstack `/design-consultation` | Full system + `DESIGN.md` |
| gstack `/design-shotgun` | Multiple variants |
| gstack `/design-html` | HTML/CSS finalization |
| gstack `/design-review` | Visual QA |
| gstack `/qa` · `/qa-only` | Browser QA |
| gstack `/browse` | Headless browser (**not** Chrome MCP) |
| `gsap-skills` (plugin) | Correct GSAP usage |
| `diagram-design` (plugin) | User-flow / IA diagrams |

### Copy / outreach (Loops 2–3)

| Skill | Role |
|-------|------|
| `copywriting` | Page copy structure |
| `copy-editing` | Edit / polish |
| `ogilvy` / `ogilvy-copywriting` | Headlines that sell |
| `stop-slop` | Kill AI-sounding prose (emails especially) |

### Research (Loop 1)

| Skill / tool | Role |
|--------------|------|
| `apify-ultimate-scraper` | Maps / social / leads (needs Apify token) |
| `firecrawl` CLI | Site crawl / extract |
| gstack `/scrape` | Structured page pulls |
| WebSearch + `/browse` | Verification |

### Optional creative

| Skill / MCP | Role |
|-------------|------|
| `higgsfield-*` | Heroes, product shots (needs CLI auth) |
| `pollinations-images` MCP | Free image gen fallback |
| `magic` MCP (21st.dev) | UI component ideas |
| `shadcn` MCP | shadcn components |

---

## MCP servers

| Server | How it runs | Required? |
|--------|-------------|-----------|
| **shadcn** | `npx -y shadcn@latest mcp` | Yes (build) |
| **magic** (21st.dev) | `npx -y @21st-dev/magic@latest` + `API_KEY` | Recommended |
| **pollinations-images** | `npx -y @pollinations/model-context-protocol` | Recommended |
| **n8n** | HTTP MCP URL + bearer | Optional automation |

**Secrets:** use environment variables. Never commit API keys or tokens.

```bash
export MAGIC_API_KEY="..."
export N8N_MCP_URL="..."
export N8N_MCP_TOKEN="..."
export APIFY_TOKEN="..."
export FIRECRAWL_API_KEY="..."   # if using Firecrawl cloud
```

See [`mcp.example.json`](./mcp.example.json).

---

## Handoff artifacts

```text
./nyc-pipeline/BOOTSTRAP_REPORT.md          # Loop 0
./nyc-leads/nyc-business-leads-batch-1.xlsx # Loop 1
./nyc-leads/nyc-business-leads-batch-1.csv
./nyc-leads/summary.md
Alkharazmi/nyc-<category>-<business>/       # Loops 2–3 (one repo per business)
```

### Per-business repo tags

| Tag | Meaning |
|-----|---------|
| `nyc-lead` | Part of this pipeline |
| `pending-beta` | Plan complete, ready to implement |
| `in-progress` | Build underway |
| `ready-for-review` | PR open for human |
| `ready-for-outreach` | Demo + email draft ready |
| `batch-1` | First batch |

### Repo naming

```text
nyc-<category-slug>-<business-slug>
```

Example: `nyc-tailor-east-side-alterations`

---

## Scoring (replaces vague “100 then 120”)

Self-review checklist, each item **0–10** (max **100**). Plan must reach **≥90** before `pending-beta`.

1. Positioning clarity  
2. Unique visual direction (not generic AI SaaS)  
3. Strengths reflected on homepage  
4. Weaknesses addressed (trust, CTA, clarity, mobile)  
5. Page-by-page IA fits that business  
6. Component inventory complete  
7. Copy direction specific (not lorem)  
8. Asset list complete  
9. `implementation.md` executable without questions  
10. Repo hygiene (README, tags, structure)

**Second pass:** improve the weakest three dimensions; target **≥95**. Do not invent a fake “120” scale.

---

## Suggested operating order

1. Run **Loop 0** on any new machine → read `BOOTSTRAP_REPORT.md`.  
2. Set verticals + batch size (e.g. tailors + auto repair, n=5).  
3. Run **Loop 1** → **Gate A**.  
4. Run **Loop 2** for **one** business → **Gate B**.  
5. Run **Loop 3** for that site → **Gate C**.  
6. Only then scale Loops 2–3 across the rest of the batch.

---

## How to run a loop in Claude Code

Paste the contents of the matching file under `loops/`, or:

```text
/loop [auto]
# then paste the loop body (from the ## Objective section onward is fine
# if you already use /goal — prefer the full file for first runs)
```

Prefer **one loop per session** so context stays clean.

---

## Related files

| File | Purpose |
|------|---------|
| [README.md](./README.md) | Project overview & quick start |
| [PIPELINE.md](./PIPELINE.md) | This document (full system) |
| [loops/00-bootstrap.md](./loops/00-bootstrap.md) | Machine setup |
| [loops/01-research.md](./loops/01-research.md) | Lead research |
| [loops/02-plan.md](./loops/02-plan.md) | Site planning + repos |
| [loops/03-build.md](./loops/03-build.md) | Implementation + email |
| [mcp.example.json](./mcp.example.json) | MCP config template (no secrets) |
| [INSTALL.md](./INSTALL.md) | Install sources cheat sheet |
