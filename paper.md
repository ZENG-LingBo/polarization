# Polarization Defusing — Lakers vs. Celtics

*LingBo ZENG — June 2026*

> Markdown mirror of `main.tex` (Introduction + Background & Related Work).
> Theory-driven RW in three strands: **2.1 Sociological · 2.2 Psychological · 2.3 Technical**.
> Citations are author–year; full details in [References](#references).

---

## 1. Introduction

Affective polarization — warmth toward one's in-group paired with animus toward the
out-group, largely independent of actual positional disagreement — has become a
defining feature of online life (Iyengar & Westwood, 2015; Iyengar et al., 2019). It
is fundamentally a matter of group identity rather than issue content: categorizing
people into groups is by itself enough to generate in-group favoritism and out-group
hostility (Tajfel & Turner, 1979). On the platforms where people now spend ordinary
social time — forums, group chats, and social feeds — this identity-driven antagonism
is enacted as toxic, self-reinforcing discourse. Our own study of a live fan forum
shows rivals recruiting generative AI to sharpen their attacks and escalating as
opposing newcomers arrive (Zeng et al., 2025), and synthetic social networks populated
by LLM agents reliably reproduce these polarized dynamics under controlled conditions
(Donkers & Ziegler, 2025). The recurring pattern is a pathology of large interpersonal
groups: the more rival identities talk past one another, the further apart they move.

Existing responses are poorly matched to this dynamic. Content moderation,
fact-checking, and corrective messaging treat polarization as a problem of bad
information delivered to individuals, yet overt persuasion provokes psychological
reactance — a rebound toward the very position it targets (Brehm, 1966) — and merely
increasing exposure to opposing views can *entrench* rather than soften division (Bail
et al., 2018). Recent HCI evidence sharpens the warning for AI specifically: when an AI
simply agrees with or validates a user's stance, confidence in the polarized position
*increases* and depolarization becomes less likely (Liu et al., 2026). Even the most
effective AI interventions share a deeper limitation of *level* and *standing*:
one-on-one dialogue durably shifts individual *belief* (Costello et al., 2024) and
dyadic chat assistants improve conversational *tone* (Argyle et al., 2023), while AI
that scales to groups acts as an *outsider* mediator summarizing views toward consensus
(Tessler et al., 2024) — none engages the group identity in which the animosity is
actually rooted, and an outside agent lacks the standing to redraw who counts as "us."
These interventions also operate one user at a time, against a phenomenon that is
fundamentally **social** — sustained by group identity, peer signaling, and the felt
presence of an audience. If generative AI can amplify polarized debate (Zeng et al.,
2025), the inverse question follows: can a **population** of AI agents instead be
arranged to defuse it?

We propose **polarization defusing**: a simulated social-media platform that recruits
members of an already-polarized rivalry and intervenes through a population of
generative-AI agents embedded as **in-group members** of each fandom, exerting
peer-level **social influence** rather than top-down correction. Our intervention is
**structural** rather than rhetorical, and it recategorizes *from within*. Drawing on
the Common Ingroup Identity Model (Gaertner & Dovidio, 2000) and the finding that
superordinate cooperative goals reduce intergroup conflict (Sherif et al., 1961;
Pettigrew & Tropp, 2006), we arrange the platform so that rival fans *discover* a
shared, more inclusive identity ("we are all NBA fans") through cooperative cross-group
interaction — a recategorization shown to shift even rival sports fans toward helping
one another (Levine et al., 2005). Crucially, group norms can be redrawn only by those
recognized as members (Tajfel & Turner, 1979; Turner et al., 1987): so rather than an
explicit AI or an outside mediator, multiple *undisclosed in-group* agents introduce
the superordinate identity from within, *modeling* de-escalated behavior and a dual
"team-fan-*and*-NBA-fan" identity (Crisp et al., 2006) for participants to imitate,
using low-reactance structural moves — seeding a shared cooperative task,
acknowledging-then-redirecting — rather than argument. Our prior systems supply the
building blocks: multimodal agents that prompt human action (Zhang et al., 2025b), LLM
agents that simulate a reactive public (Tang et al., 2025), and conversational agents
whose pacing and active listening earn social standing (Jiang et al., 2026).

We study the Los Angeles Lakers versus Boston Celtics rivalry: a historic,
city-and-identity-based conflict that is widely recognized across both Western and
Asian audiences, making it a tractable yet ecologically familiar model of affective
polarization. Because Social Identity Theory and the Common Ingroup Identity Model are
domain-general, an intervention that works here speaks to affective polarization more
broadly. This design lets us study defusing along two axes prior work has treated
separately: whether the intervention shifts **opinion** (expressed stance, affect
toward the out-group) or **behavior** (how members post, escalate, and engage).
Accordingly, we ask:

- **RQ1 (interaction / process).** How do participants in polarized fan groups interact
  with the embedded in-group agents on the simulated platform?
- **RQ2 (effect).** How do the embedded in-group agents affect interaction patterns and
  group-level affective polarization between the opposing fan groups?

We treat the hypothesized mechanism — a perceived common in-group identity — as a
measured mediator within RQ2 (does any reduction run through recategorization, and does
it persist?), rather than as a separate question.

This work makes the following anticipated contributions: (1) the framing and design of
**polarization defusing** as a structural, multi-agent social-influence intervention
sited in a simulated social platform; (2) a system in which *undisclosed in-group*
GenAI agents drive cooperative recategorization from within — extending depolarization
from the individual to the **group** level, and from outsider persuasion to *in-group*
recategorization; and (3) empirical findings, on the Lakers–Celtics rivalry, on whether
and how such agents defuse affective and behavioral polarization. The remainder of the paper develops three lines
of background — the sociological, psychological, and technical foundations of this
approach — which we review next.

---

## 2. Background and Related Work

Our project asks how to *defuse* affective polarization between rival fan communities —
specifically Los Angeles Lakers and Boston Celtics supporters — within a simulated
social-media platform, using a population of generative-AI agents *embedded as in-group
members* that exert peer-level **social influence** rather than top-down correction. We choose an identity-based sports
rivalry because it is a tractable, ecologically familiar instance of affective
polarization whose mechanisms are domain-general. We situate the project along three
lines — **sociological** (§2.1), **psychological** (§2.2), and **technical** (§2.3) —
and Table 1 positions representative prior *systems* against our design commitments.

**Table 1.** Representative prior systems against the design commitments of
*Polarization Defusing*. ✓ = central, ~ = partial/indirect, – = absent. "Target" marks
*opinion* (O) or *behavior* (B). Bottom row is the gap our project fills. (Foundational
theory is discussed in the prose, not tabulated.)

| Prior system | Platform / medium | Reduce polariz. | LLM/GenAI | Multi-agent | Influence lever | Target |
|---|---|:---:|:---:|:---:|---|:---:|
| Ronaldo's a poser (Zeng et al., 2025) | Live online forum (fan debate) | ~ | ✓ | – | Argument construction | O |
| Donkers & Ziegler (2025) | Synthetic LLM social network | – | ✓ | ✓ | (studies polarization) | O |
| Govers et al. (2024) | Online debate | ✓ | ✓ | – | AI mediation | O |
| Breaking the News (Tang et al., 2025) | Social-media-sim game | ~ | ✓ | ✓ | Role-play + simulated public | O |
| Can AI Prompt Humans (Zhang et al., 2025b) | Serious game (NPC dialogue) | – | ✓ | ✓ | Prompt act + show consequence | B |
| Hear You in Silence (Jiang et al., 2026) | 1:1 conversational agent | – | ✓ | – | Active listening / turn pacing | ~ |
| **Ours (Polariz. Defusing)** | **Simulated social platform** | **✓** | **✓** | **✓** | **In-group recategorization (CIIM)** | **O / B** |

### 2.1 Sociological: Polarization as a Group-Level, Identity-Driven Phenomenon

Contemporary polarization is increasingly understood as *affective* rather than merely
issue-based: people feel warmth toward their in-group and animus toward the out-group,
independent of how far apart their actual positions are (Iyengar & Westwood, 2015;
Iyengar et al., 2019). This animus is rooted in group identity. Social Identity Theory
holds that simply categorizing oneself into a group generates in-group favoritism and
out-group derogation, so conflict is driven by identity rather than tangible stakes
(Tajfel & Turner, 1979). Sports fandom is a paradigmatic case: degree of identification
with a team is a genuine social identity that structures perception and behavior (Wann &
Branscombe, 1993), which is why a historic, city-based rivalry such as Lakers versus
Celtics functions as identity-based polarization rather than a mere difference of
preference — and a cleaner model than player-versus-player disputes.

On everyday platforms, this identity-driven antagonism plays out as toxic,
self-reinforcing discourse. Our own study of a live online forum shows rival fans
recruiting generative AI to sharpen their arguments and escalating as opposing newcomers
arrive (Zeng et al., 2025), while our work on how people express contested opinions and
emotions on TikTok (Zhang et al., 2026a) and build identity-laden communities on
Instagram (Zhang et al., 2026b) and online-dating platforms (Zhang et al., 2025a)
documents the affective, performative character of online opinion expression. Critically
for our method, Donkers and Ziegler (2025) demonstrate that a *synthetic* social network
populated by LLM agents can reproduce the key dynamics of polarized discourse under
controlled, manipulable conditions — establishing both the construct validity of a
simulated platform and a methodological precedent for the environment we build.
Together these works establish the problem space: rival identities produce affective
polarization that is enacted and amplified online, motivating an intervention sited in
the medium itself.

### 2.2 Psychological: Intergroup Mechanisms and Where Intervention Cuts In

If polarization is sustained by social categorization, decades of intergroup research
specify how to loosen it. The Contact Hypothesis, confirmed across hundreds of studies,
shows that contact between groups reduces prejudice under supportive conditions
(Pettigrew & Tropp, 2006); the Robbers Cave studies show that *superordinate cooperative
goals* — tasks that require the groups to work together — reduce conflict more durably
than contact alone (Sherif et al., 1961). The Common Ingroup Identity Model (CIIM)
explains why: recategorizing former out-group members into a shared, more inclusive
in-group ("we are all NBA fans") redirects in-group favoritism toward the erstwhile
rival, reducing bias (Gaertner & Dovidio, 2000). This mechanism has direct empirical
support in our exact domain: Levine et al. (2005) found that football fans helped an
injured rival supporter far more often when a superordinate "football fan" identity,
rather than a narrow team identity, was salient. This is the theoretical core of our
design — and it carries two cautions. First, recategorization that erases subgroup
identities can trigger distinctiveness threat, so a *dual-identity* framing that
preserves team identity while adding the superordinate one is typically more robust
(Crisp et al., 2006); and a shared cooperative goal is preferable to a common *enemy*,
which tends to displace hostility rather than dissolve it.

The second caution concerns *how* — and by *whom* — an intervention is delivered.
Psychological Reactance Theory holds that perceived attempts to constrain one's freedom
— including overt persuasion — provoke resistance and a rebound toward the threatened
position (Brehm, 1966). Recent HCI evidence sharpens this for AI: when an AI simply
agrees with or validates a user's existing stance, confidence in the polarized position
*increases* and depolarization becomes less likely (Liu et al., 2026). Standing matters
as much as style: by Self-Categorization Theory, group norms can be redefined only by
those recognized as in-group members, so an *outside* agent lacks the legitimacy to
recategorize and is apt to provoke reactance (Turner et al., 1987). Heavy-handed,
content-level persuasion by an explicit or outsider LLM is therefore the wrong lever.
This motivates our commitment to *structural* intervention delivered *from within*:
arranging the platform so that participants *discover* a common identity through
cooperative cross-group interaction, with *in-group* agents shaping the social context
rather than arguing positions.

### 2.3 Technical: Multi-Agent LLM Social Influence in Simulated Platforms

LLMs can already intervene inside a conversation: one-on-one dialogue durably reduces
belief in conspiracy theories (Costello et al., 2024), and real-time chat assistants
improve the tone and perceived quality of contentious political exchanges without
shifting attitudes (Argyle et al., 2023). Two limitations recur. *Level*: these
interventions operate at the individual or dyadic level, treating depolarization as
changing what a single person thinks — they move belief or tone while leaving the group
relationship untouched, exactly as expected if animosity is rooted in group identity
rather than private belief. Even AI that scales to group deliberation positions the
system as a neutral *mediator* summarizing competing views toward consensus (Tessler et
al., 2024). *Standing*: the agent is an *outsider* — an explicit AI or third-party
mediator — and so cannot redefine who counts as "us." We instead embed multiple agents
as *in-group members* and intervene at the level of group identity, introducing a
superordinate identity from within (§2.2).

Realizing such a structural intervention requires agents that can populate and shape a
live platform. Generative agents can credibly simulate human memory, reflection, and
social action at scale (Park et al., 2023), and our own systems show this is achievable
for influence: multimodal agents can prompt people's actions and shift behavior (Zhang
et al., 2025b), and LLM agents can simulate a reactive public whose opinion moves
believably (Tang et al., 2025). AI mediators can measurably depolarize online debate,
though — consistent with the standing argument — their effect depends on social
positioning and conversational style rather than on argument alone (Govers et al.,
2024).

