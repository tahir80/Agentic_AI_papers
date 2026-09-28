# Letting AI Teammates Speak Up: How DocuTeam Lets Agents and Humans Both Steer the Conversation

**Authors:** Heechan Lee, Juhyeon Choi (Seoul National University), Tae Soo Kim, Juho Kim (KAIST / SkillBench), Joseph Seering (KAIST)
**Publication date:** 2026-09-24 (arXiv v1)
**Venue:** arXiv preprint, cs.HC / cs.AI; peer-reviewed venue not confirmed at time of writing
**Paper link:** https://arxiv.org/abs/2609.29309
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-09-28

> **A note on sourcing:** direct network access to arxiv.org (including the HTML and PDF renderings) was blocked at the network egress layer of the environment this summary was written in — not a paywall; the paper itself is a public, open-access arXiv preprint. This write-up is built from cross-checked search-engine excerpts of the paper's abstract, stated methodology, and reported findings, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that couldn't be verified that way is marked "not available" or "not confirmed." Readers who want exact statistics, full quotes, or the complete system architecture should consult the arXiv preprint directly.

---

## The problem the paper addresses

Imagine you're drafting a plan with a couple of AI assistants helping out — one might be good at logistics, another at creative ideas. Today, most systems that let you "discuss" your work with multiple AI agents treat that discussion as its own separate chat window: you have to stop writing, open the chat, explain what you want feedback on, get the agents' input, and then go back and manually apply anything useful to your document. The agents themselves are purely reactive — they only speak when spoken to, and they have no sense of how your document is actually changing while you work. This paper asks: what if the agents could notice your document evolving and jump into the discussion on their own, right where the relevant part of the document is — while you still keep the ability to steer, redirect, or ignore them?

## Why this problem matters

Human teams don't work by scheduling a separate meeting every time someone wants to sanity-check an idea — people naturally interject, glance over a colleague's shoulder, or raise a concern the moment they notice something in the shared work. The authors argue that today's multi-agent discussion tools miss this: they force users to manually orchestrate every exchange, which adds coordination overhead precisely when people are trying to focus on open-ended, creative problem solving. If AI teammates could time their input the way an attentive human collaborator does — and if people could still fluidly fold that input back into their work — it could make brainstorming and planning with AI feel less like operating a tool and more like working with a team.

## What makes the system agentic

DocuTeam's agents are not just chatbots waiting for a prompt. According to the paper, they continuously **monitor changes to a shared, evolving document**, and autonomously decide **when** to proactively start or redirect a discussion as the work evolves — without being asked. Discussions are also **anchored to specific regions of the document**, meaning the agents connect their initiative to a particular part of the evolving artifact rather than a generic chat thread. This combination — a goal (helping develop the document), autonomous initiative (deciding on its own when to speak up), and action that goes beyond a single text reply (starting, redirecting, and sustaining a discussion thread tied to a location in a live document) — is what puts DocuTeam's multi-agent system squarely in agentic territory, evaluated here not as a static text generator but as a proactive collaborator embedded in an ongoing task.

## How humans and the AI agent collaborate

DocuTeam is explicitly built as a **mixed-initiative** system: both the user and the agents can start, steer, or redirect a discussion. Agents can proactively open a discussion thread anchored to a part of the document they've noticed changing or worth revisiting; the user can just as easily start their own discussion, jump into one the agents started, reshape where it goes, or simply adopt an idea straight from the conversation into the document. The document itself functions as the shared medium that grounds these exchanges — rather than treating "talking to the agents" and "writing the document" as two separate activities, DocuTeam interleaves them.

## What role the human plays

The human is the author and final decision-maker: they write and revise the shared document, decide which of the agents' proactively raised points are worth engaging with, choose whether to redirect a discussion the agents started, and selectively pull ideas from the conversation into their actual work. According to the study's reported interaction-pattern results, participants using DocuTeam engaged significantly more often in "Discussion-mode" conversations — that is, responding to and building on points the agents raised — rather than only initiating their own broad, open-ended "Idea-mode" brainstorming from scratch, as they did more often with the baseline system.

## What role the AI agent plays

Each agent in the multi-agent team watches the evolving document and can independently decide to open a discussion tied to a specific region of it, contributing a perspective, question, or suggestion the user might not have generated alone. Agents can also have their threads redirected by the user, meaning their initiative is real but not unchecked — the human retains override power over where any given discussion goes.

## How control, initiative, and decisions are shared

This is the paper's central design axis: **initiative is genuinely bidirectional**. Agents can act first (starting or redirecting a discussion based on document changes) and humans can act first (starting their own discussion, or simply continuing to write). Once a discussion is underway, either side can further redirect it, and the human always retains the final say over what — if anything — gets incorporated into the document. The baseline condition in the study kept the same underlying multi-agent discussion capability but removed this in-situ, agent-initiated quality, requiring the user to initiate and orchestrate every discussion themselves — which the authors use as the comparison point for isolating the effect of mixed initiative specifically.

## The paper's main idea

**Claim by the authors:** giving AI discussion agents the ability to proactively initiate and anchor conversations to specific, evolving parts of a shared document — while preserving the user's ability to steer or ignore them — improves the novelty, relevance, and specificity of the resulting work, and does so by redistributing (rather than simply adding) cognitive effort: users spend less effort orchestrating who talks when, and more attention stays on the document itself as the shared point of grounding.

## How the approach works

