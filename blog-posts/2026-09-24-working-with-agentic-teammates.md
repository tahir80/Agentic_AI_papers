# When Your New "Teammate" Isn't Human: What Happens When AI Agents Join Real Work Teams

**Authors:** Rida Qadri, Remi Denton, Michael Madaio, Mahima Pushkarna, Leslie Lai, Sherry Moore, Michelle Chen Huebscher, Andrew Butcher, Ritom Sen, Hsiao-Yu Tung, Shaan Mathur, Yimeng Liu, Shibl Mourad, Noah Fiedel, Edward Grefenstette, Michael Terry (Google Research / Google DeepMind)
**Publication date:** 2026-09-24 (arXiv v1)
**Venue:** arXiv preprint, cs.HC; peer-reviewed venue not confirmed at time of writing
**Paper link:** https://arxiv.org/abs/2609.29901
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-09-26

> **A note on sourcing:** direct network access to arxiv.org and every mirror tried (Hugging Face, Semantic Scholar, export.arxiv.org) was blocked at the network egress layer of the environment this summary was written in — not a paywall; the paper itself is a public, open-access arXiv preprint. This write-up is built from cross-checked search-engine excerpts of the paper's abstract, stated methodology, and reported findings, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that couldn't be verified that way is marked "not available" or "not confirmed." Readers who want the full qualitative record, complete quotes, and the authors' full design-and-research agenda should consult the arXiv preprint directly.

---

## The problem the paper addresses

Most of us have gotten used to AI tools that wait for us to ask them something: you type a prompt, the tool responds, done. But a new generation of "agentic" AI is starting to behave less like a tool and more like a coworker — one that doesn't wait to be asked, that acts on behalf of a whole team rather than one person, and that sticks around across many conversations and days rather than resetting after each request. This paper studies exactly that shift, in the wild: Google researchers embedded themselves with real employees at a large technology company who had started using a persistent, proactive AI "teammate" (the paper calls it **Team Agent**) inside their actual teams, and asked a deceptively simple question — what actually happens, day to day, when you give an AI system the kind of standing and initiative a human teammate would have?

## Why this problem matters

A chatbot that gives a wrong answer is annoying. An AI "teammate" that proactively takes initiative inside a team's shared workflows — surfacing information unprompted, acting across multiple people's work rather than just one person's — is a different kind of risk and a different kind of opportunity. If it works well, it could genuinely lighten the coordination load that eats up so much of real teamwork. If it works badly, it can quietly rewrite the unwritten rules that make teams function: who owes whom an update, who gets credit, who is allowed to speak for the group, and who is actually in control of a decision. Companies are already shipping this kind of proactive, multi-user AI teammate into real workplaces (the paper cites products like Slackbot-style and enterprise chat-integrated agents), but — as the authors point out — there has been very little grounded research into what actually happens to real teams once one arrives. This paper is an early, empirical look at that gap, at a moment when many organizations are deciding whether and how to roll out exactly this kind of system.

## What makes the system agentic

Team Agent is described as a **persistent, proactive, multi-user AI agent teammate** — three properties that distinguish it from a conventional single-user chatbot or assistant. "Persistent" means it maintains continuity across time and interactions rather than starting fresh each session. "Proactive" means it can take initiative and act without being explicitly prompted, rather than only responding to a direct query. "Multi-user" means it operates inside a shared team context — interacting with and acting on behalf of a whole team, not a single individual's private assistant. Because it pursues goals inside real, ongoing team workflows, takes initiative on its own schedule, and is evaluated based on how it actually behaves once embedded in that environment (rather than being tested as a single-turn question-answering system), it fits the profile of agentic AI examined by this research log — though this paper, being a qualitative organizational-behavior study rather than a systems paper, does not spell out its internal tool-use architecture (e.g., exactly which APIs or actions it can invoke); that detail could not be confirmed from the sources available for this summary.

## How humans and the AI agent collaborate

