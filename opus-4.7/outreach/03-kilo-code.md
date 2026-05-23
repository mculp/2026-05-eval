# 3. Kilo Code

- **Domain:** kilocode.ai (308-redirects to kilo.ai)
- **OpenRouter rank:** #3 (~5.21T tokens; 356 models; team self-reports "six trillion tokens a month")
- **Category:** dev-productivity (open-source AI coding agent)
- **Prospect status:** PROSPECT — strongest reachable target in this batch. Real venture-backed company (raised $8M in Dec 2025 per CNBC), real CEO with operator background, real margin pressure (KiloClaw is a managed hosted offering — Kilo bears the inference COGS).

## Founder / contact

- **Founder(s):**
  - **Scott Breitenother** — Co-founder & CEO. Previously founded Brooklyn Data (grew to 100+ person consultancy, sold). Operator who'll look at the math. Based DC-Baltimore metro per LinkedIn.
  - **Sytse "Sid" Sijbrandij** — Co-founder. Former GitLab co-founder & CEO. The famous open-source-radical-transparency operator; not the day-to-day CEO of Kilo but the inspiration for the open-source thesis.
- **Email:** Not publicly listed on the kilo.ai about page. Inferred-but-unverified pattern would be `scott@kilo.ai` or `scott@kilocode.ai` — **not sending until verified** (per the hard rule). LinkedIn is the primary route.
- **LinkedIn:** [Scott Breitenother](https://www.linkedin.com/in/scottbreitenother) (verified)
- **Twitter/X:** [@kilocode](https://x.com/kilocode) (company); Scott's personal X handle not surfaced in public sources I could verify
- **Sources:**
  - [kilo.ai/about](https://kilo.ai/about) — team page (Scott named as Co-founder & CEO)
  - [Crunchbase: Scott Breitenother](https://www.crunchbase.com/person/scott-breitenother)
  - [CNBC: Kilo raises $8M (Dec 2025)](https://www.cnbc.com/2025/12/10/former-gitlab-ceo-raises-8-million-for-kilo-to-compete-in-vibe-coding.html)
  - [GitHub: Kilo-Org/kilocode](https://github.com/kilo-org/kilocode)
  - [Tessl blog interview](https://tessl.io/blog/inside-kilo-code-an-open-source-ai-coding-agent-with-plans-to-reshape-software-development/)

## Bloat hypothesis

**Primary pattern:** #5 — No Semantic Cache on Repeat Sub-Prompts (compounded by #3 — Full-Context Stuffing for "codebase understanding")

**Evidence (public signals):**
- Marketing language: *"AI that understands your entire codebase"* and *"reads entire codebases for context-aware assistance"* — pattern #3 indicator. Codebase-understanding without RAG = stuffing the codebase in context on every turn. No mention of embedding indexes, retrieval, or chunk-level scoping in the public docs.
- Coding-agent prompts cluster heavily on a small intent set: "explain this error", "write a test for X", "refactor this method", "what does this regex do." That's pattern #5 cache territory — and the OpenRouter page shows 356 models routed through, but no `gptcache` / `redis` / `langfuse-cache` mention in the kilocode GitHub repo's README or stack docs.
- 5 agent modes (Code, Architect, Debug, Ask, Custom) all sharing one model-selection surface — but no surfaced eval gate documentation (pattern #7 supporting indicator). They CAN route across 500+ models and Kilo Gateway, but routing-by-mode without an eval set means defaults stay flagship "to be safe."
- They self-report "six trillion tokens a month" — at that volume, even a 10% cache hit rate on repeat sub-prompts is huge.
- The KiloClaw managed offering ($55/mo) bears their inference COGS directly — Scott has direct margin incentive to care.

**Estimated savings:** 25-50% on KiloClaw-side inference if semantic cache + per-mode eval gates land. Less material on BYOK users (where the customer eats the cost) — but those are also customers Kilo could differentiate by exposing cache hit rates.

## Day-0 cold email

**Subject:** Kilo Code on OpenRouter — quick observation

**Body:**

> Hi Scott,
>
> Kilo at #3 on OpenRouter (~5T tokens, 356 models) — congrats, that's a real spend signal. CNBC piece on the $8M raise was a good read; the Brooklyn Data → Kilo arc tracks.
>
> Hypothesis from the outside: KiloClaw is the surface where the inference COGS lands on you (not BYOK users), and two patterns probably help — (1) coding-agent prompts cluster heavily on a small intent set ("explain this error", "write a test for X"), so a semantic-cache layer over repeat sub-prompts likely lands a 20-40% cut on the cacheable share; (2) the "AI reads your entire codebase" framing suggests full-context stuffing where a chunk-retrieval pass would trim input tokens 5-10x on most turns. Could be wrong — possible you're already running both.
>
> I run a small consultancy doing token-bloat audits. Ruby/infra background, peer-to-peer not salesy. Offer: 20 min on Zoom, I show you the 2-3 patterns I'd dig into first on KiloClaw specifically, you get a one-page writeup. Free, no obligation.
>
> {{CAL_LINK}} if it's interesting.
>
> Matt

## Priority score

**Score:** 9

**Rationale:** Highest-priority of the batch. Real margin pressure (KiloClaw hosted), real volume (6T/mo), reachable operator-CEO (Brooklyn Data → Kilo arc means he speaks consulting-engineer fluently), recently-funded so they have budget for a fixer if the audit lands. The drag is finding a verified personal email — LinkedIn is the safer first surface.

## Notes for Matt

- **LinkedIn is the channel here**, not email — I couldn't verify a personal email and the hard rule says don't guess. LinkedIn DM with the connection-note template from the outreach pack is the right play.
- **Brooklyn Data background = strong tell that he'll engage**. He grew an operator-craft consultancy himself, so the "peer-to-peer audit offer" frame will read as native rather than salesy.
- **KiloClaw is the wedge.** The free `Kilo Code` extension is BYOK (the user eats the cost); KiloClaw at $55/mo and Kilo Pass ($19-$199/mo) are where Kilo eats the cost. Frame the audit around "KiloClaw margins" specifically — that's where the conversation has real leverage.
- **Cross-reference with rank #2 (OpenClaw):** Kilo's KiloClaw is *literally a managed OpenClaw* deployment. So inference patterns on OpenClaw upstream (cache_control, system-prompt size) directly affect KiloClaw COGS. There's a "we use the same runtime you do" credibility play for Matt here — without disclosing fleet details, just framing as "we operate at the OpenClaw layer too."
- **Funding context:** $8M Dec 2025 + Sid Sijbrandij involvement means they're well-resourced but also under pressure to demonstrate efficient use of capital. Token-bloat audit hits that narrative perfectly.
- **Verify email before any send.** Try `git log --format='%ae' | sort -u` on the kilocode repo for Scott's commit email, or check his Crunchbase profile. If nothing verified, LinkedIn-first.
