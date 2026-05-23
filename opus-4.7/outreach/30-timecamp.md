# 30. TimeCamp
- **Domain:** timecamp.com
- **OpenRouter rank:** 30
- **Category:** Established time-tracking SaaS, recently bolted on AI ("TIC" autonomous agent)
- **Prospect status:** Researched, founder confirmed, contact channel TBD

## Founder / contact

- **Kamil Rudnicki** — Founder & CEO. Polish founder, based in Wrocław. Founded TimeCamp in 2008-2009. Personally programmed first version. 4000+ customers worldwide.
- **Crunchbase:** https://www.crunchbase.com/person/kamil-rudnicki
- **GitHub:** https://github.com/kamil-rudnicki
- **Personal site:** https://kamilrudnicki.com/
- **Education:** University of Wrocław; Wrocław University of Economics (e-business).
- **Recognition:** 2018 "50 Most Creative People in Business" listing.
- **LinkedIn:** referenced in Crunchbase + The Org but URL not surfaced in this pass. Findable via direct LinkedIn search "Kamil Rudnicki TimeCamp Wrocław."
- **Personal email:** not publicly listed; possibly findable via his personal site or `kamil@timecamp.com` (common pattern for founder-CEO at his stage of company).

## Bloat hypothesis

**This is a different-shape prospect from the rest of the lane.** TimeCamp is a 16-year-old SaaS with 4000+ customers. They're not LLM-native — they bolted AI onto an existing product. That changes the bloat pattern profile:

1. **Pattern #4 (No Batch API for Async Jobs) — VERY HIGH probability.** TIC's job is to "auto-categorize time from apps/calendar" — that's batch-shaped work by definition. Time entries from yesterday don't need a streaming response; they need to be correctly classified by morning. If TIC is hitting realtime endpoints per-transaction, EVERY time-entry classification call is paying 2x what it could pay. With 4000+ customers and presumably hundreds of thousands of categorization decisions per day, the per-call savings × volume is brutal in the right way.

2. **Pattern #5 (No Semantic Cache on Repeat Sub-Prompts) — HIGH probability.** Time-tracking AI categorization has MASSIVE prompt repeat structure across users. "User spent 47 min in Slack with this title and these calendar conflicts — what project?" The space of distinct prompts is enormous in theory but follows a heavy power-law in practice — common app+title combos appear millions of times across users. Embedding-based semantic cache (cosine > 0.95) likely has a hit rate above 40% on these workloads.

3. **Pattern #2 (Flagship-for-Easy) — MEDIUM probability.** Auto-categorizing "47 minutes in Slack" doesn't need GPT-5 or Sonnet 4.5. Haiku or Gemini Flash is plenty. If they shipped TIC on a flagship model "to be safe" without an eval gate, the per-call cost is 5-10x what it needs to be.

4. **Pattern #6 (Streaming on Aborted UIs) — LIKELY irrelevant.** Time-categorization isn't user-facing streaming UX; it's background batch. Skip in pitch.

**Lead with #4 (Batch API)** for the same reason as Vectoron — it's the most vendor-documented, single-config, undebatable savings. Combined with #5 (semantic cache) it's a credible 60-80% cost reduction story for the TIC workload specifically without touching the user-facing product.

## Day-0 cold email

**Channel:** TimeCamp has a contact form, sales email, and Kamil has a personal site. The cleanest cold open is via his personal site contact (founders read these) OR LinkedIn DM. Avoid generic sales@/support@ — those go to a queue.

**Subject:** `TimeCamp on OpenRouter — observation on TIC's infra shape`

**Body:**

```
Hi Kamil,

TimeCamp showed up on the OpenRouter rankings this week — congrats, TIC must be doing real volume to surface there.

Outside observation: TIC's job (auto-categorize tracked time from apps + calendar) is the textbook shape for two infra-side cost levers most realtime LLM stacks miss:

1. Batch API. Time entries from yesterday don't need a streaming response — they need to be correctly classified by morning. Anthropic + OpenAI both publish 50%-off pricing on Batch endpoints for exactly this workload. If TIC is hitting realtime endpoints per-transaction, that's a single-config flip on a meaningful share of the bill.

2. Semantic cache. "47 minutes in Slack with title X" is going to repeat across users at huge scale — common app+title combos hit a long-tail distribution. Embedding-based cache with cosine > 0.95 typically lands a 40%+ hit rate on this shape of workload, which translates to 40%+ off on the cached share.

I run a small Ruby/infra consultancy out of Mississippi doing token-bloat audits — peer engineer, not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation.

{{CAL_LINK}} if it's interesting.

Matt
```

