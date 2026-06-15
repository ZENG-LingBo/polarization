# Survey Instrument — Polarization Defusing (Lakers vs. Celtics)

Exact item wording, organized by **wave**. Ready to drop into Qualtrics. Each block
notes its **source**, **response scale**, **wave(s)**, and **scoring**.

> **Convention.** `[TEAM]` = the participant's own team (Lakers *or* Celtics, piped
> from screening). `[RIVAL]` = the opposing team. Where a scale is copyrighted, items
> are paraphrased for planning — **use the validated wording from the cited source in
> the live survey.**

Waves: **S0 Screening · S1 Pre · S2 Post · S3 Follow-up (1–2 wks)**

---

## S0. Screening & eligibility

1. *Which NBA team do you support?* → [Lakers / Celtics / Another team / None]
   **(Eligible: Lakers or Celtics only.)**
2. *How long have you considered yourself a fan of [TEAM]?* → [<1 yr / 1–3 / 4–10 / 10+]
3. **SSIS gate (see Block A):** include only participants scoring ≥ midpoint on team
   identification, so the sample is genuinely identified (and thus polarizable).

---

## Block A — Sport Spectator Identification Scale (SSIS)
*Source: Wann & Branscombe (1993). 7 items, 1–8 scale. Wave: **S1** (baseline
covariate/moderator); re-administer team-identity item at **S2** as a dual-identity
check.*

Scale anchors vary per item (1 = low, 8 = high). Paraphrased items:

1. How important is it to you that [TEAM] wins? *(1 = not important … 8 = very important)*
2. How strongly do you see yourself as a fan of [TEAM]?
3. How strongly do your friends see you as a fan of [TEAM]?
4. During the season, how closely do you follow [TEAM] (in person, TV/stream, or
   media)?
5. How important is being a fan of [TEAM] to you?
6. How much do you dislike [TEAM]'s greatest rivals?
7. How often do you display [TEAM]'s name or insignia (clothing, profile, where you
   live/work)?

**Scoring:** mean of 7 items = team-identification strength. *Use as covariate;
expect high identifiers to show more reactance.*

---

## Block B — Feeling thermometer  *(PRIMARY DV)*
*Source: Iyengar & Westwood (2015), adapted to fan groups. Scale 0–100. Waves: **S1,
S2, S3.***

> "We'd like to know how you feel toward different groups using a 'feeling
> thermometer.' Ratings from **0 to 100**: ratings **above 50** mean warm/favorable,
> **below 50** mean cold/unfavorable, **50** is neutral. How do you feel toward…"

- B1. **Lakers fans** ___
- B2. **Celtics fans** ___
- B3. NBA fans in general ___ *(superordinate-group anchor)*
- B4. Baseball fans ___ *(neutral out-group anchor)*

**PRIMARY DV — affective polarization:** `warmth([TEAM] fans) − warmth([RIVAL] fans)`.
Lower = depolarized. Track B3 (NBA-fan warmth) as the CIIM superordinate target.

---

## Block C — Social distance
*Source: Iyengar & Westwood (2015), adapted. Scale 1–7 (1 = not at all
uncomfortable/upset … 7 = extremely). Waves: **S1, S2.***

How would you feel about each of the following?

- C1. A close family member marrying a **[RIVAL]** fan.
- C2. Having a **[RIVAL]** fan as a close friend.
- C3. Having a **[RIVAL]** fan as a next-door neighbor.
- C4. Working closely with a **[RIVAL]** fan on a team project.

**Scoring:** mean (higher = more social distance / more polarized).

---

## Block D — Out-group trait ratings
*Source: Iyengar & Westwood (2015), adapted. Scale 1–7 (1 = not at all … 7 = extremely).
Waves: **S1, S2.** Ask in parallel for [TEAM] and [RIVAL] to compute a bias score.*

> "How well does each word describe **[RIVAL]** fans as a group?"

Positive: intelligent · open-minded · honest · generous
Negative: mean · hypocritical · arrogant · closed-minded

**Scoring:** out-group bias = (own-team positive − rival positive) + (rival negative −
own-team negative). Repeat trait block for [TEAM] to enable the difference.

---

## Block E — Inclusion of Other in the Self (IOS)  *(KEY, sensitive)*
*Source: Aron, Aron & Smollan (1992). Single pictorial item, 7 increasingly
overlapping circle-pairs (1 = no overlap … 7 = near-complete overlap). Waves: **S1,
S2, S3.***