This is not a lab study where participants were handed a new tool and watched for an hour. The researchers studied **real, ongoing adoption**: employees across 11 different teams at the company had already started incorporating Team Agent into their actual daily work before the study began, and the researchers interviewed them about what that experience had actually been like — the friction points, the surprises, and the moments where the agent's behavior didn't fit smoothly into how the team already worked together.

## What role the human plays

Employees are the ones who have to make Team Agent's presence work in practice: deciding how much to rely on it, when to override or ignore it, how to explain its actions to teammates, and how to fit its proactive behavior into workflows and norms that were built around human-only collaboration. The paper frames this as active, ongoing labor — employees aren't passively "using a tool," they are continuously renegotiating the boundaries of what this new, non-human participant is and isn't allowed to do.

## What role the AI agent plays

Team Agent acts as a standing member of the team's shared workspace: proactively surfacing input, taking actions that affect multiple team members (not just the person who happened to configure it), and persisting across time in a way that gives it an ongoing "presence" in the team's work, similar in some respects to a human teammate's ongoing presence — but, crucially, without a human teammate's social instincts, accountability, or tacit understanding of how the team operates.

## How control, initiative, and decisions are shared

The paper's central finding is that this division of control is **not settled or stable** — it is actively being worked out, team by team, in real time. Employees described ongoing "breakdowns and negotiations" as they tried to figure out where the agent's initiative should end and human judgment should begin. The authors organize these negotiations into three areas: (1) the **tacit rules of collaborative human workflows** — the unwritten norms of who does what, and when, that Team Agent doesn't automatically know or follow; (2) the **relational boundaries** of this new non-human actor — how much standing, trust, and social space it should be given relative to a human colleague; and (3) the **redistribution of trust and human agency** — how much control and credit shifts away from individual humans once a proactive agent is empowered to act on the team's behalf.

## The paper's main idea

**Claim by the authors:** when an AI system is granted the kind of standing and initiative normally reserved for a human teammate, it inherits the *privileges* of that role — acting proactively, affecting the whole team, persisting over time — without inheriting the *obligations* that come with it: a human teammate's social accountability, relational capital built through shared history, and tacit, situated knowledge of how their specific team actually operates. The authors argue this mismatch is precisely what produces the breakdowns and renegotiations they observed, and that it should be treated as a first-class design problem rather than a rollout detail to be smoothed over later.

## How the approach works

The researchers conducted an **in-situ qualitative study**: rather than building a prototype and testing it in a lab, they studied a system already deployed and in real use inside a large technology company. To choose whom to interview, they first sent a short pre-interview survey to the agent's existing user base to capture people's general attitudes toward and patterns of use of Team Agent. They then used **purposive sampling** based on those survey responses to deliberately recruit a varied set of interviewees — people with both positive and negative overall attitudes toward the agent, spanning multiple job roles and teams, and with differing lengths of experience using it — rather than simply interviewing whoever was easiest to reach or most enthusiastic. This is a methodologically deliberate choice meant to surface friction and disagreement, not just success stories.

## Human study or evaluation design

**Real human participants, real deployment, qualitative methods.** The study used **virtual semi-structured interviews**, conducted in June and July 2026, analyzed thematically to surface recurring patterns of breakdown and negotiation across teams. This is not a controlled experiment with a treatment/control comparison or a quantitative outcome metric; it is an exploratory, grounded, interview-based study designed to characterize *how* a proactive multi-user agent actually gets absorbed (or fails to be smoothly absorbed) into existing human teamwork.

## Participants and study setting

**17 employees across 11 different teams** at a large technology company, all of whom had genuine, ongoing experience using the deployed Team Agent as part of their real jobs — not a simulated task, not paid crowdworkers doing an unfamiliar exercise for an hour, but people describing their actual working relationship with a system they use at work.

## Experiments or benchmarks

None in the conventional sense — this is a qualitative field study, not a benchmark paper. There is no public dataset, leaderboard, or automated metric associated with this work; the "data" is the interview corpus and the researchers' thematic analysis of it.

