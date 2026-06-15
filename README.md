# Polarization Defusing — Lakers vs. Celtics

Defusing **affective polarization** between rival fan communities (LA Lakers vs.
Boston Celtics) inside a **simulated social-media platform**, using a population of
**generative-AI agents** that exert peer-level **social influence** — *structurally*
(cooperative recategorization, behavioral modeling) rather than by direct persuasion.

**Theory spine:** Social Identity Theory → Common Ingroup Identity Model (CIIM) →
recategorization toward a superordinate "we're all NBA fans" identity, delivered by
multiple peer-like agents that model de-escalation and inclusive turn-taking. We avoid
direct LLM persuasion because reactance (Brehm) and *When AI Agrees* (Liu et al. 2026)
show it backfires.

**Research questions:**
- **RQ1 (process/behavior):** how do polarized fan groups interact on the platform, and
  what behavioral change emerges when a structured recategorization mechanic is added?
- **RQ2 (effect):** how does a CIIM-based multi-agent LLM intervention affect affective
  polarization between the groups?
- **RQ3 (mechanism):** is any reduction mediated by perceived common identity, and does
  it persist?

---

## Repository map

### 📄 The paper (compiles on Overleaf)
| File | What it is |
|---|---|
| [`main.tex`](main.tex) | Entry point. Preamble (`booktabs`, `amssymb`, `tabularx`, `natbib`) + `\input`s below. |
| [`introduction.tex`](introduction.tex) | §1 Introduction — problem, structural-intervention framing, RQ1–3, contributions. |
| [`background.tex`](background.tex) | §2 Related Work — 3 subsections (**2.1 Sociological · 2.2 Psychological · 2.3 Technical**) + comparison table. 2.3 is **provisional** pending the system design. |
| [`refs.bib`](refs.bib) | 29 references. External theory verified via Crossref/DBLP; Ray LC lab papers; measurement instruments. |
| [`paper.md`](paper.md) | **Markdown mirror** of intro + background for quick reading on GitHub. |

### 🧪 Study materials
| File | What it is | TODO |
|---|---|---|
| [`measures.md`](measures.md) | Measurement plan — constructs → validated instruments → RQ → pre/during/post/follow-up timing → analysis. | FIRST |
| [`survey_instrument.md`](survey_instrument.md) | Exact survey item wording per wave (SSIS, feeling thermometer, social distance, traits, IOS, CIIM mediator, allocation, reactance, manipulation checks) + scoring. | — |
| [`pilot_protocol.md`](pilot_protocol.md) | ~20-person toxicity-induction pilot that doubles as the control cell: induction levers, procedure, 4 measure buckets, success criteria, ethics. | SECOND |

### 🤖 Intervention eval kit
| File | What it is | TODO |
|---|---|---|
| [`intervention_examples.md`](intervention_examples.md) | Design principles + example agent posts by strategy + anti-patterns + the 1–5 eval rubric. | #1 |
| [`agent_posts_batch1.md`](agent_posts_batch1.md) | **18 candidate agent posts** (5 mechanisms, both team leans) + scoring sheet. | #1 |
| [`agent_posts_negcontrol.md`](agent_posts_negcontrol.md) | **8 deliberately-bad posts** (anti-patterns) — blind-mix with Batch 1 as the negative control. | #1 |

---

## How to build the paper
Overleaf is linked to this repo. **Menu → GitHub → Pull GitHub changes**, then compile
`main.tex`. (No local LaTeX toolchain is assumed; the build happens on Overleaf.)
All `\cite` keys resolve against `refs.bib` — verified each push.

## How to run the intervention eval (TODO #1)
1. **Blind-mix** the 18 posts in `agent_posts_batch1.md` with the 8 in
   `agent_posts_negcontrol.md`; randomize order; strip the strategy labels.
2. Reviewers score each on the rubric (peer · non-reactance · identity · de-escalation ·
   naturalness · cleanliness) + gut-check "would you engage? (Y/N)".
3. Compare **mean(de-escalation × engage-Y)**: Batch 1 vs. negative control. A clear gap
   = the intervention texts do real work.
4. The winning **mechanism** (A/B/C/D/E) anchors the intervention design and Batch 2.

---

## Status

| Team TODO | State | Where |
|---|---|---|
| **ZERO** — decide topic | ✅ Lakers vs. Celtics | — |
| **FIRST** — find measures that move | ✅ drafted | `measures.md`, `survey_instrument.md` |
| **SECOND** — induce + measure toxic convo | ✅ protocol drafted | `pilot_protocol.md` |
| **#1** — eval LLM intervention texts | ✅ materials ready; needs Discord scoring | `intervention_examples.md`, `agent_posts_*.md` |
| Write RW, 3 subsections | ✅ in Overleaf (2.3 provisional) | `background.tex` |
| Recruit participants | ⬜ not started | (screener TBD) |
| Finalize system / lock §2.3 Technical | ⬜ pending design | `background.tex` |

### Open items
- **§2.3 Technical** is marked provisional — finalize once the agent/platform design is
  locked.
- **"Interruption paper"** referenced in the TODOs: induction currently folds in
  *Ronaldo* + *Hear You in Silence* mechanics; confirm if a specific other paper is meant.
- **Author names** for the newer lab papers in `refs.bib` are initials from the lab
  listing — expand to full first names before submission.
- Lab-paper DOIs `hui2025moral` (ScienceDirect URL) and a couple of CSCW'26 entries lack
  clean DOIs — chase down before camera-ready.

---

## Citation accuracy
All external/theory and instrument references were verified against Crossref / DBLP /
publisher records. No citations were fabricated; unverifiable fields were omitted.
Drop in the validated wording for copyrighted scales (SSIS, Hong Reactance) before
fielding the survey.
