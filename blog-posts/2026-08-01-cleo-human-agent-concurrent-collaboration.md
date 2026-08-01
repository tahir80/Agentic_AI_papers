# "When to Hand Off, When to Work Together": Expanding Human-Agent Co-Creative Collaboration through Concurrent Interaction

**Authors:** Kihoon Son, Hyewon Lee, DaEun Choi, Yoonsu Kim, Tae Soo Kim, Yoonjoo Lee, John Joon Young Chung, HyunJoon Jung, Juho Kim (KIXLAB, KAIST, with co-authors whose current affiliations may include Adobe Research / Midjourney / other industry labs — exact per-author institutional affiliations at time of publication not independently confirmed)
**Publication date:** 2026-03-02 (arXiv v1, id 2603.02050); revised 2026-04-07 (v4)
**Venue:** arXiv preprint; a project page exists (see below), but peer-reviewed venue/acceptance status (e.g. CHI) could not be independently confirmed from available sources
**Paper link:** https://arxiv.org/abs/2603.02050 (PDF: https://arxiv.org/pdf/2603.02050)
**Code link:** Not available (the authors describe a planned public release of a 214-turn interaction-log dataset; no confirmed live repository found at the time of writing)
**Project page:** https://cleo.kixlab.org/
**Date added:** 2026-08-01

> **A note on sourcing:** arXiv could not be directly fetched from this research session's network (the outbound proxy returned policy-denial errors for arxiv.org, export.arxiv.org, and related mirror hosts), so this summary is built from the paper's publicly circulated abstract and cross-checked secondary descriptions gathered across many independent searches, rather than a direct read of the full PDF. Facts corroborated across multiple independent searches (authors, dates, study design, participant details, and headline findings) are reported as such; anything that could not be cross-confirmed this way is marked "not available" or flagged as uncertain rather than invented.

---

## The problem the paper addresses

Most tools that let an AI agent do creative work for you — draft a slide, generate a UI layout, edit a design — are built around a simple loop: you ask, you wait, you get a result, you either accept it or ask again. The paper argues this "sequential delegation" model breaks down once agents start working *visibly*, step by step, inside the same shared canvas a person is using. When a designer can literally watch the agent editing a file in real time, something changes: people don't just wait passively — they start jumping in mid-execution, nudging the agent, or quietly doing their own edits alongside it. Today's agents mostly can't tell the difference between "the human is giving me feedback" and "the human is just doing their own thing next to me," so they either barrel ahead and ignore useful signals, or get confused by actions that were never meant for them.

## Why this problem matters

As AI design and coding agents move from black-box chat responses into tools where their step-by-step work is visible on screen (think Figma Make, Lovart, or similar AI-native design surfaces), the old "prompt, wait, review" pattern stops matching how people actually want to work. If agents can't correctly read a person's in-the-moment actions, collaboration either regresses to rigid turn-taking (slow, and it wastes the value of watching the agent work) or produces messy conflicts where the agent overwrites what a person just did, or ignores a correction it should have caught. Getting this right matters for anyone building the next generation of AI-native creative and productivity tools, where humans and agents are expected to share a live workspace rather than take strict turns.

## What makes the system agentic

The paper studies AI agents that operate directly inside a design canvas — interpreting instructions, planning a sequence of edits, and executing those edits step by step on real design artifacts (the study recruited professional designers experienced with agentic design tools such as Figma Make and Lovart, situating this squarely in the current wave of LLM/VLM-driven generative design agents). The system the authors built, CLEO, goes further: it doesn't just execute a plan, it continuously monitors the shared canvas *while it is acting*, so it can notice when the human has just done something and decide, in real time, whether that action was feedback meant for it or independent work to leave alone. That live monitoring-and-adapting loop, layered on top of multi-step design execution, is what pushes this beyond a single-response generator into agentic territory.

## How humans and the AI agent collaborate

