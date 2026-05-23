# 6. Cline

- **Domain:** cline.bot
- **OpenRouter rank:** #6 (24.8B tokens / week — 680B cumulative since Oct 2024, #9 daily global, #2 in IDE Extensions)
- **Category:** dev-productivity
- **Prospect status:** PROSPECT (with caveats — see notes)

## Founder / contact
- **Founder(s):** Saoud Rizwan (Founder/CEO) — originally released as "Claude Dev" June 2024, renamed Cline October 2024. Co-founder per Latent Space podcast: Nik Pash.
- **Email:** s******@cline.bot (RocketReach-masked; pattern suggests `saoud@cline.bot` — high confidence but not publicly verified)
- **LinkedIn:** https://www.linkedin.com/in/saoud-rizwan/
- **Twitter/X:** https://x.com/sdrzn
- **GitHub:** https://github.com/saoudrizwan (personal) / https://github.com/cline/cline (project, 61k+ stars)
- **Sources:** RocketReach, LinkedIn, GitHub, Latent Space podcast, cline.bot/blog (Series A $32M announcement led by Emergence Capital + Pace Capital)

## Bloat hypothesis
**Primary pattern:** #1 Uncached System Prompt + #2 Flagship-for-Easy + #8 Tool-Use Without Result Caching — a coding-agent triple-hit.

**Evidence:**
- GitHub Discussion #9892 ("Enable Prompt Caching for Claude Code Provider") confirms `supportsPromptCache: false` is set for all Claude Code models in `src/shared/api.ts`. Users in that thread document "slower response times due to re-processing full context every turn" and contrast against native Claude Code achieving ~90-96% cache hit rates. **This is documented bloat, not hypothesis** — they know about it; it's a config flag away.
- 308 models used on OpenRouter means many users self-route, but the headline volume is overwhelmingly going to flagship Sonnet/Opus/GPT-5 class models. Their own blog post "One API key for Claude, Gemini, GPT, and everything else" doesn't describe any internal task-class routing — it's a credential-aggregator, not a model-router.
- Cline Kanban (May 2026) and Cline SDK launches suggest agentic loops running tools repeatedly. No published architecture for tool-result memoization → same `read_file`, same `ls`, same `grep` re-injected into context every turn.
- 24.8B tokens/week → conservative-estimate-with-Sonnet pricing puts weekly inference burn in the $25-75K range pre-discount. Prompt caching alone (10% read-cost vs 100% on Anthropic) on a coding agent with a stable preamble = 50-80% of input cost recoverable.

**Estimated savings:** 50-70% on Anthropic-routed input tokens via cache_control flag flip + audit. Tool-result memoization layer on top: another 20-40% on agent-loop traces.

## Day-0 cold email
**Subject:** Cline on OpenRouter — quick observation

**Body:**

```
Hi Saoud,

Cline showed up at #6 on the OpenRouter rankings this week (~25B tokens) — congrats, that's a real spend signal.

Hypothesis from the outside: GitHub discussion #9892 has users documenting that supportsPromptCache: false is still set for the Claude Code provider in src/shared/api.ts, and they're seeing the re-processing latency every turn. If that's still true in main, an Anthropic cache_control flag flip on the stable preamble + tool-defs is in the 50-70% input-cost range on the Sonnet/Opus share.

Could be wrong — maybe it's already shipped in a branch I missed. But it's the pattern I see most on coding agents the size of yours.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 min on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation. If there's nothing there, we shake hands and move on.

cal.com/matt-culpepper/token-audit if it's interesting.

Matt
```

## Priority score
**Score:** 7/10

**Rationale:** High token volume + documented bloat in a public GitHub discussion = very high signal-to-noise for the opener. BUT — Cline just raised $32M Series A (Emergence + Pace), they have a real eng team, they likely already know this gap and have a roadmap reason for not fixing it (OAuth-token Claude Code subscription model interactions, vendor-neutrality concerns per their "Architects or Tenants" blog post). Lowered from 9 to 7 because the rational counter — "we're well-funded and already aware" — is high. Still worth the email because the specific reference (discussion #9892) makes it credible.

## Notes for Matt
- The Anthropic OAuth-token / Claude Code provider issue is a known thorny one — Anthropic blocks subscription tokens outside their official CLI. Cline may have intentionally disabled caching there because the SUPPORTED path (BYO API key with caching enabled) is the one they care about; the OAuth path may be a deliberate second-class citizen. Worth reading discussion #9892 in full before the call if Saoud bites.
- They just raised $32M. They have a paid eng team. The pitch can't be "we'll save you money" — it has to be "you have a publicly visible perf gap that users are complaining about in your own GitHub, and a 20-min outside read might catch what's politically hard to surface internally."
- Their blog post "Architects or Tenants" reads like Saoud cares about vendor independence and infrastructure ownership — a *Ruby-dev-from-Mississippi-with-infra-background* identity will resonate. Don't lead with $$$; lead with the patterns.
- Twitter @sdrzn is active and engineering-flavored — LinkedIn DM as fallback if Day-4 email doesn't land. Twitter DM as last-resort only.
- Don't pitch the Cline Kanban orchestration angle — that's their own product surface; coming in with "let me optimize your shiny new thing" reads as condescending.
