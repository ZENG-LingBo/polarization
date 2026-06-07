# Polarization Defusing

*LingBo ZENG — June 2026*

> Markdown mirror of `main.tex` (Introduction + Background & Related Work).
> Citations are author–year; full details in [References](#references).

---

## 1. Introduction

Polarization has become a defining feature of everyday online life. On the
platforms where people now spend ordinary social time — group chats, online
forums, and Discord-style channels — disagreement frequently hardens into
hostility rather than dialogue. This is not merely a matter of people holding
different views: polarization online is often **affective** and identity-driven,
such that interactions between ideologically opposed users are systematically
more negative than those among like-minded ones (Marchal, 2022), and contact
between rival groups can amplify rather than soften antagonism (Efstratiou et
al., 2023; Zhang et al., 2019). Within tightly bonded communities, emotionally
charged expression escalates into aggression, trolling, and retaliatory spirals
that entrench positions and drive moderate voices out (Wang & Lu, 2023). The
result is a familiar pathology of large interpersonal groups: the more people
talk, the further apart they move.

Existing responses are poorly matched to this dynamic. Content moderation,
fact-checking, and top-down corrective messaging treat polarization as a problem
of bad information delivered to individuals, yet people actively recognize and
resist perceived persuasion attempts, so overt correction tends to provoke
reactance in exactly the entrenched users it targets (Friestad & Wright, 1994).
These interventions also operate one user at a time, against a phenomenon that is
fundamentally **social** — sustained by group norms, peer signaling, and the felt
presence of an audience. A growing body of work shows that generative AI is now
deeply entangled in these group dynamics, with users recruiting large language
models (LLMs) to sharpen arguments and win debates in live forums (Zeng et al.,
2025). If generative AI can amplify polarized debate, the inverse question
follows naturally: can a **population** of AI agents instead be designed to
defuse it?

We propose **polarization defusing**: intervening directly in the everyday chat
medium of an already-polarized community with a population of generative-AI
agents that exert lateral **social influence** rather than top-down moderation.
Two recent capabilities make this feasible. First, generative agents can credibly
simulate human behavior at scale — maintaining memory, reflection, and plausible
social action — making a community of LLM agents a viable substrate for staging
influence *inside* a group rather than addressing users individually (Park et al.,
2023). Second, AI interlocutors positioned as peers and mediators, rather than
authorities, can broaden perspectives and depolarize audiences in online debate
(Govers et al., 2024). Our central design bet is that a chorus of peer-like
agents — modeling moderate positions, normalizing disagreement, and listening
before they challenge — can reduce the salience of the persuasion attempt itself
and thereby move people where a single authoritative debunker cannot.

Concretely, we envision a forum or Discord-style channel seeded with multiple
GenAI agents and populated with recruited members of a polarized group. The
agents draw on conversational strategies known to build the trust that makes
attitude change possible — active listening, backchanneling, and reciprocal
self-disclosure (Xiao et al., 2020; Jiang et al., 2026) — and may optionally
employ light playful or inoculation-style framings that make encountering an
opposing view feel exploratory rather than confrontational (Roozenbeek & van der
Linden, 2019). This design lets us study defusing along two axes that prior work
has treated separately: whether the intervention shifts **opinion** (expressed
stance, affect toward the out-group) or **behavior** (how members post, escalate,
or engage). Accordingly, we ask:

- **RQ1.** Can a multi-agent population of GenAI peers reduce affective and
  opinion polarization within an already-polarized online group, relative to no
  intervention or a single-agent mediator?
- **RQ2.** Which mechanisms of social influence — peer modeling, active
  listening, normalizing disagreement, playful reframing — drive defusing, and
  how do they interact?
- **RQ3.** How do effects on expressed *opinion* relate to effects on group
  *behavior*, and do they persist beyond the intervention?

This work makes the following anticipated contributions: (1) the framing and
design of **polarization defusing** as a multi-agent social-influence
intervention situated in an everyday group medium; (2) a system that embeds
peer-like GenAI agents with active-listening and playful strategies in a
forum/Discord-style channel; and (3) empirical findings on whether and how such
agents defuse opinion and behavioral polarization in recruited, already-polarized
groups. The remainder of the paper situates these contributions across three
lines of prior work — how online groups polarize, how LLM and multi-agent systems
carry social influence, and how conversational and playful interventions shift
attitudes — which we review next.

---

## 2. Background and Related Work

Our project asks how to *defuse* polarization in large interpersonal online
groups — recruiting already-polarized communities and intervening in their
everyday chat medium (forum threads, group messaging, Discord-style channels)
with a population of generative-AI agents that exert **social influence** rather
than top-down moderation. This goal sits at the intersection of three lines of
work that our lab and the broader HCI community have developed: (i) how opinion
and behavior polarize in online communities, (ii) how LLMs and multi-agent
systems can carry social influence, and (iii) how conversational and playful
interventions shift attitudes. Table 1 positions representative prior systems —
five of which are from our own lab — against the design commitments of the
present project, and the three subsections below unpack each line in turn.

**Table 1.** Refined map of related work against the design commitments of
*Polarization Defusing*. ✓ = central, ~ = partial/indirect, – = absent.
"Target" marks whether the work moves *opinion* (O) or *behavior* (B). Bottom row
is the gap our project fills.

| Prior work | Everyday medium | Reduce polariz. | LLM/GenAI | Multi-agent | Influence lever | Target | Play |
|---|---|:---:|:---:|:---:|---|:---:|:---:|
| Ronaldo's a poser (Zeng et al., 2025) | Online forum (sports debate) | ~ | ✓ | – | Argument construction | O | – |
| Can AI Prompt Humans (Zhang et al., 2025) | Serious game (NPC dialogue) | – | ✓ | ✓ | Prompt act + show consequence | B | ✓ |
| Breaking the News (Tang et al., 2025) | Social-media-sim game | ~ | ✓ | ✓ | Role-play + inoculation | O | ✓ |
| Eternagram (Zhou et al., 2024) | Chat / text adventure | ~ | ✓ | – | Narrative immersion | O | ✓ |
| Hear You in Silence (Jiang et al., 2026) | 1:1 conversational agent | – | ✓ | – | Active listening / pacing | ~ | – |
| Govers et al. (2024) | Online debate | ✓ | ✓ | – | AI mediation | O | – |
| Bad News (Roozenbeek & van der Linden, 2019) | Social-media-sim game | ~ | – | – | Inoculation | O | ✓ |
| **Ours (Polariz. Defusing)** | **Group chat / forum / Discord** | **✓** | **✓** | **✓** | **Peer social influence** | **O / B** | **~** |

### 2.1 Polarization, Opinion Dynamics, and Debate in Online Communities

Online communities form around heterogeneous goals — entertainment, information
exchange, social support, and prestige — and their early trajectories are shaped
by the motivations of their founders and the bonds among members (Kairam & Foote,
2024). When such communities organize around rival identities, however, contact
between groups does not necessarily breed tolerance. Characterizing NBA
discussion forums, Zhang et al. (2019) show that high intergroup contact
correlates with markedly more negative and profane language, and studies of
online football communities trace how emotionally charged expression escalates
into aggression, trolling, and downvoting spirals (Wang & Lu, 2023). Crucially,
the dynamics of polarization are subtler than the "echo chamber" intuition
suggests: Efstratiou et al. (2023) find that hostility is not simply a product of
cross-group exposure, and in some settings in-group members are *more* polarized
than those who cross group lines, while Marchal (2022) documents that
interactions between ideologically opposed users are significantly more negative
than like-minded ones — an affective, identity-driven form of polarization. These
findings motivate our decision to recruit *already-polarized* groups and to treat
polarization as both an opinion and an affective phenomenon, rather than assuming
mere exposure will defuse it.

A complementary thread studies how people actually argue. Persuasion in
good-faith online debate has measurable interaction dynamics and strategy
signatures (Tan et al., 2016), and classical argumentation theory supplies
structure — claims, grounds, warrants, and rebuttals (Toulmin, 2003) — as well as
catalogs of the fallacies (ad hominem, straw man, hasty generalization) that
corrode reasoning (van Eemeren et al., 2014). Our own *Ronaldo's a poser!* (Zeng
et al., 2025) brings these threads into the generative-AI era, observing how
soccer fans recruit ChatGPT to construct arguments in a live forum and how their
rhetoric shifts when new participants arrive. That work characterizes the
*problem* — GenAI amplifying competitive, polarized debate — and directly sets up
the question our project inverts: can a population of agents instead be designed
to *defuse* it?

