# Exploring The Impact Of Proactive Generative AI Agent Roles In Time-Sensitive Collaborative Problem-Solving Tasks

**Authors:** Anirban Mukhopadhyay (Virginia Tech), Kevin Salubre, Hifza Javed, Shashank Mehrotra, Kumar Akash (Honda Research Institute USA, Inc.)
**Publication date:** 2026-02-19 (arXiv id 2602.17864)
**Venue:** ACM CHI Conference on Human Factors in Computing Systems (CHI '26), April 13–17, 2026, Barcelona, Spain (DOI: 10.1145/3772318.3791592)
**Paper link:** https://arxiv.org/abs/2602.17864 (PDF: https://arxiv.org/pdf/2602.17864)
**Code link:** Not available (no public repository found at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-26

> **A note on sourcing:** arXiv and ACM's Digital Library were not directly reachable from this research session's network (the outbound proxy blocked both domains). This summary is built from the paper's publicly circulated abstract, the CHI '26 program listing, and secondary descriptions that independently agree with each other, rather than a direct read of the full PDF. Facts that could be cross-confirmed across multiple sources (authors, venue, study design, participant count, and the reported statistics) are reported as such; anything we could not verify is marked "not available" rather than invented.

---

## The problem the paper addresses

Picture a team of three people racing against the clock in an escape room — juggling clues, half-formed theories, and a ticking timer. Now imagine handing that team an AI assistant that can jump into the group chat on its own, without being asked, to suggest an idea or summarize where things stand. Would that help, or would it just be one more voice competing for attention when attention is already scarce?

That's the exact question this paper investigates. Most "helpful AI" research studies agents that wait to be asked. This paper instead studies agents that decide **for themselves** when to speak up during fast-moving, real-time teamwork — and asks whether that proactivity actually helps.

## Why this problem matters

A lot of real work is done this way: a support team triaging a live incident, a group brainstorming under a deadline, first responders coordinating in the field. In these settings, waiting for someone to formally "ask the AI a question" can be too slow, and too demanding of already-stretched attention. AI systems are increasingly designed to be proactive — to notice and act without being prompted — but proactivity is a double-edged sword: an AI that interrupts at the wrong moment can be worse than one that says nothing. Before builders wire "speak up automatically" into products, we need real evidence about what proactive AI actually does to a team's performance, flow, and mental workload.

## What makes the system agentic

The AI in this study isn't a plain chatbot that only replies when spoken to. It continuously observes the team's shared, real-time conversation and progress, and it autonomously decides *when* to intervene and *what kind* of contribution to make — proposing an idea, answering an implicit need, or offering a summary — without being explicitly invoked. That combination of ongoing environment monitoring, self-initiated decision-making about timing and content, and taking action inside a live task (rather than producing one isolated text reply) is what makes it agentic under our working definition, even though its "actions" are conversational rather than tool calls or API use. The paper's own framing is explicit about this: it studies *proactive* agent roles, in contrast to purely reactive, request-response AI assistants.

## How humans and the AI agent collaborate

Three real, co-located human participants worked together on timed digital escape-room puzzles. The AI agent shared the same real-time group channel as the humans and — depending on the experimental condition — could jump in unprompted with hints, ideas, or status summaries, the same way a human teammate might chime in without being asked.

## What role the human plays

The humans are the primary problem-solvers: they read clues, propose solutions, coordinate who does what, and ultimately decide whether to accept, ignore, or build on anything the AI contributes. They retain full control over the task; the AI never takes an action for them, it only participates in the conversation the team uses to solve the puzzle together.

## What role the AI agent plays

The paper tested two distinct agent roles:
- **A peer agent**, which behaved like an equal team member — proposing ideas and answering questions on its own initiative.
- **A facilitator agent**, which stayed one level removed from the puzzle content — offering periodic summaries and lightweight structure to help the group organize itself, closer to a process coach than a problem-solving participant.

Both were compared against a **no-AI** baseline condition.

## How control, initiative, and decisions are shared

This is a study of **mixed initiative** in its purest form: both the humans and the agent can initiate contributions at any time, with the agent choosing, on its own, when the moment calls for a hint, an idea, or a summary. The humans hold veto power in practice (they can ignore or override the AI), but the AI does not wait for permission to speak — initiative is genuinely shared, not scheduled or gated by a human request.

## The paper's main idea

**Claim by the authors:** proactive AI support is not automatically beneficial in fast, real-time, co-located teamwork — its value depends heavily on *what kind* of proactive role the agent plays. A peer-style agent that jumps into the content of the problem can help, but it can also disrupt the team's flow and cause people to lean on it too much; a lighter-touch facilitator role is safer but correspondingly less impactful.

## How the approach works

The researchers built a digital escape-room platform where a team of three humans (plus, in two of the three conditions, the AI) shared a live workspace and communication channel under time pressure. The AI agent's behavior differed by condition: in the peer condition it could proactively propose solutions and answer implicit questions; in the facilitator condition it proactively offered group-level summaries and structure rather than content-level suggestions. Puzzle difficulty was also varied as a factor in the design.

## Human study or evaluation design

**Demonstrated in the paper:** a within-subjects study in which the same participants experienced all three conditions — no AI, peer agent, facilitator agent — while working through timed escape-room puzzles, allowing direct comparison of how the same people and teams performed and felt across conditions. The authors report using an Aligned Rank Transform ANOVA (ART-ANOVA), a nonparametric approach suited to workload and performance ratings, along with estimated marginal means and post-hoc contrasts.

## Participants and study setting

**24 participants**, organized into real-time, co-located teams of three, took part in a controlled lab study using the researchers' digital escape-room platform. This is a genuine hands-on, real-human study — not a simulation — though it is a lab setting with a fixed puzzle format rather than a field deployment.

## Experiments or benchmarks

There is no public benchmark here; the "task" is the researchers' own digital escape-room puzzle suite, varied by difficulty, used specifically to create the kind of time-pressured, ambiguous, multi-step problem-solving that the authors argue is representative of real collaborative work.

## Main results

**Demonstrated in the paper (per available, cross-confirmed descriptions):**
- **Workload (NASA-TLX):** a significant main effect of condition on perceived workload (F = 5.75, p = .005). Post-hoc contrasts showed the **peer agent produced significantly higher workload** than both the facilitator condition (β = −17.10, SE = 5.63, t = −3.04, p = .011, d = −0.88) and the no-AI condition (β = −15.90, SE = 5.63, t = −2.82, p = .013, d = −0.82).
- Puzzle difficulty also significantly affected workload (F = 16.78, p < .001), as expected.
- **Group performance:** a significant main effect of AI condition on group performance (F = 16.66, p = .004) — meaning the choice of agent role measurably changed how well teams actually solved the puzzles, not just how they felt about it.
- Qualitatively, the authors report that the peer agent *occasionally* helped by offering timely hints and acting as a memory aid, but it also disrupted the team's flow and encouraged over-reliance on it. The facilitator agent provided only light scaffolding and had a comparatively limited effect on outcomes.

We were not able to independently confirm the exact direction/magnitude of the performance effect (e.g., which condition performed best) from the sources available in this session — readers who need that specific number should consult the paper directly.

## Effects on human performance, trust, workload, safety, or decision quality

This is the empirical core of the paper. The peer agent's proactive, content-level contributions came at a measurable workload cost (significantly higher NASA-TLX ratings than either alternative) and, per the authors' qualitative account, created flow disruption and over-reliance — a team leaning on the AI's suggestions rather than working the problem themselves. The facilitator agent avoided that workload penalty but also achieved comparatively little. **This is our interpretation of the tradeoff the authors describe: more content-level proactivity bought occasional value at a real cost to team process, while more conservative, structure-only proactivity was safer but nearly inert.** We could not confirm specific trust-scale results from the sources available to us.

## What is genuinely new

- A controlled, within-subjects comparison of **two distinct styles of AI proactivity** (peer vs. facilitator) against a no-AI baseline, in a real-time, co-located, multi-person task — most prior human-agent collaboration work studies one human and one agent, or purely dyadic settings, rather than a small human team plus an autonomously-initiating AI.
- Quantitative evidence that an agent's *initiative style*, not just its presence or absence, is what drives workload and performance outcomes — a peer-style proactive agent and a facilitator-style proactive agent are not interchangeable "AI help," they have measurably different, sometimes opposite, effects.
- Direct evidence of an over-reliance risk specifically tied to a *proactive* (self-initiating) agent, as opposed to the more commonly studied on-request assistant.

## Limitations and open questions

- **Lab setting, single task genre.** The study used one type of task (digital escape-room puzzles) in a controlled lab environment; the authors themselves would be expected to flag that findings may not transfer directly to other time-pressured collaborative settings (e.g., professional incident response, brainstorming meetings).
- **Team size fixed at three.** It's unclear from available sources whether the effects (especially the workload penalty for the peer agent) would hold at different team sizes.
- **We could not independently verify** the full statistical results tables, the exact effect on group performance (direction and magnitude), or the paper's own stated limitations section from the sources available in this session, since the full PDF could not be fetched over this network. Readers who need precise, complete results should consult the paper directly.

## Practical implications

If these findings hold up under closer reading, they carry a clear, actionable lesson for anyone building proactive AI teammates: the *type* of proactivity matters as much as whether an agent is proactive at all. A content-suggesting "peer" agent that jumps in with ideas can occasionally help but risks raising cognitive load and fostering over-reliance in a fast-moving team task; a lighter "facilitator" agent that only offers structure and summaries is safer on workload but may not move the needle on outcomes. Designers of real-time collaborative AI tools may need to actively choose — and perhaps let users configure — where on that spectrum their proactive agent sits, rather than assuming "more proactive help" is uniformly good.

## Why you should care

This paper speaks directly to a design choice that is becoming common as AI agents move from "wait to be asked" to "act on their own initiative" inside shared workspaces, chats, and tools. It offers a concrete, measured answer to a question many product teams are currently guessing at: proactive AI participation in a human team is not free — it can measurably raise workload and change how a team performs, and the specific way an agent chooses to intervene (content suggestions vs. process structure) changes the outcome in different directions. That's a useful, evidence-based caution against simply making agents "more proactive" without thinking carefully about what kind of initiative they take.
