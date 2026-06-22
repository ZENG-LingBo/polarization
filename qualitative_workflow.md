# Qualitative Analysis Workflow — Polarization Defusing (Lakers vs. Celtics)

Written to match the **lab's house style** (Ray LC, *Mixed Methods Research Methods*,
HCIX; the lab open-coding/observation spreadsheets; the lab's hybrid Braun & Clarke ×
Saldaña thematic analysis). Reference materials live in `../Quant_Analysis/`.

## What we analyze qualitatively (two streams)

| Stream | Data | Serves | Coding rigor |
|---|---|---|---|
| **A. Interviews** | post-session semi-structured interviews (`interview_guide.md`) | RQ1 (felt experience), **RQ2 (mechanism:** did they discover common identity? feel pushed?) | **looser** — consensus reconciliation, no κ (per lab: "a bit looser on the interviews") |
| **B. Platform behavior (observation/content)** | the forum/Discord conversation logs | **RQ1 (behavior:** toxicity, cross-group engagement, de-escalation, response to agents) | **stricter** — shared codebook, **two coders, Cohen's κ ≥ .70** (per lab observation template + `measures.md`) |

Stream B is the qualitative complement to the quantitative toxicity pipeline
(Perspective API + LIWC + incivility coding in `measures.md`) — concurrent
mixed-methods ("zoom in and out on the same group").

---

## The coding pipeline (lab "levels")

Following Ray's grounded-theory pyramid:

