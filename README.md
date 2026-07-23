<div align="center">

# NYC Website Pitch Pipeline

**Find local businesses with weak websites → plan unique demos → build → outreach.**

An agent-ready operating system for **Alkharazmi** sales demos in New York City.  
Aesthetics first. Human gates. No generic templates.

<br />

[![Org](https://img.shields.io/badge/org-Alkharazmi-0B0B0F?style=for-the-badge&labelColor=111827)](https://github.com/Alkharazmi)
[![Loops](https://img.shields.io/badge/loops-0→1→2→3-F59E0B?style=for-the-badge&labelColor=111827)](#the-four-loops)
[![Stack](https://img.shields.io/badge/demos-Next.js_+_shadcn-38BDF8?style=for-the-badge&labelColor=111827)](#stack-defaults)
[![Gates](https://img.shields.io/badge/quality-human_gates_A·B·C-22C55E?style=for-the-badge&labelColor=111827)](#human-gates)

<br />

```text
  RESEARCH ──► PLAN ──► BUILD ──► EMAIL
     Excel      repos     demos    outreach
      ▲          ▲         ▲
   Gate A     Gate B    Gate C
```

</div>

---

## Why this exists

Cold-building “a website for every shop in NYC” without structure produces:

- samey AI templates  
- invented contact data  
- unfinished repos  
- emails nobody would send  

This pipeline forces **research quality**, **unique design per business**, **human approval**, and **honest demo positioning**.

The first site is not the product. **The conversation is.**

---

## The four loops

| # | Loop | File | Output | Stops for |
|---|------|------|--------|-----------|
| **0** | Bootstrap | [`loops/00-bootstrap.md`](./loops/00-bootstrap.md) | Skills, MCP, CLIs, `BOOTSTRAP_REPORT.md` | Machine ready |
| **1** | Research | [`loops/01-research.md`](./loops/01-research.md) | Excel + CSV of NYC leads | **Gate A** |
| **2** | Plan | [`loops/02-plan.md`](./loops/02-plan.md) | One GitHub repo + plan pack per business | **Gate B** |
| **3** | Build | [`loops/03-build.md`](./loops/03-build.md) | Demo site PR + `EMAIL_DRAFT.md` | **Gate C** |

Full system write-up: **[`PIPELINE.md`](./PIPELINE.md)**  
Install sources: **[`INSTALL.md`](./INSTALL.md)**  
MCP template: **[`mcp.example.json`](./mcp.example.json)**

---

## Quick start

### 1. Clone this repo

```bash
gh repo clone Alkharazmi/nyc-website-pitch-pipeline
cd nyc-website-pitch-pipeline
```

### 2. Bootstrap the machine (new PC)

Open Claude Code and paste the full prompt from:

```text
loops/00-bootstrap.md
```

Or open [`PIPELINE.md`](./PIPELINE.md) and run Loop 0 only.

### 3. Run the pipeline in order

```text
Loop 0  →  verify BOOTSTRAP_REPORT.md
Loop 1  →  review Excel          (Gate A)
Loop 2  →  review first plan     (Gate B)
Loop 3  →  review first build    (Gate C)
Then scale Loops 2–3 across the batch
```

### 4. How to invoke a loop

In Claude Code:

```text
/loop [auto]
```

Then paste the fenced prompt body from the matching `loops/*.md` file  
(or `/goal` with that body, depending on your setup).

**One loop per session** keeps context clean.

---

## Human gates

| Gate | When | You check |
|------|------|-----------|
| **A** | After research | Real businesses, public contacts only, fit scores honest |
| **B** | After first plan | Unique direction, executable `implementation.md`, not a template |
| **C** | After first build | Mobile polish, distinct look, plan match, email sounds human |

> Do not batch-plan or batch-build past a gate. One excellent sample beats ten weak clones.

---

## What “good” looks like

### Research (Loop 1)

- NYC only, focused verticals  
- **15** qualified rows (batch discipline)  
- Email only when public + **source URL**  
- Strengths / weaknesses from evidence (Maps, reviews, site)

### Plans (Loop 2)

- Different design **lane** per business (minimal / industrial / high-end / etc.)  
- Score **≥ 90 / 100** on the written rubric (no fake “120”)  
- Repos under **`Alkharazmi`**: `nyc-<category>-<business>`  
- Tags: `pending-beta`, `nyc-lead`, `batch-1`

### Builds (Loop 3)

- Follow that repo’s plan exactly  
- CI green → **human** reviews PR  
- `EMAIL_DRAFT.md` written with `stop-slop` discipline  
- Demo labeled as a concept unless contracted otherwise

---

## Stack defaults

| Layer | Pitch demo default |
|-------|--------------------|
| App | Next.js App Router + TypeScript |
| Style | Tailwind + shadcn/ui |
| Motion | GSAP / anime.js when the concept needs it |
| Data | Skip Nest/PHP/Postgres on v0 unless the brief requires it |

Later full products may use PHP / Node / Nest + PostgreSQL — only when justified.

---

## Skills & tools (high level)

| Layer | Examples |
|-------|----------|
| Design | `impeccable`, `design-taste-frontend`, gstack `/design-consultation`, `/design-shotgun`, `/design-review` |
| Copy | `copywriting`, `ogilvy`, `stop-slop` |
| Research | Apify scraper skill, Firecrawl, gstack `/browse` · `/scrape` |
| MCP | shadcn, magic (21st.dev), pollinations-images |
| Motion | `gsap-skills` plugin |
| Diagrams | `diagram-design` plugin |

Full maps live in [`PIPELINE.md`](./PIPELINE.md) and [`INSTALL.md`](./INSTALL.md).

---

## Repo layout

```text
nyc-website-pitch-pipeline/
├── README.md                 ← you are here
├── PIPELINE.md               ← full system (rules, skills, scoring, handoffs)
├── INSTALL.md                ← install sources cheat sheet
├── mcp.example.json          ← MCP template (no secrets)
└── loops/
    ├── 00-bootstrap.md       ← new machine setup
    ├── 01-research.md        ← leads → Excel
    ├── 02-plan.md            ← unique plans + repos
    └── 03-build.md           ← implement + email
```

Per-business demo repos (created by Loop 2) live **alongside** this pipeline repo under the org, e.g.:

```text
Alkharazmi/nyc-tailor-example-shop
Alkharazmi/nyc-auto-example-garage
```

---

## Legal & ethics (non-negotiable)

- Public business contacts only  
- Record source URLs for emails  
- No invented identities or addresses  
- Demos are sales tools — say so in README when relevant  
- Outreach only after a human has read the email  

---

## Operating rhythm

```text
Day 0   Loop 0 on the machine
Day 1   Loop 1 → Gate A (Excel)
Day 1–2 Loop 2 sample → Gate B (one plan)
Day 2–3 Loop 3 sample → Gate C (one demo)
Day 3+  Scale remaining batch with the same bars
```

Keep batches small (**≤ 5** plans/builds at a time unless expanded on purpose).

---

## Contributing inside Alkharazmi

1. Branch from `dev` (or `main` if that is default).  
2. Change docs with clear commits.  
3. Open a PR; keep pipeline instructions executable (agents paste them).  
4. Never commit API keys — use env vars and `mcp.example.json` only.

---

## Maintainers

- **Org:** [Alkharazmi](https://github.com/Alkharazmi)  
- **Operator account:** Taha Mahmoodi (`Taha-Mahmoodi`)

---

<div align="center">

**Read the system · run one loop · pass the gate · then scale.**

[`PIPELINE.md`](./PIPELINE.md) · [`loops/`](./loops/) · [`INSTALL.md`](./INSTALL.md)

</div>
