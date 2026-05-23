# 17. Codebuff
- **Domain:** codebuff.com
- **OpenRouter rank:** 17
- **Category:** CLI coding agent (multi-agent: file-picker, planner, editor, reviewer); YC F24
- **Prospect status:** Active prospect — but harder sell (OpenRouter-native, model-mix savvy)

## Founder / contact

- **James Grugett** — Founder/CEO. LinkedIn: [james-grugett](https://www.linkedin.com/in/james-grugett/). Twitter/X: [@jahooma](https://x.com/jahooma). Previously founded Manifold Markets (prediction-market site, 150k user-created markets). YC F24 batch.
- **Brandon Chen** — engineering, on LinkedIn.
- Team is small (YC seed, 2024 batch).

Public email: not listed on landing page, but Grugett is highly active on X and LinkedIn. Email is likely discoverable via YC profile or his public-facing posts. The pattern with Manifold-alumni founders is they tend to publish their email in their bio or pinned tweet.

**Contact gap:** no public mailto on codebuff.com. LinkedIn or X DM is the realistic first touch. Could also be findable via `git log --format='%ae'` on the CodebuffAI/codebuff GitHub repo.

## Bloat hypothesis

**This is the hardest sell on this list — Codebuff is already model-savvy.** Their marketing leans into "supports any OpenRouter model" and Grugett has publicly tweeted about "building a new harness to maximize Opus 4.5 performance." They're not in the naive Flagship-for-Easy bucket.

That said, two real angles:

**Pattern #8 (Tool-Use Without Result Caching) — primary.** Multi-agent architecture means File Picker scans the codebase, Planner produces an ordered file list, Editor mutates, Reviewer re-reads. Across runs in the same session (and across users on the same OSS repo), File Picker results, AST scans, and dependency-map outputs are stable and recomputed. No mention of tool-result memoization in their public README or docs. 20-50% savings on agentic-loop input tokens is the live-eval target.

**Pattern #1 (Uncached System Prompt), per-agent variant — secondary.** Four agents = four system prompts (or one big one, depending on architecture). Each agent's prompt likely includes role + tool schemas + style guide + examples — easily 3-8k tokens each. With multi-agent orchestration, that's 4× the cache-eligible prefix. If they've cached the main agent prompt but not the sub-agent prompts, the secondary agents are the cost sink.

The Opus 4.5 harness work suggests they've tuned for accuracy; the question to ask Grugett is whether they ran the same eval rigor on Haiku 4.5 for the File Picker and Reviewer steps specifically. Those two roles are highly amenable to small-model routing — they don't write code, they classify and validate.

## Day-0 cold email

**Channel:** X DM (preferred — Grugett is active there) OR LinkedIn DM with the connection-request pattern.

**Subject (if email surfaces):** `Codebuff on OpenRouter — File Picker / Reviewer question`

```
Hi James,

Codebuff on the OpenRouter rankings — congrats, real spend signal.

Hypothesis from the outside: you've clearly done the Opus-4.5 harness work for the Editor and Planner, but I'd bet the File Picker and Reviewer agents are still on the same flagship endpoint when they don't have to be. Both are classify/validate roles — they don't write code. Haiku 4.5 on a 50-prompt eval set per role probably matches on accuracy and cuts ~70% of the per-call input cost for those two agents. Could be wrong, but it's the pattern I see most on multi-agent harnesses that grew from a single-agent baseline.

Second angle: tool-result memoization across runs (same OSS repo, multiple users, identical File Picker outputs). Less direct dollar-shave, but big latency win — which your "100s faster than Claude Code" framing rewards.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation. If there's nothing there, we shake hands and move on.

[CAL_LINK] if it's interesting.

Matt
```

## Priority score

**5 / 10**

- (+) YC-backed, real spend, clear public contact (Grugett is high-signal on X).
- (+) Multi-agent architecture is genuine token-bloat territory in the sub-agent prompts.
- (+) Their own marketing leans into "fast and cheap" — they care about this axis, conversation should be welcomed.
- (–) They're already OpenRouter-native and model-savvy. The "you should try Haiku" pitch lands flat — they probably have.
- (–) High likelihood they've already done some of the obvious work. Audit value lives in the secondary/sub-agent details, which is harder to convince-on-first-touch.
- (–) YC founder = tons of inbound, low marginal value of one more cold note.

## Notes for Matt

- This is the prospect where you should READ their changelog and Grugett's recent X posts BEFORE the call — coming in with the wrong hypothesis blows the trust budget. He's tweeted specifics about his harness work.
- The pitch angle that lands best is probably tool-result caching for the latency story (matches their "100s faster" branding), not raw cost reduction.
- If they reply "we already do all of this," ask which 2-3 patterns from the playbook they've addressed — Grugett is the type to actually answer that honestly, and you'll either learn or get leverage.
- Don't bother emailing a generic address. X or LinkedIn DM, naming a specific sub-agent.
