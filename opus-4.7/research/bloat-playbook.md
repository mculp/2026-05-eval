# Inference-Bloat Playbook

**Audience:** Matt, using this to grade OpenRouter-leaderboard apps from public signals BEFORE talking to the founder.

**Use:** scan the candidate's docs/changelog/jobs/OpenRouter rankings page → match against 2-3 patterns below → pick the strongest hypothesis as the `{{BLOAT_HYPOTHESIS}}` token in outreach.

**Source notes:** Anthropic Batch API is documented at 50% off list. Anthropic prompt caching is documented at 10% of base input price for cache reads. OpenAI Batch API is documented at 50% off. Every other "estimated savings" number below is a directional rule-of-thumb from public engineering write-ups (Notion, Sourcegraph, Vercel, Anthropic cookbook), not a vendor quote — treat as hypothesis bait, not proof.

---

## 1. Uncached System Prompt

**What it looks like:** App sends the same multi-thousand-token system prompt (instructions, persona, formatting rules, few-shot examples) on every API call with no `cache_control` markers (Anthropic) or `prompt_caching` enabled (OpenAI). Every turn re-bills the full prompt at base input rate.

**External signals:**
- OpenRouter rankings page shows them sending >1M tokens/day to Sonnet/Opus/GPT family and they shipped before mid-2025 → likely predates their team's caching audit.
- Public system prompts leaked or doc'd (Cursor, v0, Perplexity — these are reference points; if your prospect publishes their system prompt in a blog post and it's >500 tokens, that's the signal).
- Docs mention "personality" / "house style" / "tone guidelines" — implies long static preamble.
- Changelog/blog doesn't mention "prompt caching", "cache_control", or "implicit caching" anywhere.
- LangChain / LlamaIndex / Vercel AI SDK in their stack with no caching wrapper visible.

**Estimated savings:** 50-90% of input cost on the repeated prefix. Anthropic prices cache reads at 10% of base input; OpenAI cached_input is 50% of base. Math depends on prefix ratio to fresh tokens — apps with long prompts and short user turns get the biggest cut.

**Fix sketch:** Add `cache_control: {type: "ephemeral"}` to the last block of the static prefix (Anthropic). For OpenAI, ensure the static prefix is byte-identical across calls so implicit caching kicks in.

---

## 2. Flagship-for-Easy

**What it looks like:** Single model selection — usually Claude Sonnet 4.5 / GPT-5 / Opus — used for every task in the app regardless of difficulty. Classification, formatting, rerank, summarization, and hard reasoning all hit the same flagship endpoint.

**External signals:**
- OpenRouter app page shows 95%+ of volume going to ONE expensive model (Sonnet 4.5, Opus 4.1, GPT-5, Gemini 2.5 Pro).
- No Haiku/Mini/Flash in the model mix.
- Pricing page doesn't tier features by complexity (everything is "AI-powered" with no internal model distinction).
- Job postings mention "AI cost optimization" or "LLM ops" → they feel the pain.
- Engineering blog posts about "we use Claude Sonnet for everything" — common in 2024-era startups that never revisited.

**Estimated savings:** Often 60-85% on the routable share. Haiku 4.5 is ~$1/M input vs Sonnet 4.5 ~$3/M; Gemini Flash is ~$0.30/M vs Pro ~$1.25/M. The win is in WHAT FRACTION of calls can be routed down, not the per-call delta.

**Fix sketch:** Build a 50-prompt eval set per task class, run Haiku/Mini against it, route the tasks where small-model accuracy matches flagship. Keep flagship for the long tail.

---

## 3. Full-Context Stuffing

