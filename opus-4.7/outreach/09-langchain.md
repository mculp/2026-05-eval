# 9. LangChain

- **Domain:** langchain.com
- **OpenRouter rank:** #9 (13.2B tokens/week — though this is likely *aggregated framework users*, not LangChain-the-company's own product spend)
- **Category:** dev-productivity (infrastructure / observability play, B2B SaaS shape)
- **Prospect status:** PROSPECT — but with the unusual angle that they're a tooling competitor, not a customer

## Founder / contact
- **Founder(s):** Harrison Chase (Co-Founder & CEO), Ankush Gola (Co-Founder & CTO)
- **Email:** harrison@langchain.com (verified pattern — Harrison's company email per ZoomInfo/RocketReach). Backup personal: hw.chase.17@gmail.com (older, less appropriate for cold outreach).
- **LinkedIn:** https://www.linkedin.com/in/harrison-chase-961287118/
- **Twitter/X:** @hwchase17 (Harrison's Twitter handle, derived from gmail prefix — verify before use; well-known in AI eng community)
- **GitHub:** https://github.com/hwchase17 (LangChain creator, very active)
- **Sources:** ZoomInfo, RocketReach, LinkedIn, [LangChain platform page](https://langchain.com), Crunchbase

## Bloat hypothesis
**Primary pattern:** This is the unusual one. LangChain's own product (LangSmith observability) is exactly the kind of tool that surfaces bloat in *others'* stacks. So the angle is **not** "you have bloat" — it's the *meta* layer.

**Two real angles:**

**Angle A — Their own demo/eval workloads:**
- LangSmith pricing: $0.005 per deployment run + $0.0036/min per deployment uptime. They run their own demo agents, eval suites, customer onboarding deployments at non-trivial scale. Pattern #4 (No Batch API for Async Jobs) applies — overnight eval suites against the Promptfoo/Braintrust-style golden sets are batch-shaped traffic that's almost certainly going through realtime endpoints.
- They eat their own dogfood across `langchain` / `langgraph` / `deepagents` / `Fleet` — 4 framework surfaces means 4 demo apps that all run inference. Probably no internal cross-framework cost audit.

**Angle B — Their customer cost-disclosure surface (the partnership angle):**
- LangSmith surfaces "total cost" per trace, but Matt Rubens-style "here's WHERE you're bleeding" diagnostics could be a feature gap that complements their observability instead of competing with it. Position: "I'm not building competing observability — I'm doing 20-min bloat reads using your traces as the input." That's a value-add to their platform.

**Evidence for Angle A:**
- 13.2B tokens/week shown on OpenRouter is largely *user* spend (people using `langchain` framework against OpenRouter), not LangChain-the-company. But LangChain-the-company DOES have an OpenRouter footprint via demo workloads, eval suites, the Fleet no-code product, and the deployment infrastructure.
- Klarna / Lyft / Gong / Nvidia case studies imply substantial deployment scale — their HOSTING infra (Plus plan at $39/seat * 6,000 LangSmith customers + Fortune 10 enterprise) is running real workloads.

**Estimated savings:** Specifically for LangChain-the-company's own ops — 40-60% on async eval workloads via Batch API routing. But the bigger play is the partnership angle, which has no $-savings number attached.

## Day-0 cold email
**Subject:** LangChain on OpenRouter — quick observation

**Body:**

```
Hi Harrison,

LangChain showed up at #9 on the OpenRouter rankings this week (~13B tokens) — congrats, the framework reach is showing up in the spend signal.

I'm going to frame this differently from a normal cold pitch because you literally build the observability layer for this stuff. So this isn't "you have bloat I can see" — you can see it better than I can. Two thoughts that might still be useful:

(1) Your own dogfood surface: across langchain / langgraph / deepagents / Fleet you're running 4+ demo apps and customer-facing eval suites. Overnight eval runs are batch-shaped traffic and Anthropic / OpenAI Batch APIs are documented at 50% off list. Curious if there's a cross-framework audit on that internally.

(2) The complementary angle: I do 20-min bloat reads on apps. LangSmith traces are exactly the right input format. If your customers ever ask "WHERE in our agent loop are we bleeding," there might be a partner-shaped thing here that surfaces alongside your observability instead of competing with it. Not pitching that — just noting it exists if you want to compare notes.

Ruby/infra background, small consultancy. cal.com/matt-culpepper/token-audit if you want to spend 20 min on either angle.

Matt
```

## Priority score
**Score:** 5/10

**Rationale:** Hard to score. The token volume is huge but it's framework-aggregated, not LangChain-the-company's own spend — so the "you have bloat" framing is mostly wrong. The partnership angle is interesting but speculative. Harrison Chase gets cold pitches by the truckload — anything that doesn't immediately differentiate gets binned. The "I'm not selling observability, I'm doing 20-min reads against your traces" framing might survive his filter because it's structurally complementary. **Realistically expect no reply.** But the email is cheap to send and the *one* reply would be high-value.

## Notes for Matt
- **Harrison Chase is the most over-pitched person on this list.** ZoomInfo / RocketReach put his email behind paywalls because everyone hammers it. The pitch has to differentiate in the first paragraph or it dies.
- The partnership angle is the only one that doesn't sound naive given who LangChain is. Lead with "I'm not building competing observability" to neutralize the competitive read.
- LangSmith pricing is in the public — $2.50/1k traces base, $5/1k extended retention, etc. Worth knowing for the call if Harrison bites.
- **6,000+ LangSmith customers and 5 Fortune 10 — this is no longer an early-stage startup.** A pitch that reads as "I'll save your startup money" is wrong-coded. Pitch the COMPLEMENT to their platform, not the optimization of it.
- Consider sending this LAST in the batch (after Cline, Mira) — the LangSmith ecosystem might pay off as a *referral source* for your audits more than as a direct customer. LangSmith dashboards surface "this trace costs $X" — perfect lead-gen for "want to know WHY?" follow-ups.
- If Harrison doesn't reply but LangChain's developer relations folks do, that's a Tier-2 win — they could refer specific customer accounts to you.
- Don't sweat the lukewarm priority score. The asymmetric upside on a Harrison-Chase-replies-to-anything event is large.
