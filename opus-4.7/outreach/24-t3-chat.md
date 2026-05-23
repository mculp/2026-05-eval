# 24. T3 Chat
- **Domain:** t3.chat
- **OpenRouter rank:** 24
- **Category:** Multi-model AI chat ($8/mo), local-first via IndexedDB + Cloudflare edge, YC-backed
- **Prospect status:** **YC company, public-engineer-founder, peer-to-peer outreach lands or fails fast.** Theo Browne is one of the most online dev personalities — his radar for bad pitches is high, his radar for legitimate engineering observations is also high. High-information founder.

## Founder / contact
- **Theo Browne** — Founder. Also runs T3.gg (personal site / brand), Create-t3-app (the popular Next.js scaffolding tool), and a major YouTube channel (@t3dotgg).
  - Co-founder: **Mark Florkowski** (per public sources)
  - Personal site: https://t3.gg
  - X/Twitter: https://x.com/theo (primary surface — he posts and replies constantly)
  - GitHub: https://github.com/t3dotgg
  - YouTube: https://www.youtube.com/@t3dotgg
  - Twitch: https://twitch.tv/theo
  - Discord community via t3.gg
  - YC profile: https://www.ycombinator.com/companies/t3-chat
  - LinkedIn: https://www.linkedin.com/posts/t3gg_t3-chat-is-now-the-cheapest-fastest-and-activity-7307892576580161536-eYBv (account exists, less actively used than X)
- **Public email:** not surfaced in fetches. T3.gg has a Contact/Discord route. **X DM is the lane brief's stated best channel** — verified.
- **Verified pricing context:** $8/mo Pro plan. Theo has publicly stated he leverages Azure credits to keep OpenAI costs low. He's price-conscious and engineering-aware about LLM costs.

## Bloat hypothesis
**This is the trickiest hypothesis of the batch because Theo already knows about cost optimization at a deep level.** He's publicly discussed Azure credits, à-la-carte API pricing, and the math behind why $8/mo works. A naive "you should use Haiku" pitch will get instantly bounced.

**The real angle is Pattern 5 (No Semantic Cache on Repeat Sub-Prompts) + Pattern 1 (Prompt Caching, edition-Anthropic).**

Reasoning:
1. T3 Chat is a unified-interface multi-model chat — users send the same kinds of prompts repeatedly across the user base ("summarize this", "explain this code", "rewrite this email"). Cross-user semantic caching on the cheapest tier with consent-gated reuse could cut 20-40% of flagship calls at the long-tail intent layer.
2. Theo's local-first architecture (IndexedDB) means he already has a per-user history surface — extending it with a server-side semantic-cache layer that hits on cross-user near-duplicates is a small step architecturally.
3. T3 Chat's unique cost-saver isn't "use cheaper models" — Theo's already model-shopping. The unique cost-saver is **caching at the prompt-prefix layer for the long static system instructions T3 ships with each model**, AND the cross-user semantic cache for "top intents" (explain-code, summarize, rephrase).
4. Pattern 8 (Tool-Use Without Result Caching) likely doesn't apply — T3 Chat is chat, not agentic.

**Honest framing for the pitch: he probably already addressed prompt caching where it's easy. The peer-to-peer ask is "have you tried cross-user semantic cache on the top 5 intents, and where do you draw the privacy/consent line on it."** That's a real engineering conversation, not a sales pitch.

## Day-0 cold email (X DM format, 280 char limit primary; longer DM if open)

**X DM (open with the 280-char version since it's the stated best channel):**

```
Theo — t3.chat on the OpenRouter board this week. Curious if you've experimented with cross-user semantic cache on the top intents (explain-code, summarize, rephrase) — feels like the next cut after model-shopping + Azure credits. Happy to share what I've seen. Ruby/infra dev, no pitch.
```

**Follow-up DM if he engages (or initial DM if he replies open-bio):**

```
Quick context — I run a small consultancy doing token-bloat audits on apps that show up on the OpenRouter rankings. T3 Chat is interesting because you've already done the obvious cuts (Azure credits, model-by-message, local-first to skip server-side history rebuild), so the question is more "what's the next 10-20% look like."

My guess: cross-user semantic cache on the top-N intents with a privacy/consent gate. Embed incoming prompt, cosine sim > 0.95 against past cached completions, return cached if hit. Hit rate probably 15-30% on chat workloads where users ask variants of "summarize this PR" / "rewrite this email" / "explain this regex." The hard part is the consent UX, not the cache.

If it's interesting, I'd love 20 min — show what I've seen on similar apps, you push back. One-page writeup at the end. Free, no obligation.

[Cal.com link]
```

## Priority score
**6 / 10.** Theo is the highest-information founder in this batch — the pitch needs to be peer-engineer-level or it bounces. Conversion isn't about "saving him money" (he already cares); it's about **respect-trading for engineering insight he hasn't tried yet.** If Matt frames it as "I'm curious what you've tried on X, here's what I've seen elsewhere" instead of "you should hire me," there's a real conversation. If he frames it as a normal cold pitch, it dies.

## Notes for Matt
- **Channel order:** X DM is the lane brief's stated best — verified by Theo's public-posting cadence. Avoid email (not surfaced, and Theo's email signal-to-noise is rough). LinkedIn as last resort (he posts there but barely engages).
- **DO NOT pitch him on "use Haiku."** He knows. He'll close the DM.
- **Lead with curiosity, not the offer.** "I'm curious if you've experimented with X" beats "I noticed you could save Y."
- **Acknowledge the moat.** Mentioning the Azure-credits trick early signals "I did real homework on YOUR specific cost structure, not just any LLM-chat app."
- **He may publicly tweet about the DM.** Theo posts engineering encounters. Make sure the DM is something Matt would be comfortable being screenshot — it likely will be, win or lose.
- **Contact gap:** no email surfaced. X DM is the channel, and it's the right one anyway.
