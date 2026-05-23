# OpenRouter Leaderboard Outreach Pipeline — 2026-05-23

A compiled 30-prospect B2B outreach pipeline built from the OpenRouter `/apps` leaderboard, an inference-bloat playbook, and a per-app personalization pass.

**Total prospects:** 30
**Breakdown:**
- PROSPECT — 23
- NON-PROSPECT — 4 (Claude Code, Codex, Open WebUI, Qwen Code)
- CONFLICT-OF-INTEREST — 2 (OpenClaw, Portkey AI)
- SHUT-DOWN — 1 (Roo Code)

## How this was built

1. **Leaderboard scrape** — pulled top apps from `https://openrouter.ai/apps` + `/apps/category/coding` + `/apps/category/productivity` (other endpoints are JS-shell-only). Output: [`raw/leaderboard-top30.json`](raw/leaderboard-top30.json) with method notes in [`raw/leaderboard-method-notes.md`](raw/leaderboard-method-notes.md).
2. **Bloat playbook** — distilled 10 inference-bloat patterns from public engineering write-ups + vendor pricing docs. See [`research/bloat-playbook.md`](research/bloat-playbook.md).
3. **Outreach templates** — drafted 4 reusable templates (Day-0 email, Day-4 nudge, Day-10 breakup, LinkedIn DM) tuned to Matt's voice. See [`research/outreach-templates.md`](research/outreach-templates.md).
4. **6 parallel lanes** — split the 30 into batches of 5, each lane did founder/contact research, picked the strongest bloat hypothesis, drafted the Day-0, and scored priority 1-10.
5. **Compiled** — this README + [`pipeline.csv`](pipeline.csv) roll everything up into a CRM-importable shape.

## The bloat catalog (TL;DR)

One-line summary of each of the 10 patterns in [`research/bloat-playbook.md`](research/bloat-playbook.md):

1. **Uncached System Prompt** — long static prefix sent fresh on every call; no `cache_control`. 50-90% input-cost cut available.
2. **Flagship-for-Easy** — Sonnet/Opus/GPT-5 used for every task including classification, reranking, formatting. 60-85% on routable share.
3. **Full-Context Stuffing** — "200k context" used as a feature instead of a budget; whole codebase/docs loaded per turn instead of RAG. 80-95% on retrieval-amenable workloads.
4. **No Batch API for Async Jobs** — overnight digests, bulk classification, eval runs hitting realtime endpoints. Vendor-documented 50% off.
5. **No Semantic Cache on Repeat Sub-Prompts** — same intents arriving across users with no cosine-sim cache hit. 30-70% on cacheable share.
6. **Streaming on Aborted UIs** — `stream: true` everywhere even on form-fill / structured-output surfaces. 5-15% on abort-prone surfaces.
7. **No Eval Gate on Model Swap** — defaults to flagship "to be safe" because there's no offline harness to prove smaller is fine. Unblocks patterns 2, 8, 10.
8. **Tool-Use Without Result Caching** — agent loop re-bills identical tool results (web search, file read, SQL) every turn. 20-50% on agentic workloads.
9. **Re-Embedding Identical Chunks** — ingestion re-embeds byte-identical content on every sync. 60-95% of embedding cost.
10. **Verbose System Prompts** — prompt accreted over a year, 4k tokens of mostly-redundant rules. 30-60% of system-prompt tokens recoverable via compression.

## Outreach templates (TL;DR)

One-line summary of each of the 4 templates in [`research/outreach-templates.md`](research/outreach-templates.md):

1. **Cold Email, Day 0** — `{{APP_NAME}} on OpenRouter — quick observation`. Subject + body lean on a public verifiable observation; "could be wrong" inoculates against defense reaction.
2. **Email Nudge, Day 4** — `re: {{APP_NAME}} on OpenRouter — one more thought`. Reply-thread subject + pre-commit to a breakup ("I'll stop after this") boosts reply rates.
3. **Breakup Email, Day 10** — `closing the loop on {{APP_NAME}}`. Passive offer with the Cal link in sign-off; founders reply because the pressure is off.
4. **LinkedIn DM (with connect)** — 300-char connect note + substantive follow-up DM 1-2 days after acceptance. EU founders skew LinkedIn-primary.

