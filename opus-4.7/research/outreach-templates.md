# Outreach Template Pack — OpenRouter Leaderboard Targets

**Sender voice:** Matt — Ruby dev (~30 years), solo consultancy out of Mississippi, peer engineer not a salesperson. No "I noticed you're growing fast." No "10x your efficiency." Concrete, specific, short.

**Tokens used across all templates:**
- `{{APP_NAME}}` — the app's product name as it appears on OpenRouter
- `{{FOUNDER_FIRST_NAME}}` — founder's first name (preferred) or "team" if multi-founder ambiguous
- `{{BLOAT_HYPOTHESIS}}` — ONE sentence specific to them, drawn from `bloat-playbook.md`. Example: "you're running Sonnet 4.5 on the classification step that probably routes to Haiku" or "your system prompt looks long enough that prompt caching would cut input cost ~70%"
- `{{ESTIMATED_SAVINGS}}` — % range, only used where it's defensible (e.g. "50%" for Batch API since that's a vendor-published number). Avoid dollar figures.
- `{{CAL_LINK}}` — Cal.com or Calendly link, used once per template max

---

## Template 1 — Cold Email, Day 0

**Subject options (pick one based on what's specific):**
- `{{APP_NAME}} on OpenRouter — quick observation`
- `Saw {{APP_NAME}} on the OpenRouter rankings`
- `OpenRouter rankings — {{APP_NAME}} token mix question`

**Body:**

```
Hi {{FOUNDER_FIRST_NAME}},

{{APP_NAME}} showed up on the OpenRouter rankings this week — congrats, that's a real spend signal.

Hypothesis from the outside: {{BLOAT_HYPOTHESIS}}. Could be wrong, but it's the pattern I see most on apps in your category.

I run a small consultancy doing token-bloat audits — Ruby/infra background, peer-to-peer not salesy. Offer: 20 minutes on Zoom, I show you the 2-3 patterns I'd dig into first, you get a one-page writeup. Free, no obligation. If there's nothing there, we shake hands and move on.

{{CAL_LINK}} if it's interesting.

Matt
```

**WHY THIS WORKS:**
- Public verifiable observation (OpenRouter rankings) bypasses spam filter pattern-matching AND signals "I did homework" without sycophancy.
- "Could be wrong" inoculates against the founder's natural defense reaction; engineers respect uncertainty more than confidence.

---

## Template 2 — Email Nudge, Day 4

**Subject:** `re: {{APP_NAME}} on OpenRouter — one more thought`

**Body:**

```
{{FOUNDER_FIRST_NAME}} —

Quick nudge on the note from Monday. One more thing I'd check: {{BLOAT_HYPOTHESIS_2}}.

Same offer — 20 min, one-page writeup, free. {{CAL_LINK}}

If now's not the time, no worries; I'll stop after this.

Matt
```

**WHY THIS WORKS:**
- Reply-thread subject ("re:") boosts open rate on the same recipient and signals continuity, not a fresh cold blast.
- "I'll stop after this" pre-commits to the breakup; founders feel less pressure and are MORE likely to reply because they know this isn't a 12-touch sequence.

---

## Template 3 — Breakup Email, Day 10

**Subject:** `closing the loop on {{APP_NAME}}`

**Body:**

```
{{FOUNDER_FIRST_NAME}} —

Closing the loop on the audit offer. Going quiet on my end — assume the timing's off.

If token spend ever does become a thing worth a second look, the door's open: {{CAL_LINK}}.

Good luck with {{APP_NAME}}.

Matt
```

**WHY THIS WORKS:**
- "Closing the loop" is a recognized polite-exit pattern; founders know what it is and often reply BECAUSE the pressure is off.
- Leaves the link without re-asking — passive offer means the response rate on this email is often higher than the Day-0 because the recipient feels in control.

---

## Template 4 — LinkedIn DM (with connection request)

**Connection request note (300 char limit):**

```
Hi {{FOUNDER_FIRST_NAME}} — saw {{APP_NAME}} on the OpenRouter rankings. Ruby dev / small consultancy doing token-bloat audits. No pitch in the connect, just wanted to follow your work.
```

**Follow-up DM (send 1-2 days after they accept):**

```
Thanks for connecting, {{FOUNDER_FIRST_NAME}}.

Outside hypothesis on {{APP_NAME}}: {{BLOAT_HYPOTHESIS}}. Could be off — happy to be wrong.

Offering free 20-min audits to apps on the OpenRouter board. One page of findings, no follow-up unless you want it. {{CAL_LINK}} if it's interesting.

Matt
```

**WHY THIS WORKS:**
- Connection request with a substantive non-pitch line gets accepted at a much higher rate than blank or pitchy ones.
- Splitting the connect note from the pitch lets the founder accept based on relevance, then encounter the offer in a separate frame — feels less ambush-y.

---

## POSITIONING NOTES

### Subject line patterns ranked by intuitive open rate (highest → lowest)

1. **`{{APP_NAME}} on OpenRouter — quick observation`** — names them, names the public source, signals brevity. Best.
2. **`Saw {{APP_NAME}} on the OpenRouter rankings`** — same content, more casual. Good for second-tier founders who like informal energy.
3. **`re: {{APP_NAME}} on OpenRouter — one more thought`** — only for nudges; the `re:` prefix on a fresh cold email is dishonest and burns trust.
4. **`OpenRouter rankings — {{APP_NAME}} token mix question`** — question framing, slight curiosity bump, but more salesy.
5. **`closing the loop on {{APP_NAME}}`** — only for breakup. Don't lead with it.

Avoid: anything with `[free]`, `[important]`, emojis in subject, ALL CAPS, "?" at end of cold email (looks like spam survey).

### Tells that get this filtered as spam (avoid these phrases)

- "I noticed you're growing fast" / "saw your recent growth"
- "I help companies like yours..."
- "Just wanted to reach out..."
- "Hope this finds you well"
- "Quick question" (every salesperson opens with this — auto-classified)
- "Circling back" / "touching base" / "synergies"
- Anything with "10x" / "scale" / "unlock"
- "Are you the right person to talk to about..."
- Any subject line starting with "Question about..." or "Quick question..."
- Em-dashes are fine in body but avoid in subject (some filters flag)
- Avoid more than 1 link in the body; 2+ links trips Gmail's promotions tab.

### Email vs LinkedIn vs Twitter DM — when to use which

- **Email FIRST when:** founder email is on the company about page, in a public GitHub commit history (`git log --format='%ae' | sort -u`), in a YC profile, or in their own blog's author bio. Email has the highest reply rate when the address is verified.
- **LinkedIn SECOND when:** email unfindable OR Day-0 email got no reply by Day 4 (use LinkedIn as a different-surface nudge, not a duplicate ask). Also use LinkedIn first if the founder is European — EU founders skew LinkedIn-primary.
- **Twitter DM LAST RESORT when:** they're an indie / one-person team / no company website / DMs visibly open in bio. Twitter DM is high-noise; reserve for prospects with no other channel. Keep it under 280 chars and treat it like a connection ping, not a pitch.
- **Apps that typically lack public founder emails:** anything wrapping consumer apps (AI girlfriend/companion stuff, mobile-only utilities, anonymous-account-friendly tools). For these, LinkedIn is primary.
- **Apps that typically DO have public emails:** B2B SaaS, dev tools, infra, anything with a "contact sales" page (find the founder's personal email separately — generic "hello@" is the wrong target).

### Calendly / Cal.com link placement guidance

- **One link per message, end of body, on its own line.** Multiple links trips spam filters and dilutes the CTA.
- **Cal.com > Calendly** for technical audience optics; founders who care about open source notice.
- **Link should go to a SPECIFIC 20-min event type** ("Token Audit / 20 min"), not your generic "Meet Matt" page. Specificity makes the ask concrete and lowers commitment friction.
- **Don't link in the breakup email's body — link in the sign-off line instead.** Reduces "this is still a sales pitch" energy.
- **No tracking parameters in the URL.** UTMs visible to the recipient look mercenary; if you need attribution, use Cal.com's built-in source field or a per-template event slug (`/matt/audit-cold-email`, `/matt/audit-linkedin`).
- **NEVER include a "book a time" button image.** Plain-text link only. HTML buttons in cold emails are an instant spam tell.

### Reply-handling notes (not templates, but related)

- If they reply with "send the audit", DON'T — the value is in the call. Reply: "Easier to walk you through it live, it's 20 min and you get the writeup at the end. {{CAL_LINK}}."
- If they reply with "what would you charge if we wanted you to actually fix it" — that's the conversion. Don't quote a number; book the call, scope live.
- If they reply "we already do all of this" — ask which 2-3 patterns from the bloat playbook they've already addressed. Either you learn (good), or they're bluffing (also good — you have leverage).