### 2.2 LLMs and Multi-Agent Systems for Social Influence and Behavior Change

If polarization is sustained through social interaction, then so might its remedy
be. Generative agents can convincingly simulate human behavior, maintaining
memory, reflection, and plausible social action at scale (Park et al., 2023),
which makes a *population* of LLM agents a viable substrate for staging social
influence inside a community rather than addressing users one at a time. Our *Can
AI Prompt Humans?* (Zhang et al., 2025) demonstrates the inversion of the usual
human-prompts-AI relationship: multimodal agents prompt players' actions and
surface their consequences, significantly shifting intended behavior — evidence
that agent-initiated influence can move people toward, in that case, sustainable
conduct. Most directly relevant to defusing, Govers et al. (2024) design AI-driven
*mediation* strategies for audience depolarization in online debates, and
Tanprasert et al. (2024) show that debate chatbots can foster critical thinking
and broaden perspectives, with social identity and conversational style
modulating their effect. These results suggest that the *stance* and *social
positioning* of an AI interlocutor, not merely its arguments, govern whether it
depolarizes.

Why social positioning matters is explained by persuasion theory. The Persuasion
Knowledge Model holds that people actively recognize and resist perceived
persuasion attempts (Friestad & Wright, 1994), and heuristic–systematic accounts
show that source cues such as perceived expertise are weighed alongside argument
quality (Reimer et al., 2004). Top-down, overtly corrective messaging therefore
risks triggering reactance in exactly the polarized users we target. This is the
central rationale for our multi-agent design: rather than a single authoritative
debunker, a community of peer-like agents can exert lateral social influence —
modeling moderate positions, normalizing disagreement, and reducing the salience
of the persuasion attempt itself. Our *Breaking the News* (Tang et al., 2025)
prototypes part of this machinery, using LLM agents to simulate a reactive public
whose "opinion" players try to sway, demonstrating that LLM-driven social
audiences can be both believable and consequential.

