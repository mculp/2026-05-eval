# 11. Portkey AI

- **Domain:** portkey.ai
- **OpenRouter rank:** 11
- **Category:** AI Gateway / LLMOps infrastructure (B2B, dev-tools)
- **Prospect status:** CONFLICT-OF-INTEREST (they SELL inference optimization — gateway, observability, prompt mgmt, semantic cache, governance). Treat as peer/partnership conversation, not a customer pitch.

## Founder / contact

- **Rohit Agarwal** — Co-founder & CEO. LinkedIn: https://www.linkedin.com/in/1rohitagarwal/ (verified). Two-time founder, ex-Freshworks (their first startup got acquired there), built one of the earliest GPT-3 content-gen apps in early 2021 at Pepper Content.
- **Ayush Garg** — Co-founder & CTO. Ex-Head of Engineering at Pepper Content; built Peppertype.ai.
- **Company:** Portkey, Inc. HQ 2261 Market St #5205, San Francisco. Series A, ~$18M raised (Lightspeed, Elevation Capital). Founded Jan 2023.
- **Founder email:** not publicly listed. Best guess pattern is `rohit@portkey.ai` but unverified — don't fabricate. LinkedIn DM is the right first surface here.
- **Contact page:** portkey.ai/book-a-demo (sales funnel — wrong target for peer outreach).

## Bloat hypothesis

The meta-irony — Portkey IS the inference-optimization vendor. They publish the open-source LLM pricing dataset. They sell prompt caching, semantic cache, model fallbacks, cost guardrails. So the bloat hypothesis can't be "you're running Sonnet on classification" — they know that song.

The genuinely interesting hypothesis is one level up: **their OWN platform — control plane, evals, gateway routing logic — is the LLM workload that's hard for them to optimize because they're customer 0.** A gateway provider running internal observability, anomaly detection, prompt-improvement suggestions, and now MCP orchestration is a heavy meta-LLM workload. The signal that lands here is not "we save you 50%" — it's "would love to compare notes on how you internally route the eval/anomaly-detection workloads that power the product itself." Peer-engineering frame, not pitch.

Secondary angle: Portkey's customers use Portkey because they don't want to build prompt caching themselves. The natural partnership lane is — Matt finds the bloat on apps NOT yet on Portkey, hands off to Portkey for fix-implementation. Referral relationship rather than competitor. That's the real opening.

## Day-0 cold email

**Subject:** `Portkey on OpenRouter — peer-engineering note`

**Body:**

```
Hi Rohit,

Portkey showed up on the OpenRouter rankings this week — congrats on the spend signal, though I imagine that's the easiest one to read in this whole business.

I'm reaching out peer-to-peer, not as a pitch. I run a small consultancy doing token-bloat audits on apps from the OpenRouter board — Ruby/infra background, ex-Pepper Content's neighbor in the 2021 GPT-3 content-gen era so we may have crossed wires.

The reason I'm writing: the apps I audit are exactly the ones who SHOULDN'T be DIY-ing prompt caching, semantic cache, fallback routing — they should be on Portkey. My audit-then-fix lane and your platform aren't competitors; they're sequential. Would value 15 min to compare notes on where you see the worst bloat patterns landing on your gateway lately, and whether a referral relationship makes sense for the apps I find that need a control plane.

If the timing's off, no worries — just wanted to put the offer in writing.

Matt
```

## Priority score

**Priority: 4/10 (peer/partner, not customer)**

- Conflict-of-interest as a customer = downgrade.
- BUT a referral/partnership lane has real value — Portkey is exactly where ~60% of the apps Matt audits should land for fix-implementation if they don't want to roll their own.
- Rohit is a two-time founder, technical, will respond to a peer-engineering frame faster than a sales pitch.
- Founder email gap is the real blocker — LinkedIn DM is mandatory here, NOT email.

## Notes for Matt

- **DO NOT** pitch them as a customer. They sell exactly what you'd be selling them. They'll smell it instantly and you'll burn the partnership lane.
- **DO** frame as a referral relationship — they get qualified leads from audits, you get a fix-implementation partner for the apps that need a real control plane.
- LinkedIn DM Rohit FIRST (1rohitagarwal). Email is unverified and guessing burns trust.
- If they engage, the real ask is: "can I introduce my next 5 audit clients who would benefit from your platform, in exchange for me getting better at recognizing Portkey-shaped fits?"
- Their open-source LLM pricing dataset is the actual conversation starter — read it before you DM him so the peer-engineering frame is grounded.
- Skip the Day-4 nudge and Day-10 breakup template here; partnership lanes need a longer cadence (3-week follow-up at most).
