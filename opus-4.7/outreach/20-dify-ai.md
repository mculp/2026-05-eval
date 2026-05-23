# 20. Dify.AI
- **Domain:** dify.ai
- **OpenRouter rank:** 20
- **Category:** Visual agentic workflow builder — RAG pipelines, agents, observability, MCP; open-source LLMOps
- **Prospect status:** Active prospect — pitch the hosted SaaS tier (where Dify pays inference), not the self-hosted edition

## Founder / contact

- **Luyu Zhang** — Founder & CEO of Dify (LangGenius Inc). LinkedIn: [luyu-zhang](https://www.linkedin.com/in/luyu-zhang/). Previously: product director at Tencent CODING (DevOps platform). Recently relocated to the US as Dify scales (per Aitoolsbee 2025 piece).
- LangGenius parent entity. 280+ enterprise clients including Volvo, ThermoFisher.
- Raised $30M at $180M valuation (March 2025). Top-52 most-starred GitHub repo globally.
- China-headquartered, US presence growing.

Public email: not on the landing page. LinkedIn is the most reliable surface. Generic contacts on the site (sales / enterprise) are wrong target — those route to AE pipeline, not the founder.

**Contact gap:** no public email for Luyu Zhang. LinkedIn-primary. Given his recent US relocation, US-business-hours timing should land.

## Bloat hypothesis

**Pattern #3 (Full-Context Stuffing) + Pattern #1 (Uncached System Prompt), at the hosted-cloud-tier layer.**

Two-faced product: self-hosted Dify is OSS (users bring their own API keys, Dify doesn't pay for inference). The hosted Dify Cloud at dify.ai IS where Dify pays — and the pricing tiers are interesting:

- Sandbox: $0 / 200 message credits
- Professional: **$59/mo / 5,000 message credits**
- Team: **$159/mo / 10,000 message credits**

Reverse-engineer: $159/mo ÷ 10,000 credits = **$0.0159/credit**. If a single "message credit" maps to one LLM turn, and the workflow includes RAG retrieval + agent + tool-use + response, you're looking at 5-50k tokens per credit easily. At Sonnet 4.5 input pricing (~$3/M), the Team tier is upside-down on any user actually building an agentic workflow with meaningful context.

**Three real angles:**

1. **System-prompt-per-app caching.** Every Dify "app" is a configured agent with a system prompt + tool list + RAG retriever config. The static prefix is BY DESIGN reused across every user turn for that app — perfect cache-eligible shape. If they're not flagging `cache_control`, that's 70-80% off input tokens for the agent body, immediately.

2. **RAG retrieval bloat.** Dify markets "Get Your Data LLM Ready with RAG" but defaults probably aren't optimal — top-K retrievals that over-retrieve, no MMR re-rank, chunk sizes that include header/footer cruft. Per-app config audit can compress retrieved context 30-50% without accuracy loss.

3. **No Batch API path for the observability/analytics layer.** Dify advertises "full observability" — that means LLM-judge eval runs, summary generation over traces, anomaly classification. Background work, no human waiting. If those go through the realtime endpoint, that's 50% off via the documented Batch discount.

The Team tier is the cleanest pitch — that's where users with the heaviest workflows live, and that's where Dify's COGS pressure shows up first.

## Day-0 cold email

**Channel:** LinkedIn DM to Luyu Zhang (post-US-relocation, US-hours timing).

**Subject (if email surfaces):** `Dify on OpenRouter — Cloud tier unit-economics question`

```
Hi Luyu,

Dify on the OpenRouter rankings — congrats, real spend signal on the hosted side.

Hypothesis from the outside: the per-app system prompt is the same on every user turn (by design, that's how Dify apps work), and looking at the public docs I don't see prompt caching flagged in the LLM-call layer. On Anthropic-routed apps that's ~70-80% off input tokens with no product change. On the Team tier where users are running 10k credits/mo against multi-step agentic workflows, that's where the unit economics live or die.

Second angle: the RAG defaults in the visual builder (top-K, chunk size, no MMR) are tuned for "it works" rather than "it's tight." A per-template retrieval audit usually compresses retrieved context 30-50%.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation. Targeting the hosted Cloud tier specifically — the self-hosted users bring their own bills.

[CAL_LINK] if it's interesting.

Matt
```

## Priority score

**7 / 10**

- (+) Real hosted-tier inference bill, visible margin pressure on the Team pricing math.
- (+) Architecturally clean for the pitch — Dify apps are perfectly cache-eligible by design.
- (+) Founder is reachable on LinkedIn, recently US-relocated (no APAC timezone friction).
- (+) Well-resourced ($30M raise) means there's budget for a paid follow-on if the audit lands.
- (–) Large org now (280+ enterprise customers, $180M valuation) — CEO-direct may not respond; pitch routes to a VP-Eng instead.
- (–) China-rooted org means there may be internal engineering culture norms about US consultants that I can't read from outside.
- (–) Open-source LLMOps means they have eyes on every cost-line themselves; novel findings need to be novel.

## Notes for Matt

- Strong #2 on this lane after OpenHands. The pricing-math reverse-engineering on the Team tier is the cleanest opener — credible, specific, math-grounded, no vibes.
- The China-HQ history matters less now that Luyu moved to US. Treat as a US-based startup CEO for outreach pacing.
- If Luyu doesn't respond, the second-best contact is whoever runs Dify Cloud infrastructure — that person is named in their engineering blog if they have one (didn't surface in the WebFetch but worth a deeper dive).
- Dify's enterprise client list (Volvo, ThermoFisher) implies they have customer-facing SLAs that punish ANY latency win — pair the cost-reduction pitch with a "and this also lowers TTFT on the agent loop" angle.