Our design leans on *multiple* agents as the active ingredient. Rather than a single
authoritative mediator, a population of peer-like agents can *model* de-escalated
behavior for participants to imitate — showing both sides in respectful exchange, or
enacting cross-rival harmony that establishes a descriptive norm. Agent *turn-taking*
can itself be a lever: visibly alternating, inclusive participation signals that
"everyone talks," nudging the group away from pile-on dynamics. The conversational
competencies our group has developed support this — context-aware pacing and active
listening govern when and how an agent should speak to seem human and earn standing
(Jiang et al., 2026) — as do low-reactance, playful framings of cooperative tasks, in
the register of our LLM-driven games for attitude change (Zhou et al., 2024; Du et al.,
2025). Finally, because agents will be steered to model moderate, prosocial positions,
how LLMs encode moral and attitudinal stances is a live design concern that our analysis
of model moral responses begins to map (Hui et al., 2025).

#### Summary and gap

The sociological literature establishes that rival identities produce affective
polarization enacted online (§2.1); the psychological literature specifies
recategorization toward a common in-group as a defusing mechanism — one that only
recognized in-group members have the standing to trigger — while warning that overt AI
persuasion backfires (§2.2); and the technical literature shows that prior LLM
interventions act at the individual or outsider level, even as LLM multi-agent systems
can simulate and influence social environments (§2.3). As Table 1 shows, no prior system
unites these: a *simulated social platform* that recruits an *already-polarized* rivalry
and embeds a *multi-agent* community of *undisclosed in-group* GenAI peers to defuse
affective polarization *structurally* — recategorizing from within through cooperative
tasks and behavioral modeling rather than outsider persuasion. Our project occupies
precisely this gap.

