# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# AI 201: Beyond the Basics — Vanderbilt Learning Series

Single-page interactive classroom experience (Learning on Demand): a facilitator
projects `index.html` while learners follow on their own devices via QR code.
Plain HTML/CSS/JS — no frameworks, no build step, no package manager, no tests.

- Learner edition: https://me5231979.github.io/AI-Advanced/ (GitHub Pages, `gh-pages` branch)
- Facilitator edition: https://me5231979.github.io/AI-Advanced/facilitator/ (generated, see below)

Sequel to AI Basics (me5231979/AI_Classroom); sister programs
Difficult_Conversations and Coaching-for-Performance; catalog at
me5231979/Course_Library. Same engine, same standing principles.

## Commands

```bash
python3 -m http.server 8000          # preview locally (no build step)
python3 tools/build-facilitator.py   # regenerate facilitator edition — REQUIRED after
                                     # any change to index.html or facilitator/notes.json;
                                     # must print "15 notes rails injected"
git push origin main && git branch -f gh-pages main && git push -f origin gh-pages   # publish
```

There is no linter or test suite. Verification = open the page in a browser,
exercise the interactives, and confirm the build script's rail count.

## Architecture

**Learner site** — three files carry everything:

- `index.html` — all copy for 15 `<section class="slide" id="s-*" data-title="…">`
  slides, separated by `<!-- ============ N · NAME ============ -->` banner
  comments. `data-count` marks the seven numbered teaching sections.
- `assets/js/main.js` — one IIFE, organized by banner comments. Key pieces:
  - `makeTrainer(cfg)` — generic quiz engine instantiated five times (method
    matcher, pattern matcher, agent-trace trainer, hallucination challenge,
    tier sorter). Each config supplies element selectors, `items`
    (`{q, opts?/labels, answer, why}`), pass threshold, and pass/fail copy.
  - Context-window simulator: `MESSAGES` / `BANDS` arrays.
  - RAG toggle: `setRag`.
  - Scored recap: `QUESTIONS` (6 items, mapped 1:1 to the hero objectives).
  - Capstone: `PATTERN` / `CHECK` / `TIER` lookup maps building the copyable
    workflow card.
  - Deck navigation (dots, arrows, keyboard), reveal-on-scroll, hero video
    montage (Higgsfield CDN playlist in `data-playlist`) with particle-canvas
    fallback.
- `assets/css/styles.css` — one file; brand tokens are CSS custom properties
  (`--vu-gold-flat`, `--vu-black`, font vars). Fonts self-hosted in
  `assets/fonts/`; QR lib vendored at `assets/js/qrcode.js`.

**Facilitator pipeline** — `tools/build-facilitator.py` reads `index.html` +
`facilitator/notes.json` and writes `facilitator/index.html` (generated output —
never hand-edit). It works by literal string/regex replacement on index.html, so
these anchors must survive any edit to index.html:

- the exact `<title>AI 201: Beyond the Basics | Vanderbilt</title>` string
- `<div class="qr-card" id="qrCard" data-reveal>`
- the `<!-- ============ 0 · WELCOME / QR ============ -->` banner (briefing
  slide is injected before it)
- the footer line `AI 201: Beyond the Basics · A Vanderbilt learning experience`
- slide closing tags indented exactly two spaces (`\n  </section>`) — the
  notes-rail regex depends on it

`facilitator/notes.json` schema: `meta` (program info, `paths` Full 90/Core 60,
ATD front matter: `materials`, `prep` {weekBefore, dayBefore, thirtyMinBefore},
`contingencies` {if, then}, `toughQuestions` {q, a}, `templates` {title, body},
`postSession`) plus `sections[]` keyed by slide `id` with per-slide `minutes`,
`coreMinutes` (null = skipped in Core), `purpose`, `say`, `facilitate[]`,
`ask` {q, expect[], respond}, `debrief`, `validate`, `watchFor`, `transition`,
`coreNote`. **Timing must sum: Full 90 / Core 60.**

**Standalone pages:** `cheatsheet.html` (take-home reference),
`worksheet.html` (paper capstone / no-device fallback), `404.html`.
`FACILITATION.md` documents the run-of-show and validation model.

## Standing design principles (do not regress these)

1. **Simulators, practice, and play throughout.** Every teaching section
   has an interaction; the context-window simulator and RAG toggle are the
   signature pieces, Spot-the-Hallucination is the energy peak.
2. **A reason and facilitation behind every activity.** Learner-visible
   "Why this matters" lines; activities labeled As a group / On your own
   with steps, timings, and solo variants.
3. **Every section facilitatable, learning validatable.** ATD runbook in
   `facilitator/notes.json`. Kirkpatrick: L1 fist-to-five, L2 recap mapped
   to the six objectives, L3 workflow card + 7-day pulse + 30-day census.
4. **Facilitator edition is generated, never hand-edited** — run
   `python3 tools/build-facilitator.py` after ANY change to index.html or
   notes.json. Its QR encodes the LEARNER url.
5. **Consistency with AI Basics.** Same green/yellow/red data tiers, same
   verification habit, same Jules White lineage for prompt patterns. Never
   contradict the 101 course; extend it.
6. **Brand: Vanderbilt FLH system.** Black #1C1C1C / white / flat gold
   #CFAE70; Libre Caslon Display headlines (one italic word), Inter body,
   Antonio eyebrows; motion ≤400ms; real VU lockups (authorized use only).
7. **No frameworks.** One CSS file, one JS file, vendored QR lib,
   self-hosted fonts; hero montage streams from Higgsfield CDN with the
   particle canvas fallback.

## Layout (15 slides)

Welcome/QR (prereq note) → Hero (6 objectives + skills row + montage) → Agenda →
01 Context & attention (window simulator + 3B1B video) → manifesto →
02 RAG (grounding toggle + IBM video) → 03 Choosing your method (matcher) →
04 Advanced patterns (matcher + rewrite drill) →
05 Multimodal & agentic (failure cards + trace trainer + IBM video) →
06 Spot the hallucination (6-round challenge) →
07 Governance (NIST RMF cards + tier sorter) → Recap quiz →
Capstone Team AI Workflow → Glossary → Closing (commitment).

Slide ids: `s-welcome`, `s-hero`, `s-agenda`, `s-attention`, `s-belief`,
`s-rag`, `s-method`, `s-patterns`, `s-agents`, `s-halluc`, `s-govern`,
`s-recap`, `s-plan`, `s-glossary`, `s-close`.

## Editing map

- Copy: `index.html` · Recap: `QUESTIONS` in `assets/js/main.js`
- Trainers: `makeTrainer` configs (method, pattern, agent, hallucination, tier)
- Simulators: context (`MESSAGES`/`BANDS`), RAG (`setRag`) in main.js
- Capstone maps: `PATTERN` / `CHECK` / `TIER` in main.js
- Runbook: `facilitator/notes.json` (timing must sum: Full 90 / Core 60)
- Skills row (hero): VU core competencies + course skills pills in `index.html`
- Citations to keep honest: 3Blue1Brown (attention), IBM (RAG, agents,
  multimodal), White et al. prompt pattern catalog, Wei et al. (CoT),
  Brown et al. (few-shot), Adaline Labs (agent failures), NIST (red-teaming,
  AI RMF), Jules White Coursera (closing pointer).