## Main results

**As reported by the authors (per available search excerpts):** the boundaries of the human-agent workplace are actively "in flux." Adopting Team Agent produced recurring breakdowns and renegotiations in three areas — tacit workflow norms, the agent's relational standing on the team, and how trust and personal agency get redistributed once a non-human actor can act with teammate-like initiative. A recurring theme is that a system given a human teammate's *privileges* (proactive initiative, team-wide reach, persistence) without a human teammate's *social obligations and tacit knowledge* creates friction that has to be actively, continuously managed by the humans around it, rather than being a one-time onboarding issue.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central human-related finding concerns **trust and agency**, not speed or accuracy. Employees reported having to actively renegotiate how much trust and control to extend to the agent, precisely because it lacked the social accountability and situated knowledge that would normally justify that level of trust in a human colleague. The authors frame this as an early warning sign worth designing for now, rather than a problem to patch after the fact — but this is a qualitative, thematic finding from interviews, not a measurement on a standardized trust or workload scale, and no such quantitative instrument was confirmed from the sources used for this summary.

## What is genuinely new

- A **real, in-the-wild study of an already-deployed proactive, multi-user AI "teammate"** — not a lab prototype, not a simulated persona, and not a single-user assistant, which is what most human-AI collaboration studies examine.
- A **deliberately dissenting-voice-inclusive sample**, recruited via a pre-interview survey specifically to include people with negative as well as positive attitudes toward the agent, rather than only enthusiastic early adopters.
- A **conceptual framing — "privileges without obligations"** — that gives organizations and designers a concrete lens for anticipating friction before it happens: ask what social obligations and tacit knowledge a human in this role would carry, and notice what the AI teammate is missing.
- A **research and design agenda aimed explicitly at preserving human agency** in workplaces that now include non-human organizational actors, rather than treating agency erosion as an unavoidable side effect of automation.

## Limitations and open questions

- **Single company, qualitative sample.** 17 participants across 11 teams at one large technology company is a rich but bounded sample; whether the same dynamics play out at smaller organizations, in different national/organizational cultures, or with differently designed agents is untested here.
- **No quantitative outcome metrics.** The study does not report trust scores, task-performance numbers, or workload measurements on any standardized instrument — its contribution is thematic and conceptual, not statistical.
- **Peer-review status.** This appears to be a recent arXiv preprint; formal peer-reviewed publication status could not be confirmed from the sources used here.
- **Sourcing caveat (this summary).** Because full-text access was blocked in the environment this summary was written in, exact interview quotes, the complete breakdown of themes, and the authors' full proposed research/design agenda could not be independently verified beyond what surfaced in search excerpts. Readers should treat this as a faithful best-effort synthesis, not a substitute for reading the paper.

## Practical implications

For any organization rolling out a proactive, multi-user AI agent into real teams — not just a single-user chat assistant — this paper is a caution against assuming adoption will be a smooth, one-time onboarding event. It suggests that designers and organizations should explicitly plan for an ongoing negotiation period, build in ways for teams to renegotiate the agent's scope of initiative as trust is built or broken, and be honest that granting an AI system teammate-like privileges (proactive reach across a whole team, persistence over time) without teammate-like accountability is likely to generate friction that needs active management, not a feature that can simply be shipped and forgotten.

## Why you should care

Most human-AI collaboration research studies a person and a single assistant talking to each other. This paper studies something structurally different and increasingly common: an AI system embedded as a standing presence inside a whole team's shared work, deployed for real, inside a real company, and examined through the eyes of the actual employees who have to work alongside it. As agentic AI products increasingly market themselves as "teammates" rather than "tools," this paper's central insight — that granting an AI system a teammate's privileges without a teammate's obligations is where the real friction lives — is a genuinely useful, and fairly unsettling, lens for anyone evaluating whether their own organization is ready to bring one of these systems into a real team.
