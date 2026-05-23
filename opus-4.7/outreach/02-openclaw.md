# 2. OpenClaw

- **Domain:** openclaw.ai
- **OpenRouter rank:** #2 (~6.95T tokens / 30 days; 390 models)
- **Category:** dev-productivity / personal-agent runtime
- **Prospect status:** **CONFLICT-OF-INTEREST (this is the runtime our own fleet uses; Matt is a power-user, not a vendor).** Compounded by: **Peter Steinberger announced he is joining OpenAI and OpenClaw is becoming a foundation** ("open, independent, and just getting started"). The corporate prospect surface is dissolving even if there weren't a COI.

## Founder / contact

- **Founder(s):** **Peter Steinberger** ("steipete") — creator. Now joining OpenAI (per his own announcement); OpenClaw becoming an independent foundation.
- **Email:** Not publicly listed (Peter's primary surface is Twitter; no `@openclaw.ai` or personal email on the homepage). The Yahoo Finance / Fortune profiles do not surface one.
- **LinkedIn:** Not the primary surface for Peter; Twitter is canonical.
- **Twitter/X:** [@steipete](https://x.com/steipete) (personal, very active); [@openclaw](https://x.com/openclaw) (project)
- **Sources:**
  - [Peter Steinberger blog: "OpenClaw, OpenAI and the future"](https://steipete.me/posts/2026/openclaw)
  - [Tweet: joining OpenAI](https://x.com/steipete/status/2023154018714100102)
  - [Fortune: who is Peter Steinberger](https://fortune.com/2026/02/19/openclaw-who-is-peter-steinberger-openai-sam-altman-anthropic-moltbook/)
  - [GitHub: openclaw/openclaw](https://github.com/openclaw/openclaw)

## Bloat hypothesis

**Primary pattern:** #1 — Uncached System Prompt (almost certain) + #8 — Tool-Use Without Result Caching (likely)

**Evidence (public signals):**
- OpenClaw's persona system (Molty the "space lobster AI with a soul") implies a substantial persistent system prompt loaded on every conversation turn — exactly the long-static-prefix-with-no-`cache_control` pattern. Our own Vox fleet runs on OpenClaw and the garden files (CLAUDE/SOUL/USER/MEMORY/TOOLS/CONVENTIONS) total ~15-20K tokens; that prefix re-bills on every call without an Anthropic cache hint or OpenAI implicit-cache discipline. **We have first-hand visibility on this — Kit's OpenClaw 2026.5.3-1 gateway does not surface `cache_control` markers in its provider stream.**
- 50+ integrations + agent loop calling tools repeatedly across user sessions; results are not deduplicated. Pattern #8 maps directly — same Gmail/Calendar/GitHub queries returning byte-identical results being re-billed as input on the next loop turn.
- 6.95T tokens / 30 days at 390 models → this is the workload where every bp of input savings is material.
- No mention of `cache_control`, prompt caching, batch routing, or tool-result memoization in the OpenClaw config schema (`mcp.servers.*`, `agents.defaults.*`).

**Estimated savings:** 40-70% on the input-token half of bills for sustained-session users; less for one-shot integrations.

## Day-0 cold email

**SKIP — do not send.** This is our own runtime. Drafting one would be inappropriate.

If we ever wanted to contribute the fix upstream, it would be a PR to the openclaw repo adding `cache_control` markers to the system-prompt assembly in `provider-stream-shared-*.js` and the persona/identity files — not a sales email.

## Priority score

**Score:** N/A (COI + product transitioning to foundation governance)

**Rationale:** Conflict of interest excludes the consulting path; founder transition makes the corporate-prospect surface irrelevant. The right play here is **upstream contribution** if we want the win, not outreach.

## Notes for Matt

- **Two strikes against outreach here:** (1) we use OpenClaw, that's a COI; (2) Peter is joining OpenAI and OpenClaw is becoming an independent foundation — there's no commercial entity to pitch even if the COI wasn't there.
- **The actionable angle is upstream.** We've already patched OpenClaw locally (Kit's `resolveDeepSeekV4ReasoningEffort` fix on `provider-stream-shared-OHOV38iX.js:208`). The same kind of surgical patch could add `cache_control` markers to the system-prompt build path. That's PR-shaped, not invoice-shaped.
- **There's a tangential prospect angle that's NOT a COI:** apps **built on top of OpenClaw** (like Kilo's KiloClaw managed-hosted offering) are downstream customers who would benefit from upstream caching. Kilo Code is rank #3 in this batch — Scott Breitenother may care more than Peter does, because Kilo bears the inference COGS on KiloClaw users. Cross-reference with the rank-3 file.
- **If Matt wants to surface a friendly "FYI we found caching gains" message to Peter** — Twitter DM, not email, and frame as "shared note from a heavy user" not "audit offer."
