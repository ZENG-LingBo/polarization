# Pilot / Control Protocol — Inducing & Measuring Toxic Polarized Conversation

**TODO "SECOND".** Before the main experiment, run a **~20-person, no-intervention
pilot** that does two jobs at once:

1. **Induction validity** — prove we can *reliably* produce toxic, polarized
   conversation in our model platform (study the mechanics of *Ronaldo's a poser!*
   and the turn-taking/interruption dynamics from *Hear You in Silence*).
2. **Measurement validity** — prove our instruments (Perspective API, LIWC, incivility
   coding, the survey) **actually capture** that toxicity, with enough variance to move
   under intervention.

> Strategic payoff (per Ray's note): this pilot **doubles as the control condition**.
> If the induction is reliable and the measures are clean, *we don't have to re-run the
> control* when we later swap in a new intervention — the baseline is banked.

---

## 1. Design

- **N ≈ 20**, balanced: **10 Lakers fans + 10 Celtics fans** (screened ≥ midpoint on
  SSIS so identities are real).
- **Single between-subjects baseline cell** (no agents, no recategorization). Humans
  only — *no deception/bots in the pilot*, which also keeps IRB simple.
- **Format options** (pick one to pilot, A/B if time):
  - **(a) One 10v10 forum thread** — closest to *Ronaldo* (rival fans + arriving
    opponents). Maximizes group salience and pile-on dynamics.
  - **(b) Two–three 3v3 / 4v4 sessions** — more replicates, easier to moderate, better
    for per-session statistics.
  - *Recommendation:* run **(b)** for clean replicates, plus one **(a)** big thread to
    stress-test the worst-case toxicity ceiling.

---

## 2. Platform

Simulated forum / Discord-style channel (the *Ronaldo* platform is the reference
implementation). Required features for the pilot:

- **Visible team identity** on every user — flair/badge/jersey-color + handle tag
  (e.g., `@user · LAL`). Identity salience is the main induction lever (SIT).
- **Threaded replies + up/down-votes** (votes are a behavioral toxicity signal).
- **Full message logging** with timestamps and reply-graph (for turn-taking / pile-on
  metrics and Perspective scoring).
- **Seeded opening posts** (see §3) and the ability to **inject an arriving opponent**
  mid-thread (the *Ronaldo* escalation trigger).

---

## 3. Toxicity-induction levers (how to *reliably* get toxic outcomes)

Stack these; each is grounded in what we know escalates fan conflict:

1. **Maximally contentious, identity-framed prompt.** e.g.,
   *"Settle it once and for all: which franchise is the real NBA GOAT — Lakers or
   Celtics? Defend your side."* (Forces a zero-sum, identity-based stance.)
2. **Make team identity salient first** (badges + a pre-task "rep your team" intro
   post). Salient group identity → in-group favoritism (SIT).
3. **Competitive, zero-sum framing / stakes** — "the side with the better arguments
   wins." Competition over a single prize drives conflict (Robbers Cave logic, run in
   reverse).
4. **Seed provocation** — 2–3 confederate-style opening posts at moderate heat to set a
   combative norm (do *not* over-seed; let participants escalate).
5. **Inject an arriving opponent mid-thread** — the *Ronaldo* finding: rhetoric sharpens
   when new opposing members appear. Time this ~10 min in.
6. **Light time pressure** — "you have 20 minutes to make your case" raises affect and
   reduces self-editing.

*Tune levers in early sessions until toxicity reliably clears the success threshold
(§6), then freeze the protocol.*

---

## 4. Procedure (per session, ~45–60 min)

1. **Consent** (incl. explicit notice they may be exposed to heated/uncivil content) +
   demographics.
2. **S1 Pre-survey** — baseline affective polarization (thermometer, social distance,
   trait ratings, IOS), SSIS identification, trait reactance. *(see `survey_instrument.md`)*
3. **Identity salience priming** — badges assigned; each posts a short "why I rep
   [TEAM]" intro.
4. **Induction phase (~20–30 min)** — the contentious prompt goes live; opponent
   injection at ~10 min; minimal moderation (safety only).
5. **S2 Post-survey** — repeat polarization DVs + state reactance + manipulation checks.
6. **Interview (subset, n≈6–8)** — semi-structured: what made it heated? did you feel
   pushed? what would have calmed you down? *(feeds RQ1/RQ3 qualitative)*