Rather than a strict "ask, then wait" cycle, both the human designer and the agent can act on the same canvas at the same time. A designer can let the agent run unsupervised, watch it work without touching anything, interrupt it with a new verbal instruction, stop it outright, or — the case the paper is most interested in — start editing the canvas themselves while the agent is still mid-execution. The agent is meant to notice that concurrent edit and figure out whether to treat it as a correction to fold into its own work or as separate work to simply not interfere with.

## What role the human plays

The human is a working collaborator, not just a requester. Across the two studies, real professional designers used the tool on their own design tasks, and — critically for the paper's contribution — didn't just issue prompts and wait. They chose, moment to moment, whether to step back and let the agent run, watch its process to build a mental model of what it was doing, jump in with new verbal direction, or physically take over part of the canvas to make their own edits in parallel with the agent's ongoing work.

## What role the AI agent plays

The agent executes multi-step design work on the shared canvas and, in the CLEO version built for Study 2, also has to continuously interpret what the human is doing concurrently — classifying incoming human actions as either feedback to incorporate into its own execution or independent activity it should leave untouched, and adjusting its behavior accordingly rather than following a single fixed script.

## How control, initiative, and decisions are shared

Initiative is explicitly shared and can shift at any point during execution, not just at the start of a task. The authors frame this as a spectrum rather than a binary handoff: from fully "hands-off" delegation, through passive observation, to active mid-execution direction, to full concurrent co-editing where both parties are changing the artifact at the same time. Which mode is active can change turn by turn, and the paper's central design question is how the agent should detect and respond to that shift rather than requiring the human to explicitly declare it.

## The paper's main idea

**Claim by the authors:** as agents become visible collaborators working inside shared creative workspaces, human-agent collaboration needs to expand beyond sequential delegation to support *concurrent interaction* — humans and agents acting on the same artifact at the same time — and doing this well requires agents to have "collaborative context awareness": the ability to interpret a human's simultaneous actions as either feedback or independent parallel work, and adapt execution accordingly.

## How the approach works

The authors first ran an exploratory study (Study 1) with a design-agent tool that made the agent's step-by-step execution visible on the canvas, to observe how professional designers naturally behaved once they could see the agent working. This revealed that designers spontaneously started intervening mid-execution — but the agent had no way to distinguish a deliberate correction from the designer simply doing unrelated work nearby. Based on that gap, the authors built CLEO, a design probe that adds collaborative context awareness: it watches the shared canvas during its own execution and interprets concurrent human actions as either feedback to incorporate or independent work to ignore, then continues adapting its execution accordingly. CLEO was then evaluated in a second, more structured study.

## Human study or evaluation design

**Demonstrated in the paper:** two sequential human studies with real professional designers. Study 1 was an exploratory observation of designers using a process-visible (but not yet context-aware) agent to surface the core problem. Study 2 was a structured evaluation of CLEO involving a two-day engagement with stimulated-recall interviews, in which the authors logged and analyzed 214 turn-level human-agent interactions to build a taxonomy of collaboration behavior.

## Participants and study setting

**Real, recruited professional practitioners** — the more detailed cohort described for the study (10 participants, labeled D1–D10; 3 male, 7 female; ages 24–36, mean 28.3) were UI/UX designers with at least one year of professional design experience, screened for daily-level Figma proficiency and prior hands-on experience with AI design agents such as Figma Make or Lovart. Study 1 similarly involved 10 professional designers. These are not crowdworkers or simulated personas, but working designers using a live design-agent tool on canvas-based design tasks.

## Experiments or benchmarks

There is no public benchmark here; the "experiment" is the two studies themselves, plus the interaction log the authors produced from Study 2: 214 annotated turns of human-agent interaction, coded into a taxonomy of five action patterns (e.g., fully hands-off delegation, passive observation, verbal mid-execution direction, stopping/terminating execution, and concurrent co-editing/takeover) and ten finer-grained codes, along with six triggers and four enabling factors describing when and why designers shifted between these modes. The authors describe releasing this annotated dataset to support future research on human-agent co-creative collaboration.

## Main results