## Day-4 nudge

**Subject:** `re: TimeCamp on OpenRouter — one more thought`

```
Kamil —

One more thing worth checking: TIC's model choice. Auto-categorizing time entries is a classification task — Haiku 4.5 or Gemini Flash will hit accuracy parity with Sonnet/GPT-5 for ~5-10x less per call. If TIC shipped on a flagship model to ensure quality and never revisited (the most common path), there's a 50-prompt eval set worth running against the cheaper models before the next contract renewal cycle.

Same offer — 20 min, one-page writeup, free. {{CAL_LINK}}

If now's not the time, no worries; I'll stop after this.

Matt
```

## Priority score

**7.5 / 10**

- **Token spend signal:** STRONG. 4000+ customers × per-transaction categorization × continuous tracking = high steady-state batch volume.
- **Bloat fit:** EXCELLENT. The TIC workload is textbook batch + semantic-cache + classification-routing.
- **Stage fit:** mature SaaS with margin pressure, AI feature recently bolted on. Established companies' CFOs care about COGS more than VC-funded startups. The pitch lands well at this stage.
- **Reply odds:** moderate-to-above-average. Founder-CEO of a mature company is a careful reader; the Polish founder culture is also typically direct-engineer-respectful. Cold-mail-skeptical but not hostile.
- **Conversion potential:** HIGH. If the audit lands and the numbers check out, the implementation budget at a mature SaaS is easier to justify than at a 3-person startup.
- **Channel access:** personal site exists, GitHub exists, LinkedIn findable. Personal email harder.
- **Geography:** Wrocław, Poland (UTC+1; Matt in MS is UTC-5/6). 6-7 hour offset. Schedule the call early morning Matt's time, afternoon Kamil's time.

Knock down 1-2 for: (a) larger company = longer sales cycle than a YC startup, (b) potential internal infra team owns AI ops; you may not be talking to the decisionmaker even if Kamil reads the email.

## Notes for Matt

- **Mature SaaS dynamics matter.** TimeCamp isn't a YC startup in scrappy-cost-cutting mode. They're a mature company with an established margin profile and existing infra contractors/staff. The pitch lands best if you frame the audit as "external second-opinion on the TIC infrastructure" rather than "you're missing the basics." The founder-CEO of a 16-year-old company has heard every cold pitch under the sun; differentiate on rigor and specificity.
- **LinkedIn might be the BEST surface here.** Polish founders skew LinkedIn-primary. Worth investing 5 minutes finding his profile + sending a substantive-line connect (per template 4) before email.
- **Don't pitch the consumer time-tracking app — pitch TIC.** The bloat is in the AI feature, not the legacy product. Be precise: "TIC's infra," "the auto-categorization workload," "the AI Time Tracker tier." Specificity = competence.
- **The Ultimate tier ($9.99/user) is where AI sits.** That tier's gross margin is the metric Kamil cares about. If you can show "shifting TIC to Batch + semantic cache improves Ultimate tier gross margin by X%," the audit becomes a board-deck-worthy finding, not just an engineering tweak. Frame outputs accordingly when the call lands.
- **Polish founder cultural note:** direct, pragmatic, low tolerance for fluff. Your normal Matt-voice (sparse, specific, technical) works perfectly. Avoid US-salesy "I'd love to chat" energy.
- **Risk:** they have a Polish dev team that already owns this stack. Audit findings may go through 2-3 hands before action. Time-to-close is longer than for a founder-decisionmaker startup. Discount the priority score by half for revenue-velocity if that matters for sequencing.
- **Wrocław time-zone honesty:** if the Cal link only shows US slots, that's a friction point. Make sure the audit call type has at least one EU-friendly slot block enabled before sending.
