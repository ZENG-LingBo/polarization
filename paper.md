# Polarization Defusing

*LingBo ZENG — June 2026*

> Markdown mirror of `main.tex` (Introduction + Background & Related Work).
> **At this stage the related work cites only papers from Ray LC's lab.**
> Citations are author–year; full details in [References](#references).

---

## 1. Introduction

Polarization has become a defining feature of everyday online life. On the
platforms where people now spend ordinary social time — group chats, online
forums, and Discord-style channels — disagreement frequently hardens into
hostility rather than dialogue. Our own studies of these media show how this
unfolds: in online forums, fans debating rival figures recruit generative AI to
sharpen their arguments, and their rhetoric shifts as opposing newcomers arrive
(Zeng et al., 2025); on everyday social platforms, people channel contested or
stigmatized stances through emotionally charged personal narrative and humor,
whether expressing opinion and emotion about climate change in TikTok videos
(Zhang et al., 2026a) or building community around ADHD through memes and comments
on Instagram (Zhang et al., 2026b). Such expression is bound up with identity, as
our work on how online-dating users craft profiles for an imagined audience
illustrates (Zhang et al., 2025a). The recurring pattern is a pathology of large
interpersonal groups: opinion is voiced in affective, identity-laden ways, and the
more people talk past one another, the further apart they move.

Existing responses are poorly matched to this dynamic. Content moderation,
fact-checking, and top-down corrective messaging treat polarization as a problem
of bad information delivered to individuals, yet overt correction tends to provoke
reactance in exactly the entrenched users it targets. These interventions also
operate one user at a time, against a phenomenon that is fundamentally **social** —
sustained by group norms, peer signaling, and the felt presence of an audience. If
generative AI can amplify polarized debate (Zeng et al., 2025), the inverse
question follows naturally: can a **population** of AI agents instead be designed
to defuse it?

We propose **polarization defusing**: intervening directly in the everyday chat
medium of an already-polarized community with a population of generative-AI agents
that exert lateral **social influence** rather than top-down moderation. Our prior
systems supply the building blocks. *Can AI Prompt Humans?* (Zhang et al., 2025b)
shows that multimodal agents can prompt people's actions and shift their behavior,
inverting the usual human-prompts-AI relationship and establishing that a
population of agents can *initiate* influence. *Breaking the News* (Tang et al.,
2025) shows that LLM agents can simulate a reactive public whose opinion shifts
believably — the machinery needed to model peer reaction at scale. Our central
design bet is that a chorus of peer-like agents — modeling moderate positions,
normalizing disagreement, and listening before they challenge — can reduce the
salience of the persuasion attempt itself and thereby move people where a single
authoritative debunker cannot.

Concretely, we envision a forum or Discord-style channel seeded with multiple
GenAI agents and populated with recruited members of a polarized group. The agents
draw on conversational strategies our group has shown to build trust and elicit
disclosure — active listening realized through context-aware pacing and strategic
silence (Jiang et al., 2026) — and may optionally employ playful or
perspective-taking framings, in the register of our LLM-driven games for shifting
attitudes, that make encountering an opposing view feel exploratory rather than
confrontational (Zhou et al., 2024; Du et al., 2025). This design lets us study
defusing along two axes that prior work has treated separately: whether the
intervention shifts **opinion** (expressed stance, affect toward the out-group) or
**behavior** (how members post, escalate, or engage). Accordingly, we ask:

- **RQ1.** Can a multi-agent population of GenAI peers reduce affective and opinion
  polarization within an already-polarized online group, relative to no
  intervention or a single-agent mediator?
- **RQ2.** Which mechanisms of social influence — peer modeling, active listening,
  normalizing disagreement, playful reframing — drive defusing, and how do they
  interact?
- **RQ3.** How do effects on expressed *opinion* relate to effects on group
  *behavior*, and do they persist beyond the intervention?

This work makes the following anticipated contributions: (1) the framing and
design of **polarization defusing** as a multi-agent social-influence intervention
situated in an everyday group medium; (2) a system that embeds peer-like GenAI
agents with active-listening and playful strategies in a forum/Discord-style
channel; and (3) empirical findings on whether and how such agents defuse opinion
and behavioral polarization in recruited, already-polarized groups. The remainder
of the paper situates these contributions against our group's prior work along
three lines — how people express opinion and form communities on everyday
platforms, how our LLM and multi-agent systems carry social influence, and how our
conversational and playful designs shift attitudes — which we review next.

---

## 2. Background and Related Work

Our project asks how to *defuse* polarization in large interpersonal online
groups — recruiting already-polarized communities and intervening in their
everyday chat medium (forum threads, group messaging, Discord-style channels) with
a population of generative-AI agents that exert **social influence** rather than
top-down moderation. Rather than survey the field broadly, we position this
project against our group's own prior work, which has independently developed each
ingredient the project must combine: (i) studies of how people express opinion and
form communities on everyday online platforms, (ii) systems in which LLM and
multi-agent technologies steer opinion or behavior, and (iii) conversational and
playful designs that shift attitudes. Table 1 maps representative lab systems
against the design commitments of the present project, and the three subsections
below unpack each line. Read together, they show that while our group has built
every piece, no prior project has assembled them into a multi-agent intervention
for defusing polarization — precisely the gap we target.

**Table 1.** Map of prior **lab** work against the design commitments of
*Polarization Defusing*. ✓ = central, ~ = partial/indirect, – = absent. "Target"
marks whether the work concerns *opinion* (O) or *behavior* (B). Bottom row is the
gap our project fills.

| Lab work | Everyday medium | Reduce polariz. | LLM/GenAI | Multi-agent | Influence lever | Target | Play |
|---|---|:---:|:---:|:---:|---|:---:|:---:|
| Ronaldo's a poser (Zeng et al., 2025) | Online forum (sports debate) | ~ | ✓ | – | Argument construction | O | – |
| Climate-change TikTok (Zhang et al., 2026a) | Social media (short video) | – | – | – | Personal narrative / emotion | O | – |
| ADHD on Instagram (Zhang et al., 2026b) | Social media (memes/comments) | – | – | – | Community engagement / humor | O | ~ |
| Online dating profiles (Zhang et al., 2025a) | Online dating platform | – | – | – | Self-presentation | O | – |
| Can AI Prompt Humans (Zhang et al., 2025b) | Serious game (NPC dialogue) | – | ✓ | ✓ | Prompt act + show consequence | B | ✓ |
| Breaking the News (Tang et al., 2025) | Social-media-sim game | ~ | ✓ | ✓ | Role-play + inoculation | O | ✓ |
| Eternagram (Zhou et al., 2024) | Chat / text adventure | ~ | ✓ | – | Narrative immersion | O | ✓ |
| Designing for the Invisible (Du et al., 2025) | Serious game | – | ✓ | – | Empathy / perspective-taking | O | ✓ |
| Hear You in Silence (Jiang et al., 2026) | 1:1 conversational agent | – | ✓ | – | Active listening / pacing | ~ | – |
| **Ours (Polariz. Defusing)** | **Group chat / forum / Discord** | **✓** | **✓** | **✓** | **Peer social influence** | **O / B** | **~** |

### 2.1 Opinion Expression and Community Dynamics on Everyday Platforms

Our group has studied how people voice opinions and coalesce into groups across
the very media our project targets. Most directly, *Ronaldo's a poser!* (Zeng et
al., 2025) observes soccer fans debating in a live online forum, showing how
participants recruit generative AI to construct arguments and how their rhetoric
shifts as new, opposing members arrive — a close model of the competitive,
identity-driven dynamics that harden into polarization. Complementing this, work
on how creators express emotions, opinions, and data about climate change in
TikTok short videos (Zhang et al., 2026a) and on how an ADHD community engages
through memes and comments on Instagram (Zhang et al., 2026b) characterizes opinion
and affective expression in everyday social media, including the humor and personal
narrative through which contested or stigmatized stances circulate. At the level of
identity, our study of how online-dating users construct profiles for effective
self-presentation (Zhang et al., 2025a) shows how people perform and manage
identity for an imagined audience — an antecedent of the in-group signaling that
fuels polarization. Together these studies establish the *problem space*: large
groups on everyday platforms express opinion in emotionally charged, identity-laden
ways, motivating our choice to recruit already-polarized communities and to treat
polarization as both an opinion and an affective phenomenon. What none of this work
attempts is to *intervene* in those dynamics, which is the project's aim.