## Top 10 prospects (ranked by priority score)

| # | App | Founder | Channel | Bloat hypothesis (1-line) | Why-this-priority | File |
|---|---|---|---|---|---|---|
| 1 | Kilo Code | Scott Breitenother | LinkedIn | Pattern #5 semantic-cache + #3 codebase-stuffing on KiloClaw hosted tier | Real margin pressure on KiloClaw + reachable operator-CEO + 6T tokens/mo self-reported volume + recent $8M raise = budget for a fixer | [outreach/03-kilo-code.md](outreach/03-kilo-code.md) |
| 2 | Ito | Barron Caster | LinkedIn | Pattern #8 tool-use without result caching across agentic QA re-runs | Token-heavy by product design (agent loops + computer-use), pre-seed = runway-sensitive, specific hypothesis lands credibly | [outreach/14-ito.md](outreach/14-ito.md) |
| 3 | Gobii | Andrew Christianson | LinkedIn | Pattern #8 tool-result caching (same scrapes across users) + DeepSeek prompt-cache markers | Already cost-conscious (DeepSeek-default blog) but easy wins are taken — second-order patterns land with an engineer-founder | [outreach/26-gobii.md](outreach/26-gobii.md) |
| 4 | Hermes Agent | Jeffrey Quesnelle | Email (jeff@jeffq.com) | Pattern #4 Atropos trajectory pipeline = textbook Batch API workload | #1 OpenRouter app + verified personal CEO email + Atropos public-facing claim maps directly to vendor batch discount | [outreach/01-hermes-agent.md](outreach/01-hermes-agent.md) |
| 5 | Mira | Daria Yakovleva | LinkedIn | Pattern #2 (intra-provider routing) + Pattern #5 (top-intent semantic cache) on 500k MAU consumer chat | Steep growth curve + TOP/f4-backed = pre-fundraise pressure to look efficient; hypothesis is mechanically tied to product shape | [outreach/08-mira.md](outreach/08-mira.md) |
| 6 | OpenHands | Robert Brennan | LinkedIn | Pattern #2 CodeAct loop running Sonnet end-to-end when 3 of 4 sub-steps are Haiku-tier | Public eval harness = safe path to ship a router; Graham Neubig on team = eval rigor in DNA; hosted-tier margin pressure | [outreach/18-openhands.md](outreach/18-openhands.md) |
| 7 | GPT Workspace | unknown (Pulkit Goyal unverified) | Twitter | Pattern #1 + #2 — $9.99/mo "unlimited Opus/GPT-5/Gemini Pro" upside-down pricing | Cleanest unit-economics pitch in the batch; flat-price-on-flagship is the textbook bloat target — BUT contact gap is severe | [outreach/23-gpt-workspace.md](outreach/23-gpt-workspace.md) |
| 8 | Vectoron | Mike Myles | LinkedIn | Pattern #4 — entire async pipeline running realtime endpoints | Multi-stage healthcare content pipeline × low-margin vertical-agency model = audit converts cleanly; 50%-off-printed-on-vendor-page savings | [outreach/29-vectoron.md](outreach/29-vectoron.md) |
| 9 | Crush | Christian Rocha | Email (vt52@charm.land) | Pattern #2 — default Catwalk picker surfaces flagships; no cheap-step router in agent loop | Verified enterprise inbox + $6M funded + "publishable preset" angle fits Charm's glamorous-open-source brand | [outreach/22-crush.md](outreach/22-crush.md) |
| 10 | TimeCamp | Kamil Rudnicki | LinkedIn | Pattern #4 (TIC batch-shaped categorization on realtime endpoints) + Pattern #5 (heavy app+title repeat across users) | Mature SaaS 4000+ customers × per-transaction categorization = high steady-state spend; mature CFOs care about COGS | [outreach/30-timecamp.md](outreach/30-timecamp.md) |

