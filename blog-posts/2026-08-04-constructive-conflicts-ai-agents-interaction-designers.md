# Should Your AI Design Assistant Argue With You? A CMU Study Says Maybe It Should

**Authors:** Howard Ziyu Han, Nikolas Martelaro (Carnegie Mellon University, Human-Computer Interaction Institute)
**Publication date:** 2026-08-04 (arXiv v1)
**Venue:** arXiv preprint; conditionally accepted to the 14th International Conference on Human-Agent Interaction (HAI 2026)
**Paper link:** https://arxiv.org/abs/2608.04166
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-20

> **A note on sourcing:** this session's outbound network access to arxiv.org and mirror sites (ar5iv, Semantic Scholar, Hugging Face, personal author pages) was blocked by the organization's egress policy — this is a network restriction in the research environment, not a paywall; the paper is a public arXiv preprint. This summary is built from the arXiv abstract and cross-checked search-engine excerpts describing the paper's method, study design, and findings, rather than a direct read of the full PDF. Anything that could not be corroborated this way is marked "not available" or "not independently verified."

---

## The problem the paper addresses

Design students working with generative AI tools often get an assistant that behaves like an eager brainstorming partner: it adds ideas, expands the option space, and generally agrees that more is better. What it rarely does is push back. The authors argue that this "yes-and" style of AI support can leave novice designers without a proper stress test for their own proposals — nobody in the loop is asking the hard question of "what would a skeptical stakeholder actually object to here?" This paper asks whether an AI agent that is deliberately built to *disagree constructively* — to voice the pushback of stakeholders the designer hasn't fully accounted for — can get novice designers to genuinely reconsider their work, rather than just pile on more ideas.

## Why this problem matters

Reconsideration — actually revisiting and potentially changing a design decision — is a core professional skill in interaction design, but it's hard to teach and even harder to self-generate. Novices in particular tend to anchor on their first proposal. As AI design tools become a routine part of design education and early-career practice, how those tools are built matters: an assistant that only ever elaborates and validates could quietly reinforce exactly the anchoring problem it should help correct. This paper is a direct test of an alternative design philosophy — an AI that argues rather than agrees — and whether it actually changes what designers do, not just how they feel about their work.

## What makes the system agentic

The system is an LLM-based agent explicitly built around "adversarial design theory," a design methodology that treats stakeholder conflict as a generative resource rather than a problem to avoid. Rather than answering a single query, the agent sustains an interactive, multi-turn critique session: it reads a student's design proposal, synthesizes the perspectives of multiple stakeholders who would plausibly object to it, and voices that pushback conversationally as the designer engages with it — adapting its objections to the specifics of what the designer has proposed. That combination — a standing goal (surface stakeholder tension), multi-turn interactive behavior grounded in the artifact under discussion, and evaluation of its effect on a human's downstream task performance — is what makes this an agentic system rather than a one-shot critique generator.

## How humans and the AI agent collaborate

A design student brings a proposal to the interaction, and the agent's job is to interactively challenge it. The human isn't delegating a task to the agent to complete on their behalf — the agent's "goal" is to produce friction in service of the human's own reconsideration process. The collaboration is adversarial-but-constructive: the agent's real-time stakeholder pushback is the input the designer has to metabolize, and what the designer does with that pushback — revise, defend, ignore — is the outcome the study measures.

## What role the human plays

The human is a novice interaction design student who authors a design proposal, then engages directly with the agent's stakeholder objections, deciding in real time how (or whether) to respond and revise. Their reconsideration behavior, shifts in design thinking, and concrete edits to the proposal are the object of study — the human is an active participant whose decisions are the paper's primary outcome measure, not a passive recipient of AI output.

## What role the AI agent plays

The agent plays an antagonist, not an assistant. Instead of proposing solutions, it plays back the tensions and objections that real stakeholders would plausibly raise against the student's specific proposal, doing so interactively and adaptively rather than through a fixed script. Its role is deliberately to complicate the designer's confidence in their own proposal, on the theory that constructive conflict — not more suggestions — is what drives genuine reconsideration.

## How control, initiative, and decisions are shared

The agent takes the initiative in raising objections — it's built to be interactive and to synthesize pushback proactively rather than waiting to be asked for criticism. The human retains full control over the design artifact itself: they choose whether to revise, how to respond to each objection, and when the review session ends. This is a mixed-initiative setup where the agent's initiative is expressed through *critique*, and the human's initiative is expressed through *revision* — control over the actual work product never leaves the human's hands.

## The paper's main idea

**Claim by the authors:** giving a design-review AI agent an antagonistic role, grounded in adversarial design theory and delivered interactively, produces more genuine reconsideration and more concrete design changes in novice designers than either unguided self-reflection or a static, non-interactive version of the same critique framework.

## How the approach works

