# 23. GPT Workspace
- **Domain:** gpt.space
- **OpenRouter rank:** 23
- **Category:** Chrome extension + Google Workspace add-on — brings GPT-5.2 / Claude / Gemini into Docs, Sheets, Slides, Gmail, Drive
- **Prospect status:** **Highest unit-economic pressure in this batch.** Flat ~$9.99/mo Pro tier with "unlimited credits and priority model access" + free tier with monthly credits, running on flagship models. Margin is razor-thin or negative on power users.

## Founder / contact
- **Founder identity is the biggest gap in this lane.** The lane brief said "Pulkit Goyal" — I could not verify a Pulkit Goyal connected to gpt.space through public sources. Multiple Pulkit Goyals on LinkedIn (CA, AI researcher, project manager, Badho, Guardian, GateMedia, etc.), none with a confirmable gpt.space link.
- The GitHub organization (https://github.com/GPT-Workspace) shows the Chrome extension repo but no public maintainer names — the listed dev credit in some Chrome Store mirrors is "Qualtir Group Account" (unverified).
- Public surfaces:
  - GitHub org: https://github.com/GPT-Workspace
  - Extension repo: https://github.com/GPT-Workspace/GPT-Workspace-Chrome-Extension
  - Chrome Web Store: https://chromewebstore.google.com/detail/gpt-workspace/jgocjgkdladclacgmkkiklmdcmngjcba
  - Twitter: @gpt_workspace
  - YouTube: @gptworkspace
  - Instagram: @gptworkspace
  - Support portal: https://support.gpt.space/
- **No publicly listed founder email or LinkedIn — channel of choice is the X DM (`@gpt_workspace`) or the support portal escalation.** "Qualtir" may be a company name worth a separate LinkedIn search before sending.
- **Action item before sending:** Matt should (a) check the Chrome extension's privacy policy / "developer contact" field on the Chrome Web Store listing — Chrome requires a public developer email, (b) check the GPT-Workspace GitHub org's "people" tab to identify maintainers, (c) check the @gpt_workspace X bio for a founder handle.

## Bloat hypothesis
**Pattern 1 (Uncached System Prompt) + Pattern 2 (Flagship-for-Easy) compounding under a fixed-price subscription.**

The homepage explicitly markets "GPT-4o, Claude Opus, and Gemini Pro" — i.e. the **most expensive tier of each provider** — at $9.99/mo unlimited. The math is brutal:

- 100 power users at 1M tokens/day × Claude Opus ($15/M input + $75/M output) = $9,000/day in COGS to make $999 in MRR. Even with cheap-skewed mixes, $9.99/mo unlimited Claude Opus is a runway burn.
- The Workspace integration pattern (Docs/Sheets/Slides/Gmail/Drive) means each call ships:
  1. A long static system prompt explaining tool context (Docs vs Gmail vs Sheets) — Pattern 1 caching candidate.
  2. The full document/sheet content in the user prompt — Pattern 3 (Full-Context Stuffing) — when chunking/retrieval would work for most edit operations.
  3. A flagship model selection regardless of task — summarization, formula generation, and email reply drafting do not need Opus.
- Pattern 4 (No Batch API for Async Jobs) likely applies to the "Drive search" and "Sheets bulk analysis" features — these are batch-shaped workloads going through realtime endpoints.

**Estimated cut: 50-75% of token COGS** by (a) tiering models per surface (Haiku/Flash for Gmail summaries, Sonnet for Docs writing, Opus only for explicit "deep work" requests), (b) caching the per-surface system prompts, (c) retrieval over Drive contents instead of full-doc stuffing.

This is the **strongest unit-economics pitch in the batch** — a flat-price subscription on flagship models is the literal canonical bloat-audit target from the playbook's "pricing page reverse-engineering" bonus section.

## Day-0 cold email

**Subject:** `GPT Workspace on OpenRouter — quick observation`

**Body (assuming Matt identifies a verified email or routes via X DM with the same text trimmed to 280 chars):**

```
Hi team,

GPT Workspace showed up on the OpenRouter rankings this week — congrats, that's a real spend signal.

Hypothesis from the outside: $9.99/mo unlimited with Opus/GPT-5/Gemini Pro across Docs/Sheets/Slides/Gmail/Drive is the kind of unit-economics where the COGS curve gets interesting fast. Best guess at the cut: per-surface model tiering (Haiku/Flash for Gmail summaries, Sonnet for Docs writing, Opus only on explicit deep-work requests), prompt caching on the per-surface system prefixes, and retrieval over Drive instead of full-doc stuffing. 50-75% feels achievable. Could be wrong — but the pricing page is the strongest external signal I've got.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation.

[Cal.com link]

Matt
```

## Priority score
**8 / 10 if a verified contact surfaces. 4 / 10 if it doesn't.** The unit-economics pitch is the cleanest of this batch — flat-price subscription on flagship models is textbook bloat — but the founder/contact gap is severe. **Conversion potential is high IF Matt can route the message; otherwise dead on arrival.** Worth Matt's 10-minute pre-flight to nail the contact before sending.

## Notes for Matt
- **Channel order:** (1) Chrome Web Store developer-contact field on the extension listing — Chrome mandates a public email, that's the cleanest. (2) X DM `@gpt_workspace` with a 280-char compressed version. (3) Support portal escalation as a long-shot.
- **The pricing-page-reverse-engineering pitch** maps perfectly onto this prospect. Use it.
- **Don't claim a specific dollar number.** "50-75%" is defensible; "save you $40k/mo" is not.
- **Pulkit Goyal as founder is UNVERIFIED.** If Matt confirms via the Chrome Store dev field, swap "team" → first name in the salutation. Otherwise the "Hi team," opener is the honest default.
- **Contact gap is the binding constraint.** I'd defer this outreach by a day rather than send to a generic support inbox — pursuit only after Matt locates a real founder/maintainer surface.
