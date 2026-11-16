# When Planning Agents Don't Ask the Right Questions: What Happens When an AI Scheduler Actually Talks to a Person

**Paper title:** From Questions to Decisions: Benchmarking How LLM Agents Acquire Decision-Relevant Information from Human Beings
**Authors:** Yuhan Tang, Ke Fan, Xinkai Zou, Baichuan Mo, Kangxin Cui, Ao Qu, Ou Zheng, Jiangbo Yu, Haris N. Koutsopoulos, Jinhua Zhao, Yuan Zhou
**Publication date:** 2026-11-09 (arXiv v1)
**Venue:** arXiv preprint, cs.AI; peer-reviewed venue not confirmed
**Paper link:** https://arxiv.org/abs/2611.13015
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-11-16

> **A note on sourcing:** this session's network access to arXiv and its usual mirrors (arxiv.org, export.arxiv.org, ar5iv, alphaXiv, Hugging Face, Semantic Scholar) was blocked by the environment's network policy, so the full PDF could not be opened directly. This summary is built from the paper's abstract and results excerpts as they surfaced across several web searches, cross-checked against each other for consistency. The paper is a freely available, open-access arXiv preprint. Numbers and quotes below are reported as they appeared in those excerpts; anything not independently confirmed against the primary PDF is marked accordingly. Author affiliations could not be confirmed and are marked "Not available." Please check the arXiv preprint directly before citing specific figures.

---

## The problem the paper addresses

Imagine asking an AI assistant to "schedule the drivers for next week" or "assign nurses to Monday's shifts." That request sounds complete, but it almost never is — maybe one driver just went on leave, or a nurse requested an unusual preference, and you forgot to mention it. A human colleague who knew something was missing would probably ask you about it before handing back a finished schedule. This paper asks whether today's large language model (LLM) agents do the same thing when they're put in charge of real planning tasks: when they're missing a piece of information that would change the plan, do they actually ask for it — and if they do ask, do they ask about the *right* things?

## Why this problem matters

LLM agents are increasingly being pointed at real operational planning jobs — scheduling, routing, staff assignment — where a wrong assumption doesn't just produce an awkward sentence, it produces an infeasible or costly plan. If an agent silently assumes missing facts instead of asking, the person who asked for help may not notice the plan is wrong until it's already been acted on. The paper's authors argue that most existing agent benchmarks dodge this problem entirely: they either hand the agent a fully specified task (so there's nothing to ask about) or simulate the "person on the other end" with an uncalibrated, scripted LLM response — which, as this paper shows, behaves nothing like how real people actually answer.

## What makes the system agentic

The systems under test are LLM-based planning agents that do more than answer a question in one shot. According to the paper's own description, an agent can ask the human "operator" clarifying questions, write an optimization/planning model, solve it, and then submit a final plan. That's a multi-step loop — gather information, formulate a model, solve it, decide whether more information is needed, and only then commit to an answer — which is evaluated as agent behavior (does it ask, what does it ask, does the resulting plan actually work) rather than as a single piece of generated text.

## How humans and the AI agent collaborate

The collaboration is structured as an interactive question-and-answer exchange embedded inside the planning process. The agent is handed an under-specified planning task; a human plays the role of the "operator" (the person requesting the plan, who holds information the agent doesn't have); and the agent can choose to interrupt its own planning process to ask that operator questions before finalizing a plan. The human's answers can supply, confirm, or correct facts that change what the optimal plan actually looks like.

## What role the human plays

Human participants act as the **operator** — the real-world stakeholder who holds decision-relevant facts the agent doesn't have (for example, a changed availability, an outdated constraint, or a preference that wasn't in the original request). When the agent asks a question, the human answers it based on what they know, including, crucially, volunteering (or failing to volunteer) a correction when the agent's assumption is wrong.

## What role the AI agent plays

The agent is the planner: it receives an initial, incompletely specified task, decides whether to ask clarifying questions, formulates a solvable planning model, and produces a plan. It has to balance asking enough to get a workable plan against asking so much that it becomes annoying or useless — the paper notes that simply asking *more* questions doesn't reliably mean asking the *right* ones.

## How control, initiative, and decisions are shared

This is a case of the **agent asking the human for clarification or assistance** mid-task: the agent, not a fixed script, decides when to pause and what to ask, and the human supplies real-world ground truth that the agent cannot infer on its own. Initiative is shared — the agent initiates each question, but the human controls what information actually comes back, including whether they spontaneously correct a wrong assumption the agent never directly asked about.

## The paper's main idea

**The authors' claim:** real people do not answer agents' questions the way today's benchmarks assume. Specifically, the authors report that human operators frequently *omit* a fact that would correct the agent's plan — more often than an uncalibrated simulated user does — which means benchmarks relying on scripted or uncalibrated LLM "users" are testing agents against an easier, unrealistic version of the clarification problem. Their broader point is that acquiring decision-relevant information through interaction, not just reasoning well once information is given, is itself a major unsolved bottleneck for LLM planning agents.

## How the approach works

