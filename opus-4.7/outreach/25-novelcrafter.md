# 25. Novelcrafter
- **Domain:** novelcrafter.com
- **OpenRouter rank:** 25
- **Category:** AI-powered novel-writing toolbox — Codex worldbuilding wiki, scene beats, BYO-AI, 157k+ authors
- **Prospect status:** **Bootstrapped two-person → small team. Real revenue ($4/mo entry, 21-day free trial, 157k+ authors). BYO-key (so app doesn't pay token bills directly) — leverage is at the config-defaults / preset layer for the user base.**

## Founder / contact
- **CORRECTION TO LANE BRIEF:** The brief named "Bjorn Granitza" as founder. **Public sources (the Novelcrafter "About Us" page) identify "Leonie" as the founder and developer.** I could not surface any "Bjorn Granitza" connected to Novelcrafter — that name may be inaccurate or refer to a former/different person. Matt should treat the founder identity as **"Leonie (last name not publicly surfaced on novelcrafter.com/about-us)"** until verified.
  - About page: https://www.novelcrafter.com/about-us — lists "Leonie (Founder and Developer, Germany)" but no last name.
  - LinkedIn search for "Bjorn Granitza Novelcrafter" returned no matches.
  - Company LinkedIn: https://www.linkedin.com/company/novelcrafter
  - Company is "Novelcrafter UG (haftungsbeschränkt)" — German limited-liability form. Hamburg.
  - Founded 2023 as a one-person passion project, now a bootstrapped company.
- **Team (per About page):** Leonie (Founder/Dev, Germany), Kate (Education/Support, UK), Kevin (Marketing, Germany), Vivien (Dev, Germany), Marius (Dev, Germany), Linsey (Customer Support, USA), Kat (Community Support, Germany), Nikola (Editor, USA), plus two office dogs (Cassie and Dylan, UK).
- **Public email:** not on the homepage or About page. Routes are (a) help-center contact form at https://www.novelcrafter.com/help, (b) Discord community, (c) the German company-registry filing (likely lists a director email but adds friction).
- **Best initial channel:** **LinkedIn DM to the company page or to Leonie directly once last-name is confirmed.** European founders skew LinkedIn-primary per the outreach-templates guidance.

## Bloat hypothesis
**Pattern 2 (Flagship-for-Easy) at the user-config layer + Pattern 10 (Verbose System Prompts) on the Codex-aware preset.**

Novelcrafter is BYO-key (OpenAI / Anthropic / Gemini / Mistral / Llama / OpenRouter 300+ / LM Studio / Ollama) — the platform itself doesn't pay token bills. The leverage is **what models the default presets recommend, and how verbose the Codex-context injection system prompt is per call.**

Specific signals:
1. **157k+ authors** writing novels = high per-user token volume. Even small per-call savings compound across that user base.
2. Worldbuilding wiki (Codex) + scene beats + planning tools = **rich context that gets injected as system prompt on every generation call.** Pattern 1 + Pattern 10 candidate — the Codex chunks are likely shipped uncached, and probably stuffed-not-retrieved (Pattern 3).
3. AI Workshop / brainstorming / writing / review = **distinct task classes that should NOT all route to the same flagship model.** Brainstorm and outline-review route fine to Haiku/Flash; flagship should reserve for prose-quality scene generation.
4. The README/marketing mentions BYO-AI but does not mention prompt caching, retrieval over the Codex, or per-task model tiering — none of these appear to be opinionated defaults.

**Pitch shape: "publish a config-defaults preset pack that saves your 157k authors 40-60% on their OpenAI/Anthropic bills" — a marketing line competing AI-writing tools cannot match.** Bootstrapped Hamburg company will absolutely care about a feature that ALL their authors get for free, especially when those authors are price-sensitive (Novelcrafter starts at $4/mo for a reason).

## Day-0 cold email (routed as LinkedIn DM since email is not public)

**LinkedIn connection request (300-char limit):**

```
Hi Leonie — saw Novelcrafter on the OpenRouter rankings this week. Ruby dev / small consultancy doing token-bloat audits. No pitch in the connect — wanted to follow Novelcrafter's path; you've built something rare (bootstrapped, 157k authors, BYO-AI).
```

**Follow-up DM (1-2 days after accept):**

```
Thanks for connecting, Leonie.

Outside hypothesis on Novelcrafter from the OpenRouter signal: your authors are running flagship models (Sonnet, Opus, GPT-5) across brainstorm + outline + scene-write + review steps, when brainstorm/outline/review would route fine to Haiku 4.5 or Gemini Flash. Add an uncached Codex-context system prompt repeated each turn, and the per-author monthly token bill is probably 2-4x what it needs to be.

The pitch isn't "Novelcrafter pays for an audit." It's "Novelcrafter publishes a config-defaults preset pack that saves all 157k authors 40-60% on their provider bill." A feature your competitors can't match.

I run a small consultancy doing these audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first against Novelcrafter's BYO-key surface, you get a one-page writeup. Free, no obligation.

[Cal.com link]

Matt
```

## Priority score
**7 / 10.** Bootstrapped + 157k users + price-sensitive customer base + BYO-key architecture = the "save your USERS money" pitch lands clean. Conversion path is less obvious than the gpt.space unit-economics pitch (since Novelcrafter doesn't directly pay token bills) but the marketing-feature angle is strong. **Leonie is the bottleneck** — solo-founder-becoming-CEO of a 10-person bootstrapped company means her attention is the scarce resource, not budget.

## Notes for Matt
- **Channel order:** LinkedIn DM (connection request + follow-up DM pattern from Template 4 in `outreach-templates.md`). German founder = LinkedIn-primary per playbook. Avoid help-center contact form (routes to support, not founder).
- **Lane brief named "Bjorn Granitza" — this could not be verified.** Matt should confirm Leonie's last name via the company LinkedIn page (https://www.linkedin.com/company/novelcrafter) and the Novelcrafter UG German company registry filing before sending. The DM I drafted uses "Leonie" as first-name-only, which is honest given current info.
- **Lean into the "save your AUTHORS money" framing, not "save Novelcrafter money."** Novelcrafter doesn't pay token bills; their users do. The marketing feature angle is the whole pitch.
- **Mention the 21-day free trial / $4 entry / bootstrapped status** in the DM — it signals Matt knows their economics, not just their press releases.
- **Contact gap:** Leonie's last name + direct email/LinkedIn URL — both publicly unverified. Worth 5 minutes via the Novelcrafter company LinkedIn page + German company registry before sending.
- **Side opportunity:** Kevin (Marketing, Germany) is probably the right routing if Leonie's queue is closed — a marketing person will receive "feature your competitors can't match" framing favorably.