### 2.2 LLM and Multi-Agent Systems for Social Influence and Behavior Change

A second strand of our work builds AI systems that actively steer opinion or
behavior. *Can AI Prompt Humans?* (Zhang et al., 2025b) inverts the usual
human-prompts-AI relationship: multimodal agents prompt players' actions and
surface their consequences, significantly shifting intended behavior — direct
evidence that a *population* of agents can initiate influence rather than merely
respond, and the closest precedent for our multi-agent design. *Breaking the News*
(Tang et al., 2025) uses LLM agents to simulate a reactive public whose "opinion"
players try to sway, demonstrating that LLM-driven social audiences can be
believable and consequential — the machinery a defusing intervention would need to
model peer reaction at scale. At a more foundational level, our analysis of moral
responses in large language models (Hui et al., 2025) quantifies how LLMs encode
attitudes and value judgments, informing both how agents might be steered to model
moderate positions and where their biases could distort a depolarization attempt.
These projects show our group can make GenAI agents that influence people and that
simulate social others, but they pursue sustainability or misinformation goals, not
the reduction of interpersonal polarization, and only *Can AI Prompt Humans* uses
more than one agent.

### 2.3 Conversational Agents and Playful Interventions for Attitude Change

The third strand concerns how an agent should engage so that polarized users stay
in dialogue rather than entrench. *Hear You in Silence* (Jiang et al., 2026)
designs conversational agents that perform active listening through context-aware
pacing and strategic silence, showing that *how* and *when* an agent responds
shapes human-likeness, trust, and self-disclosure — the very levers a defusing
agent needs to earn standing before it ever challenges a view. On the playful side,
our group has repeatedly used games and speculative play as a low-reactance route
to attitude change: *Eternagram* (Zhou et al., 2024) probes and nudges climate
attitudes through a ChatGPT-driven text adventure; *Designing for the Invisible*
(Du et al., 2025) uses an LLM-based serious game to build empathy and
perspective-taking toward a stigmatized out-group; and *Cracking Aegis* (Fu et al.,
2025) turns adversarial role-play with an LLM into awareness change. *Bricolage*
(Agcal et al., 2025) further shows that playful, participatory speculation can align
people with a contested cause. These designs establish that our group can shift
attitudes through conversation and play — grounding the optional *play* dimension of
our project — yet each addresses a single user or a non-adversarial topic, rather
than defusing entrenched disagreement among a polarized group.

