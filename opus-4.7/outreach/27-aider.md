# 27. Aider
- **Domain:** aider.chat
- **OpenRouter rank:** 27
- **Category:** Open-source AI pair programming (terminal CLI, BYOK)
- **Prospect status:** Researched, founder confirmed, alternative-pitch posture required

## Founder / contact

- **Paul Gauthier** — Creator and maintainer. Started Aider April 2023. ~30 years systems programming experience. Co-founded Inktomi in 1996 (early search engine, powered HotBot/Yahoo, CTO until 2010). BSC Dalhousie '94, grad work at Univ. of Washington.
- **GitHub:** https://github.com/paul-gauthier (project lives at github.com/Aider-AI/aider, ~40k+ stars)
- **LinkedIn:** not surfaced cleanly in this pass; he has a low LinkedIn footprint (typical of senior systems engineers).
- **Email:** not publicly listed on aider.chat. Check git log on the repo (`git log --format='%ae' | sort -u` — peer norm in OSS) — likely the cleanest channel.
- **Twitter/X:** Aider has an account; Paul's personal handle not surfaced this pass.

## Bloat hypothesis

**The key shift for Aider:** this is NOT an app paying for tokens. Aider is BYOK — every user brings their own Anthropic/OpenAI/OpenRouter key. Paul has no API bill to optimize. So the "your token bill" pitch doesn't land.

What DOES land:

1. **Prompt caching is OPT-IN, not default (Pattern #1).** Confirmed at https://aider.chat/docs/usage/caching.html: "You must explicitly enable it by running aider with the `--cache-prompts` flag." For a code-pair tool where the system prompt + repo map + read-only files are byte-identical across many turns, this is the single biggest user-cost lever — and most users don't know to set the flag.
2. **`--no-stream` is also opt-in for cost visibility.** Cache stats and accurate cost reporting require disabling streaming. Most users stream by default.
3. **Repo-map prompt size scales with codebase.** Aider auto-builds a map of the codebase; on large repos this is many thousands of tokens per turn. No obvious mechanism for users to see what they're sending or trim it interactively.

**Pitch posture for Aider is NOT "let me audit your bill" — it's "let me help your USERS save money."** Paul is an OSS maintainer with a community-first ethos; the credible offer is content collaboration, not a paid audit.

## Day-0 cold email

**Channel:** GitHub-discovered email is the cleanest cold open for an OSS maintainer. Twitter/X mention as fallback. If neither, open a GitHub Discussion (transparent, low-pressure).

**Subject:** `Aider + prompt caching — draft for your blog?`

**Body:**

```
Hi Paul,

Aider showed up on the OpenRouter rankings this week — congrats on hitting that scale of BYOK usage.

I'm not coming with the usual "audit your token bill" pitch because the bill is on your users, not you. But I noticed --cache-prompts and --no-stream are both opt-in, and a lot of users don't know to set them. On a Sonnet-driven repo-map workflow, prompt caching can cut input cost ~70%; most Aider users are leaving that on the table by default.

Offer: I'll draft a "How to cut your Aider bill by X%" blog post — full numbers from a real eval run on a representative repo, configs that work, write-up styled to fit the aider.chat docs voice. Yours to publish under your name, your URL, no attribution needed for me. If it's useful, great. If not, you keep the draft, I move on.

I run a small Ruby/infra consultancy out of Mississippi (30 years coding, last 2 deep in LLM-cost work). Peer engineer, not a salesperson — happy to chat in a GitHub Discussion if email feels weird for first contact.

Matt
```

**Why this is different from the standard template:** Paul doesn't pay an API bill, so the bloat hypothesis is about user cost, not vendor cost. The offer is content collaboration that helps his community — content he'd value, low cost to him to accept. The Cal link / 20-min call frame is wrong for OSS maintainer cold outreach; substitute a tangible artifact (draft blog post).

## Day-4 nudge

**Subject:** `re: Aider + prompt caching — one more thought`

```
Paul —

Quick nudge on the blog draft offer. One more angle if you're considering it: repo-map size in the system prompt scales with codebase. For users on monorepos the cost adds up fast — most don't notice because they only see the per-message cost, not the cached-prefix savings they're missing.

Same offer — I write the draft, you decide if it ships. No follow-up if not. If GitHub Discussion is easier than email, that works too.

Matt
```

## Priority score

**5.5 / 10**

- **Token spend signal:** WRONG ANGLE. Aider doesn't pay for tokens — users do. OpenRouter ranking reflects aggregated user spend, not Aider's.
- **Conversion potential:** LOW for direct paid work. Paul is an OSS solo maintainer; he's not buying an audit. There's no "engineering team" to pitch.
- **Indirect value:** MEDIUM-HIGH. A guest blog post on aider.chat with Matt's byline (~40k stars, active community) is a marketing asset. If it lands well, it's funnel-building, not deal-closing.
- **Reply odds:** moderate — OSS maintainers get a lot of cold mail; the content-collab framing helps but he may just say "thanks, send a PR to the docs."
- **Risk:** he writes the blog himself in 2 hours and ships it without Matt. That's a real possibility — once you tell him the angle, the work is mostly done in his head. Mitigate by making the offer about the EVAL DATA (which takes 4-6 hours and a small budget for real model runs) not just the rec.

Knock down 2-3 from the obvious "rank 27, good signal" because of the BYOK structural mismatch with the audit business model. This is a relationship/marketing play, not a sales play.

## Notes for Matt

- **Skip the Cal link.** OSS maintainers don't book sales calls. The artifact (draft blog post) is the close.
- **Real workflow if he says yes:** spin up Aider against a representative open-source repo (e.g. a Rails project or a Ruby gem so you're in your wheelhouse), run two configs — default and `--cache-prompts --no-stream` — capture cost deltas across 50-100 representative tasks. Use Promptfoo or just a simple eval harness. That's the data the post needs.
- **Submit as a PR to aider.chat docs first?** Could be a faster first contact than email — open a draft PR adding a "Cost Optimization Cookbook" page with eval data, ping Paul on the PR. Demonstrates competence and respects OSS norms. Lower upfront commitment from him to engage.
- **Don't pitch a follow-up audit at the end of the blog work.** Let it sit. If the post lands in his community, inbound from Aider users will follow naturally — and those users ARE potential audit prospects with their own teams.
- **Cross-link possibility:** Aider users tend to be in larger eng orgs (they bring API keys, which means corporate accounts). The blog asset is a top-of-funnel piece for the actual audit business; Aider itself is not the customer.
- **Risk: low-priority for time-allocation.** If overnight queue is full, this one can wait — it's marketing-shaped, not deal-shaped. Higher-priority ranks above (Vellum, Gobii, Vectoron, TimeCamp) deserve the focused attention first.
