# Measurement Plan — Polarization Defusing (Lakers vs. Celtics)

**Purpose (TODO "FIRST").** Lock the measures that should *really* move under a CIIM
intervention, before we touch the intervention design. Some measures can be null —
but we need a few that will be **statistically significant**. This sheet maps each
construct to a **lit-prevalidated instrument**, the **RQ** it serves, **when** it's
collected, and the **analysis**. All instrument citations are verified (Crossref /
DBLP) and ready to drop into the `.bib`.

> Design backbone: **pre / during / post / follow-up**, between-subjects
> (control vs. intervention). The **pre** wave exists to *prove control and
> intervention groups start equally polarized* — reviewers will demand it.

**Two-RQ structure (synced with the prototype outline).** The outline now carries
**two** research questions — there is no RQ3; the former RQ3 (mediation/mechanism and
persistence) is absorbed into **RQ2**. RQ1 is descriptive interaction/process; RQ2 is
the with-vs-without-agents effect on interaction patterns and group-level affective
polarization, with **common in-group identity** measured as the mediator inside RQ2.
Any item labeled "RQ3" in an older draft now falls under RQ2.

**Model-paper anchor (the rule: adapt validated instruments, never invent).** Every
construct maps to a published, validated instrument, and the whole battery is anchored
to a directly comparable HCI study — **GuesSync!** (Rajadesingan et al., CSCW 2023),
a platform-based, pre-registered intervention that reduces affective polarization with
a **feeling-thermometer** + **willingness-to-engage** battery. We borrow those
individual-level outcomes unchanged in form (re-targeting the out-party to the rival
fanbase, and measuring warmth toward **ordinary rival fans** rather than
players/management, per Druckman & Levendusky 2019) and **add** the group-level
instruments GuesSync does not cover (common in-group identity, we/they language,
cross-group replies). Construct-by-construct grounding and the GuesSync crosswalk live
in the prototype's companion
[`MEASURES.md`](https://github.com/ZENG-LingBo/polarization-prototype/blob/master/MEASURES.md);
keep the two in sync.

---

## A. Primary outcome — Affective polarization (RQ2)

The headline DV. Affective polarization = in-group warmth − out-group animus
(Iyengar & Westwood 2015; Iyengar et al. 2019). Use **three** convergent measures so
at least one is powered to move:

| Measure | Instrument / source | What it captures | Timing | Analysis |
|---|---|---|---|---|
| **Feeling thermometer** | Iyengar, Sood & Lelkes (2012) | 0–100 warmth toward own-team vs. rival-team fans; DV = difference score | pre, post, follow-up | mixed ANOVA (group × time) |
| **Social-distance items** | Iyengar, Sood & Lelkes (2012) | comfort with rival-fan as neighbor / friend / in-law | pre, post | repeated-measures |
| **Out-group trait ratings** | Iyengar & Westwood (2015) | rate rival fans on warmth/competence/trait adjectives | pre, post | difference-in-differences |
| **Inclusion of Other in Self (IOS)** | Aron, Aron & Smollan (1992) | single-pictorial item: felt closeness/overlap with rival group | pre, post, follow-up | ordinal / t-test |

**Why these move:** CIIM predicts recategorization shrinks the in/out-group warmth
gap and raises IOS overlap. IOS is cheap, validated, and historically sensitive — a
good bet for a significant effect.

---

## B. Mechanism — Common ingroup identity & identification (RQ2 mediator)

Tests *whether the effect runs through perceived common identity* (mediation), and
controls for baseline fandom intensity.

| Measure | Instrument / source | Role | Timing |
|---|---|---|---|
| **Sport Spectator Identification Scale (SSIS)** | Wann & Branscombe (1993) | baseline strength of team identity (covariate / moderator) | pre |
| **One-group / common-identity representation** | Gaertner & Dovidio (2000) CIIM items | the proposed **mediator**: do participants now see "one group of NBA fans"? | post |
| **Dual-identity check** | adapt Gaertner & Dovidio (2000); Crisp et al. (2006) | did we add a superordinate identity *without erasing* team identity? (guards against distinctiveness-threat backfire; multicomponent identity per Leach et al. 2008) | post |

**Analysis:** mediation (intervention → common-identity representation → Δ affective
polarization), e.g., bootstrapped indirect effect. SSIS as covariate/moderator —
expect stronger reactance in high-identifiers.

---

## C. Behavioral & process measures (RQ1) — from the platform logs

Measured *in vivo* during the session; no self-report needed, so high power and hard
to fake.

| Measure | Instrument / method | Captures | Timing |
|---|---|---|---|
| **Automated toxicity** | Perspective API (Lees et al. 2022) | per-message toxicity / insult / threat scores | continuous (during) |
| **Incivility coding** | Coe, Kenski & Rains (2014) coding scheme | human-coded incivility categories (name-calling, aspersion, etc.) | during (sample) |
| **Linguistic markers (LIWC)** | Tausczik & Pennebaker (2010) | pronouns (we/they), affect, anger, cognitive words | during, pre/post text |
| **Behavioral engagement** | platform analytics | cross-group replies, up/down-votes, pile-on size, who-talks share | continuous |

**Key DVs:** (1) toxicity trajectory over the session; (2) **rate of cross-group
(vs. in-group) replies** — a direct behavioral signature of recategorization;
(3) **we/they pronoun ratio** — LIWC's most theory-aligned marker of common identity.

---

## D. Behavioral intention / "voting" (RQ1 → RQ2 bridge)

Downstream behavior beyond talk — the kind reviewers find convincing.

| Measure | Source | Captures | Timing |
|---|---|---|---|
| **Resource/allocation task** | adapt Iyengar & Westwood (2015) (the scholarship/economic-game paradigm) | willingness to allocate a reward to rival-fan vs. own-fan | post |
| **Willingness to interact** | survey items | intention to join a mixed-fan group / cooperative event again | post, follow-up |
| **Cooperative-task contribution** | platform log | did they actually participate in the superordinate task (Strategy C)? | during |

---

## E. Guardrail — Reactance (so we can detect backfire)

Because overt influence can backfire (Brehm 1966; *When AI Agrees*, Liu et al. 2026),
measure reactance to confirm the *structural* approach avoided it — and to explain any
null/negative effects.

| Measure | Instrument | Timing |
|---|---|---|
| **Trait reactance** | Hong Psychological Reactance Scale (Hong & Faedda 1996) | pre (covariate) |
| **State reactance** | Dillard & Shen (2005) (anger + negative cognitions) | post |

---

## F. Qualitative (RQ1, RQ2) — why & how

- **Post-session interviews** (subset): did they *notice* the agents? did they feel
  pushed (reactance) or did the shared identity feel self-discovered? what changed
  their tone? Thematic analysis.
- Use to interpret nulls and to surface the *mechanism* narrative behind the stats.

---

## Timing matrix (what's collected when)

| Wave | Measures |
|---|---|
| **Pre** | Feeling thermometer, social distance, trait ratings, IOS, **SSIS**, trait reactance — *establishes equivalent baseline polarization across conditions* |
| **During** | Perspective API toxicity, LIWC, incivility coding, engagement logs, cooperative-task participation |
| **Post** | Feeling thermometer, social distance, trait ratings, IOS, common-identity & dual-identity items, allocation task, willingness-to-interact, state reactance |
| **Follow-up (e.g., 1–2 wks)** | Feeling thermometer, IOS, willingness-to-interact — *persistence (RQ2)* |

---

## Power / pragmatics notes

- **Best bets for significance:** IOS, feeling-thermometer difference score, and
  we/they pronoun ratio (LIWC) — all sensitive, validated, low-noise.
- **Pre-register** the primary DV (feeling-thermometer difference) and the mediation
  path; treat the rest as secondary to control false positives.
- The pilot ("control with ~20 people to get very toxic outcomes") should validate
  that Perspective API + LIWC + incivility coding **actually capture** the toxicity we
  induce *before* the main study — i.e., confirm the measures have a signal to move.
- Keep team identity salient at pre (so baseline polarization is real), then measure
  whether the intervention adds the superordinate identity on top.

---

## Verified instrument citations (ready for `.bib`)

Already in `refs.bib`: `iyengar2015fear`, `iyengar2019origins`,
`wann1993identification`, `gaertner2000reducing`, `brehm1966reactance`,
`whenaiagrees2026`, `aron1992ios`, `hong1996reactance`, `dillard2005reactance`,
`coe2014incivility`, `tausczik2010liwc`, `lees2022perspective`. **Added for the
literature-grounding / two-RQ sync:** `rajadesingan2023guessync` (model paper),
`iyengar2012affect` (thermometer + social-distance origin), `druckman2019measure`
(ordinary-member targeting), `crisp2006recategorization` and
`leach2008identification` (dual-identity / multicomponent identity).
