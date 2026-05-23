# 21. LibreChat
- **Domain:** librechat.ai
- **OpenRouter rank:** 21
- **Category:** Open-source self-hosted ChatGPT clone (multi-model, MCP, agents, multi-user auth)
- **Prospect status:** Open-source / donation-funded — direct revenue path uncertain. **Pursue at the deployment / preset / config-template level OR target enterprise/self-host operators referencing them.** Founder is approachable; the prize is influence over thousands of self-hosted deployments and any future enterprise offering.

## Founder / contact
- **Danny Avila** (technical founder, creator). Based in Queens, NY. Hack Reactor alum. 30K+ GitHub stars.
- LinkedIn: https://www.linkedin.com/in/danny-avila/
- Authors page on librechat.ai: https://www.librechat.ai/authors/danny
- GitHub: https://github.com/danny-avila
- X / Twitter: https://x.com/lgtm_hbu
- **Public email:** not publicly listed on librechat.ai or his LinkedIn. GitHub commit history may expose it (`git log --format='%ae' | sort -u` on the LibreChat repo) — Matt should verify before sending.
- LibreChat company page on LinkedIn: https://www.linkedin.com/company/librechat
- Recent context: LibreChat moved to ClickHouse for analytics ("ClickHouse welcomes LibreChat" — Nov 2025-era post). They're scaling observability, which means cost visibility is on his mind.

## Bloat hypothesis
**Pattern 7 (No Eval Gate on Model Swap) + Pattern 1 (Uncached System Prompt) at the preset/config level.** LibreChat is BYO-key — the project itself doesn't pay token bills — but the **default presets, the model dropdown ordering, and the agent system prompts shipped in-repo are what thousands of self-hosters actually run.** The README highlights "token spend tracking" as a feature, which means operators are watching cost rise but the project ships:

1. No `cache_control` defaults on the agent system prompts (Anthropic prompt caching cuts repeated-prefix cost ~90%).
2. No model-routing layer — every agent task hits whatever flagship the operator picked in the dropdown, including the cheap classification/format steps that would route to Haiku 4.5 or Gemini Flash.
3. No `evals/` folder visible in the repo to gate a model swap, so self-hosters default to flagship "to be safe."

The leverage isn't LibreChat-the-project — it's the 50-150 enterprise / heavy self-host deployments where LibreChat is the chat tool, OpenRouter is the proxy, and the operator is bleeding $5-50k/mo on token spend that a default-config audit would cut 40-60%.

## Day-0 cold email

**Subject:** `LibreChat on OpenRouter — quick observation`

**Body (assumes Matt finds a usable email; if not, route as LinkedIn DM):**

```
Hi Danny,

LibreChat showed up on the OpenRouter rankings this week — congrats, that's a real spend signal across the self-host fleet.

Hypothesis from the outside: the default agent presets ship without cache_control markers on the system prompt, and the model dropdown has no routing layer for cheap-vs-flagship task splits — so every heavy self-host operator running LibreChat-on-OpenRouter is paying full input rate on prefixes Anthropic would cache at 10%, and Sonnet rates on classifier/format calls that route fine to Haiku. Could be wrong, but it's the pattern I see most on multi-model chat platforms.

Not asking you to take it on as project work — the leverage is in publishing a "config defaults that save 40-60%" preset pack for the enterprise / heavy-user crowd. I run a small consultancy doing token-bloat audits, Ruby/infra background, peer-to-peer not salesy.

Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first against LibreChat's repo + defaults, you get a one-page writeup you can publish or ignore. Free, no obligation.

[Cal.com link]

Matt
```

## Priority score
**6 / 10.** Open-source/donation-funded = no direct paid engagement, but Danny is visible, approachable, and has a real audience of self-host operators who DO pay token bills. The audit work would land as published config-defaults / blog content — slow-burn lead-gen into the enterprise self-host crowd rather than a direct contract. **High-leverage / low-conversion.** Skip if Matt's queue is tight; pursue if he wants reputational positioning in the open-source LLM-chat ecosystem.

## Notes for Matt
- **Channel order:** Email if a public address surfaces from GitHub commit history. Otherwise LinkedIn DM (he's responsive there based on activity volume). Avoid X DM — he posts publicly but his @ is muted-bait-flavor.
- **Don't pitch LibreChat-the-project paying for an audit** — donations-funded. Pitch publishing a config pack, or position him as a referrer into the heavy-self-host operators (the real wallets).
- **He'll respect uncertainty.** Hack Reactor + builds-in-public + 352 contributors — he's seen every pitch. The "could be wrong" inoculator from the playbook is load-bearing here.
- **ClickHouse-LibreChat partnership is a fresh news hook** — could open with "saw the ClickHouse post, cost visibility is clearly on the roadmap" but only if Matt's confident the timing is recent; risk of stale-news embarrassment.
- **Contact gap:** no verified email. Worth ~5 minutes of `gh api` against the LibreChat repo to pull commit author addresses before sending.
