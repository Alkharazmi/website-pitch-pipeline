# Loop 3 — Build + outreach email

> Find `Alkharazmi` repos tagged `pending-beta`, implement their plans, open PRs for human review, draft a human-sounding outreach email.  
> **Build one site fully → Gate C** before the rest of the batch.

---

## Paste into Claude Code

```text
/loop [auto]
/goal
# Loop 3 — Implement pending-beta plans + outreach email

## Prerequisite
Only implement repos in Alkharazmi with topic/tag: pending-beta
Skip any repo not approved at Gate B.
Build max 1 full site, then pause for human Gate C before continuing.

## Objective
Implement each plan faithfully. When implementation matches plan acceptance criteria, add a human-sounding outreach email draft and retag repo ready-for-outreach (after human merge + demo URL when available).

## Skills — MUST use
Implement:
  - implementation.md of that repo is law
  - impeccable + design-taste-frontend + chosen style skill while coding
  - image-to-code if design refs exist
  - gsap-skills when implementing motion
  - shadcn MCP to add components correctly
  - magic MCP only for gaps, not to homogenize batch
  - install anime.js if the plan calls for it
  - use custom global skills installed on the machine

QA:
  - gstack /browse + /qa or /qa-only
  - /design-review after visual complete
  - redesign-existing-projects audit pass if porting from old site patterns

Copy polish:
  - copy-editing + stop-slop + ogilvy on headlines/CTAs
  - stop-slop on EMAIL_DRAFT.md (must sound human)

## Build rules
- Follow that repo's implementation.md and page-plans exactly
- Unique result per business; no copying components wholesale across repos
- Mobile-first, fast, polished UI
- Demo CTAs allowed (Call / Get quote) using public business phone/email from brief
- Mark concept clearly in README (sales demo concept site)
- Do not stop until each approved repo meets its plan criteria (with evidence)

## QA before "done" (must evidence)
- [ ] Matches plan pages/sections
- [ ] Mobile layout checked in browser
- [ ] No broken links/images
- [ ] Lighthouse performance sensible for a marketing page
- [ ] Distinct from other batch sites
- [ ] CI green; PR opened for human review (do not self-merge if policy forbids)
- [ ] skills-used.md updated with what was actually used

## GitHub workflow (per plan's github-workflow.md)
- Work on feature branches → PR into dev
- GitHub Actions must pass before requesting review
- Human reviews and merges
- Promote dev → prod only after verified
- If problems: open issue, fix on PR, mark issue solved, then merge

## Email draft (EMAIL_DRAFT.md in repo)
Must include:
- Subject line options (3)
- Short human email (not salesy AI tone) — run stop-slop
- What we noticed about their business (specific)
- Link placeholder for demo
- Soft CTA to chat
- No fake urgency, no fake "we already built your site live on your domain" claims unless true

## Tagging
- while building: in-progress
- after PR ready: ready-for-review
- after human merge + demo URL: ready-for-outreach
- remove pending-beta when implementation complete

## Done when
- All approved pending-beta repos in this batch are ready-for-review or ready-for-outreach
- Each has EMAIL_DRAFT.md
- Summary table: business | repo | demo URL | status
- First site paused at Gate C before batch continues
```

---

## Acceptance checklist

- [ ] Plan criteria met with QA evidence  
- [ ] Unique vs other batch sites  
- [ ] PR open; CI green; human review path respected  
- [ ] `EMAIL_DRAFT.md` human-sounding  
- [ ] Tags updated  
- [ ] Batch summary table written  
- [ ] First of batch stopped for **Gate C**  

---

## End of pipeline

After Gate C and remaining builds: send emails only with human approval. Demos support negotiation — they are not a substitute for a signed engagement.