**Demonstrated in the paper (per available descriptions, not independently verified against the full PDF):**
- Designers naturally moved between multiple modes of collaboration rather than sticking to one style — sequential delegation was common, but concurrent interaction (working on the canvas *at the same time* as the agent) was also frequent, reported as present in roughly 31.8% of the 214 analyzed turns.
- Several of the five action patterns (e.g., fully hands-off delegation, observational monitoring, and directive verbal steering) each showed up in a substantial share of turns, according to secondary summaries — with fully hands-off behavior and passive observation each reported around 68–70% of turns and directive steering around 28.5% (these patterns are not mutually exclusive per turn, so the figures overlap; exact definitions and full statistical detail should be checked against the primary PDF).
- The taxonomy of triggers and enabling factors gives a structured account of *why* designers shifted modes — for example, seeing the agent's process unfold prompted intervention, and having enough context/confidence about what the agent was doing enabled a person to safely work concurrently rather than waiting.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's human-related contribution is primarily about **collaboration process**, not a single trust/workload score. **Demonstrated:** Study 1 showed that making agent execution visible changed designer behavior, prompting more mid-task intervention than a black-box agent would — but exposed real friction when the agent misread these interventions. **Our interpretation:** this suggests visible, steerable agent execution is a double-edged design choice — it invites richer, faster collaboration, but only pays off if the agent can correctly separate "this is feedback for you" from "this is my own parallel work," which is exactly the gap CLEO was built to close. The paper does not appear to report standardized trust/workload/safety questionnaire scores (e.g., NASA-TLX or a validated trust scale); its evidence is primarily qualitative/taxonomic (coded interaction patterns and interview themes) rather than statistical effect sizes.

## What is genuinely new

- Naming and empirically characterizing **concurrent interaction** — human and agent acting on the same artifact at the same time — as a distinct collaboration mode from sequential delegation, in agentic (not just chat-based) creative tools.
- The concept of **collaborative context awareness**: an agent's ability to interpret a human's simultaneous canvas actions as feedback versus independent work, and adapt execution mid-task rather than only at the start or end of a turn.
- A grounded taxonomy — five action patterns, ten codes, six triggers, four enabling factors — built from real professional designers' logged behavior, plus a released interaction-log dataset intended to support future research on human-agent co-creative collaboration.

## Limitations and open questions

- Both studies used small samples (10 professional designers each); it is not established from available sources how well these patterns generalize beyond UI/UX design work to other creative or technical domains.
- We could not confirm from available sources the exact underlying model/agent architecture behind CLEO, the full statistical methodology behind the reported percentages, or whether Study 1 and Study 2 used the same or different sets of designers, since the full PDF could not be fetched in this session — readers who need precise methodology should consult the paper directly.
- The paper does not appear to report a formal, quantified safety or workload evaluation of concurrent interaction (e.g., whether letting agent and human edit simultaneously introduces new error types); this is presented mainly as a design and taxonomy contribution rather than a controlled outcome study.
- Peer-review/venue status could not be independently confirmed at the time of writing.

## Practical implications

If these findings hold up, they suggest that builders of agentic creative tools (design copilots, coding agents, document editors) should design explicitly for concurrent interaction rather than assuming a strict prompt-wait-review loop: agents need a way to sense what a human is doing on a shared artifact *while* the agent is still working, and to distinguish "this is a correction for me" from "this is unrelated human work happening nearby." The released taxonomy of action patterns and triggers offers a concrete vocabulary designers of such systems could use when deciding which collaboration modes to support and how to surface them in the interface.

## Why you should care

Most public conversation about AI agents in creative and knowledge work assumes a delegate-and-wait model — you ask, the agent does the work, you check it after the fact. This paper is a useful corrective: it shows, with real professional designers, that once agents become visible collaborators, people naturally want to work *alongside* them, not just hand off to them and step away. That has real design consequences — an agent that can't tell the difference between a human correcting it and a human just doing their own thing nearby is going to frustrate exactly the kind of engaged, expert user it's meant to help most.
