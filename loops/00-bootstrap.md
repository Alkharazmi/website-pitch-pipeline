# Loop 0 — Bootstrap

> Run this on a **new PC** or empty Claude Code setup before research or builds.  
> Produces a verification report. Does **not** start business research.  
> Location-agnostic: only installs tools; campaigns set geography in Loop 1+.

---

## Paste into Claude Code

```text
/loop [auto]
/goal
# Loop 0 — Bootstrap skills, plugins, MCP, CLIs for local business website pitch pipeline

## Objective
On this machine, install and verify every skill, plugin, MCP server, and CLI needed to run Loops 1–3 for **any geography**. Produce a verification report. Do not start business research until verification passes. Do not lock the pipeline to a single city or country.

## Prerequisites to check first
- macOS or Linux with Node.js 20+, npm, git, gh CLI
- Claude Code installed and logged in
- Bun installed (required by gstack): https://bun.sh
- User can provide API keys via env vars (never hardcode secrets into git)

## Phase A — Core agent stack

### A1. Skills CLI + find-skills
Browse: https://skills.sh/
Install finder:
  npx skills add <find-skills-package-or-owner/repo>
  # Discovery: npx skills find <query>
Document installed path under ~/.agents/skills and/or ~/.claude/skills

### A2. gstack (browse, design, qa, ship)
Source: https://github.com/garrytan/gstack
Install:
  git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
  cd ~/.claude/skills/gstack && ./setup
Ensure CLAUDE.md (user or project) says:
  - use /browse for web browsing
  - never use mcp__claude-in-chrome__* tools
  - list gstack skills including /design-consultation /design-shotgun /design-html /design-review /qa /qa-only /browse /ship /review

### A3. Claude Code plugins (marketplaces + enable)
Add marketplaces / install plugins:

1) Official marketplace
   repo: https://github.com/anthropics/claude-plugins-official
   enable:
     - superpowers@claude-plugins-official
     - frontend-design@claude-plugins-official

2) GSAP skills
   repo: https://github.com/greensock/gsap-skills
   enable: gsap-skills@gsap-skills

3) Diagram design
   repo: https://github.com/cathrynlavery/diagram-design
   enable: diagram-design@diagram-design

4) Ponytail (optional simplicity guardrails)
   repo: https://github.com/DietrichGebert/ponytail
   enable: ponytail@ponytail

Verify in Claude settings: enabledPlugins matches the list above.

## Phase B — Design + copy skills (pipeline-critical)

Install via `npx skills add <source>` when available on skills.sh, otherwise clone/copy SKILL.md into ~/.claude/skills/<name>/ or ~/.agents/skills/<name>/ and symlink into Claude skills if needed.

### B1. Must-have design skills
Search on https://skills.sh/ and GitHub; install best available match for:
- impeccable
- design-taste-frontend
- high-end-visual-design
- ui-ux-pro-max
- minimalist-ui
- industrial-brutalist-ui
- brandkit
- imagegen-frontend-web
- image-to-code
- redesign-existing-projects
- frontend-design (covered by plugin if skill missing)

### B2. Must-have copy skills
- copywriting
- copy-editing
- ogilvy / ogilvy-copywriting
- stop-slop
  known source: https://github.com/hardikpandya/stop-slop
  install: npx skills add hardikpandya/stop-slop   # if published; else clone into ~/.agents/skills/stop-slop

### B3. Research skills
- apify-ultimate-scraper (needs Apify CLI + token) — works for many countries/platforms
  Apify CLI: npm install -g apify-cli
  Auth: apify login  OR  export APIFY_TOKEN=...
  Console tokens: https://console.apify.com/settings/integrations
- find-skills (already via skills CLI)

### B4. Optional creative (Higgsfield)
Source skills: https://github.com/higgsfield-ai/skills
  npx skills add higgsfield-ai/skills
CLI: npm install -g @higgsfield/cli
Auth: follow higgsfield login docs

### B5. Firecrawl (site research) — https://github.com/firecrawl/firecrawl
  npm install -g firecrawl-cli
  export FIRECRAWL_API_KEY=...   # https://firecrawl.dev
  # Advanced self-host: clone firecrawl/firecrawl and follow Docker docs
  which firecrawl && firecrawl --help | head

### B6. Crawl4AI — https://github.com/unclecode/crawl4ai
  pip install -U crawl4ai
  # run package browser setup if required (crawl4ai-setup / playwright install)
  python -c "import crawl4ai; print('crawl4ai ok')"

### B7. Browser Use — https://github.com/browser-use/browser-use
  # Prefer uv + Python 3.12 per upstream
  uv pip install browser-use || pip install browser-use
  browser-use skill install   # when CLI provides it
  # Docs: https://docs.browser-use.com

### B8. Scrapling — https://github.com/D4Vinci/Scrapling
  pip install "scrapling[all]"
  scrapling install           # browser deps
  # MCP: pip install "scrapling[ai]"

### B9. Webclaw — https://github.com/0xMassi/webclaw
  brew install webclaw || cargo install --git https://github.com/0xMassi/webclaw.git webclaw-cli
  npx skills add 0xMassi/webclaw-skill
  # also install webclaw-mcp for local MCP when possible

### B10. No AI Slop — https://github.com/petergyang/no-ai-slop
  # Install skill globally for Claude/agent:
  # "Install this skill globally: https://github.com/petergyang/no-ai-slop"
  git clone https://github.com/petergyang/no-ai-slop.git ~/.agents/skills/no-ai-slop 2>/dev/null || true
  # symlink/copy SKILL into ~/.claude/skills if needed

### B11. Emil Kowalski design skills — https://github.com/emilkowalski/skills
  npx skills@latest add emilkowalski/skills

### B12. AI Marketing Claude — https://github.com/zubair-trabzada/ai-marketing-claude
  curl -fsSL https://raw.githubusercontent.com/zubair-trabzada/ai-marketing-claude/main/install.sh | bash
  # or: git clone + ./install.sh
  pip install reportlab   # PDF reports if needed

### B13. Digital Marketing Pro — https://github.com/indranilbanerjee/digital-marketing-pro
  # In Claude Code:
  # /plugin marketplace add indranilbanerjee/neels-plugins   # if needed
  # /plugin install digital-marketing-pro@neels-plugins
  # Manual fallback: git clone --depth=1 https://github.com/indranilbanerjee/digital-marketing-pro.git

### B14. SkillOpt (optional meta) — https://github.com/microsoft/SkillOpt
  pip install skillopt
  # Optional: clone repo for Claude Code integration shells / skillopt-sleep

### B15. Kepano Obsidian vault template (optional ops) — https://github.com/kepano/kepano-obsidian
  git clone https://github.com/kepano/kepano-obsidian.git ~/Obsidian/kepano-template
  # Use as structure for campaign notes (not required for agent runs)

Full catalog: TOOLS.md in this pipeline repo.

## Phase C — MCP servers

Write mcpServers into Claude user config using ENV placeholders only.
Template: this repo's mcp.example.json

### C1. shadcn (required for build)
  command: npx
  args: ["-y", "shadcn@latest", "mcp"]
  Docs: https://ui.shadcn.com/docs/mcp

### C2. magic / 21st.dev (UI components)
  command: npx
  args: ["-y", "@21st-dev/magic@latest"]
  env: API_KEY from env MAGIC_API_KEY
  Site: https://21st.dev

### C3. pollinations-images (image gen fallback)
  command: npx
  args: ["-y", "@pollinations/model-context-protocol"]
  Site: https://pollinations.ai

### C4. webclaw MCP (recommended local extract)
  command/path per https://github.com/0xMassi/webclaw (webclaw-mcp or brew install)

### C5. scrapling MCP (recommended hard scrapes)
  after: pip install "scrapling[ai]" — wire per Scrapling docs

### C6. n8n (optional — only if user wants automation)
  type: http
  url + Authorization bearer from env
  Do not block pipeline if n8n fails

After config: restart Claude Code and list MCP tools. Failures = report, not silent skip for shadcn/magic/pollinations/webclaw.

## Phase D — GitHub org readiness
- gh auth status (use Taha-Mahmoodi / account with org access)
- Confirm access to org: Alkharazmi
- gh repo list Alkharazmi --limit 5

## Phase E — Verification report
Write: ./pipeline-runs/BOOTSTRAP_REPORT.md

Checklist (pass/fail each):
[ ] node, npm, git, gh, bun
[ ] gstack installed + /browse works
[ ] plugins: frontend-design, gsap-skills, diagram-design, superpowers
[ ] design skills present (list paths)
[ ] copy skills present
[ ] apify CLI + auth (or marked SKIP with reason)
[ ] firecrawl CLI/API (https://github.com/firecrawl/firecrawl)
[ ] crawl4ai installed
[ ] browser-use installed (or SKIP + reason)
[ ] scrapling + browsers
[ ] webclaw CLI and/or MCP
[ ] no-ai-slop skill
[ ] emilkowalski/skills
[ ] ai-marketing-claude
[ ] digital-marketing-pro plugin (or SKIP + reason)
[ ] skillopt optional status
[ ] kepano vault template optional status
[ ] MCP: shadcn, magic, pollinations, webclaw reachable
[ ] higgsfield optional status
[ ] GitHub org access (Alkharazmi)
[ ] Confirmed: pipeline geography is campaign-variable (not hardcoded)
[ ] TOOLS.md catalog present in pipeline repo

## Done when
- All required items PASS (optional items may SKIP with reason)
- BOOTSTRAP_REPORT.md written
- Stop and show report; do NOT run Loop 1 until user says proceed and sets Campaign variables (GEOGRAPHY, GEO_SLUG, LOCALE, VERTICALS)
```

---

## Done definition

| Required | Optional |
|----------|----------|
| Node, git, gh, bun, pip/uv | Higgsfield |
| gstack + `/browse` | n8n MCP |
| Design + copy skills | Ponytail |
| shadcn + magic + pollinations MCP | SkillOpt |
| Firecrawl + Crawl4AI | Kepano vault |
| Scrapling + Webclaw (or documented SKIP) | |
| no-ai-slop + emilkowalski/skills | |
| ai-marketing-claude | digital-marketing-pro (SKIP ok if install blocked) |
| browser-use (or SKIP + reason) | |
| `Alkharazmi` org access | |
| `BOOTSTRAP_REPORT.md` referencing TOOLS.md | |

---

## Next

→ [01-research.md](./01-research.md) after the human accepts the bootstrap report **and** fills Campaign variables (any geography).
