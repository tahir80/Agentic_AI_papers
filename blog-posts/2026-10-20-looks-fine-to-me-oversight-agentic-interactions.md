# "Looks Fine to Me": Why People Miss the Quiet Mistakes of Coding Agents

**Paper title:** Looks Fine to Me: Understanding Oversight in Agentic Interactions
**Authors:** Dinithi Dissanayake, Pattie Maes, Suranga Nanayakkara, and four further co-authors (names not confirmed from the sources used)
**Publication date:** 2026-10-20 (arXiv v1)
**Venue:** arXiv preprint, cs.HC; not peer-reviewed, peer-reviewed venue not confirmed
**Paper link:** https://arxiv.org/abs/2610.27801
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-10-25

> **A note on sourcing:** the full text of the paper could not be opened in the environment this summary was written in (arXiv and its mirrors were blocked at the network layer; the paper itself is an open-access preprint). This summary is built from the paper's abstract and the excerpts of its HTML page that surfaced in search results, cross-checked across several queries. Exact statistics, effect sizes, participant demographics, the agent's implementation, and the full set of limitations were **not** verified; those are marked "not available". Please check the arXiv preprint before citing numbers.

---

## The problem the paper addresses

When an AI coding agent hands you its work, someone has to decide: is this right, or should I look harder? The authors define effective oversight as recognizing *when* closer evaluation is needed and re-engaging at the right moment. The trouble is that agents often produce output that looks plausible. This paper asks what people actually do when they supervise an agent whose mistakes don't announce themselves.

## Why this problem matters

Most proposals for safe agents lean on "a human will review it." That only works if humans notice problems. Think of proofreading your own essay: the typos you can't see are the ones you've stopped looking for. If people wave through confident-looking agent output, human review gives a false sense of safety.

## What makes the system agentic

Participants worked on programming tasks with an AI coding agent. Per the abstract, the agent produced code that was then checked by hidden pre-merge checks, so it acts on a goal and produces working software rather than a single chat reply. The agent's underlying model, tools, and architecture were **not confirmed** from the sources used. Note that the paper's focus is the human side of oversight, not agent capability.

## How humans and the AI agent collaborate

A person gives the task and then reviews what the agent returns, deciding whether to accept it or dig deeper. The collaboration is review-and-accept supervision, not live co-working.

## What role the human plays

The human is the reviewer and final decision-maker: they run checks, read code, form a judgement and report how confident they are.

## What role the AI agent plays

The agent does the programming work. In the experiment its behaviour was controlled so that, per task, it either produced a correct solution, a **silent defect** (a plausible bug that passed the hidden checks, with no visible warning), or a **visible failure** (the checks fail visibly).

## How control, initiative, and decisions are shared

The agent does the work; the human holds the accept/reject decision. As far as the sources show, initiative sits with the agent for production and with the human for deciding when to scrutinize. Whether the agent offered any oversight support was not confirmed.

## The paper's main idea

**Claim by the authors:** oversight is not a single act of "reviewing". It can be studied through what people do, look at, feel and say, and doing so can inform future systems that prompt people to re-engage at the right moment.

## How the approach works

The authors treat oversight as something to be measured, not a tool to be built. They compare how people behave across three kinds of agent output (correct, silent defect, visible failure) and combine several data streams: task outcomes, interface interaction logs, first-person-view and gaze sensing, physiological sensing (heart signals via PPG/HRV), and self-reports.

## Human study or evaluation design

- A **formative study with 12 participants** found that users accepted plausible outputs without thorough evaluation and recognized the lapses only in hindsight (as reported by the authors).
- A **within-subject main study with 36 participants** did Python programming tasks with the coding agent across the three output conditions.

## Participants and study setting

Real human participants (12 formative, 36 main). Recruitment, expertise, and demographics: **Not available**. The setting was a controlled lab-style study with wearable/eye and physiological sensing.

## Experiments or benchmarks

No public benchmark. Custom programming tasks and hidden pre-merge checks as ground truth. Dataset/code release: not available.

## Main results

**Reported by the authors (from the abstract):** participants were often highly confident while missing silent defects. They tended to perform generic checks, failed to generate diagnostic evidence, or misinterpreted the evidence they did find. When a failure was visible, people were able to spot faulty outputs. Specific rates, effect sizes, and gaze/physiology findings were **not verified**.

## Effects on human performance, trust, workload, safety, or decision quality

The main demonstrated effect concerns **decision quality and calibration**: high confidence did not go along with catching silent defects. Effects on workload and trust as measured constructs were not confirmed from the sources used.

## What is genuinely new

*Authors' framing, not independently assessed:* an oversight study of an agentic coding setting that goes beyond outcomes, pairing behavioural logs with gaze, physiological, and self-report data, and that separates silent defects from visible failures.

## Limitations and open questions

- *My interpretation:* a single task domain (Python) and a short lab session may not carry over to real engineering workflows.
- The agent was presented with controlled error conditions, so real-world error rates and types may differ.
- The paper studies oversight; it does **not** (as far as verified) evaluate an intervention that improves it. So it does not show a collaboration design that works.
- Full-text details (sample demographics, statistics, limitations section) were not verified.

## Practical implications

*My interpretation:* don't treat "a human reviews it" as a safety guarantee. Tools may need to nudge reviewers at moments when output looks fine but verification is warranted, and give them ways to produce diagnostic evidence (tests, traces) rather than eyeballing.

## Why you should care

If you use coding agents, the dangerous bug isn't the one that crashes; it's the one that looks fine. This study, with real participants, is evidence that confidence and correctness come apart in agent oversight. It does not yet tell us how to fix that.
