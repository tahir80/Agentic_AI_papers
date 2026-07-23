# Human Tool: Treating People Like an API an AI Agent Can Call

**Paper title:** Human Tool: An MCP-Style Framework for Human-Agent Collaboration
**Authors:** Yuanrong Tang, Huiling Peng, Bingxi Zhao, Hengyang Ding, Hanchao Song, Tianhong Wang, Chen Zhong, Jiangtao Gong (Tsinghua University, with co-authors affiliated with Zhejiang University, Beijing Jiaotong University, The Hong Kong University of Science and Technology, and Anhui University)
**Publication date:** 2026-02-13 (arXiv v1, cs.HC)
**Venue:** arXiv preprint. No confirmed peer-reviewed venue or acceptance was found.
**Paper link:** https://arxiv.org/abs/2602.12953
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-07-23

> **A note on sourcing:** arXiv and general web pages were unreachable from this research session's network (an organization egress policy blocked direct fetches, including to arxiv.org itself), and this is an unattended scheduled run with no user available to supply the PDF directly. This summary is instead built from many independent, cross-checked web searches that surfaced direct excerpts of the paper's abstract, method section (sample size, task design, procedure), results (specific means/SDs for both tasks), and limitations/discussion text. Numbers below (e.g., N=33, task scores, workload figures) appeared consistently across multiple independent searches, which is why they are reported with confidence — but this is not the same as a full linear read of the PDF, so some structural details (e.g., exact statistical tests used) could not be verified and are omitted rather than guessed.

---

## The problem the paper addresses

As AI agents get better at complex, multi-step work, they increasingly outperform humans on parts of a task — but humans are still the ones legally and practically responsible for the outcome (approving a plan, catching a bad decision, supplying judgment the AI lacks). Most human-AI collaboration tools today put the human in the driver's seat, asking them to supervise, approve, or correct the AI at every turn. The authors ask a different question: what if the AI is in charge of orchestrating the work, and calls on a human only when — and exactly when — human judgment is the more valuable resource for that specific moment?

## Why this problem matters

Continuous human supervision doesn't scale: it burns attention and creates a "management burden" where people spend more effort coordinating with the AI than actually contributing their expertise. But removing humans from the loop entirely risks losing exactly the judgment, values, and contextual knowledge that AI still struggles to supply. The paper is trying to find a middle path — one where an AI system can lead a task end-to-end but still knows how to selectively "reach out" for a human's input, the way a well-run team routes questions to whichever teammate is best positioned to answer them.

## What makes the system agentic

Human Tool is built as a Model Context Protocol (MCP)–style extension: in modern LLM agent systems, MCP is the standard by which an agent discovers and calls external "tools" (a calculator, a search API, a code interpreter). This paper's central technical move is to expose **a human being as one more callable tool** in that same interface. The agent plans a task, decides at each step whether a computational tool or a human is the better resource to invoke, calls the human tool when appropriate, and integrates the human's response back into its ongoing plan — the same multi-step, tool-using, goal-directed loop that defines any agentic LLM system, just with a person wired into the toolbelt.

## How humans and the AI agent collaborate

The AI, not the human, drives the workflow. It's described as "AI-led" and "proactive": the agent decides when to bring the human in, based on a structured model of what that person can contribute. The paper is explicit that calling someone a "tool" here is a coordination abstraction, not a demotion — the framework is built specifically to preserve human authority and responsibility even while the AI handles orchestration.

## What role the human plays

Humans contribute exactly where they have a comparative advantage — supplying preferences, judgment calls, missing information, or approvals that the AI can't infer on its own. Their input is captured through structured "schemas" covering three things: what they're capable of doing, what information only they hold, and what authority (approval power) they carry. Beyond that, the humans in the study also acted as the two human-subjects study's participants: they performed real collaborative tasks (see below) and reported afterward on effort, control, and how well-supported they felt.

## What role the AI agent plays

The AI is the orchestrator. It plans the task, executes what it can on its own, and treats the human as a resource to invoke on demand rather than a constant supervisor to check in with. According to the authors, this is meant to let the AI "do the dirty work" — handling routine coordination and busywork — while directing genuine decision-making moments to the person.

## How control, initiative, and decisions are shared

This is the paper's central design question, and its answer is a form of **mixed initiative with the AI holding the default initiative**: the agent proactively drives the task and only cedes the floor to the human at moments it identifies as needing human capability, information, or authority. That's a deliberate contrast to two more familiar patterns — an AI that must ask permission at every step (human-led, high oversight) or an AI that never asks at all (fully autonomous). Human Tool sits in between, with the AI making the call about *when* to hand off.

## The paper's main idea

Treat "asking a human" as a first-class, structured tool call — with a defined schema for what that person can offer — rather than an ad hoc interruption, a rigid approval gate, or a vague "human-in-the-loop" checkbox. Doing so, the authors argue, lets an AI-led system stay efficient most of the time while still drawing on human strengths exactly when they matter most.

## How the approach works

The framework operationalizes "Human Tool" through structured tool schemas describing a human's capabilities, the information only they possess, and the authority they hold to approve or decide. The AI agent's planning loop can invoke this human-tool schema the same way it would invoke any computational tool, dynamically choosing to call on a person when the task benefits from what only a human can supply, and folding the resulting input back into its ongoing plan through what the authors describe as an efficient, natural interaction protocol.

## Human study or evaluation design

