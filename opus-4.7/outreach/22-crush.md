# 22. Crush
- **Domain:** charm.land (product) / github.com/charmbracelet/crush (source)
- **OpenRouter rank:** 22
- **Category:** Open-source CLI/TUI coding agent (model-agnostic, split-pane diff view, "glamorous" TUI)
- **Prospect status:** Established CLI shop (Charm / Charmbracelet) — **funded ($6M from Gradient Ventures / Google's AI fund, Nov 2023), distributed team (US/Brazil/Canada/Kosovo/Sweden), revenue model is enterprise (`vt52@charm.land` for enterprise inquiries).** Real budget exists.

## Founder / contact
- **Christian Rocha** — Co-Founder & CEO of Charm. Background: Creative Director at Betaworks Studios, Head of Voice at Zenly, Head of Product/Technology/Editorial at Poncho. ArtCenter College of Design (graphic design).
  - GitHub: https://github.com/meowgorithm
  - Crunchbase: https://www.crunchbase.com/person/christian-rocha-2
  - The Org: https://theorg.com/org/charm/org-chart/christian-rocha
- **Toby Padilla** — Co-founder. Featured on Go Time podcast ep. 222 ("Making the command line glamorous").
- **Enterprise contact:** `vt52@charm.land` (publicly listed for enterprise inquiries on charm.land — VERIFIED from the homepage fetch)
- **General contact:** `vt100@charm.land`
- **Christian's email (per ZoomInfo, partially redacted):** `c***@charm.sh` — likely `christian@charm.sh`. **Not publicly verified — Matt should treat as inference, not fact.** Safer to use `vt52@charm.land` for first touch.
- Discord community available via charm.land
- Charmbracelet repo (Crush source): https://github.com/charmbracelet/crush
- Funding context: TechCrunch Nov 2023 — $6M led by Gradient Ventures.

## Bloat hypothesis
**Pattern 2 (Flagship-for-Easy) + Pattern 7 (No Eval Gate on Model Swap) at the Catwalk-catalog level.** Crush's architecture is model-agnostic by design — Anthropic, OpenAI, Gemini, Groq, Cerebras, Bedrock, Azure, Ollama, LM Studio, custom-OpenAI-compatible providers — and uses a **Catwalk catalog** ("community-supported repository of Crush-compatible models") to populate the model picker on first launch.

The bloat angle isn't Charm's own spend — Crush is BYO-key, users pay their own provider bills. It's **what the default Catwalk catalog surfaces at the top of the picker, and whether the agent loop has cheap-task routing for grep/format/classify steps vs the heavy diff-generation step.**

Three specific outside-the-box signals:
1. README explicitly says "runs great with no configuration" — meaning the default picker ordering is what most users see and accept.
2. No mention of per-step model routing inside the agent loop — every tool call's reasoning leg likely hits the user's selected flagship.
3. No mention of prompt caching / `cache_control` defaults in the published config — repeated system prompt + repeated tool definitions get re-billed every turn on Anthropic-backed sessions.

For a 25k+ install footprint, even a 30% input-cost cut via prompt-caching defaults + a "cheap-step router" config preset would be a publishable feature that drives Crush adoption (and gives Christian a "we save you money out of the box" marketing line vs competitors).

## Day-0 cold email

**Subject:** `Crush on OpenRouter — quick observation`

**Body:**

```
Hi Christian,

Crush showed up on the OpenRouter rankings this week — congrats, that's a real spend signal from the Crush install base (and a useful proxy for the model-picker UX winning).

Hypothesis from the outside: Crush's default Catwalk picker surfaces flagships at the top, and the agent loop calls the user's selected model for every tool-call reasoning step — including the grep / classify / format steps that route fine to Haiku 4.5 or Gemini Flash. Add no default cache_control on the system+tool-def prefix, and BYO-key Crush users are paying ~3-5x what they need to. Could be wrong — but if you ever wanted to ship a "Crush saves you money out of the box" config default, that's where I'd start digging.

Not pitching you for Charm-the-company spend — pitching you for a publishable preset + a marketing angle competing CLI coding agents can't match.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation.

[Cal.com link]

Matt
```

## Priority score
**7.5 / 10.** Funded ($6M), real enterprise contact path published, established team with multi-year shipping cadence, BYO-key product that benefits from "cheaper out of the box" positioning. **Best conversion shape of this batch.** Christian's background is product/creative (not pure infra) — peer-to-peer engineer pitch lands harder. Toby is the dev-side co-founder; a parallel touch to him via GitHub (@toby...) or Go Time podcast referral could work if Christian doesn't bite.

## Notes for Matt
- **Channel order:** Email `vt52@charm.land` first (it's the enterprise-inquiries inbox, so it gets read). If silence by day 4, LinkedIn DM to Christian. X DM as last resort; he's @meowgorithm on GitHub, likely similar on X.
- **Don't say "10x" or "scale" or "AI cost optimization"** — Christian's a designer-CEO; the visual-language tells of a salesperson will get filtered instantly.
- **Lean into the "publishable preset" angle.** Charm's whole brand is "glamorous open source"; a token-saving config that becomes a Crush release note is more interesting to them than a private cost-audit.
- **Catwalk is the real lever** — if Matt can frame the audit output as "I'll PR a tuned default catalog to the catwalk repo" instead of "I'll send you a PDF," that's a much warmer reception.
- **Contact gap:** Christian's direct email is inferred but not verified. The `vt52@charm.land` route is verified and appropriate for a first cold touch.
