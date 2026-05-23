# 7. Roo Code

- **Domain:** roocode.com
- **OpenRouter rank:** #7 (17.8B tokens/week)
- **Category:** dev-productivity
- **Prospect status:** SHUT-DOWN (defunct, archived 2026-05-15)

## Founder / contact
- **Founder(s):** Matt Rubens (announced shutdown 2026-04-21; team pivoting to Roomote cloud agent)
- **Email:** n/a — extension archived, no outreach to Roo Code itself
- **LinkedIn:** n/a (not pursuing)
- **Twitter/X:** n/a (not pursuing)
- **Sources:** [The New Stack — Roo Code pivots to cloud-based agent](https://thenewstack.io/roo-code-cloud-ides-ai-coding/), [Kilo migration guide](https://kilo.ai/articles/roo-to-kilo-migration-guide), [cursor-alternatives.com shutdown writeup](https://cursor-alternatives.com/blog/roo-code-rules/)

## Bloat hypothesis
**Primary pattern:** N/A — product is dead. The interesting hypothesis is about the *displaced user base*.

**Evidence:**
- 17.8B tokens/week represented ~3M installs / 23k GitHub stars worth of users.
- Roo Code's own official migration recommendation: **Cline** (the upstream project Roo forked from). Also recommended by Roo itself: Kilo Code (Roo fork with continuity migration tool), Continue.dev, Bodega One.
- Token volume doesn't evaporate — it redistributes. Kilo Code is the likeliest top-1 destination because Kilo's migration tooling explicitly imports Roo custom modes / project rules / MCP configs. Cline is the institutional fallback.
- Roomote (cloud pivot) is a different product surface (chat-app, not IDE extension) — *some* Roo Code Pro subscribers will follow Matt Rubens there, but the IDE-extension power-user crowd is more likely to land on Kilo or Cline.

**Estimated savings:** N/A for Roo. **For the migrating user base** — same patterns as other coding agents (uncached system prompts, flagship-for-easy, tool-result re-injection). Migration shock means destination tools (Kilo especially) are absorbing 3M users very fast; their backend cost models are about to get stress-tested.

## Day-0 cold email
**Subject:** N/A — not contacting Roo Code.

**Body:**

```
N/A — product is defunct. See "Notes for Matt" for the actual play.
```

## Priority score
**Score:** 0/10 for direct outreach to Roo Code.
**Score: 8/10 for the displaced-users play — see notes.**

**Rationale:** Direct pitch to Roo Code is moot — extension archived 2026-05-15, team pivoted to Roomote. The actual play is reaching out to Kilo Code (the primary fork absorbing the user base) with a partnership/referral angle: their infrastructure is about to inherit Roo's token-bloat profile if they haven't audited.

## Notes for Matt

**The real opportunity is the migration cascade, not Roo itself.** Three angles worth considering:

1. **Kilo Code (kilo.ai)** — the Roo fork with the migration import tool. They're inheriting the largest share of Roo's 3M displaced users. Their backend hasn't been stress-tested at 17.8B-tokens-per-week scale. Pitch: "you just absorbed a 3M-user migration wave; the same uncached-system-prompt + flagship-for-easy patterns that scaled-hurt Roo's economics are now your problem. 20-min outside read while the cost curve is still tractable." This is the strongest play.

2. **Continue.dev (continue.dev)** — MIT-licensed, mature, more conservative user base. Smaller migration share but a real one. Same playbook.

3. **Bodega One (bodegaone.ai)** — standalone IDE absorbing the "I want out of VS Code entirely" cohort. Smaller but interesting because they're a full-stack IDE play with more architectural surface area to audit.

**Don't pitch Roomote** — it's a different product (cloud chat, not IDE), and Matt Rubens just finished a brutal shutdown announcement; he's in pivot mode, not optimization mode. Maybe revisit in 6 months when Roomote has its own OpenRouter ranking.

**Don't waste a slot on Roo Code itself.** Mark this row done, redirect the energy.

**Practical next step if Matt wants to pursue the cascade:** spawn a separate research lane for Kilo Code as a fresh prospect (find founder, draft Day-0 referencing the migration absorption directly). That's not in scope for this rank-6-10 batch but it's the highest-leverage descendant of this row.