1. **Level 1 — Initial / Open coding.** Label raw data datum-by-datum. Keep
   **in-vivo codes** (participant's own words, in quotes) distinct from **constructed
   codes** (researcher's). First-cycle Saldaña methods we'll lean on: *In Vivo,
   Descriptive, Process, Values, Emotion, Versus* (Versus is apt for rival-group talk).
2. **Level 2 — Focused coding / category development.** Re-examine Level-1 codes;
   keep the frequent/significant ones; cluster into categories (Pattern/Focused coding).
3. **Level 3 — Axial / thematic coding.** Relate categories → **themes & subthemes**
   (interpretive constructs, *not* themselves coded).
4. **Saturation.** "Keep gathering info until no new findings"; themes emerge from
   **saturated** categories.

**Always:** keep **memos apart from the data**; **state interpretation/bias in the
paper** (lab "must"). Tools: SaturateApp / Miro (statement cards + affinity diagram).

---

## Day-by-day (your workflow, made specific)

- **Day 1 AM** — run pre-survey (demographics + content) → interview → **initial/open
  code** that interview same day (Stream A template below).
- **Day 1 PM** — continue open coding → write the **`SUMMARY`** + **`RQs Inspiration`**
  block → fold into the paper (RQ section, intro, notes/comments).
- **Day 2** — initial code → **focused coding** → reflect into **results subsections**
  (with inline comments) as candidate themes form.
- **Day X (after 5–10 interviews)** — build the **codebook together** (especially for
  Stream B observation; looser for Stream A interviews); finish/modify focused codes →
  draft **themes & subthemes** = paper section skeleton.
- **Day Y** — reconcile separate coders' work into **collective themes** via a
  **consensus workshop / affinity diagram** (sticky notes on Miro).
- Flexible — adapt to reach **validated** insights.

> Sample-size anchors (Ray's table): **interviews ≈ 5** to first codebook, continue to
> saturation; **observation ≈ 3+** sessions, but with **two coders + κ**. The lab's
> worked example ran n=20 interviews → 415 statement cards → 66 clusters → 6 themes.

---

## Stream A — Interview coding (lab open-coding format)

**Workbook = one study. Tabs:** an `index` roster + one tab per participant (tab name =
participant ID, e.g. `P1`, `P7`).

**`index` tab columns:** `ID | gender (M/F) | age | note (team + lean, e.g. "LAL, high SSIS") | finished (1 / 待访 / <assignee>)`

**Per-participant coding sheet:** (template in `coding_templates/interview_opencoding_template.csv`)

| (col A — *leave header blank*) quote/excerpt | code1 | code2 | code3 | code4 | code5 |
|---|---|---|---|---|---|

- One excerpt per row. Put the **interviewer prompt inline in parentheses** before the
  answer, lab-style: `（what made that moment heated?）honestly it was when the other
  guy brought up 2008…`.
- Fill codes left-to-right, one per cell, blanks OK. Lab convention: interview codes are
  written as **short descriptive sentences/phrases** (mini-memos), with **in-vivo codes
  in quotes** (e.g. `"2008 was elite"`).

**Initial-coding notes doc** (the condensed counterpart; lab `…Notes_InitialCoding.docx`
format): start with a legend, then one line per turn, then synthesis:
```
P1: N    P2: C    P3: W
P1: felt the thread was hostile from the first reply, "ratio" culture, didn't want to engage
P2: noticed someone staying calm and asking questions, found it "weirdly disarming", started replying nicer
...
SUMMARY
hostility front-loaded -> a calm peer reply -> norm shift -> cross-group reply
"we're all hoops fans" surfaced only after the shared prediction task (not when stated directly)
RQs Inspiration:
How does a calm peer turn-taking model shift the descriptive norm of a heated fan thread?
```

---

## Stream B — Platform-behavior coding (lab observation format + κ)

**Workbook tabs:** a shared **`Codebook`**, then one tab per **(session × coder)**
(e.g. `Session3_code by A`, `Session3_code by B`), then a **`Cohen's Kappa`** tab.

**Unit of analysis:** per **message** (preferred for chat) — and/or 30-sec time bins if
you want the lab's interval grid. Two coders code **independently**; reconcile; report κ
per category (target **≥ .70**, `measures.md`).

**`Codebook` seed** (`coding_templates/observation_codebook_seed.csv`) — category → code:

| Category | Behavior code (examples) |
|---|---|
| **Incivility / toxicity** (Coe et al. 2014) | name-calling, aspersion, lying accusation, vulgarity, pejorative-for-speech |
| **Group framing** | in-group ("we/us" team) reference, out-group ("they/them" rival) derogation, **superordinate "we're all NBA fans"** expression |
| **Cross-group engagement** | reply to rival fan, agree-with-rival, ask rival a genuine question, help/concede a point |
| **Escalation dynamics** | pile-on join, "ratio"/dismissal, dogpile, sarcasm-as-attack |
| **De-escalation moves** | acknowledge feeling, refuse bait, humor-to-defuse, common-ground bid |
| **Response to agents** | imitates agent's tone, takes up agent's question, **calls out a bot/AI** (← critical for the agent-detection moderator) |
| **Cooperative-task** | joins shared task, contributes to cross-fanbase goal |

Code Stream B **blind to condition** where possible. These codes triangulate with the
automated toxicity scores (convergent validity check).

---

## From codes to themes to paper

Hybrid **deductive → inductive** TA (lab recipe):

1. **Deductive code manual** seeded from RQs + interview guide (the provisional table
   below) — built *before* coding.
2. Each coder makes **statement cards** (raw quote + participant ID + interpretive
   title) on Miro.
3. **Consensus workshop** — keep agreed cards, merge overlaps, decide disputes together.
4. **Cluster** cards (inductive) → connect clusters into **themes**.
5. Review cards under themes → finalize **themes + subthemes** with evocative names
   (not direct quotes as names) → these become **results subsections**.
6. **Decision rule** for promoting a code to a reported finding (state it explicitly,
   e.g. "appeared for ≥ half of participants, or carried a substantive mechanism").

Map every theme back to an RQ (RQ1 process/behavior · RQ2 mechanism/effect). Quotes are tagged
`P#`. **Write the reflexivity/bias statement** in Methods (lab must).

---

## Provisional deductive code manual (seed — refine in the codebook workshop)

| Category (deductive) | From | Maps to | Example seed codes |
|---|---|---|---|
| Team-identity salience | SIT / SSIS | RQ1 | reps-team-hard, banner-pride, rival-disdain |
| Out-group animus | affective polariz. | RQ1/RQ2 | derogates-rival, dehumanizing-humor, "delusional" |
| Toxicity / incivility | Coe 2014 | RQ1 | name-calling, dogpile, "ratio" |
| De-escalation experience | active listening | RQ1 | felt-disarmed, calmed-by-peer, chose-not-to-bite |
| **Common-identity discovery** | **CIIM** | **RQ2** | "we're all NBA fans", found-common-ground, dual-identity-felt |
| Cooperative-task effect | superordinate goals | RQ1/RQ2 | enjoyed-shared-task, teamed-with-rival |
| **Reactance / agent detection** | Brehm; *When AI Agrees* | RQ2 | felt-pushed, suspected-bot, resisted-message |
| Persistence | follow-up | RQ2 | softened-view, still-rivals-but |

---

## Trustworthiness checklist (state these in the paper)

- [ ] Saturation reached (no new codes) — report how judged.
- [ ] Interviews: consensus reconciliation; Observation: **Cohen's κ per category (≥ .70)**.
- [ ] Memos kept apart from data; audit trail of code→category→theme.
- [ ] Reflexivity / researcher-bias statement (lab "must").
- [ ] Decision rule for code→finding stated explicitly.
- [ ] Stream B coded blind to condition where feasible; triangulated with Perspective/LIWC.

## Method citations (added to `refs.bib`)
`braun2006thematic`, `saldana2016coding`. Existing: `coe2014incivility`,
`tausczik2010liwc`, `lees2022perspective`.
