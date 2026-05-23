# 1. Hermes Agent

- **Domain:** hermes-agent.org (redirects to hermes-agent.nousresearch.com)
- **OpenRouter rank:** #1 (~8.8T tokens cumulative; #1 daily on rankings)
- **Category:** dev-productivity / agent-runtime
- **Prospect status:** PROSPECT (with nuance — see Notes for Matt). The audit target is the **product team** (Hermes Agent the framework + Nous Portal subscription path) — not the model training lab (Hermes / Nomos / Psyche).

## Founder / contact

- **Founder(s):**
  - **Jeffrey Quesnelle** — Co-founder & CEO, Nous Research (formalized 2023). Per his LinkedIn and personal site, also listed as CTO on some sources. Detroit Metro.
  - **Karan Malhotra** — Co-founder, Head of Behavior.
  - **Teknium** — Co-founder, Head of Post-Training (the most active OSS LLM-fine-tuning contributor; pseudonymous).
  - **Shivani Mitra** — Co-founder.
- **Email:** `jeff@jeffq.com` (Jeff's personal, publicly listed on his homepage — verified)
- **LinkedIn:** [Jeffrey Quesnelle](https://www.linkedin.com/in/jeffrey-quesnelle-2490a524/)
- **Twitter/X:** [@theemozilla](https://x.com/theemozilla) (Jeff); [@NousResearch](https://x.com/NousResearch) (org); [@Teknium1](https://x.com/Teknium1) (Teknium)
- **Sources:**
  - [Jeff Quesnelle homepage](https://jeffq.com/) — personal email confirmed here
  - [Nous Research startup intros](https://startupintros.com/orgs/nous)
  - [Turing Post: Hermes Agent breakdown](https://www.turingpost.com/p/hermes)
  - [GitHub: NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent)

## Bloat hypothesis

**Primary pattern:** #4 — No Batch API for Async Jobs (compounded by #2 — Flagship-for-Easy on the RL trajectory pipeline)

**Evidence (public signals):**
- The Hermes Agent homepage and docs explicitly advertise **"batch processing for generating thousands of tool-calling trajectories in parallel"** for RL training via Atropos integration. This is exactly the batch-shaped workload that vendor Batch APIs (Anthropic 50% off, OpenAI 50% off) target — and the framework integrates with OpenRouter + custom OpenAI-compatible endpoints with no documented Batch routing.
- Self-improving loop ("ShareGPT trajectory export for fine-tuning") implies regular bulk inference for trajectory regeneration — overnight/async workload pattern from playbook #4.
- 356 different models on OpenRouter, ~8.8T tokens cumulative — at this volume, even a 5pp routing improvement is meaningful. The framework is **model-agnostic** which is great for flexibility but suggests no internal routing policy for difficulty (pattern #2 indicator on the lab-internal pipelines).
- No mention of Anthropic `cache_control`, OpenAI `prompt_caching`, or batch endpoint integration anywhere in the public docs.
- Engineering culture is RL-research-flavored — the bias is toward fast iteration on quality, less toward inference-cost discipline (per Turing Post and DayaHimour coverage).

**Estimated savings:** 30-50% blended on the bulk trajectory/RL pipeline if Batch + caching gates are added to Atropos. Less material on user-facing chat turns (where realtime latency matters), but the lab-internal generation pipeline is the fat target.

## Day-0 cold email

**Subject:** Hermes Agent on OpenRouter — quick observation

**Body:**

> Hi Jeff,
>
> Hermes Agent is sitting at the top of OpenRouter — congrats, that's a real spend signal (~8.8T tokens and 356 models).
>
> Hypothesis from the outside: the Atropos trajectory-generation pipeline ("thousands of tool-calling trajectories in parallel" per your docs) is exactly the workload Anthropic and OpenAI's Batch APIs discount 50% on — and I don't see Batch routing or `cache_control` mentioned in your public docs. If true, the lab-internal RL pipeline could give back a meaningful share of inference budget without touching latency on the user-facing agent.
>
> Could be wrong — possible you're already routing through OpenRouter batch and I just can't see it.
>
> I run a small consultancy doing token-bloat audits. Ruby/infra background, peer-to-peer not salesy. Offer: 20 min on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation.
>
> {{CAL_LINK}} if it's interesting.
>
> Matt

## Priority score

**Score:** 8

**Rationale:** #1 OpenRouter app + verified personal email for the CEO + active research culture that talks publicly about its pipeline = highest-leverage prospect in this batch. The one drag is that Nous Research is research-lab-first; they may rationalize cost as the price of velocity. Still the top of my five.

## Notes for Matt

- **The research-lab-vs-product-team split matters.** Nous Research is BOTH a model training lab (Hermes/Nomos/Psyche models) AND the product team behind hermes-agent. The lab side has Paradigm money and a thesis about decentralized AI — they're not going to take a cost-audit call about model training. The angle is the **product team** running the agent framework and the Nous Portal subscription. Jeff is the bridge; he's CEO and former Eden Network MEV engineer (infra background — will actually look at the numbers).
- **The framework is MIT-licensed free.** Their revenue path is Nous Portal subscription (`portal.nousresearch.com/manage-subscription`) and the OpenRouter share for users who route through them. Inference bloat hits their own COGS on Portal traffic, not the OSS users — so the pitch needs to land on Portal margins, not "save your users money."
- **Teknium is the other reachable founder** ([@Teknium1](https://x.com/Teknium1)) — pseudonymous, very online, would likely be the more receptive contact if the email route stalls. Twitter DM is appropriate for him given the persona.
- **The Atropos angle is the strongest** — it's a public-facing claim about batch generation that maps directly to vendor batch discounts. If they're already using it, the conversation is short and amicable. If not, it's a layup.