**What it looks like:** Instead of retrieval, the app loads the entire knowledge base (docs, codebase, conversation history, user's notes) into the context window on every turn. "200k context" used as a feature, not a budget.

**External signals:**
- Marketing language: "We give the model your entire {codebase, document set, conversation history}".
- App is in: codegen / customer support / "AI search over your docs" / personal knowledge mgmt — and the docs brag about long-context use.
- Average user-facing latency >10s on follow-up turns (long-context first-token latency is the tell).
- OpenRouter rankings: high token counts per request, low request count → few but huge calls.
- No mention of "embeddings", "vector search", "RAG", "pgvector", "Pinecone", "Turbopuffer", "LanceDB" anywhere in their stack docs.

**Estimated savings:** 80-95% of input tokens on retrieval-amenable workloads. RAG with a tight retriever sends 5-20k tokens per turn vs 200k stuffed.

**Fix sketch:** Add an embedding index (text-embedding-3-small is fine to start), retrieve top-K chunks, only stuff what's relevant. Keep stuffing only for tasks that genuinely need global context (e.g. cross-file refactor).

---

## 4. No Batch API for Async Jobs

**What it looks like:** Background jobs — overnight digests, bulk classification, re-indexing, eval runs, summary regeneration — go through the same realtime endpoint as user-facing chat. App pays full price for work that has no human waiting on it.

**External signals:**
- Product has a "daily digest" / "weekly report" / "overnight enrichment" / "background processing" feature.
- Changelog mentions "we now generate X overnight" or "we re-summarize Y nightly".
- Job postings mention "data pipeline" + "LLM" — they have batch workloads.
- OpenRouter usage curve has a 24h cycle (huge spikes at fixed times) → batch-shaped traffic going through realtime.
- No mention of `/v1/messages/batches` (Anthropic), `/v1/batches` (OpenAI), or "OpenRouter batch" anywhere.

**Estimated savings:** 50% off list price for everything routed through Batch (documented vendor discount). Plus better rate-limit headroom.

**Fix sketch:** Move anything that can tolerate a 24h SLA to the Batch endpoint. Queue submission is one HTTP call; results poll back when ready.

---

## 5. No Semantic Cache on Repeat Sub-Prompts

**What it looks like:** Same or near-identical user prompts arrive across users — "summarize this PR template", "explain this error", "what does this regex do" — and the app calls the model fresh each time. No semantic cache layer.

**External signals:**
- Product is in: code assistants, customer support deflection, search-with-LLM, dev tools — where prompts cluster around a small set of intents.
- Public Discord / community shows users asking variations of the same question repeatedly.
- Their analytics page (if public) shows "top questions" — a long-tail signal.
- No mention of Redis + embeddings, GPTCache, Helicone Cache, Langfuse Cache, Portkey semantic cache in their stack.
- Open-source repo: search for "cache" returns only HTTP cache, no LLM cache.

**Estimated savings:** 30-70% on the cacheable share of traffic. Heavily workload-dependent — cache hit rate above 30% is where it becomes worth the complexity.

**Fix sketch:** Embed every incoming prompt, check vector DB for cosine sim > 0.95 against past prompts, return the cached completion if hit. Invalidate on a TTL or on context-shift signals.

---

## 6. Streaming on Aborted UIs

**What it looks like:** App streams every response token-by-token, but the UX context doesn't require it — users frequently navigate away, hit "stop", or the response is being post-processed before display. Tokens billed regardless of whether the user saw them.

**External signals:**
- UX is: form-fill / structured-output / "AI generates this report, then we display it" / search-result-reranking — non-conversational surfaces that stream anyway.
- Their docs/SDK examples default to `stream: true` everywhere.
- Frontend has a "Stop" button prominently placed → user abort is expected behavior.
- Response post-processing visible (JSON parsing, markdown rendering, structured extraction) — streaming wasted because the user only sees the parsed result.

**Estimated savings:** 5-15% on abort-prone surfaces. Smaller than other items but free to fix.

**Fix sketch:** Audit per-surface: keep streaming on chat, kill it on form-fill / structured-output / report-gen. Set `stream: false` and use the full response.

---

## 7. No Eval Gate on Model Swap

**What it looks like:** Engineering wants to try Haiku / Mini / Flash but has no offline eval harness, so they default to flagship "to be safe." Cost stays high not because flagship is necessary, but because they can't prove it isn't.

**External signals:**
- No public eval methodology — no `evals/` folder in their open-source repo, no blog post about "how we test model changes", no mention of Braintrust / Promptfoo / Inspect / Langfuse.
- Engineering blog says "we standardized on Claude Sonnet" with no comparison data.
- Founder tweets / podcasts: "we tried switching to X but it broke Y" → they tried once, got burned, gave up.
- Hiring for "ML / LLM evaluation engineer" — they know the gap, haven't filled it.

**Estimated savings:** 0% directly — but unblocks every other pattern in this list. Without an eval gate you can't safely apply patterns 2, 8, or 10.

**Fix sketch:** Build a 50-100 prompt golden set per task class with expected-output assertions. Run candidate models against it, compare pass rates + cost. Promptfoo or Braintrust handle the harness.

---

## 8. Tool-Use Without Result Caching

**What it looks like:** Agent loop calls tools (search, DB query, file read) and feeds results back to the model. Same tool-call returning same result happens across users/sessions, but the result tokens are re-billed every time they enter the context.

**External signals:**
- Product is agentic — "AI agent that searches your X" / "deep research" / "Cursor-like" / "autonomous coding".
- Public tool definitions show stable tools: web search, GitHub file read, SQL over a known schema.
- Latency complaints in community: "the agent re-searches the same thing 3 times in one session".
- No mention of "tool call cache", "result memoization", "tool result store" in their architecture posts.
- Stack uses LangGraph / OpenAI Agents SDK / Anthropic computer-use without a memo layer.

**Estimated savings:** 20-50% on agentic workloads. Tool results often dominate context length on long agent traces.

**Fix sketch:** Hash (tool_name, args) → result. Return cached result if hit within TTL. Also helps latency.

---

## 9. Re-Embedding Identical Chunks

**What it looks like:** Document ingestion re-embeds chunks every time a doc is re-uploaded, re-synced, or a user "refreshes" their knowledge base — even when the chunk content is byte-identical. Embedding costs scale with churn, not actual change.

**External signals:**
- Product is: "AI search over your Notion / Drive / GitHub / Slack" — ingestion-heavy.
- Changelog mentions "improved sync" or "faster re-indexing" → they're aware ingestion is slow.
- OpenRouter / OpenAI usage shows steady embedding-model traffic (text-embedding-3-small, voyage, cohere) that doesn't correlate with user growth.
- Their docs say "we re-sync every X hours" with no mention of content-hash dedup.

**Estimated savings:** 60-95% of embedding cost. Embeddings are cheap per-call, but ingestion-heavy products run them at high volume.

**Fix sketch:** Content-hash each chunk before embedding. Skip if hash already in vector store. Re-embed only on actual content change.

---

## 10. Verbose System Prompts (No Compression)

**What it looks like:** System prompt grew organically — every bug fix added "do not do X" rules, every customer complaint added a clause, every persona tweak added paragraphs. Now it's 4k tokens of mostly-redundant instructions, much of which the model is ignoring anyway.

**External signals:**
- Team has been shipping for 12+ months with multiple "personality" iterations (visible in changelog: "improved tone", "more concise responses", "less robotic").
- Leaked / published system prompt is long and visibly accreted (numbered rule list with 30+ items, repeated instructions, conflicting guidelines).
- No mention of "prompt audit" / "prompt compression" / "prompt distillation" in engineering blog.
- Founder has tweeted prompt screenshots — often a tell.

**Estimated savings:** 30-60% of system-prompt tokens via deduplication + condensation. Compounds with pattern 1 (caching) — shorter prompt + cache = double win.

**Fix sketch:** Audit the prompt against actual model behavior. Remove rules the model ignores. Collapse redundant instructions. Move rare-case rules into dynamic few-shot examples loaded only when relevant.

---

## Bonus signal: pricing page reverse-engineering

The prospect's PRICING page is one of the strongest external signals. If they charge a flat $20/mo for "unlimited AI" and OpenRouter shows them sending heavy Sonnet/Opus traffic — they're either burning runway or have heavy abuse mitigation we can't see. Either way, "your unit economics look interesting" is a credible opener.

If they charge per-message / per-credit, look at the price per credit, estimate token cost per call, and compare against flagship pricing. A $0.01-per-message product running on Opus is bleeding.
