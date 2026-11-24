# AI 201: Beyond the Basics — How Models Actually Work, and How to Run Them Responsibly

An interactive, single-page teaching site for anyone who completed
**AI Basics (101)** and wants to go under the prompt box. A **Learning on
Demand** program: the facilitator projects it while learners scan a QR code
and work every exercise on their own devices, or share the link for
self-paced review. Still no code, still no math.

Part of the Vanderbilt Learning Series. Catalog:
[Course Library](https://flh-learning-library.vercel.app/) ·
Prerequisite: [AI Basics](https://futureslearninghub.github.io/AI_Classroom/)

- **Learner edition:** https://futureslearninghub.github.io/AI-Advanced/
- **Facilitator edition:** https://futureslearninghub.github.io/AI-Advanced/facilitator/

## Running it

Plain HTML/CSS/JS, no build step:

```bash
python3 -m http.server 8000
```

## What it teaches (7 sections)

1. Context & attention — the finite window, why models "forget" (3Blue1Brown)
2. Grounding with RAG — trustworthy raw material, clickable receipts (IBM)
3. Choosing your method — prompting vs RAG vs fine-tuning, cheapest first
4. Advanced prompt patterns — Few-Shot, Chain-of-Thought, Template, Flipped
   Interaction (White et al., Wei et al., Brown et al.)
5. Multimodal & agentic AI — the plan/act/observe loop and its documented
   failure modes (wrong tool, misread I/O, infinite loop)
6. Spot the hallucination — fluency vs accuracy, and why red-teaming exists (NIST)
7. Governance — the NIST AI RMF's four functions and green/yellow/red tiering

Ends with a scored recap mapped 1:1 to the objectives, the **Team AI
Workflow capstone** (trigger, AI step, pattern, human checkpoint, governance
tier), a flip-card glossary, and a commitment close. `worksheet.html`
mirrors the capstone on paper; `cheatsheet.html` is the take-home reference.

## The interactive tools

| Slide | Tool | What learners do |
|---|---|---|
| Attention | **Context-window simulator** | Drag deeper into a chat and watch the opening instruction fall out of the window; the answer degrades live |
| RAG | **Grounding toggle** | Flip the same question between "general chatbot" (fluent guess) and "RAG-connected" (cited answer + retrieved source) |
| Method | **Pick the method** | Route five real requests: prompting, RAG, or fine-tuning |
| Patterns | **Match the pattern** | Fit Few-Shot / CoT / Template / Flipped to five tasks |
| Agents | **Babysit the agent** | Read five agent traces and name the failure mode (or the healthy checkpoint) |
| Evaluation | **Spot the hallucination** | Call six AI answers accurate or invented; learn the tells and their limits |
| Governance | **Tier the information** | Classify five items green / yellow / red before they touch a tool |
| Recap | **Scored quiz** | 6 questions mapped 1:1 to the objectives |
| Capstone | **Team AI Workflow** | Build and copy a governed workflow card |

## Instructional design

- **Bloom's ladder:** objectives run Explain/Describe → Choose/Apply →
  Recognize/Analyze → Classify-and-build (Create).
- **Kirkpatrick:** L1 fist-to-five at close; L2 inline checks + recap mapped
  to objectives; L3 workflow card + 7-day pulse + 30-day workflow census
  (templates on the facilitator briefing slide).
- **Adult learning:** learners bring one real recurring task (pre-work),
  every drill uses their own prompts and workflows, and the capstone ships
  as a usable team artifact within a week.

## The facilitator edition

Generated at `/facilitator/` by `python3 tools/build-facilitator.py` from
`facilitator/notes.json` — ATD-scripted rails (Say / Do / Ask with expected
answers / Debrief / Transition), a briefing slide (prep, materials,
contingencies, tough questions, three copy-paste templates), Full 90 /
Core 60 timing. Its QR encodes the learner URL.

## Editing map

- Copy: `index.html` · Recap: `QUESTIONS` in `assets/js/main.js`
- Trainers: `makeTrainer` configs · Simulators: `MESSAGES`/`BANDS` (context)
  and `setRag` (RAG) in main.js · Capstone maps: `PATTERN`/`CHECK`/`TIER`
- Runbook: `facilitator/notes.json` (timing must sum Full 90 / Core 60)
- Publish: `git push origin main && git branch -f gh-pages main && git push -f origin gh-pages`