## Full pipeline table (all 30, sorted by priority score desc)

| OR-rank | App | Founder | Channel | Status | Priority | File |
|---|---|---|---|---|---|---|
| 3 | Kilo Code | Scott Breitenother | linkedin | PROSPECT | 9 | [outreach/03-kilo-code.md](outreach/03-kilo-code.md) |
| 14 | Ito | Barron Caster | linkedin | PROSPECT | 9 | [outreach/14-ito.md](outreach/14-ito.md) |
| 26 | Gobii | Andrew I. Christianson | linkedin | PROSPECT | 8.5 | [outreach/26-gobii.md](outreach/26-gobii.md) |
| 1 | Hermes Agent | Jeffrey Quesnelle | email | PROSPECT | 8 | [outreach/01-hermes-agent.md](outreach/01-hermes-agent.md) |
| 8 | Mira | Daria Yakovleva | linkedin | PROSPECT | 8 | [outreach/08-mira.md](outreach/08-mira.md) |
| 18 | OpenHands | Robert Brennan | linkedin | PROSPECT | 8 | [outreach/18-openhands.md](outreach/18-openhands.md) |
| 23 | GPT Workspace | unknown (Pulkit Goyal unverified) | twitter | PROSPECT | 8 | [outreach/23-gpt-workspace.md](outreach/23-gpt-workspace.md) |
| 29 | Vectoron | Mike Myles | linkedin | PROSPECT | 8 | [outreach/29-vectoron.md](outreach/29-vectoron.md) |
| 22 | Crush | Christian Rocha | email | PROSPECT | 7.5 | [outreach/22-crush.md](outreach/22-crush.md) |
| 30 | TimeCamp | Kamil Rudnicki | linkedin | PROSPECT | 7.5 | [outreach/30-timecamp.md](outreach/30-timecamp.md) |
| 4 | Descript | Laura Burkhauser | linkedin | PROSPECT | 7 | [outreach/04-descript.md](outreach/04-descript.md) |
| 6 | Cline | Saoud Rizwan | email | PROSPECT | 7 | [outreach/06-cline.md](outreach/06-cline.md) |
| 12 | Zed Editor | Nathan Sobo | linkedin | PROSPECT | 7 | [outreach/12-zed-editor.md](outreach/12-zed-editor.md) |
| 20 | Dify.AI | Luyu Zhang | linkedin | PROSPECT | 7 | [outreach/20-dify-ai.md](outreach/20-dify-ai.md) |
| 25 | Novelcrafter | Leonie (last name unverified) | linkedin | PROSPECT | 7 | [outreach/25-novelcrafter.md](outreach/25-novelcrafter.md) |
| 28 | Vellum | Akash Sharma | linkedin | PROSPECT | 7 | [outreach/28-vellum.md](outreach/28-vellum.md) |
| 15 | extra.email | Naveen Gavini | linkedin | PROSPECT | 6 | [outreach/15-extra-email.md](outreach/15-extra-email.md) |
| 16 | BuddyPro AI | David Říha | linkedin | PROSPECT | 6 | [outreach/16-buddypro-ai.md](outreach/16-buddypro-ai.md) |
| 21 | LibreChat | Danny Avila | email | PROSPECT | 6 | [outreach/21-librechat.md](outreach/21-librechat.md) |
| 24 | T3 Chat | Theo Browne | twitter | PROSPECT | 6 | [outreach/24-t3-chat.md](outreach/24-t3-chat.md) |
| 27 | Aider | Paul Gauthier | email | PROSPECT | 5.5 | [outreach/27-aider.md](outreach/27-aider.md) |
| 9 | LangChain | Harrison Chase | email | PROSPECT | 5 | [outreach/09-langchain.md](outreach/09-langchain.md) |
| 17 | Codebuff | James Grugett | twitter | PROSPECT | 5 | [outreach/17-codebuff.md](outreach/17-codebuff.md) |
| 11 | Portkey AI | Rohit Agarwal | linkedin | CONFLICT-OF-INTEREST | 4 | [outreach/11-portkey-ai.md](outreach/11-portkey-ai.md) |
| 13 | Open WebUI | Timothy Baek | none | NON-PROSPECT | 3 | [outreach/13-open-webui.md](outreach/13-open-webui.md) |
| 2 | OpenClaw | Peter Steinberger | none | CONFLICT-OF-INTEREST | N/A | [outreach/02-openclaw.md](outreach/02-openclaw.md) |
| 5 | Claude Code | Anthropic | none | NON-PROSPECT | N/A | [outreach/05-claude-code.md](outreach/05-claude-code.md) |
| 7 | Roo Code | Matt Rubens | none | SHUT-DOWN | 0 | [outreach/07-roo-code.md](outreach/07-roo-code.md) |
| 10 | Codex | OpenAI | none | NON-PROSPECT | 0 | [outreach/10-codex.md](outreach/10-codex.md) |
| 19 | Qwen Code | Alibaba | none | NON-PROSPECT | 0 | [outreach/19-qwen-code.md](outreach/19-qwen-code.md) |