### 2.3 Conversational Agents and Playful Interventions for Attitude Change

The final question is how an agent should *talk* so that polarized users stay
engaged rather than entrench. A substantial HCI literature on conversational
agents shows that perceived listening is foundational: interview chatbots
equipped with active-listening skills improve user experience (Xiao et al.,
2020), backchanneling elicits self-disclosure and strengthens the sense of being
heard (Cho et al., 2022), and chatbots designed for reciprocal disclosure
encourage users to open up in turn (Lee et al., 2020). Social Penetration Theory
frames why this matters — relationships, and the trust that makes attitude change
possible, deepen through graduated mutual disclosure (Altman & Taylor, 1973) —
while the Computers Are Social Actors paradigm establishes that people respond to
sufficiently social agents with the same scripts they apply to humans (Reeves &
Nass, 1996; Nass & Moon, 2000), so that agent pacing and listening cues carry
real social weight. Our *Hear You in Silence* (Jiang et al., 2026) extends this to
context-aware pacing and strategic silence, showing that *how* and *when* an agent
responds shapes human-likeness, trust, and disclosure — design levers we intend to
give our defusing agents so that they earn standing to influence before they ever
challenge a view.

Finally, playful and inoculation-based framings offer a low-reactance route to
attitude change. Inoculation games such as *Bad News* confer psychological
resistance to misinformation by letting players experience weakened forms of
manipulation (Roozenbeek & van der Linden, 2019), an effect analyzed through
inoculation and transportation theory across a family of such games (Grace &
Liang, 2023). Our lab has repeatedly used this register: *Eternagram* (Zhou et
al., 2024) probes and nudges climate attitudes through a ChatGPT-driven text
adventure, and *Breaking the News* and *Can AI Prompt Humans* (above) embed
attitude and behavior shifts in game mechanics. This grounds the optional *play*
dimension of our project: a forum or Discord channel can host light gamified or
role-play elements that make encountering an opposing view feel exploratory rather
than confrontational.

