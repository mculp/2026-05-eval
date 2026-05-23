# 12. Zed Editor

- **Domain:** zed.dev
- **OpenRouter rank:** 12
- **Category:** Native AI code editor (B2B/B2C dev tools, Rust)
- **Prospect status:** PROSPECT (well-funded, but BYO-key model — bloat angle is around their DEFAULT Agent Panel model selection and the per-user economics of the hosted Claude/Zed-managed plans).

## Founder / contact

- **Nathan Sobo** — Founder & CEO, Zed Industries. LinkedIn: https://www.linkedin.com/in/nathan-sobo-92b46720/ (verified). Boulder, CO. Ex-GitHub lead of the Atom editor team (2011-2018). Co-led Teletype for Atom (one of first production CRDTs for collaborative editing).
- **Antonio Scandurra** — Co-founder. Ex-Atom team.
- **Max Brunsfeld** — Co-founder. Ex-Atom team. Creator of Tree-sitter.
- **Funding:** Series B, $32M (Aug 2025), Sequoia + others. Total raised est. $50M+.
- **Founder email:** not publicly listed. Pattern is likely `nathan@zed.dev` but unverified — don't fabricate. Twitter `@nathansobo` is publicly active (good secondary surface). Team page lives at zed.dev/team.

## Bloat hypothesis

Zed has TWO usage modes that create distinct bloat profiles:

1. **BYO-key users** — the user is paying for tokens, so Zed's direct cost is $0 but Zed's UX is incentivized to make agent calls SEEM cheap by hiding model selection. The bloat hypothesis here is **Flagship-for-Easy (pattern 2) by UX default** — Agent Panel ships pointing at Claude Sonnet 4.5 / Opus by default for tasks like "summarize this diff" or "rename this symbol" that Haiku 4.5 handles cleanly at 1/3 the cost. If they ever ship a "smart routing" mode for paying-tier users, the savings on the BYO-key population would be real customer-experience wins, not just margin.

2. **Zed-managed / hosted-model plans** — where Zed eats the inference cost. This is where bloat = burn. Default Agent Panel still picks Sonnet for the easy-tier work; Edit Prediction is a separate open-source model (good). If they're not aggressively routing the long tail of cheap tasks (commit-message gen, file summaries, symbol rename) to Haiku/Mini, they're either burning runway or pricing the hosted plan to absorb it.

Tertiary signal: their Agent Panel supports MCP servers + "Claude Agent, OpenCode, and MCP servers" — agentic loops without aggressive tool-result caching (pattern 8). On a multi-file refactor, a Zed agent loop probably re-feeds the same file content into context 4-5x.

**Strongest framing for outreach:** Agent Panel default-model selection is the lever. They have an eval harness already (Edit Prediction shipped open-source — that team knows how to eval models). One run of the bloat playbook's pattern-2 routing matrix against the Agent Panel's actual usage distribution probably shows 40-60% of calls route cleanly to Haiku.

## Day-0 cold email

**Subject:** `Zed on OpenRouter — Agent Panel routing question`

**Body:**

```
Hi Nathan,

Zed showed up on the OpenRouter rankings this week — congrats, that's a real spend signal even with BYO-key in the mix.

Hypothesis from the outside: Agent Panel defaults to Sonnet 4.5 across the board, but the actual task distribution (commit message, symbol rename, file summary, diff summary, agentic refactor) probably routes ~40-60% cleanly to Haiku 4.5 with no quality regression. Could be wrong — but it's the pattern I see most on agentic editors. The team that shipped Edit Prediction as open-source already knows how to build the eval gate.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 min on Zoom, I show you the 2-3 patterns I'd dig into first (Agent Panel routing, tool-result caching on multi-file edits, default model on Edit Prediction), you get a one-page writeup. Free, no obligation.

cal.com/matt-culpepper/token-audit if it's interesting.

Matt
```

## Priority score

**Priority: 7/10**

- Well-funded ($50M+) so they have budget for an audit and the infrastructure team to act on findings.
- Nathan and team are technical, ex-GitHub, will respond to a precise hypothesis over a sales pitch.
- BYO-key model means direct cost-saving impact is muted, BUT user-facing cost-experience is a real product lever.
- Edit Prediction shipped as open-source = they have eval discipline already. Outreach hits a team that CAN act on the writeup, which is the whole point of the audit lane.
- Founder email unverified — Twitter DM `@nathansobo` is the backup surface and is more in-character for him anyway.

## Notes for Matt

- Nathan is publicly active on Twitter (`@nathansobo`); if email bounces or no reply by Day 4, Twitter DM is the right secondary surface. Skip LinkedIn for him — Twitter is where the Zed/Atom community actually lives.
- The Agent Panel routing angle is the specific hypothesis to lead with. Don't generalize to "you have bloat" — they'll roll eyes.
- Their Sequoia podcast appearance ("Why IDEs Won't Die in the Age of AI Coding") is worth listening to before the call — gives you Nathan's mental model of where AI editors are going.
- If they say "we already route to Haiku where we can" — ask what the eval methodology is and which Agent Panel actions they've routed. That's the actual depth check.
- Antonio and Max are also reachable; Antonio is the more technical "show me the data" engineer if the convo goes deep.