The authors built an AI agent that operationalizes adversarial design theory: given a student's design proposal, it generates and voices the pushback of multiple relevant stakeholders in an interactive dialogue, aiming to surface conflicting perspectives the designer may not have considered. To isolate what the interactivity itself contributes (as opposed to just the content of the critique framework), they also built a non-interactive comparison condition — written, stepwise prompts that walk a designer through the same underlying constructive-conflict framework without a live back-and-forth. This lets the study separate "does the thinking framework itself help?" from "does talking to an interactive agent that pushes back help more than that?"

## Human study or evaluation design

This is a **controlled, between-subjects experiment with real participants**, not a simulation or a purely qualitative demo. Forty-five design students were randomly assigned to one of three conditions: **Self Reflection** (unsupported review of their own design proposal, no framework or agent), **Stepwise Guidance** (written prompts walking them through the constructive-conflict framework, no live agent), and **Interactive Engagement** (the AI agent enacting the constructive-conflict framework interactively, synthesizing stakeholder pushback in real time).

## Participants and study setting

**Demonstrated in the paper:** 45 real design students (novice interaction designers), split roughly evenly across the three between-subjects conditions (roughly 15 per condition). Each participant reviewed and had the opportunity to revise their own interaction-design proposal under their assigned condition. Exact recruitment details (institution, demographics, compensation) were not independently verifiable in this session and should be confirmed against the paper directly.

## Experiments or benchmarks

There is no public leaderboard or standardized benchmark here — the "experiment" is the three-condition between-subjects comparison itself, measuring self-reported reconsideration, shifts in design thinking, and the number/nature of concrete edits participants made to their design proposals after each condition.

## Main results

**Reported by the authors, per available sources:** compared with unguided Self Reflection, both Stepwise Guidance and Interactive Engagement produced significantly higher self-reported reconsideration and more concrete improvements to participants' design proposals. Compared with Stepwise Guidance, the interactive agent introduced more conflictual perspectives and was more effective at converting that reconsideration into concrete design actions, with participants reporting more shifts in design thinking and more iterative edits. Exact statistical figures (effect sizes, significance tests) could not be independently verified from the sources available in this session — readers who need precise numbers should consult the paper directly.

## Effects on human performance, trust, workload, safety, or decision quality

The study's central human-related outcome is **decision quality and reconsideration behavior**, not trust, workload, or safety. The authors report that the interactive agent condition led to more genuine reconsideration of design decisions and more design changes than both the unguided baseline and the non-interactive version of the same framework — evidence that the *interactivity* of an antagonistic agent, not just the underlying critique content, contributes to better design outcomes for novices. The paper does not report on trust calibration, cognitive workload, or safety in this study.

## What is genuinely new

- A concrete, evaluated instantiation of an **antagonistic (rather than cooperative) AI design-review role**, grounded explicitly in adversarial design theory rather than generic "critique" prompting.
- An experimental design that **disentangles framework content from interactivity** — the Stepwise Guidance condition uses the same underlying constructive-conflict prompts as the agent, letting the study isolate the added value of a live, adaptive, interactive agent over a static version of the same idea.
- Evidence, from a real between-subjects study with novice designers, that **deliberately adversarial AI interaction can outperform passive or purely suggestion-generating AI support** at prompting genuine reconsideration — a finding that runs counter to the more common "AI as agreeable brainstorming partner" design pattern.

## Limitations and open questions

- **Small sample, single population:** 45 participants across three conditions (~15 each) of design students, in what appears to be an academic setting — generalization to professional designers or other domains is unconfirmed.
- **Single task type:** all participants worked on their own interaction-design proposals within one study protocol; whether the effect holds for other design disciplines or longer, real-world projects is untested.
- **Unverified statistics:** because the full paper could not be fetched directly in this session, exact effect sizes, p-values, and the precise wording of outcome measures could not be independently confirmed.
- **Peer-review status:** as of this writing, the paper is conditionally accepted to HAI 2026 but the arXiv version is a preprint; final camera-ready details may differ.
- The paper does not appear to examine longer-term effects (e.g., whether reconsideration skills transfer to future, unassisted design work) or how designers' trust in or preference for an antagonistic agent evolves over repeated use.

## Practical implications

If the effect holds up under further study, it suggests concrete design guidance for AI-assisted creative and design tools: an assistant that is built to genuinely challenge a user's proposal — grounded in a real critique framework and delivered interactively — may do more to improve outcomes than one that only elaborates or validates. This has direct relevance for design education (where reconsideration is a skill to be trained) and for any professional AI-assisted review workflow where the goal is catching blind spots rather than just generating more options.

## Why you should care

Most "AI assistant" design patterns default to being agreeable and additive. This paper is a rare, real-world-tested counterexample: a carefully designed experiment showing that an AI agent built to argue — to surface the objections a designer would rather not think about — measurably increased how much novice designers reconsidered and revised their work, and did more of that than a static version of the same critique content. It's a useful data point for anyone designing human-AI collaboration tools: sometimes the more helpful agent is the one that disagrees with you, not the one that only says yes.