---

## References

*External theory works are verified via Crossref / DBLP / publisher. Ray LC lab papers
are marked (lab).*

1. Argyle, L. P., Busby, E. C., Bail, C. A., Gubler, J. R., Howe, T., Rytting, C., Sorensen, T., & Wingate, D. (2023). Leveraging Artificial Intelligence for Democratic Discourse: Chat Interventions Can Improve Online Political Conversations at Scale. *PNAS, 120*(41), e2311627120. https://doi.org/10.1073/pnas.2311627120
2. Bail, C. A., et al. (2018). Exposure to Opposing Views on Social Media Can Increase Political Polarization. *PNAS, 115*(37), 9216–9221. https://doi.org/10.1073/pnas.1804840115
3. Brehm, J. W. (1966). *A Theory of Psychological Reactance.* Academic Press.
4. Costello, T. H., Pennycook, G., & Rand, D. G. (2024). Durably Reducing Conspiracy Beliefs through Dialogues with AI. *Science, 385*(6714), eadq1814. https://doi.org/10.1126/science.adq1814
5. Crisp, R. J., Stone, C. H., & Hall, N. R. (2006). Recategorization and Subgroup Identification: Predicting and Preventing Threats from Common Ingroups. *Personality and Social Psychology Bulletin, 32*(2), 230–243.
6. Donkers, T., & Ziegler, J. (2025). Understanding Online Polarization Through Human-Agent Interaction in a Synthetic LLM-Based Social Network. *ICWSM 2025, 19*(1), 457–478. https://doi.org/10.1609/icwsm.v19i1.35826
7. Du, N. H., Wang, L. Z., Li, Y. R., & LC, R. (2025). Designing for the Invisible: Raising Awareness for the Experience of the Homeless in an LLM-based Serious Game. *GOODIT '25.* https://doi.org/10.1145/3748699.3749822 *(lab)*
8. Gaertner, S. L., & Dovidio, J. F. (2000). *Reducing Intergroup Bias: The Common Ingroup Identity Model.* Psychology Press.
9. Govers, J., Velloso, E., Kostakos, V., & Goncalves, J. (2024). AI-Driven Mediation Strategies for Audience Depolarisation in Online Debates. *CHI '24.* https://doi.org/10.1145/3613904.3642322
10. Hui, B. P. H., Lau, C. L., Sun, R., LC, R., Hendra, L. B., & Kogan, A. (2025). Decoding Moral Responses in AI: A Quantitative Analysis of Large Language Models. *Computers in Human Behavior.* https://www.sciencedirect.com/science/article/pii/S2451958825002696 *(lab)*
11. Iyengar, S., & Westwood, S. J. (2015). Fear and Loathing across Party Lines: New Evidence on Group Polarization. *American Journal of Political Science, 59*(3), 690–707. https://doi.org/10.1111/ajps.12152
12. Iyengar, S., Lelkes, Y., Levendusky, M., Malhotra, N., & Westwood, S. J. (2019). The Origins and Consequences of Affective Polarization in the United States. *Annual Review of Political Science, 22*, 129–146. https://doi.org/10.1146/annurev-polisci-051117-073034
13. Jiang, Z., Chen, Q., Zhang, C., Li, Y., & LC, R. (2026). Hear You in Silence: Designing for Active Listening in Human Interaction with Conversational Agents Using Context-Aware Pacing. *CHI '26.* https://doi.org/10.1145/3772318.3791238 *(lab)*
14. Levine, M., Prosser, A., Evans, D., & Reicher, S. (2005). Identity and Emergency Intervention: How Social Group Membership and Inclusiveness of Group Boundaries Shape Helping Behavior. *Personality and Social Psychology Bulletin, 31*(4), 443–453. https://doi.org/10.1177/0146167204271651
15. Liu, J. M.-E., Weng, C. C.-H., Lin, Y.-H., Hsiao, P.-Y., & Hou, Y. T.-Y. (2026). When AI Agrees, Polarization Sticks: Private AI Consulting May Increase Confidence and Reduces Depolarization. *CHI EA '26.* https://doi.org/10.1145/3772363.3798705
16. Park, J. S., O'Brien, J. C., Cai, C. J., Morris, M. R., Liang, P., & Bernstein, M. S. (2023). Generative Agents: Interactive Simulacra of Human Behavior. *UIST '23.* https://doi.org/10.1145/3586183.3606763
17. Pettigrew, T. F., & Tropp, L. R. (2006). A Meta-analytic Test of Intergroup Contact Theory. *Journal of Personality and Social Psychology, 90*(5), 751–783. https://doi.org/10.1037/0022-3514.90.5.751
18. Sherif, M., Harvey, O. J., White, B. J., Hood, W. R., & Sherif, C. W. (1961). *Intergroup Conflict and Cooperation: The Robbers Cave Experiment.* University Book Exchange.
19. Tajfel, H., & Turner, J. C. (1979). An Integrative Theory of Intergroup Conflict. In W. G. Austin & S. Worchel (Eds.), *The Social Psychology of Intergroup Relations* (pp. 33–47). Brooks/Cole.
20. Tang, H., Sun, S., Nie, K., Li, A., Sergeeva, A., & LC, R. (2025). Breaking the News: Taking the Roles of Influencer vs. Journalist in a LLM-Based Game for Raising Misinformation Awareness. *PACM HCI* (CHI PLAY 2025). https://doi.org/10.1145/3748600 *(lab)*
21. Tessler, M. H., et al. (2024). AI Can Help Humans Find Common Ground in Democratic Deliberation. *Science, 386*(6719), eadq2852. https://doi.org/10.1126/science.adq2852
22. Turner, J. C., Hogg, M. A., Oakes, P. J., Reicher, S. D., & Wetherell, M. S. (1987). *Rediscovering the Social Group: A Self-Categorization Theory.* Basil Blackwell.
23. Wann, D. L., & Branscombe, N. R. (1993). Sports Fans: Measuring Degree of Identification with Their Team. *International Journal of Sport Psychology, 24*(1), 1–17.
24. Zeng, Y., Shi, Y., Huang, X., Nah, F., & LC, R. (2025). "Ronaldo's a poser!": How the Use of Generative AI Shapes Debates in Online Forums. *CHI '25.* https://doi.org/10.1145/3706598.3713829 *(lab)*
25. Zhang, C., Huang, S. M., Wu, S. H., Chen, Y. H., & LC, R. (2026a). We are all in big trouble! Shock Emoji: Personal Narratives in Expressing Emotions, Opinions, and Data Regarding Climate Change in TikTok Short Videos. *PACM HCI* (CSCW 2026). *(lab)*
26. Zhang, F., Fu, J. Y., Chen, K. X., & LC, R. (2026b). Laughing Through the Struggles: Understanding ADHD Experience and Community Engagement Through Memes and Comments on Instagram. *CHI '26.* https://doi.org/10.1145/3772318.3790540 *(lab)*
27. Zhang, F., Chen, Y., Zeng, X. K., Wang, T. Q., Ling, L., & LC, R. (2025a). An Image of Ourselves in Our Minds: How College-educated Online Dating Users Construct Profiles for Effective Self Presentation. *PACM HCI* (CSCW 2025). https://doi.org/10.1145/3710929 *(lab)*
28. Zhang, Q., Wen, R., Hendra, L. B., Ding, Z., & LC, R. (2025b). Can AI Prompt Humans? Multimodal Agents Prompt Players' Game Actions and Show Consequences to Raise Sustainability Awareness. *CHI '25.* https://doi.org/10.1145/3706598.3713661 *(lab)*
29. Zhou, S., Hendra, L. B., Zhang, Q., Holopainen, J., & LC, R. (2024). Eternagram: Probing Player Attitudes Towards Climate Change Using a ChatGPT-driven Text-based Adventure. *CHI '24.* https://doi.org/10.1145/3613904.3642850 *(lab)*
