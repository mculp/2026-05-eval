# 18. OpenHands
- **Domain:** all-hands.dev (redirects to openhands.dev)
- **OpenRouter rank:** 18
- **Category:** Open platform for cloud coding agents — CodeAct 2.1 + SDK/CLI/Local GUI; ~53% SWE-Bench Verified (V1 SDK number)
- **Prospect status:** Active prospect, but well-resourced — different value proposition (audit-the-hosted-tier, not audit-the-OSS)

## Founder / contact

- **Robert Brennan** — Co-Founder & CEO of All Hands AI. LinkedIn: [robert-a-brennan](https://www.linkedin.com/in/robert-a-brennan/). Personal site: [rbren.io](https://rbren.io/). X: [@rbren_dev](https://x.com/rbren_dev). Previously: Google (document summarization), executive roles at multiple ML/infra startups.
- **Xingyao Wang** — Co-founder, Chief AI Officer.
- **Graham Neubig** — Co-founder, Chief Scientist (CMU faculty, well-known NLP researcher).
- ~30-person team. Raised $5M seed from Menlo Ventures (Sept 2024), total raised >$20M.
- Project was OpenDevin, renamed to OpenHands. 30k+ GitHub stars, 150+ contributors.

Public email: ZoomInfo lists `r***@openhands.dev` for Brennan — full address scraped behind paywall. Realistic guess for the public-facing pattern: `robert@openhands.dev` or `rob@openhands.dev`, but **do not assume — verify before sending**. The cleanest verified surface is LinkedIn DM or X DM.

**Contact gap:** the `r***@openhands.dev` pattern is the obvious guess but unverified. Recommend LinkedIn-primary; email only after a verified address surfaces (GitHub commit history of the openhands repo is the second-best probe — `git log --format='%ae' | sort -u`).

## Bloat hypothesis

**Pattern #2 (Flagship-for-Easy) — at the hosted-SaaS layer, not the OSS layer.**

OpenHands is open-source AND offers a hosted product (the SDK + Cloud tier is where they actually pay for inference; OSS users bring their own keys). The published numbers are SWE-Bench-Verified scores using **Claude 3.5 Sonnet** as the default `CodeActAgent` model — 77.6% with Sonnet Thinking on V0, 72.8% on V1 SDK with Sonnet 4.5. **Their default config is Sonnet end-to-end.**

CodeAct's whole premise (per the original paper and their docs) is "give the agent bash + Python + browser, let it express any action as code." That means a single mega-loop where Sonnet handles:
- Trivial bash output parsing
- File listing / directory traversal
- Stack-trace classification
- Test result interpretation
- Plus the actual code-writing

The first four are Haiku-tier tasks. Routing them down without dropping the SWE-Bench-Verified score requires an eval gate they already have (their `evaluation-harness` doc exists). So the unlock is: "you already have the eval rig — have you ever re-run it with a Sonnet/Haiku router instead of Sonnet-only?"

**Secondary:** Pattern #1 (Uncached System Prompt). CodeAct system prompts are public in the repo. If they're not flagging the stable prefix with `cache_control`, that's the 70% input-cost cut on the hosted tier, free.

## Day-0 cold email

**Channel:** LinkedIn DM to Robert Brennan (confirmed CEO). Backup: X DM. Only use email after verifying the address.

**Subject (if verified email):** `OpenHands on OpenRouter — CodeAct routing question`

```
Hi Robert,

OpenHands on the OpenRouter rankings — congrats, that's a real spend signal on the hosted side.

Hypothesis from the outside: CodeAct as published runs Sonnet end-to-end for the SWE-Bench numbers, but inside the agent loop you've got file-listing, stack-trace classification, test-output parsing, and the actual code-writing all hitting the same flagship endpoint. The first three are Haiku-tier tasks. You already have an evaluation-harness directory — has it ever been re-run with a Sonnet/Haiku router instead of Sonnet-only? My guess: ~30-50% of in-loop calls route down without moving the bench number, and the hosted-tier margin gets back a real chunk. Could be wrong.

Second angle: prompt caching on the CodeAct system prompt (it's stable across turns within a session). Anthropic prices cache reads at 10% of base input — free win on the hosted tier.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation. Your eval harness makes this a faster conversation than most.

[CAL_LINK] if it's interesting.

Matt
```

## Priority score

**8 / 10**

- (+) Highest-leverage prospect on this list: real spend (hosted tier), public eval harness (the unlock for safe model routing), well-resourced enough to actually engage a consultant if there's a finding.
- (+) Brennan is reachable via multiple verified surfaces (LinkedIn, X, personal site).
- (+) CodeAct architecture is publicly documented — audit hypothesis is verifiable from the open-source code before the call, no guessing.
- (+) Graham Neubig (academic co-founder) means eval rigor is in the team's DNA — "have you run the eval with a router?" is a question they can answer honestly.
- (–) Well-resourced means they probably HAVE thought about this. The pitch needs to be specific enough that "yes we already do that" isn't the easy out.
- (–) Open-source contributors will have file PRs about routing — check the repo for prior art before pitching.

## Notes for Matt

- **Highest priority on this lane's list.** Hosted-SaaS angle + public eval harness + named founders + verifiable public architecture = lowest-risk audit conversation.
- Before the call: read their `docs/openhands/usage/developers/evaluation-harness` page and search the repo for any PR mentioning "router", "haiku", "model selection". If they've already routed, the conversation pivots to caching + tool-result memoization.
- Graham Neubig is a published NLP researcher — bring eval-methodology language to the call, not vibes.
- Don't pitch the OSS — pitch the hosted tier where THEY pay for inference. The OSS users have their own bills.