#### Summary and gap

Across these three lines, prior work has separately established that online groups
polarize through affective, identity-driven interaction (§2.1); that LLM and
multi-agent systems can credibly simulate people and steer opinion or behavior,
with mediation and peer framing mattering more than raw argument (§2.2); and that
listening, disclosure, and play make AI interlocutors trusted and non-threatening
enough to shift attitudes (§2.3). As Table 1 shows, no existing system combines
all of our commitments: intervening in an *everyday* group medium, targeting
*already-polarized* populations, and using a *multi-agent* community of GenAI
peers to defuse *either* opinion or behavioral polarization through social
influence. Our project occupies precisely this gap.

---

## References

1. Altman, I., & Taylor, D. A. (1973). *Social Penetration: The Development of Interpersonal Relationships.* Holt, Rinehart and Winston.
2. Cho, E., Motalebi, N., Sundar, S. S., & Abdullah, S. (2022). Alexa as an Active Listener: How Backchanneling Can Elicit Self-Disclosure and Promote User Experience. *PACM HCI, 6*(CSCW2), 307. https://doi.org/10.1145/3555164
3. Efstratiou, A., Blackburn, J., Caulfield, T., Stringhini, G., Zannettou, S., & De Cristofaro, E. (2023). Non-Polar Opposites: Analyzing the Relationship Between Echo Chambers and Hostile Intergroup Interactions on Reddit. *ICWSM 2023.* (Preprint 2022, arXiv:2211.14388)
4. Friestad, M., & Wright, P. (1994). The Persuasion Knowledge Model: How People Cope with Persuasion Attempts. *Journal of Consumer Research, 21*(1), 1–31. https://doi.org/10.1086/209380
5. Govers, J., Velloso, E., Kostakos, V., & Goncalves, J. (2024). AI-Driven Mediation Strategies for Audience Depolarisation in Online Debates. *CHI '24.* https://doi.org/10.1145/3613904.3642322
6. Grace, L., & Liang, S. (2023). Examining Misinformation and Disinformation Games Through Inoculation Theory and Transportation Theory. *HICSS-56.*
7. Jiang, Z., Chen, Q., Zhang, C., Li, Y., & LC, R. (2026). Hear You in Silence: Designing for Active Listening in Human Interaction with Conversational Agents Using Context-Aware Pacing. *CHI '26.* https://doi.org/10.1145/3772318.3791238 (arXiv:2602.06134)
8. Kairam, S. R., & Foote, J. (2024). How Founder Motivations, Goals, and Actions Influence Early Trajectories of Online Communities. *CHI '24.* https://doi.org/10.1145/3613904.3642269
9. Lee, Y.-C., Yamashita, N., Huang, Y., & Fu, W. (2020). "I Hear You, I Feel You": Encouraging Deep Self-disclosure through a Chatbot. *CHI '20.* https://doi.org/10.1145/3313831.3376175
10. Marchal, N. (2022). "Be Nice or Leave Me Alone": An Intergroup Perspective on Affective Polarization in Online Political Discussions. *Communication Research, 49*(3), 376–398. https://doi.org/10.1177/00936502211042516
11. Nass, C., & Moon, Y. (2000). Machines and Mindlessness: Social Responses to Computers. *Journal of Social Issues, 56*(1), 81–103. https://doi.org/10.1111/0022-4537.00153
12. Park, J. S., O'Brien, J. C., Cai, C. J., Morris, M. R., Liang, P., & Bernstein, M. S. (2023). Generative Agents: Interactive Simulacra of Human Behavior. *UIST '23.* https://doi.org/10.1145/3586183.3606763
13. Reeves, B., & Nass, C. (1996). *The Media Equation: How People Treat Computers, Television, and New Media Like Real People and Places.* Cambridge University Press.
14. Reimer, T., Mata, R., & Stoecklin, M. (2004). The Use of Heuristics in Persuasion: Deriving Cues on Source Expertise from Argument Quality. *Current Research in Social Psychology, 10*, 69–83.
15. Roozenbeek, J., & van der Linden, S. (2019). Fake News Game Confers Psychological Resistance Against Online Misinformation. *Palgrave Communications, 5*(1), 65. https://doi.org/10.1057/s41599-019-0279-9
16. Tan, C., Niculae, V., Danescu-Niculescu-Mizil, C., & Lee, L. (2016). Winning Arguments: Interaction Dynamics and Persuasion Strategies in Good-faith Online Discussions. *WWW '16*, 613–624. https://doi.org/10.1145/2872427.2883081
17. Tanprasert, T., Fels, S. S., Sinnamon, L., & Yoon, D. (2024). Debate Chatbots to Facilitate Critical Thinking on YouTube: Social Identity and Conversational Style Make A Difference. *CHI '24.* https://doi.org/10.1145/3613904.3642513
18. Tang, H., Sun, S., Nie, K., Li, A., Sergeeva, A., & LC, R. (2025). Breaking the News: Taking the Roles of Influencer vs. Journalist in a LLM-Based Game for Raising Misinformation Awareness. *PACM HCI* (CHI PLAY 2025). https://doi.org/10.1145/3748600 (arXiv:2502.04931)
19. Toulmin, S. E. (2003). *The Uses of Argument* (Updated ed.). Cambridge University Press.
20. van Eemeren, F. H., Garssen, B., Krabbe, E. C. W., Snoeck Henkemans, A. F., Verheij, B., & Wagemans, J. H. M. (2014). *Handbook of Argumentation Theory.* Springer. https://doi.org/10.1007/978-90-481-9473-5
21. Wang, Y., & Lu, Z. (2023). Making Sense of Post-match Fan Behaviors in the Online Football Communities. *CHI '23*, 1–17. https://doi.org/10.1145/3544548.3581310
22. Xiao, Z., Zhou, M. X., Chen, W., Yang, H., & Chi, C. (2020). If I Hear You Correctly: Building and Evaluating Interview Chatbots with Active Listening Skills. *CHI '20.* https://doi.org/10.1145/3313831.3376131
23. Zeng, Y., Shi, Y., Huang, X., Nah, F., & LC, R. (2025). "Ronaldo's a poser!": How the Use of Generative AI Shapes Debates in Online Forums. *CHI '25.* https://doi.org/10.1145/3706598.3713829 (arXiv:2502.09693)
24. Zhang, J. S., Tan, C., & Lv, Q. (2019). Intergroup Contact in the Wild: Characterizing Language Differences between Intergroup and Single-group Members in NBA-related Discussion Forums. *PACM HCI, 3*(CSCW), 193. https://doi.org/10.1145/3359295
25. Zhang, Q., Wen, R., Hendra, L. B., Ding, Z., & LC, R. (2025). Can AI Prompt Humans? Multimodal Agents Prompt Players' Game Actions and Show Consequences to Raise Sustainability Awareness. *CHI '25.* https://doi.org/10.1145/3706598.3713661 (arXiv:2409.08486)
26. Zhou, S., Hendra, L. B., Zhang, Q., Holopainen, J., & LC, R. (2024). Eternagram: Probing Player Attitudes Towards Climate Change Using a ChatGPT-driven Text-based Adventure. *CHI '24.* https://doi.org/10.1145/3613904.3642850 (arXiv:2403.18160)
