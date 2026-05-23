# 4. Descript

- **Domain:** descript.com
- **OpenRouter rank:** #4 (token volume not exact but in the multi-trillion range — they're on the leaderboard via Underlord's AI co-editor)
- **Category:** vertical-productivity (AI video / podcast editor with Underlord AI co-editor)
- **Prospect status:** PROSPECT — late-stage venture-backed company (Andrew Mason ex-Groupon founder, Laura Burkhauser now CEO), real product team, real margin pressure. Underlord is the AI surface that drives the OpenRouter spend.

## Founder / contact

- **Founder(s):**
  - **Andrew Mason** — Founder, currently Executive Chairman. Former Groupon co-founder/CEO, former Detour founder/CEO. Based Berkeley CA.
  - **Laura Burkhauser** — CEO (took over from Mason in 2025). Background: Director of Product at Twitter and Rent the Runway. UC Berkeley Haas. Based SF.
- **Email:** Both have `@descript.com` addresses but they're partially redacted in public sources (RocketReach, ZoomInfo show first-letter-masked formats like `l***@descript.com` for Laura, `a***@descript.com` for Andrew). **Not publicly listed in the cold-email-ready sense.** Pattern is almost certainly `first@descript.com` or `firstlast@descript.com` but I cannot verify without doing it once on a different employee and reading the bounce — which would burn the prospect. **Mark as: not publicly listed in cold-emailable form; LinkedIn is the verified channel.**
- **LinkedIn:**
  - [Laura Burkhauser](https://www.linkedin.com/in/burkhauser/) (CEO, primary target)
  - [Andrew Mason](https://www.linkedin.com/in/andrewmason/) (Exec Chair, secondary)
- **Twitter/X:** [@andrewmason](https://x.com/andrewmason) (Andrew); Laura's X handle not prominently surfaced in public results.
- **Sources:**
  - [Descript pricing page](https://www.descript.com/pricing)
  - [Descript Changelog: Underlord model picker including Claude Sonnet 4.5](https://descript.canny.io/changelog/introducing-model-selection-for-underlord-including-claude-sonnet-45)
  - [Crunchbase: Andrew Mason](https://www.crunchbase.com/person/andrew-mason)
  - [LinkedIn announcement: new CEO Laura](https://www.linkedin.com/posts/andrewmason_congratulations-to-descripts-new-ceo-activity-7366543425963290624-g0Av)

## Bloat hypothesis

**Primary pattern:** #1 — Uncached System Prompt (very likely) + #4 — No Batch API for Async Jobs (likely)

**Evidence (public signals):**
- Descript's changelog explicitly says Underlord is *"not just one AI model doing everything—it's a mix of models from different providers, each handling different parts of the agent"* — which actually means **pattern #2 (Flagship-for-Easy) is LESS likely** than for other apps in this batch. They've done the model-routing work. **That makes caching the higher-EV target.**
- Underlord operates on transcript-grounded context: the user's full conversation transcript gets injected into every editing instruction. For a 60-minute podcast that's 8K-15K tokens of transcript per call, mostly stable across the editing session. **Pattern #1 applies hard** — the transcript prefix is byte-identical across many user edits in the same session, but with no Anthropic `cache_control` marker every edit re-bills the full input.
- The pricing tier is **credit-based** ("AI Credits track your usage of AI features"; Free = 100 credits, Hobbyist = 400, Creator = 800+500 bonus) — which means **Descript pays vendor list, charges users in opaque credits**, and absorbs the delta. That's the classic margin-on-credit-bundles model where prompt caching directly improves unit margin.
- Async surfaces in their product (auto-transcribe, studio sound, eye contact correction, green screen, AI-generated avatars) all have batch-shaped traffic — user uploads, work happens in background, result shown later. Pattern #4: these don't need realtime endpoints. Anthropic / OpenAI Batch API = 50% off, vendor-documented.
- Long-running product (shipping since 2017+) with multiple "improved tone / less robotic / more concise" changelog entries — pattern #10 supporting indicator (Verbose System Prompts) but not the primary tell.

**Estimated savings:** 30-50% blended on Underlord input cost (pattern #1) + 40-50% on batch-amenable async features (pattern #4). The combination compounds.

## Day-0 cold email

**Subject:** Descript / Underlord on OpenRouter — quick observation

**Body:**

> Hi Laura,
>
> Descript on the OpenRouter rankings via Underlord — congrats, that's a real spend signal. The recent Underlord model picker (Haiku/Sonnet/Opus 4.5) is a nice piece of routing work — clearly someone on the team owns model mix.
>
> Hypothesis from the outside that the model picker doesn't address: Underlord edits run against the transcript-grounded context, and a 60-min podcast transcript (8-15K tokens) re-bills every edit in a session. With Anthropic `cache_control` on the transcript prefix, that's a 70-90% input-cost cut on the cacheable share — and it doesn't change Underlord's output behavior. Same logic on the async surfaces (Studio Sound, Eye Contact, AI-avatar gen) where Batch API discounts ~50% on workloads that already tolerate non-realtime latency.
>
> Could be wrong — possible the team's already cache-tuned at the API layer.
>
> I run a small consultancy doing token-bloat audits. Ruby/infra background, peer-to-peer not salesy. Offer: 20 min on Zoom, I show you the 2-3 patterns I'd dig into first on Underlord specifically, you get a one-page writeup. Free, no obligation.
>
> {{CAL_LINK}} if it's interesting.
>
> Matt

## Priority score

**Score:** 7

**Rationale:** Big, real, well-funded company with documented inference surface and visible margin-on-credits model — but bigger orgs have longer cycles, and Laura just became CEO (Aug 2025) so her priority surface is product/people, not COGS audits. LinkedIn-first is the right play. Drops below Hermes (which has a more reachable founder) and Kilo (which has tighter margin pressure on KiloClaw).

## Notes for Matt

- **The transcript-caching angle is genuinely insight-shaped.** It's pattern #1 applied to a vertical-specific workload (audio/video editing on a fixed transcript) where the prefix-ratio is unusually high. Even if they're not interested in a consult, this is a real engineering observation that may earn a reply on merit.
- **Laura > Andrew for outreach.** Andrew is Executive Chair (board-shaped role); Laura is operating CEO who'll make budget decisions. The LinkedIn note should reference the Underlord model-picker work explicitly — it shows you've actually used the product.
- **Andrew Mason is famously responsive on X** ([@andrewmason](https://x.com/andrewmason), Detour founder, mid-career second-act energy). Twitter DM from Matt may actually land if LinkedIn doesn't — but it's a less-natural surface for a B2B audit ask.
- **Email is the blocker here.** Pattern almost certainly works but I'm holding to the hard rule. If Matt wants to escalate beyond LinkedIn, the next move is searching public commits on Descript-affiliated repos (there are some Descript-owned npm packages — `descript-audio-codec` and similar — that might surface a verified email).
- **Pricing model is a gift for the pitch.** Credit-based opaque pricing means every input-token saved goes straight to gross margin — no need to pass savings to customers to realize them. That's the cleanest sales narrative in this batch.
