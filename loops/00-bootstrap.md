# Loop 0 — Bootstrap

> Run this on a **new PC** or empty Claude Code setup before research or builds.  
> Produces a verification report. Does **not** start business research.

---

## Paste into Claude Code

```text
/loop [auto]
/goal
# Loop 0 — Bootstrap skills, plugins, MCP, CLIs for NYC pitch pipeline

## Objective
On this machine, install and verify every skill, plugin, MCP server, and CLI needed to run Loops 1–3. Produce a verification report. Do not start business research until verification passes.

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
- apify-ultimate-scraper (needs Apify CLI + token)
  Apify CLI: npm install -g apify-cli
  Auth: apify login  OR  export APIFY_TOKEN=...
  Console tokens: https://console.apify.com/settings/integrations
- find-skills (already via skills CLI)

### B4. Optional creative (Higgsfield)
Source skills: https://github.com/higgsfield-ai/skills
  npx skills add higgsfield-ai/skills
  # packages: higgsfield-generate, higgsfield-websites, higgsfield-product-photoshoot,
  # higgsfield-marketplace-cards, higgsfield-soul-id
CLI: npm install -g @higgsfield/cli
Auth: follow higgsfield login docs

### B5. Firecrawl CLI (site research)
  npm install -g firecrawl-cli
  # set FIRECRAWL_API_KEY if using cloud
  which firecrawl && firecrawl --help | head

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

### C4. n8n (optional — only if user wants automation)
  type: http
  url + Authorization bearer from env
  Do not block pipeline if n8n fails

After config: restart Claude Code and list MCP tools. Failures = report, not silent skip for shadcn/magic/pollinations.

## Phase D — GitHub org readiness
- gh auth status (use Taha-Mahmoodi / account with org access)
- Confirm access to org: Alkharazmi
- gh repo list Alkharazmi --limit 5

## Phase E — Verification report
Write: ./nyc-pipeline/BOOTSTRAP_REPORT.md

Checklist (pass/fail each):
[ ] node, npm, git, gh, bun
[ ] gstack installed + /browse works
[ ] plugins: frontend-design, gsap-skills, diagram-design, superpowers
[ ] design skills present (list paths)
[ ] copy skills present
[ ] apify CLI + auth (or marked SKIP with reason)
[ ] firecrawl CLI
[ ] MCP: shadcn, magic, pollinations reachable
[ ] higgsfield optional status
[ ] GitHub org access (Alkharazmi)

## Done when
- All required items PASS (optional items may SKIP with reason)
- BOOTSTRAP_REPORT.md written
- Stop and show report; do NOT run Loop 1 until user says proceed
```

---

## Done definition

| Required | Optional |
|----------|----------|
| Node, git, gh, bun | Higgsfield |
| gstack + `/browse` | n8n MCP |
| Design + copy skills | Ponytail |
| shadcn + magic + pollinations MCP | |
| Firecrawl CLI | |
| `Alkharazmi` org access | |
| `BOOTSTRAP_REPORT.md` | |

---

## Next

→ [01-research.md](./01-research.md) after the human accepts the bootstrap report.