The authors built **Ask2Decide**, a benchmark of 43 planning tasks (drawn from operational domains like scheduling and resource/staff assignment) in which some task-relevant information is deliberately withheld from the agent at the start. An agent facing each task can ask the simulated/human "operator" questions, then must write and solve a planning model and submit a plan. To understand how real people behave as that operator, the authors ran a human-subjects data collection: **19 participants completed 79 interaction sessions**, answering agent-style questions during these planning tasks. Comparing those real responses against an uncalibrated LLM-simulated user, the authors found large behavioral differences — most notably, humans left out a correcting fact far more often (43% of the time) than the uncalibrated simulated user did (7% of the time). They then used this human-response data to build **CalOp**, a simulated operator explicitly calibrated to match observed human reply patterns, so that future agent evaluations don't have to rely on an unrealistic simulated user.

## Human study or evaluation design

This combines a **real human-subjects interaction study** (used to characterize how people actually answer clarifying questions, and to calibrate a simulator) with a **benchmark evaluation of frontier LLM agents** against both the human-calibrated simulator and uncalibrated baselines across the 43 Ask2Decide tasks. It is not a randomized controlled trial comparing competing agent designs head-to-head with users; rather, it is a measurement study of (a) how humans actually respond as information-holders during agent-led planning, and (b) how well current LLM agents exploit that interaction to get decision-relevant facts.

## Participants and study setting

**19 human participants**, generating **79 interaction sessions** in which they played the "operator" role answering an LLM planning agent's clarifying questions during under-specified planning tasks. Further demographic and recruitment detail was not confirmed from the sources used here — check the full paper for participant background and task assignment details.

## Experiments or benchmarks

**Ask2Decide**: 43 planning tasks with deliberately withheld decision-relevant information, used to evaluate four frontier LLM agents on whether and how well they elicit missing facts before committing to a plan, comparing performance under full information, no information-seeking, and interaction with either the human-calibrated simulated operator (CalOp) or an uncalibrated simulated user.

## Main results

**As reported by the authors (surfaced via search excerpts, not independently re-verified against the primary PDF):**
- Across four frontier LLMs, initial plans were **infeasible on 58–98% of tasks** when relevant information was missing and had to be elicited, compared with only **5–28% infeasible** when all facts were given upfront.
- Real human operators **omitted a correcting fact 43% of the time**, versus just **7% of the time** for an uncalibrated LLM-simulated user — a large gap showing that uncalibrated simulated users behave much more cooperatively/forthcoming than real people do.
- Agents uncovered facts that would actually **change the optimal plan only slightly more often (39–52%)** than facts that would leave the plan **unchanged (32–41%)** — i.e., agents aren't reliably distinguishing which questions matter most for the decision at hand.
- One frontier model reportedly asked many questions per task (around 11 per episode in one cited example) without proportionally improving at surfacing the facts that actually mattered — asking more wasn't the same as asking well.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's human-related contribution is less about measuring trust or workload in a live collaborative task, and more about **characterizing how real humans behave as the information source an agent must query** — and showing that this behavior differs substantially from what agent benchmarks typically assume. The practical implication for decision quality is direct: because real operators under-volunteer corrections about as often as they do (43% omission), an agent that doesn't ask precisely the right follow-up question is likely to proceed on a wrong assumption, with the plans' infeasibility rates reported above as the downstream consequence.

## What is genuinely new

*Authors' framing, as surfaced in the sources used here:* a benchmark that tests LLM planning agents specifically on **acquiring** decision-relevant information through interaction (not just reasoning over given information), paired with a real human-subjects study showing that existing uncalibrated LLM-simulated users are a poor stand-in for actual human answering behavior — plus a new calibrated simulated operator (CalOp) built directly from that human data to make future evaluations more realistic.

## Limitations and open questions

- *My interpretation:* the human study is modest in scale (19 participants, 79 sessions), which is enough to reveal a clear and large behavioral gap from simulated users but may not capture the full diversity of how different kinds of real-world stakeholders (e.g., domain experts vs. non-experts) would answer.
- The paper doesn't appear to report a live, task-level comparison of human trust, workload, or satisfaction when working with these agents — its human-subject contribution is about calibrating how operators answer, not about evaluating the end-to-end collaborative experience.
- Exact per-model figures, task domains, and statistical detail should be checked against the primary PDF before being cited precisely, since this summary relies on secondary search excerpts rather than a direct reading of the paper.
- It remains an open question whether the CalOp simulator, calibrated on this specific participant pool and these specific tasks, generalizes to other planning domains or other populations of real-world operators.

## Practical implications

*My interpretation, following the authors' own stated motivation:* anyone deploying an LLM agent to plan on a person's behalf — scheduling, staffing, routing — should not assume that giving the agent a question-asking tool solves the information-gap problem. This paper suggests two concrete lessons: (1) evaluate agents against realistic, human-calibrated models of how information-holders actually respond, not against easier uncalibrated LLM "users," and (2) specifically test whether an agent's questions target the facts that would actually change the plan, since asking more questions is not the same as asking the right ones.

## Why you should care

This paper is a useful reality check for the growing wave of "agentic" planning tools: it's not enough for an agent to have a tool for asking clarifying questions — it has to ask about the facts that matter, and it has to be evaluated against how real people actually answer, not an idealized stand-in. The headline finding that real humans omit corrections six times more often than a naive simulated user (43% vs. 7%) is a sharp, concrete illustration of why benchmarks built on simulated users can make agents look far more collaboration-ready than they actually are in practice.