#### Summary and gap

Across these three strands, our group has separately established that people
polarize through emotionally charged, identity-driven expression on everyday
platforms (§2.1); that our LLM and multi-agent systems can steer opinion and
behavior and credibly simulate social others (§2.2); and that our conversational
and playful designs can shift attitudes while keeping users engaged (§2.3). As
Table 1 shows, no single prior project combines these commitments: intervening in
an *everyday* group medium, targeting *already-polarized* populations, and using a
*multi-agent* community of GenAI peers to defuse *either* opinion or behavioral
polarization through social influence. Our project unites these threads to occupy
precisely that gap.

---

## References

*All references are from Ray LC's lab ("Studio for Narrative Spaces").*

1. Agcal, B., Yin, Z. Y., Miller, M., & LC, R. (2025). Bricolage: Aligning with Climate Action through Playful Participatory Design in Speculative Scenarios. *International Journal of Play.* https://doi.org/10.1080/21594937.2025.2464324
2. Du, N. H., Wang, L. Z., Li, Y. R., & LC, R. (2025). Designing for the Invisible: Raising Awareness for the Experience of the Homeless in an LLM-based Serious Game. *GOODIT '25.* https://doi.org/10.1145/3748699.3749822
3. Fu, J. Y., Lu, Y. Y., Yang, Z. H., Nah, F., & LC, R. (2025). Cracking Aegis: An Adversarial LLM-based Game for Raising Awareness of Vulnerabilities in Privacy Protection. *DIS '25.* https://doi.org/10.1145/3715336.3735812
4. Hui, B. P. H., Lau, C. L., Sun, R., LC, R., Hendra, L. B., & Kogan, A. (2025). Decoding Moral Responses in AI: A Quantitative Analysis of Large Language Models. *Computers in Human Behavior.* https://www.sciencedirect.com/science/article/pii/S2451958825002696
5. Jiang, Z., Chen, Q., Zhang, C., Li, Y., & LC, R. (2026). Hear You in Silence: Designing for Active Listening in Human Interaction with Conversational Agents Using Context-Aware Pacing. *CHI '26.* https://doi.org/10.1145/3772318.3791238
6. Tang, H., Sun, S., Nie, K., Li, A., Sergeeva, A., & LC, R. (2025). Breaking the News: Taking the Roles of Influencer vs. Journalist in a LLM-Based Game for Raising Misinformation Awareness. *PACM HCI* (CHI PLAY 2025). https://doi.org/10.1145/3748600
7. Zeng, Y., Shi, Y., Huang, X., Nah, F., & LC, R. (2025). "Ronaldo's a poser!": How the Use of Generative AI Shapes Debates in Online Forums. *CHI '25.* https://doi.org/10.1145/3706598.3713829
8. Zhang, C., Huang, S. M., Wu, S. H., Chen, Y. H., & LC, R. (2026a). We are all in big trouble! Shock Emoji: Personal Narratives in Expressing Emotions, Opinions, and Data Regarding Climate Change in TikTok Short Videos. *PACM HCI* (CSCW 2026).
9. Zhang, F., Fu, J. Y., Chen, K. X., & LC, R. (2026b). Laughing Through the Struggles: Understanding ADHD Experience and Community Engagement Through Memes and Comments on Instagram. *CHI '26.* https://doi.org/10.1145/3772318.3790540
10. Zhang, F., Chen, Y., Zeng, X. K., Wang, T. Q., Ling, L., & LC, R. (2025a). An Image of Ourselves in Our Minds: How College-educated Online Dating Users Construct Profiles for Effective Self Presentation. *PACM HCI* (CSCW 2025). https://doi.org/10.1145/3710929
11. Zhang, Q., Wen, R., Hendra, L. B., Ding, Z., & LC, R. (2025b). Can AI Prompt Humans? Multimodal Agents Prompt Players' Game Actions and Show Consequences to Raise Sustainability Awareness. *CHI '25.* https://doi.org/10.1145/3706598.3713661
12. Zhou, S., Hendra, L. B., Zhang, Q., Holopainen, J., & LC, R. (2024). Eternagram: Probing Player Attitudes Towards Climate Change Using a ChatGPT-driven Text-based Adventure. *CHI '24.* https://doi.org/10.1145/3613904.3642850
