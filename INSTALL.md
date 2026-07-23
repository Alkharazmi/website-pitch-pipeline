# Install sources cheat sheet

Quick reference for Loop 0 and new machines. Prefer official docs if URLs move.

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
| Firecrawl CLI | [firecrawl.dev](https://www.firecrawl.dev) | `npm i -g firecrawl-cli` |
| Bun (gstack) | [bun.sh](https://bun.sh) | install script |
| Claude Code | [Anthropic docs](https://docs.anthropic.com/en/docs/claude-code) | official installer |
| GitHub CLI | [cli.github.com](https://cli.github.com) | brew / official |

## Environment variables (never commit)

```bash
export MAGIC_API_KEY="..."
export N8N_MCP_URL="..."
export N8N_MCP_TOKEN="..."
export APIFY_TOKEN="..."
export FIRECRAWL_API_KEY="..."
```

## MCP template

Copy [`mcp.example.json`](./mcp.example.json) into your Claude MCP config and replace placeholders with env-backed values.
