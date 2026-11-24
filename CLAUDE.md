# AI 201: Beyond the Basics — Vanderbilt Learning Series

Single-page interactive classroom experience (Learning on Demand). Live at
https://futureslearninghub.github.io/AI-Advanced/ (GitHub Pages, `gh-pages` branch —
publish with `git branch -f gh-pages main && git push -f origin gh-pages`).

Sequel to AI Basics (FuturesLearningHub/AI_Classroom); sister programs
Difficult_Conversations and Coaching-for-Performance; catalog at
FuturesLearningHub/FLH-Learning-Library-. Same engine, same standing principles.

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

Welcome/QR (prereq note) → Hero (6 objectives + montage) → Agenda →
01 Context & attention (window simulator + 3B1B video) → manifesto →
02 RAG (grounding toggle + IBM video) → 03 Choosing your method (matcher) →
04 Advanced patterns (matcher + rewrite drill) →
05 Multimodal & agentic (failure cards + trace trainer + IBM video) →
06 Spot the hallucination (6-round challenge) →
07 Governance (NIST RMF cards + tier sorter) → Recap quiz →
Capstone Team AI Workflow → Glossary → Closing (commitment).

## Editing map

- Copy: `index.html` · Recap: `QUESTIONS` in `assets/js/main.js`
- Trainers: `makeTrainer` configs (method, pattern, agent, hallucination, tier)
- Simulators: context (`MESSAGES`/`BANDS`), RAG (`setRag`) in main.js
- Capstone maps: `PATTERN` / `CHECK` / `TIER` in main.js
- Runbook: `facilitator/notes.json` (timing must sum: Full 90 / Core 60)
- Citations to keep honest: 3Blue1Brown (attention), IBM (RAG, agents,
  multimodal), White et al. prompt pattern catalog, Wei et al. (CoT),
  Brown et al. (few-shot), Adaline Labs (agent failures), NIST (red-teaming,
  AI RMF), Jules White Coursera (closing pointer).
