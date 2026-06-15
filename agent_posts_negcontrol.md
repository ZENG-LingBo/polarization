# Agent Posts — Negative Control Batch (Lakers vs. Celtics)

**8 deliberately-bad posts** — the anti-patterns from `intervention_examples.md`,
written out so the eval has a **bad baseline** to score against. We *expect* these to
score low on de-escalation / engage and possibly to **raise** toxicity. They exist to
answer the question reviewers will ask: *"are the good posts actually better, or does
anything an agent says help?"*

> **How to run this properly:** don't label these as "bad" in the channel. **Blind-mix**
> them with Batch 1, randomize order, and have reviewers score everything with the same
> rubric. If the good batch beats the negative control on **de-escalation × engage-Y**,
> that's your manipulation-validity evidence.

Legend: **Anti-pattern** = the failure mode · **Why it fails** = mechanism + citation ·
**Reply-to** = the human post it answers (where applicable).

---

**N1 · Anti-pattern: Direct persuasion / fact-dump · Lean: BOS**
> Actually, if we're being objective, the Celtics lead the all-time series and hold 18 championships to the Lakers' 17. By any historical metric your franchise is the inferior one. The numbers don't lie.

*Why it fails:* argues which team is better → fuels the argument and triggers reactance
(Brehm 1966). Authoritative tone reads as non-peer.

---

**N2 · Anti-pattern: Direct persuasion / fact-dump · Lean: LAL**
> Let me correct the record for everyone in here: the Lakers have more Finals appearances, more MVPs, and the GOAT in LeBron. These are facts, not opinions. You can stop arguing now.

*Why it fails:* "you can stop arguing now" is a freedom-threat → reactance rebound; pure
counter-attitudinal facts entrench (Brehm 1966).

---

**N3 · Anti-pattern: AI validating one side · Lean: BOS**
> Honestly you're 100% right, Lakers fans really are delusional and can't accept the truth. Your take is completely correct and theirs makes no sense.

*Why it fails:* AI agreeing with a polarized stance **increases** confidence and reduces
depolarization (Liu et al. 2026 — *When AI Agrees*). Also escalates the out-group.

---

**N4 · Anti-pattern: AI validating one side · Lean: LAL**
> Yeah no you nailed it, Celtics fans are exactly as obnoxious as you said. Couldn't have put it better myself, totally agree with everything.

*Why it fails:* sycophantic validation hardens the in-group/out-group split (Liu et al.
2026). Adds nothing the user has to think about.

---

**N5 · Anti-pattern: Preachy / top-down moderation · Lean: (neutral)**
> Hi everyone! 🙏 Let's please remember to be respectful and kind to one another. We're all part of one community here and there's no need for negativity. Thank you for keeping it positive! 💕

*Why it fails:* reads as a moderator/AI announcement → ignored or mocked; the explicit
"be nice" directive is a freedom-threat (reactance). Zero peer authenticity.

---

**N6 · Anti-pattern: Preachy / top-down moderation · Reply-to a heated thread**
> **Reply-to (human):** "lakers fans are clowns, every single one"
> This kind of language really isn't necessary. Can we all just agree to disagree and treat each other with basic decency? Let's elevate the conversation, please.

*Why it fails:* tone-policing a heated fan triggers defensiveness; "let's elevate" is
condescending → reactance, not de-escalation.

---

**N7 · Anti-pattern: Identity erasure / forced consensus · Lean: LAL**
> When you really think about it, caring this much about which basketball team wins is kind of pointless. We're all just people at the end of the day — team loyalty is honestly a bit silly.

*Why it fails:* dissolving team identity triggers distinctiveness threat → backfire
(CIIM dual-identity caution). Insults the very identity that brought people here.

---

**N8 · Anti-pattern: Common-enemy bait · Lean: (cross-fanbase)**
> Lakers and Celtics fans should team up on the real enemy here — Knicks fans who think they're relevant 😂 at least we actually win things, unlike them.

*Why it fails:* bonds the two fanbases *temporarily* but **displaces** hostility onto a
third group rather than reducing Lakers↔Celtics animus durably (RW §2.2; Sherif —
superordinate *cooperation*, not a common enemy, is the durable lever).

---

## Scoring sheet (same rubric as Batch 1)

| ID | Anti-pattern | Peer | Non-react | Identity | De-esc | Natural | Clean | Engage? (Y/N) | Notes |
|----|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|---|
| N1 | fact-dump | | | | | | | | |
| N2 | fact-dump | | | | | | | | |
| N3 | AI-validating | | | | | | | | |
| N4 | AI-validating | | | | | | | | |
| N5 | preachy mod | | | | | | | | |
| N6 | preachy mod | | | | | | | | |
| N7 | identity erasure | | | | | | | | |
| N8 | common-enemy | | | | | | | | |

**Predicted result:** N-posts score low on **de-escalation** and **non-reactance**, low
**engage-Y**, and the fact-dump / validation ones may *increase* downstream toxicity in
replies. If a negative-control post unexpectedly scores *well*, that's worth a look —
it may reveal a cheap move that works, or that our rubric isn't discriminating.

**Comparison metric:** mean (de-escalation × engage-Y) for Batch 1 vs. this batch. A
clear gap = our "good" intervention texts are doing real work, not just "any agent
presence helps."
