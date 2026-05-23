# 28. Vellum
- **Domain:** vellum.ai
- **OpenRouter rank:** 28
- **Category:** Enterprise B2B AI development platform — agent builder, workflows, evals, observability
- **Prospect status:** Researched, founders confirmed; domain ambiguity flagged

## Founder / contact

Three co-founders, all from Dover (YC S19) where they worked together for 2+ years:

- **Akash Sharma** — Founder & CEO. 5 years McKinsey Silicon Valley pre-Dover.
- **Sidd Seethepalli** — Co-founder & CTO. MIT engineer, previously DataRobot MLOps.
- **Noa Flaherty** — Co-founder. MIT engineer, previously Quora ML Platform.

Company:
- **YC:** W23
- **Funding:** $20M Series A led by Leaders Fund (July 2025); $29.5M total. Backers: YC, Socii Capital, Rebel Fund, Pioneer Fund, Eastlink Capital.
- **Customers (verified from their own Series A announcement):** Swisscom, Drata, Redfin, DeepScribe, Rely Health, Rentgrata, GravityStack, Headspace.
- **LinkedIn (company):** https://www.linkedin.com/company/vellumai
- **Personal emails:** not publicly listed (typical for YC enterprise founders). Best route is LinkedIn DM to Akash (CEO) given a personalized peer-engineer framing.
- **Author page (Akash):** https://www.vellum.ai/blog/author/akash-sharma

**Domain ambiguity flag — IMPORTANT for Matt:** WebFetch on `vellum.ai` homepage on 2026-05-23 returned a personal-AI-assistant product ("Your Personal Intelligence", credit-based BYOK billing, support@vellum.ai). Crunchbase/YC/news still describe the B2B enterprise dev platform with the Drata/Redfin/Headspace customer set. Possibilities: (a) they pivoted/added a consumer brand, (b) the public marketing site is an A/B test, (c) the B2B product lives at a sub-domain (app.vellum.ai) and the root is now consumer. The OpenRouter ranking entry could be either product. Worth verifying live before send — open vellum.ai in Matt's browser. The outreach below targets the B2B platform per the lane brief; if the domain ambiguity matters to Akash, he'll tell us.

## Bloat hypothesis

**The peer/partnership angle is the play here** — they sell observability + evals. They're the people who should already know all 10 bloat patterns. Two outcomes:

1. **They've already audited their own stack** (most likely). Pitch is "let me compare notes" — peer-engineer, not vendor.
2. **They haven't, because plumbers' houses leak** (a real pattern). Pitch is "you sell this to others, I'd love to see how it looks from outside."

The specific bloat hypothesis I'd lead with is **#7 (No Eval Gate on Model Swap)** — IRONIC because they SELL the eval product. If they're not running their internal model-selection through their own platform, that's a story they'd want to tell publicly. If they ARE, then they have a public eval study to share and it's pure peer-conversation territory.

