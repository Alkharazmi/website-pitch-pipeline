# Loop 1 — Research → Excel

> Find local businesses with weak or missing websites in the **campaign geography** (any city / region / country).  
> Output: one clean Excel workbook for planning and outreach.  
> **Stop for Gate A** — do not start plans until a human approves the sheet.

---

## Campaign variables (required — fill before paste)

```text
CAMPAIGN_NAME:
GEOGRAPHY:          # e.g. Istanbul | Berlin | NYC | Lisbon metro | US Southwest HVAC
GEO_SLUG:           # e.g. istanbul | berlin | nyc | lisbon | us-sw-hvac
LOCALE / LANGUAGE:  # e.g. tr | de | en
VERTICALS:          # 1–2 niches
TARGET_COUNT:       # default 15 qualified rows
```

**Do not default to a city.** If GEOGRAPHY is empty, ask the human — do not assume NYC or any other place.

---

## Paste into Claude Code

```text
/loop [auto]
/goal
# Loop 1 — Local business lead research → Excel (geography = campaign variable)

## Campaign (filled by human)
CAMPAIGN_NAME: [required]
GEOGRAPHY: [required — city / metro / region / country / multi-area]
GEO_SLUG: [required — short slug for files]
LOCALE / LANGUAGE: [required]
VERTICALS: [required]
TARGET_COUNT: 15

## Prerequisite
Loop 0 required items PASS. Read ./pipeline-runs/BOOTSTRAP_REPORT.md if present.
If GEOGRAPHY or GEO_SLUG is missing, stop and ask — never invent a default location.

## Tools to use (prefer stack in TOOLS.md)
- apify-ultimate-scraper (Maps / directories for the target country) when auth available
- Firecrawl (https://github.com/firecrawl/firecrawl) for search/scrape at scale
- Crawl4AI (https://github.com/unclecode/crawl4ai) for local LLM-friendly crawls → Markdown
- Scrapling (https://github.com/D4Vinci/Scrapling) when sites need adaptive/stealth fetch
- Webclaw (https://github.com/0xMassi/webclaw) for fast local-first extract / MCP
- Browser Use (https://github.com/browser-use/browser-use) for multi-step interactive verification
- gstack /browse or /scrape for lighter verification
- AI Marketing Claude / Digital Marketing Pro for site audit signals when installed
- WebSearch for gaps (query in the local language when helpful)
- Do NOT invent emails; respect ToS and local law

## Objective
Find local businesses **inside the stated GEOGRAPHY** that either have no website or a clearly outdated/weak website. Produce one clean Excel workbook for outreach and site planning. Geography is not locked to any single market.

## Scope (strict)
- Geography: exactly the campaign GEOGRAPHY (include flexible location columns: Country, Region/State, City, Neighborhood or equivalent — use what fits this market; "Borough" only if that market uses it)
- Verticals: from campaign VERTICALS
- Count: TARGET_COUNT qualified businesses (default 15)
- Exclude: national/global chains with modern sites, businesses clearly outside GEOGRAPHY, businesses with strong recent websites

## “Outdated / weak web” criteria (must meet ≥2)
- No website found
- No HTTPS / broken mobile layout
- Copyright year ≤ 2019 or last obvious redesign looks ancient
- No clear services, CTA, hours, or contact path
- Looks like abandoned template / incomplete site
- Strong maps/directory presence but weak or missing site

## Required Excel columns (filters + freeze header)
Business Name | Country | Region/State | City | Area/Neighborhood | Category | Phone | Public Email | Email Source URL | Website URL | Website Status (none/outdated/weak) | Why Outdated (short) | Strengths (from reviews/maps/social) | Weaknesses (web + ops signals) | Maps/Directory URL | Social URLs if any | Estimated Fit Score 1–10 | Notes | Research Date | Campaign Name | Geo Slug

Adapt Region/City/Area labels if the market uses different admin units (e.g. ilçe, Bezirk, arrondissement) — keep the same intent: locatable columns for that geography.

## Quality rules
- Every business must clearly sit inside GEOGRAPHY
- Every email must have Email Source URL; if no public email, leave blank and set contact method = form/phone only
- Strengths/weaknesses must cite observable evidence
- No duplicates
- Sort by Fit Score descending
- Prefer local-language sources when LOCALE is not English

## Output
- File path: ./leads/<GEO_SLUG>-business-leads-batch-1.xlsx
- Also save CSV copy for agents
- Short summary: ./leads/<GEO_SLUG>-summary.md — geography, vertical mix, how many found, top 5 opportunities

## Done when
- TARGET_COUNT rows pass column completeness QA
- Filters work, header frozen, readable sheet
- User can open file and scan without cleanup
- STOP for human Gate A (user approves Excel before Loop 2)
```

---

## Acceptance checklist

- [ ] Campaign GEOGRAPHY / GEO_SLUG filled (not assumed)  
- [ ] TARGET_COUNT qualified rows inside that geography  
- [ ] Filters + frozen header  
- [ ] Flexible location columns fit the market  
- [ ] No invented emails; sources filled  
- [ ] Strengths / weaknesses evidence-based  
- [ ] `./leads/<GEO_SLUG>-summary.md` present  
- [ ] Human **Gate A** approved  

---

## Next

→ [02-plan.md](./02-plan.md) after Gate A (same campaign geo).
