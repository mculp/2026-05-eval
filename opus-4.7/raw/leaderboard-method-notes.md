# OpenRouter Leaderboard Scrape — Method Notes

**Date:** 2026-05-23
**Goal:** 30 verified high-intent B2B / Productivity AI apps using OpenRouter for prospecting outreach.
**Result:** 30 verified entries written to `leaderboard-top30.json`.

## URLs fetched

1. `https://openrouter.ai/rankings` — JS-rendered shell only; no app data in HTML (page lists only the five ranking-category headers: Top Models, Market Share, Tool Calls, Images, Audio Input). Unusable as a primary source.
2. `https://openrouter.ai/rankings/productivity` — same shell-only behavior.
3. `https://openrouter.ai/rankings/programming` — same.
4. `https://openrouter.ai/apps` — **primary source.** Returns app rankings 1-20 with token counts (e.g. Hermes Agent 419B, OpenClaw 148B, Kilo Code 143B), one-line descriptions, and category tags. Header says "1–20 of 60".
5. `https://openrouter.ai/apps/category/coding` — **secondary source.** Returns coding-category ranks 1-44 with domains, token counts, descriptions. This is where most of the dev-productivity picks came from.
6. `https://openrouter.ai/apps/category/productivity` — **secondary source.** Returns productivity-category ranks 1-38 with domains, tokens, descriptions. This was the goldmine for non-coding B2B picks (extra.email, BuddyPro, Gobii, Vectoron, TimeCamp, etc.).
7. `https://openrouter.ai/rankings/apps`, `https://openrouter.ai/apps?page=2`, `https://openrouter.ai/apps?offset=20` — all attempted to extract apps 21-60; all returned the same JS-shell-only response. Pagination is client-side rendered. The category endpoints (`/apps/category/...`) are how to dig beyond the top 20.
8. `https://openrouter.ai/apps?category=Roleplay` — confirmed exclusions: Janitor AI (#8), SillyTavern (#3 entertainment), ISEKAI ZERO (game/character).

Domain validation via WebSearch (one query per ambiguous entry) — every entry in the final 30 has a search-result-confirmed live website.

## Filtering decisions

**INCLUDED:**
- Pure dev-productivity tools (Kilo Code, Cline, Roo Code, Claude Code, Codex, Aider, OpenHands, Crush, Qwen Code, Codebuff, Zed) — all clearly B2B with paying or freemium revenue.
- Dev-infrastructure that's clearly B2B (LangChain, Portkey, Vellum, Dify) — these are platform plays with enterprise customers.
- Workplace SaaS productivity (Descript, extra.email, GPT Workspace, TimeCamp, Gobii, Vectoron, BuddyPro) — note-taking/email/scheduling/document/marketing.
- Self-hosted enterprise chat (Open WebUI, LibreChat) — included because the OSS-self-host story is increasingly common B2B procurement.
- Multi-tool agents with B2B angles (Hermes Agent, OpenClaw, Mira) — flagged ambiguous because they straddle consumer + pro use.
- Chrome-extension AI assistants with paid plans (T3 Chat, Novelcrafter) — flagged ambiguous (clearly used by individuals, but pricing tiers and Theo's "for teams" framing make them legit B2B prospects).

**EXCLUDED with reason:**
- **Janitor AI** (#8 global, 26.9B tokens) — explicit roleplay/character chatbot. Per ICP filter.
- **ISEKAI ZERO** (#9 global, 26.7B tokens) — "AI adventures, travel with your favorite characters." Game/roleplay category.
- **SillyTavern** (entertainment #3, 7.64B tokens) — "LLM frontend for power users… roleplay." Per ICP filter.
- **pi** (#6 global, 34.3B tokens) and pi (#33, #41 forks) — "There are many coding agents, but this one is yours." Couldn't pin down whether this is an actual company/website or an OpenRouter internal/test app. Description reads like a personal/private fork. **Dropped to preserve real-data integrity** (would need to mark domain_verified false and I'd rather use the slot for a verified app).
- **Relay v2 multi-turn QA** (#7 global, 27.6B tokens) — domain shown as `specific-labs.local` (literal .local TLD, internal/test). **Almost certainly an OpenRouter eval harness, not a customer app.**
- **VoyagerToken** (#14, 17.7B tokens, voyager.com) — "VoyagerToken" reads like a crypto/token app rather than B2B productivity; the voyager.com domain is the bankrupt crypto exchange. Likely a brand collision, not the target ICP. Dropped.
- **Pioneer (production)** (#15, 16.6B tokens, pioneer.ai) — Fastino Labs fine-tuning agent. **Legitimately B2B dev-infra**, but the description ("fine-tuning agent for open-source SLMs") sits squarely in research/MLOps tooling that's likely already deep-integrated with Anthropic/OpenAI direct, not the OpenRouter-using-customer ICP we want. Borderline — dropped for the rank-30 slot in favor of the cleaner TimeCamp pick.
- **Ethos AI Evals** (#11, 22.5B tokens, agent.askethos.com) — confirmed real (a16z + General Catalyst backed, expert-network play), but the OpenRouter usage is "Ethos AI Evals" — likely their internal eval pipeline, not a customer-facing app surface. Different conversion intent for outreach. Dropped from top-30 but worth a separate look.
- **VidMuse** (#17, 12.7B tokens) — video-generation tool, creative-tier not productivity B2B.
- **opengateway** (#19, 12.5B tokens, opengateway.gitlawb.com) — looks like a personal/test gateway clone, not a commercial product. Suspect.
- **Lemonade** (#7 coding, 20.2B tokens, lemonade.gg) — AI tool for **Roblox** game-building. Clearly a creative/gaming tool, not productivity B2B. Excluded.
- **Studs.gg** (#12 coding, 4.23B tokens) — same as Lemonade, Roblox game-building. Excluded.
- **GDevelop** (#15 coding, 2.88B tokens) — AI-assisted game engine. Game-dev, not productivity B2B.
- **App/Chatly walbi.com** (#29 productivity) — "crypto futures trading with AI signals." Not productivity, and crypto-trading falls outside the ICP.
- **Modmixer / starchild / Tavo / Holaboss API / Supsis AI / BavarOS / Forgely / dodaLLM / Aexol Studio / Favur / Opair / Joni / Postqode / Slate Agent / camelAI / MiroShark / Ampere / Ethoswarm** — couldn't verify enough about these to confidently slot them. They appear in the lower ranks (sub-1B token) and most have either bare-bones websites or pre-revenue product pages. A second-pass enrichment lane could verify and add them; for the rank-30 cap I prioritized verified, brand-recognized B2B players over volume.
- **OpenSquilla** (#20 coding/#11 productivity) — couldn't verify the company beyond the opensquilla.ai redirect. Skipped.
- **GitHub-hosted tools without distinct websites** (nanobot, Open WebUI plugin, Kern Agent, Qwen Code is borderline — kept since qwenlm.github.io is the canonical docs URL) — generally excluded when no clear company/product page exists.

## Data peculiarities / surprises

- **Hermes Agent dethroned OpenClaw on May 10** as #1 — Hermes is at 419B tokens vs OpenClaw 148B, a 2.8x lead. The TechTimes piece confirmed the dethroning.
- **Roo Code shut down May 15** — search results note the project was discontinued; the community fork is "ZooCode." This is a flag for outreach: the 17.8B token volume may be migrating right now. Worth treating Roo Code as a re-routable target audience (their users are looking for an alternative).
- **The 1B-tokens-per-week threshold** roughly corresponds to ~$1k-10k/mo OpenRouter spend depending on model mix, so even the bottom of this list represents meaningful real usage.
- **The productivity category has more ambiguous entries** than coding. Coding category is cleanly B2B (developers paying for tools). Productivity blurs consumer+pro (Mira, extra.email, T3 Chat, Novelcrafter all have individual + team plans).
- **No dedicated CRM/sales-tech apps on the leaderboard** at the volumes we'd expect — surprising. Tools like Apollo, Clay, Outreach don't appear (likely they're calling OpenAI/Anthropic direct, not via OpenRouter).
- **No vertical AI** (legal/medical/finance/accounting) cleared the OpenRouter ranking threshold either — Vectoron (healthcare marketing) is the closest, and even it's marketing-of-healthcare rather than clinical AI. The vertical-AI ICP is largely absent from OpenRouter's top apps. Implication for outreach strategy: this list skews dev-productivity + horizontal-SaaS, not vertical-deep.

## What I could not determine

- **No raw token counts past rank 38** in the productivity category and rank 44 in coding. The 60-app total is shown in the UI header but the deeper ranks weren't surfaced by any URL variation I tried. For a full top-60 sweep, would need either Selenium/Playwright or OpenRouter's API if they expose one.
- **Model-mix data** is largely absent from OpenRouter's app pages. Where the JSON shows `model_mix`, I sourced it from the company's own marketing/docs (e.g. Kilo Code claims Claude Sonnet 4.6 + GPT-5.4 + Gemini 3.1; Crush claims OpenAI/Anthropic/Groq/Gemini/Bedrock/Azure). Where I couldn't verify, `model_mix: null`.
- **Whether OpenRouter's "tokens" count is weekly or all-time** — the UI text "Weekly usage of models across OpenRouter" suggests weekly, and the magnitudes (419B for #1) are consistent with weekly aggregated traffic. Caveats noted in the JSON as "week of 2026-05-16" inferred.

## Gap report

- **30/30 verified.** No fabricated domains, no `domain_verified: false` entries.
- **Could expand to ~40-45 verified** with another verification pass on the borderline drops (Pioneer, Ethos, OpenSquilla, the cluster of sub-1B productivity apps).
- **Ambiguous-ICP flagged on 7 entries:** Hermes Agent, OpenClaw, Mira, Open WebUI, extra.email, LibreChat, T3 Chat, Novelcrafter. These all have plausible B2B revenue but also significant individual/consumer use. Worth a custom outreach angle vs the cleanly-B2B ones.