Second-order: **Full-Context Stuffing on agent-builder workflows (Pattern #3)**. Vellum's product lets customers build agent workflows that call LLMs — those workflows are often glue code that re-stuffs context every turn. The bloat may not be in Vellum's *own* stack; it's in their *customers'* deployed agents. Helping them make their customers cheaper is a partnership wedge.

## Day-0 cold email

**Channel:** LinkedIn DM to Akash first (verified author page exists). If a personal email surfaces from outbound research (e.g. via Apollo, Clay), email is the parallel surface.

**Subject:** `Vellum on OpenRouter — peer-engineer note from a non-competitor`

**Body:**

```
Hi Akash,

Vellum showed up on the OpenRouter rankings this week. Congrats on the Series A run too.

I'm coming at this from a slightly weird angle: I run a small consultancy doing token-bloat audits, and you literally SELL the eval+observability stack I'd normally pitch as the fix. Two ways this lands:

(a) You've already audited yourself — I'd love to compare notes. There's probably a "how we cut our own infra cost using our own product" story you could publish that's pure trust-building content.

(b) Plumber's house — you haven't run a full pass internally yet. Happy to do that pass as a peer, free, one-page writeup. If anything's there, you've got internal data; if not, you have an external confirmation to point at.

I'm specifically NOT trying to compete with what Vellum sells. Your platform IS the right place to fix this stuff; I'm a Ruby/infra consultant who's been deep in LLM cost-shape patterns the last year. Different layer.

Side angle: a lot of your customers' deployed agents likely have Pattern-#3 (full-context stuffing) in their workflows. If you ever want a partnership-shaped writeup on "common bloat patterns we see in agent workflows" co-bylined with your customer success team, that's a different conversation worth having.

Matt
```

**Why this works for Vellum specifically:**
- The "you sell this" meta-irony is the hook a sycophantic email can't replicate.
- The (a)/(b) frame gives them a graceful exit ("we already do this") that's actually still a hook for follow-up content.
- The partnership angle is real — Vellum's customers ARE the audit market. If a relationship forms, every Vellum enterprise lead is a downstream audit lead.

## Day-4 nudge

**Subject:** `re: Vellum on OpenRouter — partnership angle`

```
Akash —

Quick nudge. One thing I should have led with: the partnership shape, not the audit shape. Your customers deploy agent workflows; we see the same 3-4 bloat patterns across them (context stuffing on retrieval-amenable workloads, tool-call result re-billing in agentic loops, batch-API misses on overnight regens). A joint "common patterns" writeup co-bylined with one of your customer-success folks would do more for both of us than my audit business OR your inbound funnel does alone.

Open to a 20-min conversation if it's interesting. {{CAL_LINK}}.

Matt
```

## Priority score

**7 / 10**

- **Token spend signal:** moderate-to-strong. They built the product on top of model calls; OpenRouter ranking confirms real volume. But they likely already optimize.
- **Conversion potential:** LOW direct-deal odds (they ARE the platform that fixes this) but HIGH partnership potential (their customers = my market).
- **Reply odds:** above average for engineering co-founder cold mail because the angle is unusual and respectful (acknowledges they're not the typical target).
- **Stage fit:** post-Series A, scaling sales motion, looking for content + partnership leverage. The "co-bylined writeup" hook is at the right altitude.
- **Channel access:** LinkedIn confirmed for all 3 founders. Likely some personal-email findable via Clay/Apollo if needed.

Knock down 1-2 for: (a) they don't need an audit, (b) domain ambiguity adds friction to the cold opener (might need a "I see your homepage shows X — is the B2B product still live?" qualifying question, which weakens the hook).

## Notes for Matt

- **Lead with Akash, not the team.** CEO is the right altitude for partnership conversations. If he forwards down to Sidd or Noa, that's actually a good signal.
- **Don't try to sell an audit here — sell the partnership.** This is a different shape than every other rank in your batch. The win condition is "Vellum starts referring enterprise customers to Matt for the audit layer they sell as platform." That's a real business outcome, not a one-off.
- **The domain ambiguity is worth one quick check before send.** Open vellum.ai in a real browser; if it really is now showing the personal-AI-assistant product, the cold email needs a one-sentence acknowledgment ("noticed your public site is showing the personal-assistant product — is the enterprise platform on app.vellum.ai now?"). That earnsness is good. Faking that you didn't notice is bad.
- **Customer logos = leverage.** Drata, Redfin, Headspace are bigger than the prospect themselves. If Akash mentions any of them in reply, dig in — that's the partnership pitch landing.
- **Meta-irony is load-bearing.** The "you sell this stack" frame is the WHOLE pitch. Don't dilute it with the standard 20-min ask in the first email — earn that with the second message.
- **Risk:** they polish-respond with "we've thought about this, no thanks" and a polite door-close. Take it gracefully; the partnership angle has a much longer half-life than the audit angle.
