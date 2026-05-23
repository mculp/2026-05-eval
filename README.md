# 2026-05-eval

Multi-model evaluation — same input, different orchestrators, comparable artifacts.

## What this repo measures

Each model gets the same goal prompt and the same toolset. The output goes in its own top-level directory. We score the **run as a whole**, not the model in isolation:

| Axis | What it captures |
|---|---|
| **Parallelism shape** | Did the orchestrator identify independent vs dependent work? Did it fork the right `N` at the right moments? `wall-clock(actual) / wall-clock(serial-equivalent)` is the headline number. |
| **Fabrication discipline** | Across the whole run, count of made-up facts, guessed emails, invented founder names. Subagent ground-truth verification catching the orchestrator's stale memory counts as a *positive* signal — not a negative one. |
| **Surface-shaped output** | Are the deliverables consumable in the form the buyer will read them? CSV for CRM import, markdown for iPad, HTML for interactive exploration — not a single 200KB blob. |
| **Cost per useful unit** | Total subagent tokens / verified prospects, or / fact-check catches, or / artifacts shipped. Raw token count isn't the metric. |

The goal prompt is held constant across runs. The execution shape (lanes, subagents, surface choices) is what each model is being scored on.

## Layout

```
/
├── README.md          ← this file — eval framework
├── opus-4.7/          ← run by claude-opus-4-7[1m] (2026-05-23)
│   ├── README.md           ← compiled pipeline (top-10, full table, catches)
│   ├── eval-visualization.html ← interactive run receipt
│   ├── pipeline.csv        ← CRM-importable 30-row deliverable
│   ├── outreach/           ← 30 per-prospect markdown files
│   ├── research/           ← bloat playbook + outreach template pack
│   └── raw/                ← source data + method notes
└── (future) opus-4.6/, sonnet-4.6/, etc.
```

To add another model's run: copy the goal prompt, run it under that model, drop the artifact tree at the next top-level directory.

## Goal prompt (held constant)

> Build an outbound pipeline of 30 high-intent B2B/Productivity AI apps from the OpenRouter leaderboard, analyze their potential inference/token bloat, find founder contact info, and draft highly personalized outreach sequences.

Date issued: 2026-05-23.

## Reading the runs

Each `<model>/` directory contains a self-describing `README.md` and `eval-visualization.html`. The HTML is a single-file vanilla-DOM artifact (no build step, opens in any browser) showing the run's actual parallelism shape, per-lane token + tool-use breakdowns, and the resulting prospect table sortable in place.

The CSV is the only file the buyer (i.e. the human running outreach) is expected to import into a CRM. Everything else is provenance.