The framework was tested in a controlled, within-subject, counterbalanced human-subjects study comparing **Human Tool** against an **AI Tool** baseline (an AI-led system without the structured human-invocation mechanism) — the only manipulated variable between conditions. Each participant completed two comparable task instances in a single task domain, one per condition, with both the order of conditions (AB/BA) and the assignment of specific task instances to conditions counterbalanced to control for order and content effects. Each task run was time- and turn-limited to 15 minutes, followed by task-specific questionnaires and a short semi-structured interview; a full session took about 1.5 hours per participant.

## Participants and study setting

33 participants were recruited; one was excluded after a system error, leaving **32 analyzed participants**, aged 21–35 (M = 25.24, SD = 3.38). Participants were split into two task domains, 16 people per domain:

- **Travel Planning (TP)** — a constrained decision-making task where the participant and AI co-developed a multi-day itinerary under budget and dataset-grounded constraints.
- **Story Writing (SW)** — a creative task, structure not fully detailed in the excerpts available, but treated as the paper's second, creativity-oriented domain.

## Experiments or benchmarks

There is no public benchmark or released dataset; this is a bespoke, task-specific lab study built to compare the Human Tool framework against the AI Tool baseline across the two domains above.

## Main results

**As reported in the paper (from directly-quoted result figures):**

- **Travel Planning accuracy:** Human Tool group M = 86.72 (SD = 18.52) vs. AI Tool group M = 72.66 (SD = 12.26) — a reported 19.34% relative gain.
- **Story Writing quality:** Human Tool group M = 68.38 (SD = 5.11) vs. AI Tool group M = 58.56 (SD = 11.05) — a reported 14.35% relative gain.
- **Workload (mental effort, Story Writing):** Human Tool group M = 70.625 (SD = 31.07) vs. AI Tool group M = 87.875 (SD = 27.14) — a reported 19.63% relative decrease (lower is better).
- **Collaboration Support Index (a composite measure of how well the system supported collaboration):** Human Tool M = 75.48 (SD = 10.22) vs. AI Tool M = 52.83 (SD = 15.58) — substantially higher for Human Tool.

Participants reportedly described the AI Tool baseline as imposing a higher "management burden," while Human Tool was described as handling more of the coordination overhead ("doing the dirty work"), shifting participants' effort away from managing the AI and toward the substantive parts of the decision.

## Effects on human performance, trust, workload, safety, or decision quality

Across both tested domains, selectively invoking the human — rather than treating them as a constant supervisor — is reported to have simultaneously **improved task outcomes** (higher accuracy/quality scores), **reduced self-reported mental workload**, and **produced a more favorably-rated collaboration experience**, relative to the AI Tool baseline. This is a notable combination: many human-AI interfaces trade off performance against comfort/workload (more oversight often means more effort); here the authors report gains on both axes at once. Some participants, however, described feeling "carried along" by the AI's strong guidance — a caution flagged by the authors themselves rather than a strictly positive finding.

## What is genuinely new

**Authors' claimed contribution:** taking MCP-style tool abstractions — designed for exposing computational functions to an LLM agent — and extending that same interface pattern to a human being, with an explicit schema for capability, information, and authority. This reframes "human-in-the-loop" from a vague design principle into a concrete, callable interface an agent's planner can reason about directly, alongside its other tools.

**Demonstrated (this study):** in two controlled tasks, this selective, agent-initiated invocation pattern outperformed an AI-led baseline without it, on both task quality and self-reported workload/collaboration measures.

## Limitations and open questions

The authors state directly:
- The evaluation covers **only two tasks in a controlled lab setting**, which may not generalize to longer-horizon or higher-stakes work.
- The study lacked **direct time-based efficiency measures**; the authors recommend future work incorporate these.
- Some participants reported feeling **"carried along"** by the AI's proactive guidance, suggesting a tension between efficient AI-led orchestration and participants' sense of control/authorship. The authors suggest future designs add lightweight checkpoints to preserve proactive orchestration while making user control more explicit.

**Open question we'd add:** the study's tasks (travel planning, story writing) are collaborative-but-low-stakes; it remains untested whether AI-initiated, schema-based human invocation holds up in safety-critical or adversarial settings where a human might need to intervene even when the AI hasn't decided to ask.

## Practical implications

For anyone building agentic systems that need real human input — approvals, missing context, subjective judgment calls — this paper offers a concrete design pattern: model the human as a structured, invocable resource (with defined capability/information/authority) inside the same tool-calling interface the agent already uses for everything else, rather than bolting on a separate "ask the user" chat sidebar or a blanket approval gate. It's directly relevant to teams designing AI copilots, planning assistants, or agentic workflow tools where the AI does most of the driving but still needs a principled way to know when to hand the wheel to a person.

## Why you should care

Most human-AI collaboration advice defaults to one of two extremes: keep a human watching everything, or let the AI run free. This paper is a real, human-subjects-tested example of a third option — an AI that leads but has been explicitly taught when asking a human is the better move — and it reports that doing so can make people *both* more effective and less exhausted, not just one or the other. That's a useful data point for anyone deciding how much control to hand an agent versus keep for themselves.

---

*Claims attributed to "the authors" or "the paper" reflect what is stated in arXiv:2602.12953 as surfaced through corroborated search excerpts of the abstract, method, results, and limitations sections; passages marked as interpretation or "we'd add" are the summary writer's own reading and are not asserted by the paper itself.*
