# Facilitation Guide — AI 201: Beyond the Basics

Every activity carries a learner-visible **"Why this matters"** line, and
every teaching section has (1) an **interactive tool or practice moment**,
(2) a **labeled, timed activity** — *As a group* or *On your own* — and
(3) a **validation point**.

The full runbook lives in [`facilitator/notes.json`](facilitator/notes.json)
on the **ATD facilitator-guide framework**: per section a verbatim **Say**
script, **Do** choreography, an **Ask** with anticipated responses, a
**Debrief** line, and a scripted **Transition**, plus front matter
(materials, prep checklists, contingencies, tough questions, and copy-paste
templates: pre-work invite, 7-day pulse, 30-day workflow census).

**Prerequisite:** AI Basics (101) or equivalent. The pre-work invite
reminds participants and asks them to bring one real recurring task.

The **facilitator edition is live at `/facilitator/`** — regenerate after
any change to `index.html` or `notes.json`:

```bash
python3 tools/build-facilitator.py
```

## Run of show — two paths

| Slide | Full (90 min) | Core (60 min) |
|---|---|---|
| Welcome / QR | 3 | 2 |
| Objectives | 2 | 1 |
| Agenda | 1 | — |
| 01 Context & attention | 10 | 7 |
| Manifesto | 1 | — |
| 02 Grounding with RAG | 10 | 7 |
| 03 Choosing your method | 10 | 7 |
| 04 Advanced prompt patterns | 11 | 7 |
| 05 Multimodal & agentic AI | 11 | 7 |
| 06 Spot the hallucination | 7 | 5 |
| 07 Governance | 8 | 5 |
| Recap quiz | 4 | 4 |
| Team AI Workflow (capstone) | 8 | 6 |
| Glossary | 1 | — |
| Closing / commitment | 3 | 2 |
| **Total** | **90** | **60** |

**Core-path rules:** both simulators, all five trainers, the recap, and the
capstone stay. Skip the agenda, manifesto, glossary, and ALL in-class
videos (assign the three as the week's watch list); debriefs shrink to one
voice each. Per-section cuts live in each `coreNote`.

**Timing discipline:** the patterns drill and the agents discussion are the
stretchy blocks. Protect the last 15 minutes (recap, capstone, commitment)
by trimming debriefs first, never Spot-the-Hallucination or the capstone.

**Pre-work and follow-up:** the pre-work invite (bring one recurring task),
7-day pulse, and 30-day workflow census templates live on the facilitator
briefing slide. `worksheet.html` is the no-device fallback.

## Validation model

- **In the moment:** inline checks (01, 02), trainer scores (03, 04, 05,
  06, 07), the simulator interactions (window slider, RAG toggle), and the
  neighbor-named pattern rewrite (04).
- **End of session:** the 6-question recap maps 1:1 to the six objectives
  (Level 2); the closing fist-to-five is the Level 1 check; the workflow
  card and the trigger-and-tier commitment round are the transfer artifacts.
- **After:** the 7-day pulse (did the workflow run, what did the checkpoint
  catch) is Level 3 evidence; the **30-day workflow census** (how many
  teams have a written, tiered workflow) is the program's headline metric.
- **Consistency guard:** the governance tiers must always match AI Basics'
  green/yellow/red rules; the two courses cite each other.