7. **Debrief** — purpose, that conflict was by design, cooldown, resources.

---

## 5. Measures collected (the four buckets)

| Bucket | Instrument | DV |
|---|---|---|
| **1. Linguistics** | LIWC (Tausczik & Pennebaker 2010) | we/they pronoun ratio, anger/affect words, swear |
| **2. Behavioral toxicity** | Perspective API (Lees et al. 2022) + incivility coding (Coe et al. 2014) | per-message toxicity/insult/threat; coded incivility categories; downvote pile-ons |
| **3. Survey (pre/post)** | thermometer, social distance, traits, IOS (see instrument) | affective-polarization difference score |
| **4. Qualitative** | semi-structured interview | drivers of toxicity; felt experience |

**Before/after** is collected for the survey DVs so we can show (i) **control and (eventual)
experimental groups start at equivalent baseline polarization**, and (ii) the induction
**sustains or raises** polarization/toxicity across the session.

---

## 6. Success criteria (pre-specify before running)

The pilot **succeeds** if:

- **Toxicity signal:** ≥ a target share of messages exceed a Perspective toxicity
  threshold (e.g., ≥ 30% of messages with toxicity > 0.5 in the worst-case big thread),
  *and* incivility coding shows non-trivial name-calling/aspersion rates.
- **Measurement spread:** DVs show usable variance (no floor/ceiling); LIWC we/they and
  thermometer-difference are non-degenerate.
- **Baseline polarization is real:** S1 thermometer difference is significantly > 0.
- **Inter-rater reliability** for incivility coding ≥ κ .70 on a double-coded sample.

If toxicity is too low → escalate induction levers (§3) and re-pilot a session. If a
measure shows no spread → drop/replace it *now*, before the main study.

---

## 7. Analysis

- **Induction check:** paired test S1→S2 on affective-polarization DVs (did conflict
  hold/raise polarization?); descriptive toxicity trajectories over session time.
- **Measure validation:** inter-correlations among toxicity measures (Perspective ↔
  incivility ↔ LIWC anger) for convergent validity; variance/reliability checks.
- **Baseline equivalence template:** report S1 DVs as the table we'll reuse to show
  control ≈ experimental in the main study.

---

## 8. Ethics & safety

- IRB: informed consent **including exposure to uncivil content**; voluntary, with
  withdrawal at any time.
- **No bots/deception in the pilot** (human-only baseline) — the agent-disclosure and
  debrief questions belong to the main study's IRB amendment.
- Active **safety moderation** (remove slurs/threats/doxxing in real time; these are
  out-of-scope toxicity, not our DV).
- Structured **debrief + cooldown**; provide opt-out of data use post-hoc.
- Store logs de-identified; map handles → IDs in a separate key file.

---

## 9. Risks & mitigations

| Risk | Mitigation |
|---|---|
| Not toxic enough (polite participants) | escalate levers §3; recruit higher-identification fans; bigger thread |
| Too toxic / harmful | real-time safety moderation; clear withdrawal; cooldown/debrief |
| Lakers/Celtics rivalry weaker than expected | confirm with a quick pre-screen heat check; fall back to a sharper framing (e.g., a current playoff matchup) |
| Measures don't capture induced toxicity | that's *exactly* what the pilot is for — fix instruments before main study |
| Recruitment imbalance (one fanbase) | quota-recruit 10/10; over-recruit waitlist |

---

## 10. How this feeds the main study

- The frozen induction protocol + validated measures become the **control cell**.
- The pre-survey table becomes the **baseline-equivalence** evidence reviewers expect.
- Interview themes shape the **intervention** (which agent moves actually de-escalate;
  see `intervention_examples.md`).
- Then the only thing that changes in the experimental cell is the **multi-agent CIIM
  intervention** layered on the *same* platform and *same* measures.

> **Open item to confirm:** the TODO says "study Ronaldo and **Interruption paper**."
> I've folded in *Ronaldo*'s induction mechanics and the turn-taking/interruption
> dynamics from *Hear You in Silence*. If "Interruption paper" refers to a specific
> different paper, send the title and I'll pull its mechanics into §3.