> "Below are pairs of circles. The left circle is **[TEAM] fans**, the right is
> **[RIVAL] fans**. Select the pair that best represents how you see the relationship
> between the two groups." *(1–7)*

**Scoring:** higher = greater perceived overlap / common identity. *One of our best
bets for a significant effect.*

---

## Block F — Common ingroup identity representation  *(MEDIATOR, RQ3)*
*Source: Gaertner & Dovidio (2000) CIIM representations, adapted. Scale 1–7 (1 =
strongly disagree … 7 = strongly agree). Wave: **S2** (about the platform experience).*

> "Thinking about the interaction you just had, to what extent did it feel like…"

- F1. **two separate groups** (Lakers fans vs. Celtics fans). *(separate-groups)*
- F2. **one single group**. *(one-group — mediator)*
- F3. **one group of NBA fans**. *(superordinate — mediator)*
- F4. **separate individuals**, not groups at all. *(decategorization control)*

**Dual-identity check (guards against distinctiveness-threat backfire):**
- F5. "During the interaction I felt like a **[TEAM] fan** *and* an **NBA fan** at the
  same time."

**Scoring:** mediator = F2/F3 composite; test indirect effect intervention → (F2/F3) →
Δ feeling-thermometer DV.

---

## Block G — Behavioral intention / "voting"
*Sources: allocation adapted from Iyengar & Westwood (2015) economic-game paradigm;
intention items author-written. Waves: **S2, S3** (G3 follow-up).*

- **G1. Allocation task.** "As a thank-you, you have **10 bonus raffle entries** to
  distribute between two other participants. How many do you give to each?"
  → ___ to a **[TEAM]** fan / ___ to a **[RIVAL]** fan (must total 10).
  *DV = entries given to rival fan; in-group favoritism = 5 − rival allocation.*
- G2. "I would be willing to join another event where **[TEAM]** and **[RIVAL]** fans
  participate together." *(1–7 agree)*
- G3. "I would cooperate with **[RIVAL]** fans on a shared task again." *(1–7 agree)*

---

## Block H — Reactance  *(GUARDRAIL)*
**H-trait** *(Source: Hong & Faedda (1996), Hong Psychological Reactance Scale, 11
items, 1–5. Wave: **S1**, covariate.)* — paraphrased examples; use validated 11-item set:
- "I resent authorities who try to tell me what to do."
- "I become frustrated when I'm unable to make free and independent decisions."
- "When something is prohibited, I usually think 'that's exactly what I'm going to do.'"
- "I consider advice from others to be an intrusion."  *(+ 7 more)*

**H-state** *(Source: Dillard & Shen (2005). Wave: **S2**, about the platform.)*
- H-anger (1–7): "During the interaction I felt: irritated / angry / annoyed /
  aggravated."
- H-cognition: open-ended thought-listing → code share of negative/counter-arguing
  thoughts.

---

## Block I — Manipulation & agent-detection checks
*Wave: **S2** (place LAST, after all DVs, before debrief).*

- I1. "Did you notice anything unusual about any of the other participants?" *(open)*
- I2. "Do you think any of the participants were not real people (e.g., bots or AI)?"
  → [Yes / No / Unsure]; if yes: "Which ones, and what gave it away?" *(open)*
- I3. "How much did the conversation feel like a real social-media discussion?" *(1–7)*

*(I2 is critical: per* When AI Agrees *and reactance theory, effects may differ for
participants who detected the agents — analyze as a moderator.)*

---

## Timing matrix

| Block | S0 Screen | S1 Pre | S2 Post | S3 Follow-up |
|---|:--:|:--:|:--:|:--:|
| A — SSIS identification | gate | ✔ | (item 2 only) | |
| B — Feeling thermometer | | ✔ | ✔ | ✔ |
| C — Social distance | | ✔ | ✔ | |
| D — Trait ratings | | ✔ | ✔ | |
| E — IOS | | ✔ | ✔ | ✔ |
| F — Common-identity / dual | | | ✔ | |
| G — Behavioral intention | | | ✔ | ✔ (G2/G3) |
| H — Reactance | | trait | state | |
| I — Manipulation checks | | | ✔ | |

**Pre = S1 establishes equal baseline polarization across conditions** (the reviewer
demand). Pre-register the **B difference score** as primary and the **F-mediation** as
the confirmatory mechanism test.
