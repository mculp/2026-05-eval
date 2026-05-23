# 26. Gobii
- **Domain:** gobii.ai
- **OpenRouter rank:** 26
- **Category:** Agentic browser automation / virtual AI coworkers (lead-gen, recruiting, compliance)
- **Prospect status:** Researched, founder confirmed, ready to send

## Founder / contact

- **Andrew I. Christianson** — Founder & CTO. Also created RA.Aid (open-source coding agent). Former NSA contractor, long-time Apache NiFi contributor.
- **LinkedIn:** https://www.linkedin.com/in/andrew-i-christianson-3578629/
- **GitHub:** https://github.com/ai-christianson
- **X:** https://x.com/ai_christianson
- **Backed by:** Open Core Ventures (Catalyst program alum)
- **Other team:** Will Bonde (Growth & Eng), Matt Greathouse (Eng) — 3-person team per the team page.
- **Personal email:** not publicly listed. LinkedIn DM is the cleanest first surface; Twitter DMs reportedly open.

## Bloat hypothesis

**Gobii is already cost-conscious** — their 2025 blog "How to Get 20-60x More Work Per Dollar with Gobii and DeepSeek V3.2" explicitly pitches DeepSeek as the default for high-volume tasks with escalation to GPT/Claude for premium reasoning. That kills the "Flagship-for-Easy" angle (Pattern #2) — they already route.

The real bloat is downstream of that:

1. **Tool-Use Without Result Caching (Pattern #8).** Agents browse the web 24/7, fill forms, re-scrape sites. The same competitor pages, the same LinkedIn profiles, the same form schemas get re-loaded into context across users and sessions. Hash (URL, args) → result with a TTL would cut 20-50% on agentic context bloat. Their pricing ($0.10 per task overage on Pro, $0.04 on Scale) tells me they're paying real money per task — caching pays directly.
2. **DeepSeek prompt caching is documented but easy to miss.** DeepSeek charges $0.07/M for cache hits vs $0.27/M base — a 4x discount. If Gobii's worker system prompts (browser-tool descriptions, persona, output-format rules) are static across thousands of tasks/day and they're not setting cache markers, that's leaving meaningful money on the table even at DeepSeek prices.
3. **Long-running browse sessions = long context.** "Per-agent always-on" workers mean conversation history grows. Without summary-snapshot rollups, every action re-pays for the full session history. This is the biggest variable cost lever on 24/7 agents.

The angle to lead with is **#1 (tool-result caching)** because it's the one most legible to an engineer-founder and most clearly under-discussed in their public blog.

## Day-0 cold email

**Channel:** LinkedIn DM (no public personal email). Send connection request first with the substantive line, then follow up after acceptance.

**Connection request (300-char limit):**

```
Hi Andrew — saw Gobii on the OpenRouter rankings. Loved the DeepSeek V3.2 cost post. Ruby dev / small consultancy doing token-bloat audits. No pitch in the connect — wanted to follow your work and RA.Aid.
```

**Follow-up DM (1-2 days after acceptance):**

```
Thanks for connecting, Andrew.

Read your "20-60x more work per dollar" piece — you're already past the easy stuff (smart routing, DeepSeek defaults). The next layer I'd dig into on a 24/7-browse product: tool-result caching. Same competitor sites, same LinkedIn profiles, same form schemas get re-scraped across users and sessions and pay for context tokens every time. Hash (url, args) → result with a TTL is often 20-50% off agentic context bloat. Also worth a look: DeepSeek prompt-cache markers on your worker system prompts ($0.07/M cache vs $0.27/M base, ~4x).

Could be wrong on the specifics — but it's the pattern I see most on agentic products at your shape.

Offering free 20-min audits to apps on the OpenRouter board. One page of findings, no follow-up unless you want it. {{CAL_LINK}} if it's interesting.

Matt
```

**Subject for the email fallback (if a personal email surfaces later):** `Gobii on OpenRouter — quick observation on tool-result caching`

## Priority score

**8.5 / 10**

- **Token spend signal:** STRONG. 24/7 browse agents with long-running sessions + on the OpenRouter top 30 = real volume.
- **Already cost-conscious:** they ROUTE TO DEEPSEEK BY DEFAULT — this is rare and signals the founder thinks about unit economics. Cuts both ways: the easy wins are gone, but they'll *understand the pitch* and have appetite for the deeper layers.
- **Stage fit:** OCV-backed, 3-person team, clear product. They're past seed-noise and into scale-economics. Right window.
- **Channel access:** LinkedIn confirmed, Twitter open. Both surfaces good.
- **Reply odds:** above average — Andrew is a builder (RA.Aid open-source author) and engineer-founders reply to engineering observations.

Knock down 1.5 because no public personal email and the "easy" angles (model routing) are already addressed — the pitch has to land on the second-order patterns (caching, summarization), which is a higher-bar conversation.

## Notes for Matt

- **Don't pitch model routing.** Their public blog is literally a model-routing manifesto. Pitching that = "you didn't read the homework." Lead with tool-result caching and DeepSeek prompt-cache markers.
- **Their pricing has real per-task overages ($0.10/Pro, $0.04/Scale)** — this means you can sketch ROI math credibly. A customer doing 10k tasks/mo at Scale ($250 base + $0 included + overage) is paying real money per task; cutting 30% per-task cost is direct.
- **RA.Aid is open-source and his personal project.** Mention it in the cold approach — shows you actually looked. Don't sound creepy about it; "loved your RA.Aid post on X" is plenty.
- **Open Core Ventures** — they back open-source-first commercialization. Gobii's free tier is genuinely self-hostable and MIT-licensed. The Pro/Scale tiers are managed-service. Audit pitch fits perfectly because you're saying "I won't sell you software, I'll show you what to fix" — exactly the OCV ethos.
- **Risk:** he may have already audited this stack himself. Pre-empt by saying "could be wrong" in the opener; the 20-min ask is cheap enough that even if he's done the work, the call is a peer-to-peer comparison-of-notes rather than a sales call.
