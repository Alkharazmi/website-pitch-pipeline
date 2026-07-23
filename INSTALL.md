# Install sources cheat sheet

Quick reference for Loop 0 and new machines. Prefer official docs if URLs move.

**Full catalog with loop mapping:** [`TOOLS.md`](./TOOLS.md)

## Core agent stack

| Piece | Where | Install idea |
|-------|--------|--------------|
| Skills ecosystem | [skills.sh](https://skills.sh/) | `npx skills find …` / `npx skills add …` |
| gstack | [garrytan/gstack](https://github.com/garrytan/gstack) | `git clone … ~/.claude/skills/gstack && ./setup` |
| Claude plugins official | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Claude plugin marketplace |
| frontend-design plugin | same official marketplace | enable `frontend-design` |
| superpowers | same official marketplace | enable `superpowers` |
| GSAP skills | [greensock/gsap-skills](https://github.com/greensock/gsap-skills) | plugin marketplace |
| diagram-design | [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design) | plugin marketplace |
| ponytail | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | plugin marketplace |
| stop-slop | [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) | skills add / clone |
| Higgsfield skills | [higgsfield-ai/skills](https://github.com/higgsfield-ai/skills) | `npx skills add higgsfield-ai/skills` |
| Higgsfield CLI | npm `@higgsfield/cli` | `npm i -g @higgsfield/cli` |
| shadcn MCP | [ui.shadcn.com/docs/mcp](https://ui.shadcn.com/docs/mcp) | `npx shadcn@latest mcp` |
| 21st magic MCP | [21st.dev](https://21st.dev) | `npx @21st-dev/magic@latest` |
| Pollinations MCP | [pollinations.ai](https://pollinations.ai) | `@pollinations/model-context-protocol` |
| Apify | [apify.com](https://apify.com) · [integrations](https://console.apify.com/settings/integrations) | `npm i -g apify-cli` |
| Bun (gstack) | [bun.sh](https://bun.sh) | install script |
| Claude Code | [Anthropic docs](https://docs.anthropic.com/en/docs/claude-code) | official installer |
| GitHub CLI | [cli.github.com](https://cli.github.com) | brew / official |

## Research / crawl / browser (required additions)

| Piece | Where | Install idea |
|-------|--------|--------------|
| **Firecrawl** | [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) · [firecrawl.dev](https://firecrawl.dev) | `npm i -g firecrawl-cli` + `FIRECRAWL_API_KEY`; or self-host from repo |
| **Crawl4AI** | [unclecode/crawl4ai](https://github.com/unclecode/crawl4ai) | `pip install -U crawl4ai` + browser setup |
| **Browser Use** | [browser-use/browser-use](https://github.com/browser-use/browser-use) | `uv pip install browser-use` · `browser-use skill install` |
| **Scrapling** | [D4Vinci/Scrapling](https://github.com/D4Vinci/Scrapling) | `pip install "scrapling[all]"` · `scrapling install` |
| **Webclaw** | [0xMassi/webclaw](https://github.com/0xMassi/webclaw) | `brew install webclaw` or Cargo; MCP + `npx skills add 0xMassi/webclaw-skill` |

## Writing, marketing, design skills (required additions)

| Piece | Where | Install idea |
|-------|--------|--------------|
| **No AI Slop** | [petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop) | Install skill globally / clone into agent skills |
| **SkillOpt** | [microsoft/SkillOpt](https://github.com/microsoft/SkillOpt) | `pip install skillopt` (optional meta-optimizer) |
| **AI Marketing Claude** | [zubair-trabzada/ai-marketing-claude](https://github.com/zubair-trabzada/ai-marketing-claude) | `curl …/install.sh \| bash` or clone + `./install.sh` |
| **Digital Marketing Pro** | [indranilbanerjee/digital-marketing-pro](https://github.com/indranilbanerjee/digital-marketing-pro) | `/plugin install digital-marketing-pro@neels-plugins` |
| **Kepano Obsidian** | [kepano/kepano-obsidian](https://github.com/kepano/kepano-obsidian) | `git clone` vault template (optional ops) |
| **Emil design skills** | [emilkowalski/skills](https://github.com/emilkowalski/skills) | `npx skills@latest add emilkowalski/skills` |
| **ADHD (ideation)** | [UditAkhourii/adhd](https://github.com/UditAkhourii/adhd) | `npx skills add UditAkhourii/adhd` |
| **Branerail (architecture)** | [UditAkhourii/branerail](https://github.com/UditAkhourii/branerail) | `npm i -g @uditakhouri/branerail` |
| **Brane Code (optional runtime)** | [UditAkhourii/brane-code](https://github.com/UditAkhourii/brane-code) | clone + upstream README |
| **Udit Akhouri (author)** | [github.com/UditAkhourii](https://github.com/UditAkhourii) | profile / other experiments |

## Environment variables (never commit)

```bash
export MAGIC_API_KEY="..."
export N8N_MCP_URL="..."
export N8N_MCP_TOKEN="..."
export APIFY_TOKEN="..."
export FIRECRAWL_API_KEY="..."
# Browser Use / LLM providers as required by that tool's docs
```

## MCP template

Copy [`mcp.example.json`](./mcp.example.json) into your Claude MCP config and replace placeholders with env-backed values.  
Also wire **Webclaw** and/or **Scrapling** MCP when installed (see [`TOOLS.md`](./TOOLS.md)).
