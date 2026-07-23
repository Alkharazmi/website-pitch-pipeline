# Loop 1 — Research → Excel

> Find NYC businesses with weak or missing websites.  
> Output: one clean Excel workbook for planning and outreach.  
> **Stop for Gate A** — do not start plans until a human approves the sheet.

---

## Paste into Claude Code

```text
/loop [auto]
/goal
# Loop 1 — NYC lead research → Excel

## Prerequisite
Loop 0 required items PASS. Read ./nyc-pipeline/BOOTSTRAP_REPORT.md if present.

## Tools to use
- apify-ultimate-scraper (Google Maps / Yelp-style lead pulls) when auth available
- firecrawl for existing websites
- gstack /browse or /scrape for verification
- WebSearch for gaps
- Do NOT invent emails

## Objective
Find New York City local businesses that either have no website or a clearly outdated/weak website. Produce one clean Excel workbook for outreach and site planning.

## Scope (strict)
- Geography: NYC only (include borough column)
- Verticals: [PICK 1–2, e.g. tailors, auto repair, plumbing]
- Count: 15 qualified businesses (stop at 15 that pass QA)
- Exclude: national chains, franchises with modern sites, businesses with strong recent websites

## “Outdated / weak web” criteria (must meet ≥2)
- No website found
- No HTTPS / broken mobile layout
- Copyright year ≤ 2019 or last obvious redesign looks ancient
- No clear services, CTA, hours, or contact path
- Looks like abandoned template / incomplete site
- Strong Google/Maps presence but weak or missing site

## Required Excel columns (filters + freeze header)
Business Name | Borough | Neighborhood | Category | Phone | Public Email | Email Source URL | Website URL | Website Status (none/outdated/weak) | Why Outdated (short) | Strengths (from reviews/Maps/social) | Weaknesses (web + ops signals) | Google Maps URL | Instagram/Facebook if any | Estimated Fit Score 1–10 | Notes | Research Date

## Quality rules
- Every email must have Email Source URL; if no public email, leave blank and set contact method = form/phone only
- Strengths/weaknesses must cite observable evidence (reviews themes, missing booking, etc.)
- No duplicates
- Sort by Fit Score descending

## Output
- File path: ./nyc-leads/nyc-business-leads-batch-1.xlsx
- Also save CSV copy for agents
- Short summary.md: how many found, vertical mix, top 5 opportunities

## Done when
- 15 rows pass column completeness QA
- Filters work, header frozen, readable sheet
- User can open file and scan without cleanup
- STOP for human Gate A (user approves Excel before Loop 2)
```

---

## Acceptance checklist

- [ ] 15 qualified rows  
- [ ] Filters + frozen header  
- [ ] No invented emails; sources filled  
- [ ] Strengths / weaknesses evidence-based  
- [ ] `summary.md` present  
- [ ] Human **Gate A** approved  

---

## Next

→ [02-plan.md](./02-plan.md) after Gate A.
