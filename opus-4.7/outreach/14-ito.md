# 14. Ito

- **Domain:** ito.ai
- **OpenRouter rank:** 14
- **Category:** Agentic QA / pre-merge testing (B2B dev-tools)
- **Prospect status:** PROSPECT (strong fit — small team, agentic loops with high token spend per test run, computer-use-style flows are token-heavy by design).

## Founder / contact

- **Barron Caster** — Co-founder / CEO. LinkedIn: https://www.linkedin.com/in/barroncaster/ (verified). Based SF Bay Area.
- **Company LinkedIn:** https://www.linkedin.com/company/ito-hq
- **Co-founder** — not publicly identified on the marketing site. LinkedIn "Ito AI" company page may surface the second founder; Matt should check before outreach.
- **Funding:** not publicly disclosed (no obvious press releases found). "Early access" framing on site + small testimonial set (Truemed, Inkeep, CNaught, Temi as customers — all small/mid YC-era startups) suggests pre-seed or seed-stage, ~5-15 person team.
- **Contact:** "Get Early Access" form at ito.ai/get-early-access — likely lands in Barron's inbox at that scale. No public `team@` or founder email listed. Pattern guess `barron@ito.ai` plausible but unverified.

## Bloat hypothesis

Ito's product description IS the bloat hypothesis. They run an "agentic QA platform that actually runs your app" with "code-aware inference," "deep browser inference," "isolated sandbox execution," "computer-use agents," and "autonomous PR validation." Every one of those features is a token-heavy agentic loop.

The hypothesis stack, strongest first:

1. **Tool-use without result caching (pattern 8).** Their agent inspects the user's app, makes browser calls, reads code, generates assertions, replays flows. Same PR → same impacted files → same code-reads. If the agent doesn't memoize `(tool_name, file_path) → result`, then re-runs of the same PR's test pass re-bill identical tool reads. Saves 20-50%.
2. **Flagship-for-Easy (pattern 2).** Their agent loop almost certainly defaults to Sonnet 4.5 / GPT-5 for the entire stack: planning, action selection, assertion generation, bug report writing. The bug-report-write step ("here's a video of what broke, here's a markdown summary") is a Haiku-class task. Visual proof generation summaries and reproduction steps don't need flagship.
3. **No Batch API for the long-tail PR backfill (pattern 4).** Their marketing talks about "10x QA coverage" — implies they're running test suites on PRs that don't have a human waiting on the result in the moment (overnight regression runs, retroactive coverage on old code). Anthropic / OpenAI Batch is 50% off for anything not user-facing in the 24h SLA window.
4. **Full-context stuffing on the codebase (pattern 3).** "Code-aware inference" suggests they may be stuffing impacted files into context rather than embedding-indexed retrieval. Hard to verify from outside.

**Strongest framing for outreach:** Lead with the tool-use caching angle. It's the most specific, the most directly tied to their actual product description ("autonomous validation" = agent loops = re-reading the same files across runs), and the easiest for an engineer to A/B test in an afternoon.

## Day-0 cold email

**Subject:** `Ito on OpenRouter — agent loop caching question`

**Body:**

```
Hi Barron,

Ito showed up on the OpenRouter rankings this week — congrats. Agentic QA is the right category to be in and that's a real spend signal.

Hypothesis from the outside: your agent loop reads the same impacted files / runs the same browser actions across PR re-runs without memoizing tool results. On a busy repo, the same file probably gets read into context 5-10x per day across different test passes. Hash (tool_name, args) → result with a short TTL cuts 20-50% on agentic workloads. Could be wrong — but it's the pattern I see most on computer-use-style agents.

Secondary angle: the bug-report-write step ("video + markdown summary + repro steps") is a Haiku-class task even if planning/action-selection needs Sonnet. Worth a 50-prompt eval.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 min on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation.

cal.com/matt-culpepper/token-audit if it's interesting.

Matt
```

## Priority score

**Priority: 9/10 — top prospect in this batch**

- Token-heavy by product design — agent loops + computer-use-style browser inference + code-aware reasoning on PRs. The math is on Matt's side here.
- Small team, founder-led, no obvious LLM-ops hire yet (no public mentions of an evals engineer in their job postings or team page) — they FEEL the cost but probably haven't dedicated headcount to it.
- Pre-seed / seed-stage = runway-sensitive = receptive to "I can show you a 40% cut on your single biggest variable cost."
- Specific hypothesis (tool-result caching) is unusual enough that even if Ito has thought about it, Matt sounds credible. Generic "you have bloat" lands flat.
- Founder email gap is the friction point. LinkedIn DM to Barron is the right first surface; "get early access" form is a maybe.

## Notes for Matt

- **Lead with Barron via LinkedIn DM** (https://www.linkedin.com/in/barroncaster/) — pattern-guessed emails to small startups are 50/50 to bounce or land in spam. LinkedIn DM has higher signal here.
- Don't bother with the "Get Early Access" form — that's a marketing funnel, won't reach Barron with a peer-to-peer message intact.
- Their customer testimonials (Truemed, Inkeep, CNaught, Temi) are all small startups — Ito is selling to people who feel cost, which means the audit conversation lands easier ("your customers care about this too").
- Their `/why-we-built-ito` page is worth reading before outreach — it'll give you Barron's framing on what "QA done right" means, and you can match his vocabulary in the email.
- If they respond engaged, the natural follow-on is offering to write the tool-result cache layer for them. Don't quote a number on first reply — book the 20 min, scope live.
- This is the highest-conviction prospect in the batch. If you only do one Day-0 send tonight, do this one.