DocuTeam pairs a document-editing environment with a team of LLM-based discussion agents that watch document edits. When the agents detect a meaningful change or notice an opportunity relevant to a specific region of the document, they can proactively open a discussion thread anchored to that region. Users can respond within that thread, start their own thread elsewhere, redirect an agent-initiated thread toward a different concern, or copy ideas from the conversation directly into the document. The baseline system used for comparison provided access to the same underlying agents and discussion capability, but without the proactive, document-anchored initiation — users had to open and drive every discussion themselves, separately from their writing.

## Human study or evaluation design

The researchers ran a **within-subjects study with real human participants (N = 20)**, comparing DocuTeam against the non-proactive baseline on an open-ended problem-solving task involving a shared, evolving document. The study was designed around three research questions: (1) how mixed-initiative discussion affects the novelty, workability, relevance, and specificity of the task outcome; (2) how it changes the pattern of user–agent interactions during the task; and (3) how it affects the cognitive and coordination burden placed on users. Outcome quality was assessed via **blind evaluation**, and the researchers used Shapiro-Wilk tests to check for normality before applying paired t-tests or Wilcoxon signed-rank tests as appropriate.

## Participants and study setting

Twenty participants were recruited through the researchers' institutional online communities; per the reported recruitment criteria, participants regularly used LLM services to discuss or work through complex problems and had at least some prior experience planning an event, consistent with the study's open-ended planning-style task. Exact demographic breakdowns (age, gender, occupation) were not confirmed from the sources used for this summary.

## Experiments or benchmarks

There is no public benchmark or shared dataset associated with this work; it is a controlled, within-subjects lab study rather than a benchmark paper. The comparison was strictly DocuTeam vs. the non-proactive baseline system on the same task, with the same underlying agent team in both conditions — isolating the effect of mixed-initiative, in-situ interaction rather than the effect of the agents' raw capability.

## Main results

**As reported by the authors:** outcomes produced with DocuTeam were rated by blind evaluators as significantly more novel, relevant, and specific than those produced with the baseline. Overall self-reported cognitive load did not differ significantly between conditions. Interaction logs showed a significant shift in behavior: participants initiated agent-facing "Discussion-mode" exchanges (responding to or building on an agent's point) significantly more often with DocuTeam (reported p = 0.030), while "Idea-mode" exchanges (user-initiated, from-scratch brainstorming) were significantly more common with the baseline (reported p = 0.018).

## Effects on human performance, trust, workload, safety, or decision quality

The clearest human-related outcome concerns **output quality and effort allocation, not raw workload reduction**. Cognitive load, measured overall, was statistically unchanged — but the authors' qualitative interpretation is that effort was *redistributed* rather than simply added or removed: participants had more information to process because agents were proactively contributing, but they spent less effort managing and orchestrating who should speak when, since the agents handled the timing of their own contributions. The authors report this let more of participants' attention remain on the document itself, which they connect to the higher novelty, relevance, and specificity scores. This is the authors' interpretation of a pattern in the data, not a separately validated causal claim.

## What is genuinely new

- A discussion system where **both humans and multiple AI agents can independently initiate and redirect conversation**, rather than a strictly reactive or strictly agent-driven design.
- **Document-anchored, in-situ discussion initiation** — agents proactively raise discussions tied to a specific region of a live, evolving artifact, rather than in a generic side-channel chat.
- A **controlled, within-subjects comparison** isolating the specific effect of proactive, mixed-initiative interaction from the effect of simply having access to multiple discussion agents (the baseline had the same agents, just without the proactive, in-situ initiation).
- Evidence that mixed initiative can **shift how people use AI discussion** (more responding/building vs. more from-scratch prompting) without a measured cost in overall cognitive load.

## Limitations and open questions

- **Small sample, single task type.** Twenty participants on one open-ended, planning-style task is a controlled but modest evaluation; generalization to other document types (e.g., technical writing, code, research papers) or larger teams is untested here.
- **Single-session, lab-based study.** The study captures one working session rather than sustained, real-world use over days or weeks, so it's unclear whether the observed benefits (or the "no change" in cognitive load) hold up with prolonged use or novelty wear-off.
- **Blind evaluation criteria and rater details** (number of raters, exact rubric) were not confirmed from the sources used for this summary.
- **No public code or project page found**, which limits independent replication for now.
- **Sourcing caveat (this summary).** Because full-text access to arXiv was blocked in the environment this summary was written in, exact means, standard deviations, and full statistical tables could not be independently verified beyond what surfaced in search excerpts; the reported p-values for interaction-mode shifts were corroborated across queries but should be checked against the source PDF.

## Practical implications

For anyone building AI-assisted writing, planning, or ideation tools with multiple agents, this paper offers a concrete design pattern: let agents watch the artifact (not just the chat) and initiate discussion tied to specific regions of it, and let users freely redirect or ignore that initiative. The reported result — better outcome quality without a measured increase in overall cognitive load — suggests that proactive agent initiative, when it's anchored to the shared work and remains user-overridable, doesn't have to mean more overhead for the human, even though it does change what kind of overhead they experience.

## Why you should care

Most "AI agent" discussion features today are bolted-on side chats that agents only enter when explicitly summoned. DocuTeam is a controlled test of a genuinely mixed-initiative alternative — agents that can speak up on their own, anchored to the part of the work they're commenting on, while a human keeps full steering power. The fact that this shift measurably changed both the quality of what people produced and the way they interacted with their AI teammates, in a real study with real participants, makes it a useful, concrete data point for anyone deciding how much initiative to hand an AI collaborator — and how to keep a human firmly in control of where that initiative goes.