## Channel mix observation

Across the 23 PROSPECT entries:

- **LinkedIn primary** — 14 (~61%)
- **Email primary** — 6 (~26%)
- **Twitter/X primary** — 3 (~13%)

**LinkedIn is dominant.** That tracks with the leaderboard skew toward European/Czech/German/Polish founders (Daria/David/Leonie/Luyu/Kamil), founder LinkedIn pages outranking email-visibility for ex-Pinterest / ex-McKinsey / ex-product-design CEOs, and the broader pattern that founder personal emails are rarely surfaced publicly. Email-first works when the founder has a personal site (Jeff Quesnelle, Harrison Chase) or a verified enterprise inbox (Charm's `vt52@charm.land`). Twitter is the right channel for the three highly-online dev personalities (Theo Browne, James Grugett, and the @gpt_workspace anon team).

## Non-prospects / quirks worth Matt's eyes

- **02 OpenClaw — CONFLICT-OF-INTEREST.** We use OpenClaw as our fleet runtime; pitching them is a COI. Compounded by Peter Steinberger joining OpenAI and OpenClaw becoming an independent foundation — corporate prospect surface is dissolving anyway. Right play is an upstream PR adding `cache_control` markers, not a sales email.
- **05 Claude Code — NON-PROSPECT (vendor).** Anthropic publishes the cost-optimization patterns the playbook is derived from. Pitching them an inference-cost audit would burn cold-outreach credibility.
- **07 Roo Code — SHUT-DOWN 2026-05-15.** Extension archived; team pivoted to Roomote cloud agent. The actual play is the migration cascade — Kilo Code (already in this batch at rank 3) is absorbing the largest share of the 3M displaced users.
- **10 Codex — NON-PROSPECT (vendor).** OpenAI sells the tokens; they don't buy bloat audits. The OpenRouter footprint is users routing non-OpenAI models through OpenAI's CLI tool, which is mildly funny but generates no outreach value.
- **11 Portkey AI — CONFLICT-OF-INTEREST.** They SELL the inference-optimization stack (gateway, observability, semantic cache, prompt mgmt). Treat as peer/partnership lane — Matt audits, Portkey is the natural fix-implementation partner. Don't pitch as a customer.
- **13 Open WebUI — NON-PROSPECT for direct revenue / community play instead.** Self-hosted users pay their own token bills; Open WebUI doesn't. The angle is contributing a default-configs PR that saves 355k+ deployments money — portfolio piece + community credibility, not paid work.
- **19 Qwen Code — NON-PROSPECT (vendor).** Alibaba's own CLI around Qwen3-Coder — they own the inference stack, no bill to optimize.

## Fact-check corrections that came up during research

These are surprising facts that emerged from the per-app research lanes — flagged here so Matt sees them once instead of re-deriving each time:

1. **extra.email investor list (15-extra-email.md):** The original lane brief listed a16z as an investor. Public sources actually substantiate **Felicis Ventures (lead), Abstract Ventures, A*, and Elad Gil** — a16z is NOT confirmed as an investor and was dropped from the file. Angel list includes Ben Silbermann + Evan Sharp (Pinterest co-founders), Paul Buchheit (Gmail), Fidji Simo, Shishir Mehrotra, Gokul Rajaram, Scott Belsky, Guillermo Rauch.
2. **GPT Workspace founder unverified (23-gpt-workspace.md):** The lane brief named "Pulkit Goyal" as founder. Could not verify a Pulkit Goyal connected to gpt.space through public sources — multiple Pulkit Goyals exist on LinkedIn, none with a confirmable gpt.space link. The GitHub org maintainer credit in some Chrome Store mirrors is "Qualtir Group Account" (also unverified). **Confirm founder identity via Chrome Web Store developer-contact field before sending any outreach.**
3. **Novelcrafter founder is Leonie, not "Bjorn Granitza" (25-novelcrafter.md):** The lane brief named "Bjorn Granitza" as founder. Novelcrafter's own About page identifies **Leonie (Founder and Developer, Germany)** — last name not publicly surfaced. LinkedIn search for "Bjorn Granitza Novelcrafter" returned zero matches. Confirm Leonie's last name via the Novelcrafter company LinkedIn page or German company registry (Novelcrafter UG, Hamburg) before sending.
4. **OpenClaw foundation transition + Peter Steinberger to OpenAI (02-openclaw.md):** Peter Steinberger has publicly announced he is joining OpenAI, and OpenClaw is becoming an independent foundation per his own blog post. Combined with the existing fleet COI, this changes the prospect surface entirely. Any future "openclaw outreach" reasoning should treat the founder transition as a load-bearing fact.

## Next steps

What Matt would do tomorrow morning with this:

1. **Ship the top-3 highest-priority + lowest-friction first.** In order: (a) **Hermes Agent / Jeffrey Quesnelle** — verified personal email at `jeff@jeffq.com`, Day-0 already drafted, no contact-discovery work required; (b) **Kilo Code / Scott Breitenother** — LinkedIn connection request + 1-2 day delay + follow-up DM (Template 4); (c) **Ito / Barron Caster** — LinkedIn DM. That's the three highest-leverage sends with zero blockers.
2. **Resolve the 3 founder-identity gaps before sending those lanes.** Verify Leonie's last name (25-novelcrafter), confirm or replace the GPT Workspace founder (23-gpt-workspace), and confirm the Mike Myles LinkedIn match for Vectoron (29-vectoron). Each is ~5 min of LinkedIn / Chrome Store / German registry verification.
3. **Run `git log --format='%ae' | sort -u` on 3 OSS repos** — LibreChat (21), OpenHands (18), Aider (27) — to surface verified founder commit emails before deciding email-vs-LinkedIn for those lanes. Quick win that converts 3 prospects from LinkedIn-only to email-primary.
4. **Treat the COI / partnership prospects (Portkey, Vellum) as a separate lane.** Both could become referral partners — Portkey for fix-implementation, Vellum for enterprise-customer audit referrals. That's a different cadence (3-week follow-up, peer-engineer frame) than the cold-audit pitch and should be batched together.
5. **Spawn a follow-on lane for the displaced Roo Code user base.** Already partly absorbed by Kilo (rank 3 in this list). The other migration destinations — Continue.dev, Bodega One — deserve their own slot if Matt wants to ride the cascade. Track in the same `runbooks/outreach/` directory.
