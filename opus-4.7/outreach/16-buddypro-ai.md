# 16. BuddyPro AI
- **Domain:** buddypro.ai
- **OpenRouter rank:** 16
- **Category:** AI digital twins for coaches/consultants — white-label expert-as-AI marketplace
- **Prospect status:** Active prospect (small team, real per-user margin to defend)

## Founder / contact

Three-person founding team, Czech roots:
- **David Kirš** — Vision & Growth. Serial entrepreneur (MioWeb.cz, SmartEmailing.cz, FAPI.cz). Likely the commercial face.
- **Pavel Říha** — Online Strategist & Monetization. Ed-tech background (50,000+ clients claim).
- **David Říha** — Technology & AI Architecture. Full-stack engineer, 10+ yrs. **He is the right technical contact for an inference-cost conversation.**

Public emails: not listed on the site (about/team page lacks direct mailto). LinkedIn for the founders is the most likely surface — search "David Kirš BuddyPro", "David Říha BuddyPro". Czech-language LinkedIn results likely.

**Contact gap:** no public email on landing/about/pricing. LinkedIn-primary route.

## Bloat hypothesis

**Pattern #1 (Uncached System Prompt) + Pattern #3 (Full-Context Stuffing), per-twin variant.**

The product pitch is "expert uploads their content, we create a white-label AI that embodies their methodology and serves unlimited clients simultaneously." That architecture almost certainly means:

1. Per-twin system prompt loaded with the expert's "methodology" — likely 2-5k tokens of persona + voice + framework instructions, sent on every client message. No mention of `cache_control` or implicit caching anywhere on the site.
2. "Long-term memory" + "hundreds of specialized roles" + "automatic content analysis" reads as stuffed-context-per-turn rather than retrieval. No mention of embeddings, RAG, vector DB anywhere.
3. **Per-coach unit economics: $197/mo flat, unlimited clients.** If even one expert's twin serves 50 active clients sending 20 messages/day each = 1,000 messages/day × 3-5k system prompt × 30 days = 90-150M tokens/month just on the static prefix. At Sonnet 4.5 input pricing (~$3/M), that's ~$270-450/mo on one customer alone — pricing is upside-down unless they've already capped or cached.

The $197/mo flat-rate-unlimited model is the strongest tell: either they have hidden caps, or they're running on a cheap model (Haiku/Mini/Flash) without saying so, or they're bleeding on power users. Caching is the cleanest fix that doesn't break the product promise.

## Day-0 cold email

**Channel:** LinkedIn (DM to David Říha — Technology & AI Architecture), email if discovered.

**Subject:** `BuddyPro on OpenRouter — quick observation`

```
Hi David,

BuddyPro showed up on the OpenRouter rankings this week — congrats, that's a real spend signal.

Hypothesis from the outside: the per-twin system prompt (methodology + persona + voice) is probably re-sent uncached on every client message, and with the $197/mo flat-unlimited pricing, a single power-user expert with 50 active clients can move serious tokens. Prompt caching on the static prefix is the cleanest fix — Anthropic prices cache reads at 10% of base input, so on a 3-5k methodology prompt the per-message input cost drops ~70-80% with no product change. Could be wrong, but it's the pattern I see most on apps with per-user-twin architectures.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation. If there's nothing there, we shake hands and move on.

[CAL_LINK] if it's interesting.

Matt
```

## Priority score

**6 / 10**

- (+) Pricing-architecture mismatch is real and provable on first call.
- (+) Small team (likely no dedicated infra/LLMOps engineer) = audit findings have nowhere else to come from internally.
- (+) David Říha is a clear technical contact — single decision-maker.
- (–) No public email; LinkedIn-only is a higher-friction first touch.
- (–) Czech-based may shift to LinkedIn-primary timezone friction.
- (–) Smaller absolute spend than the dev-tool prospects below; less leverage on a paid engagement.

## Notes for Matt

- The $197/mo flat-rate-unlimited model is upside-down on power users unless they're already caching or running on a cheap model. Worth probing on the call.
- "Hundreds of specialized roles" + "long-term memory" is RAG-shaped marketing without RAG-shaped engineering language. They probably stuff context.
- Czech founders, US/global market — likely English-fluent business correspondence, no language friction.
- If LinkedIn DM lands, push for David Říha directly. Kirš is the marketer; conversation will route faster through the engineer.
