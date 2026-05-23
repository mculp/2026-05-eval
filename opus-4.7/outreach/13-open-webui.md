# 13. Open WebUI

- **Domain:** openwebui.com
- **OpenRouter rank:** 13
- **Category:** Self-hosted AI chat platform (open-source, B2B via enterprise infra)
- **Prospect status:** NON-PROSPECT for direct token-audit (their users pay token costs via BYO-key, not Open WebUI itself). Possible partnership angle: better default model configs that ship with Open WebUI saves their downstream users money — that's a credibility win, not a direct revenue line for Matt.

## Founder / contact

- **Tim Jaeryang Baek (Timothy Baek)** — Founder & lead maintainer. LinkedIn: https://www.linkedin.com/in/tjbaek/ (verified). GitHub: https://github.com/tjbck. Personal site: https://timbaek.com/. Mozilla Builders alum (project + personal profiles). Education: UoL CS (First-Class Honors), MSc Computer Science Simon Fraser University.
- **Project history:** Started as "Ollama WebUI" Sept 25, 2023; renamed to Open WebUI Jan 2024 as it grew beyond Ollama to support OpenAI-compatible APIs + RAG. As of Mar 2026: 128k+ GitHub stars, 355k+ community members.
- **Repo:** https://github.com/open-webui/open-webui
- **Contact:** website 403's on direct fetch (some kind of bot protection). GitHub issues/discussions is the real contact surface. Tim is publicly responsive on GitHub.
- **Founder email:** not directly listed on landing pages; likely available via GitHub commit history (`git log --format='%ae' | sort -u` on the repo would surface it) — Matt should pull it that way rather than guess.

## Bloat hypothesis

Open WebUI is self-hosted: their users run it on their own infra, point it at their own API keys (Ollama local, OpenAI, OpenRouter, Anthropic, etc). Open WebUI itself doesn't pay for inference. So "bloat" in the conventional audit sense doesn't apply to Open WebUI as a customer.

The reframe lane Matt should pitch instead: **Open WebUI ships DEFAULTS to 355k+ deployments. The default model selection, default RAG config, default system prompt, default chunking strategy — these are downstream cost multipliers for every user.** A small improvement in defaults (e.g. flipping the default RAG retriever from "stuff 20 chunks" to "stuff 5 chunks with re-rank") saves real money across hundreds of thousands of deployments.

Three specific levers:
1. **Default RAG config (pattern 3, Full-Context Stuffing).** If Open WebUI's default "Knowledge" feature stuffs more context than needed, every user is overpaying. A re-rank + lower-K config saves 60-80% on retrieval-amenable workloads downstream.
2. **System prompt template (pattern 1 + pattern 10).** Whatever default system prompt ships in Open WebUI gets shipped to OpenAI/Anthropic with no `cache_control` markers on the static portion. Adding cache hints to the shipped default would let every API-using deployment benefit from prompt caching automatically.
3. **Default model selection per feature** (pattern 2). The "Title generation" and "Tags generation" features in Open WebUI default to the user's selected chat model — likely Sonnet/Opus/GPT-5. Tagging is a Haiku task. Shipping a smaller default for title/tag gen would save downstream users money without UX impact.

**Pitch angle:** "I'd love to contribute a PR that improves the default configs your users inherit. Cost optimization as a community win, not a service sale." This positions Matt as a peer contributor, not a vendor.

## Day-0 cold email

**Subject:** `Open WebUI defaults — community contribution offer`

**Body:**

```
Hi Tim,

Open WebUI showed up on the OpenRouter rankings this week, which is wild given the self-hosted-first model — that's a real spend signal from your downstream users, not from you.

Outside hypothesis: the default configs Open WebUI ships (RAG K-value, title/tag generation model selection, system prompt template with no cache_control markers) are quietly costing your downstream users 30-60% more than they need to. Aggregate across 355k+ community members and that's real money you could save your users with 2-3 default-config PRs.

I run a small consultancy doing token-bloat audits, but this isn't a sales pitch — I'd genuinely love to contribute a PR or two improving the shipped defaults. Ruby/infra background, peer-to-peer.

If a "default configs audit + PR" sounds useful, happy to scope on GitHub. Or 20 min on Zoom and I write up the 2-3 patterns I'd dig into first — your call.

Matt
```

## Priority score

**Priority: 3/10 for direct revenue, 6/10 as a community/credibility play**

- Open WebUI doesn't pay for inference themselves — direct audit-and-fix lane doesn't apply.
- BUT a contributed PR to a 128k-star repo is enormous credibility signal for Matt's audit lane — proof he can ship the fixes, not just diagnose. The downstream cost-savings story across 355k+ deployments is a compelling case study Matt can show OTHER prospects.
- Tim is solo-ish (lead maintainer with a small core team per Mozilla Builders profile) and responsive on GitHub. Lower friction than a VC-backed founder dance.
- Lower priority for immediate revenue, but high priority as a portfolio/credibility play.

## Notes for Matt

- **Don't email-pitch this one as a customer.** Open the conversation on GitHub Discussions or directly via a PR that proposes a config improvement. That's the culture here.
- The Mozilla Builders profile (https://builders.mozilla.org/profile/tim-jaeryang-baek/) suggests open-source-first values — paying for an audit isn't going to land. Contributing a fix DOES land.
- Concrete first PR ideas to scope: (a) ship `cache_control` hints on the default system prompt for Anthropic backends, (b) lower the default RAG K-value and add re-rank by default, (c) ship a smaller default model selector for title/tag generation if user hasn't set one.
- Skip the Day-4/Day-10 nudge cadence here — that's for cold sales. For open-source contribution outreach, follow up via GitHub.
- Worth noting: Open WebUI's 403 on direct WebFetch means their site has some Cloudflare-tier bot mitigation — Tim's not someone who likes spam-pattern outreach. Lean even harder into the "I'm a contributor not a vendor" frame.
- This one is the "portfolio piece" play, not the "close a deal" play. Pitch accordingly.
