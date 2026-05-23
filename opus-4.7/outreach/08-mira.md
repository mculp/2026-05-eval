# 8. Mira

- **Domain:** mira.tg
- **OpenRouter rank:** #8 (12.7B tokens/week — #15 daily global, #3 in Productivity + Personal Agents, active since April 2026)
- **Category:** b2b-productivity (consumer-flavored but B2B-shaped via TOP/TON portfolio and integration count)
- **Prospect status:** PROSPECT

## Founder / contact
- **Founder(s):** Daria Yakovleva (CEO) — based in London, AI & Computer Science background, tech entrepreneur. Backed by The Open Platform (TOP, Telegram's venture arm) and f4 Fund (per [f4.fund/startups/mira-tg](https://f4.fund/startups/mira-tg)).
- **Email:** No public email found on mira.tg, mira.tg/blog, wiki.mira.tg, or LinkedIn. Likely accessible via Telegram (@mira admin route) or LinkedIn DM only.
- **LinkedIn:** https://www.linkedin.com/in/daria-yakovleva/ (500+ connections, "Mira" current role)
- **Twitter/X:** No personal handle surfaced from search; Mira's corporate angle via [@topdotco](https://x.com/topdotco/status/2020836050742981033)
- **GitHub:** https://github.com/Mira-Agent/ (org) — limited public code
- **Sources:** [Dataconomy 2026-05-20](https://dataconomy.com/2026/05/20/telegrams-ai-agent-ecosystem-mira/), [ITBrief launch story](https://itbrief.co.nz/story/mira-ai-agent-launches-inside-telegram-group-chats), [f4 Fund portfolio](https://f4.fund/startups/mira-tg), TOP/Telegram launch tweet

## Bloat hypothesis
**Primary pattern:** #2 Flagship-for-Easy + #5 No Semantic Cache on Repeat Sub-Prompts.

**Evidence:**
- Public docs: Mira "routes tasks across several AI providers, including OpenAI, Anthropic, Minimax, ByteDance and ElevenLabs, allowing the system to choose different models for different jobs." That's the *aspiration* — but only 25 models used per the OpenRouter profile (vs Cline's 308). 25 models concentrated on 12.7B tokens means the routing is real but coarse. The question is whether the *intra-provider* routing is tuned (Sonnet vs Haiku within Anthropic, GPT-5 vs Mini within OpenAI) or just inter-provider (Anthropic vs OpenAI as monolithic choices).
- Consumer chat product with **500k MAU doubling month-over-month**, 50k+ active groups, "summarize the chat" / "set a reminder" / "draft a reply" type interactions. These are textbook Haiku/Mini workloads getting silently routed to flagship because the routing dimension is *capability* not *complexity*.
- 900+ Composio app integrations means thousands of small structured-output calls per day (Google Calendar reads, Notion fetches, Gmail searches). Structured small calls on flagship = textbook flagship-for-easy.
- Telegram-native means **massive prompt repetition** across users: "what's on my calendar today", "summarize this group", "draft me a meeting reply". No public mention of semantic caching layer — and at 500k MAU doubling monthly, semantic cache hit rates on top-100 intents would be material.
- Telegram "Private Mode" routes through Cocoon decentralized GPU network — that's a SEPARATE cost path Mira eats internally vs the OpenRouter-paid public mode.

**Estimated savings:** 40-60% on input cost via task-class router (small calls → Haiku/Mini/Flash). Another 30-50% on top-100 intents via semantic cache. Compounds.

## Day-0 cold email
**Subject:** Mira on OpenRouter — quick observation

**Body:**

```
Hi Daria,

Mira showed up at #8 on the OpenRouter rankings this week (~13B tokens) — congrats, the 500k MAU doubling month-over-month is showing up in the spend signal too.

Hypothesis from the outside: Mira routes across OpenAI / Anthropic / Minimax / ByteDance / ElevenLabs which is the right structural call — but with 25 models on 13B tokens, the routing dimension reads more inter-provider than intra-complexity. The "summarize this group", "draft a reply", "what's on my calendar" workloads are Haiku/Mini-class but probably hitting Sonnet/GPT-5 because that's what the provider-level routing landed on. Could be wrong, but it's the pattern I see on Telegram-style assistants the most. Also: at your MAU doubling rate, the top 100 user intents repeat heavily across users — semantic cache hit rate there is usually 30-50% on consumer chat surfaces.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 min on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation. If there's nothing there, we shake hands and move on.

cal.com/matt-culpepper/token-audit if it's interesting.

Matt
```

## Priority score
**Score:** 8/10

**Rationale:** Highest priority of this batch. Reasons: (a) growth curve is steep and monetization model isn't publicly clear — consumer chat at 500k MAU doubling monthly with no visible paid tier means runway pressure is REAL; (b) the bloat hypothesis is mechanically specific (small-call workloads on flagship) and inherent to the product shape (Telegram chat = mostly small calls); (c) Daria is a hands-on technical CEO at a small TOP/f4-backed company, which is the sweet spot for cold-email response rates; (d) compounding hypothesis (routing + semantic cache) gives two strong shots in the same conversation. Lowered from 9 because contact discovery is harder — no public email means LinkedIn-first.

## Notes for Matt
- **LinkedIn-first, not email-first.** Daria's LinkedIn is the only verified channel. Use Template 4 (connection request → follow-up DM after accept). Her London base means EU founder skew = LinkedIn-primary anyway per your template positioning notes.
- Mira is venture-backed by **The Open Platform (TOP)** — Telegram's own venture arm — and f4 Fund. They have runway, but they ALSO have institutional pressure to look efficient when they raise the next round. Bloat audits become genuinely interesting before a fundraise. Worth checking Crunchbase / TOP portfolio updates for fundraise timing signals before reaching out.
- The **Cocoon decentralized GPU network** for Private Mode is a separate cost axis I can't see from outside. Worth asking about on the call — if Cocoon is subsidized by TON token economics, the OpenRouter-public-mode spend is the bigger pressure point.
- 900+ Composio integrations means a lot of tool-call traffic. Pattern #8 (tool-result caching) is a strong secondary hypothesis — same calendar pull / same Notion page fetch happening 10k times a day across the user base.
- **Don't pitch crypto angles** even though Mira is TON-adjacent. Daria is technical, not crypto-flavored in her LinkedIn presence; lead with the engineering pattern, mention the crypto/Cocoon side only if she brings it up.
- Russian-name founder + London + decentralized-GPU stack — be deliberately professional in tone. No Mississippi-folksy energy on the first touch.
