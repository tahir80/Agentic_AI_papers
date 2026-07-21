# Overseeing Agents Without Constant Oversight: Challenges and Opportunities

**Authors:** Madeleine Grunde-McLaughlin (University of Washington; work completed during an internship at Microsoft Research), Hussein Mozannar, Maya Murad, Jingya Chen, Saleema Amershi, Adam Fourney (Microsoft Research)
**Publication date:** 2026-02-18 (arXiv id 2602.16844, v1, cs.HC)
**Venue:** arXiv preprint. The PDF is formatted using an ACM conference template with a placeholder ("enter the correct conference title from your rights confirmation email"), suggesting a conference submission, but the specific venue and acceptance status are not confirmed in the manuscript itself.
**Paper link:** https://arxiv.org/abs/2602.16844
**Code link:** https://github.com/microsoft/Magentic-UI (the open-source computer-use agent studied in the paper; this paper's own study materials, tasks, and interface prototypes do not appear to be separately published)
**Project page:** Not available
**Date added:** 2026-07-21

> **A note on sourcing:** unlike other entries in this log, this summary is written directly from a full read of the paper's PDF (all 26 numbered pages plus appendix), not from search snippets — arXiv itself is unreachable from this research session's network, but the user supplied the PDF directly. Facts below reflect what the paper actually reports; where something wasn't stated in the text we read, it's marked "not available."

---

## The problem the paper addresses

Modern "computer-use agents" (CUAs) — AI systems that can browse the web, run code, and edit files on your behalf — are increasingly capable of completing multi-step tasks with little supervision. To keep a human meaningfully in charge, these systems show you a "trace": a record of the plan they made, the steps they took, and screenshots along the way. But there's a real design puzzle underneath that seemingly simple idea — if the trace lists every tiny action, it's exhausting to read and people miss mistakes anyway; if it's compressed into a short summary, it may hide the very details that would reveal an error. This paper asks: does the way we currently display an agent's trace actually let people catch its mistakes?

## Why this problem matters

Human oversight is supposed to be the safety net for autonomous agents — the whole idea of "human-in-the-loop" design is that a person can catch and correct an agent's errors. But that safety net only works if people can actually find the errors, without spending as much effort as it would take to do the task themselves. If existing trace designs create only an "illusion of accountability" — technically letting a human review the work, but not actually equipping them to catch problems — then oversight isn't really providing the safety it's assumed to.

## What makes the system agentic

The paper studies Magentic-UI, a computer-use agent built on Microsoft's AutoGen framework. It plans a multi-step approach to a task, then autonomously browses the web, executes code, and manipulates files inside a contained Docker environment to carry it out — for example, adding a specific pizza to an online shopping cart, or searching multiple recipe sites to compile a CSV of matching recipes. It supports human-in-the-loop features like co-planning (reviewing/editing the plan before it runs), co-tasking (taking over the live browser), action approval for risky steps, and running multiple tasks at once. The studies used real runs of the system (backed by GPT-4o, and later GPT-5), and the paper's whole contribution is about how well people can verify this agent's actual, autonomous multi-step task execution — squarely an agent-level evaluation, not a language-model one.

## How humans and the AI agent collaborate

Across three studies, people were given tasks that Magentic-UI had already completed (or, in the first study, completed while the person multi-tasked with other work) and asked to determine whether the agent's final answer was actually correct. To do that, they had access to varying forms of the agent's trace — from the existing verbose, screenshot-heavy display, to three experimental redesigns, to a final interface combining what the authors learned. This is fundamentally about **post-hoc verification**: the human is not steering the agent mid-task in this study, but deciding, after the fact, whether to trust what it produced.

## What role the human plays

The human is the reviewer and final judge. They read the agent's plan and trace, examine screenshots and (in later studies) a checklist of "requirements" and "assumptions," and decide "yes," "no," or "insufficient information" on whether the agent's answer is correct — then explain why in their own words. In the first (formative) study, participants also multi-tasked, splitting attention between other work and reviewing the agent, mirroring how people are likely to actually use such systems day to day.

## What role the AI agent plays

Magentic-UI does the actual task: forming a plan, browsing sites, running code, and generating a final answer, while producing a trace of what it did — planned steps, individual actions, screenshots, and (for the final study) a checklist of requirements it believed it had satisfied and assumptions it had made along the way (e.g., guessing a museum-membership price when the exact figure wasn't posted).

## How control, initiative, and decisions are shared

This is squarely about **human oversight of an already-autonomous agent**, rather than moment-to-moment shared control: the agent runs the full task by itself, and the human's role is to catch errors afterward. The paper is explicit that this only covers one slice of the oversight picture (post-hoc verification with a binary correct/incorrect framing) and explicitly flags "during-execution" intervention and co-planning-stage clarification as separate, related directions it doesn't test here.

## The paper's main idea

**Claim by the authors:** the standard approach many human-in-the-loop agentic systems take — describing and summarizing the planning steps and actions taken — does not adequately support effective human verification. Listing every action in full detail is overwhelming and verbose; summarizing it away can hide execution errors. The authors argue the fix isn't necessarily "the right level of detail" in the abstract, but giving people **navigation** — an outcome-oriented overview (what the agent claims it did/found) that lets a reviewer drill down into the specific execution details behind any claim, rather than forcing an all-or-nothing choice between a wall of steps and a hollow summary.

## How the approach works

The authors ran three sequential studies. First, a **formative study** (n=12) had participants review Magentic-UI's existing interface — a step-by-step plan/action trace plus screenshots — while multi-tasking on three researcher-assigned tasks (e.g., adding an item to a cart, compiling a CSV of recipes, computing museum-pass savings). This surfaced that the existing trace is verbose and that small errors get missed. Second, a **design-probe study** (n=12, 8 of whom overlapped with study 1) tested three new ways of summarizing the trace in a Wizard-of-Oz setup: a **Flowchart** (process-oriented, showing the sequence of steps as a diagram), a **Citation** (a short justification with clickable, cited evidence), and a **Specification/Spec** (an outcome-oriented checklist of requirements the answer needed to satisfy, plus a list of assumptions the agent made). Third, a **controlled study** (n=12, no overlap with the earlier studies) built a final interface around the Spec design — adding direct links from each requirement/assumption to the relevant screenshot or trace text — and compared it, in a counterbalanced within-participant design, against a baseline that reproduced the existing Magentic-UI interface. All three studies were IRB-approved, in-person, about an hour long, and used real runs of the agent (not simulated).

## Human study or evaluation design

**Demonstrated in the paper:** three separate real-participant HCI studies (formative, design-probe, controlled), each with 12 participants, all employees of a large technology firm with prior experience using agentic tools. The controlled study specifically measured, for each of two tasks per condition (two correct, two incorrect outputs), whether participants judged the agent's answer as correct, how long they took, and how confident they were on a 1–7 scale, then analyzed effect sizes (Hedges' g, an unbiased version of Cohen's d) with 95% confidence intervals rather than relying on statistical significance from a small sample.

## Participants and study setting

All 36 participant-slots (12 per study, with 8 people appearing in both the formative and design-probe studies) were real employees of a large technology firm with some existing experience with agentic tools — not crowdworkers or simulated personas. Sessions were in person (ten of twelve in-person and two virtual in the controlled study) with a pre-installed system, lasted about an hour including a semi-structured interview, and were IRB-approved.

## Experiments or benchmarks

There's no public leaderboard-style benchmark; tasks were adapted from **AssistantBench**, chosen and modified so they couldn't be verified from a single screenshot and, where needed, so answers stayed valid despite the world having changed since the benchmark was created. Each study used two-to-three tasks with known ground-truth correctness (a mix of correct and intentionally incorrect agent outputs).

## Main results

**Demonstrated in the paper:**
- **Formative study:** with the existing trace design, the human-agent team completed only 1 of 9, 5 of 10, and 2 of 12 attempts correctly across the three tasks (excluding runs lost to timeouts/technical issues) — participants frequently missed small but consequential errors (e.g., an added item that didn't match the request, or a museum price the agent estimated rather than confirmed).
- **Design-probe study:** the outcome-oriented Specification design had the highest error-finding accuracy (77.14% averaged across conditions) but also took the longest to review; the process-oriented Flowchart had the lowest accuracy and was least preferred.
- **Controlled study:** the final linked-Specification interface reduced review duration with a small-to-medium effect overall (Hedges' g −0.29, and −0.65 specifically when participants correctly caught a wrong answer), but did **not** meaningfully improve accuracy (g 0.18, confidence interval crossing zero). Confidence rose with a medium-to-large effect (g 0.56 overall), and the effect was largest and most concerning (g 0.85) exactly in cases where the agent's answer was wrong but the participant said it was correct.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper:** the study directly measures verification **accuracy**, **time-to-decision**, and **self-reported confidence** as its core outcome variables — a more rigorous, quantified take on "does this design actually help oversight" than most entries in this collection. **Our interpretation:** the standout, if uncomfortable, finding is that a better-designed interface made people faster and more confident without making them more correct — and the confidence increase was concentrated precisely in the cases where people were wrongly trusting a bad answer. That's a fairly direct empirical warning about overreliance/miscalibrated trust: an interface can look and feel like it's improving oversight while doing nothing to catch more real errors, or even encouraging misplaced confidence.

## What is genuinely new

- A rare **quantified, effect-size-based comparison** of trace/summary designs for a real, deployed computer-use agent (rather than a purely qualitative interview or a single-condition usability study), using HCI-recommended reporting of Hedges' g and confidence intervals given the small sample.
- Clear evidence that verbosity and summarization pull in opposite directions for oversight — detailed traces are accurate-but-overwhelming, high-level summaries are scannable-but-error-hiding — and a concrete design response (linking an outcome-oriented checklist directly into the underlying trace) aimed at getting both at once.
- A direct empirical demonstration that a design intervention can speed up review and raise confidence while leaving actual accuracy essentially unchanged — a caution against treating "faster, more confident reviewers" as proof that oversight has improved.
- Documentation of a subtler oversight challenge: participants held **subjective, shifting definitions of "correct enough"** (e.g., accepting 5 of 6 requested recipes as "probably good enough"), which existing benchmark-style single-answer correctness criteria don't capture.

## Limitations and open questions

- The authors note their participants were all employees of one large technology firm with prior agent experience — not representative of the broader public who might use these tools.
- Only one CUA system (Magentic-UI) was tested; other agents or reasoning models that also rely on long traces as explanation may behave differently.
- The study covers only **post-hoc** verification (reviewing a completed task) — not during-execution intervention, co-planning-stage steering, or the earlier action-approval features Magentic-UI itself supports.
- Confidence was measured on a self-defined 1–7 scale rather than a validated psychometric instrument, which the authors flag as worth revisiting given how large and consequential the confidence effect was.
- Because the controlled study gave participants browser access to double-check the agent's work themselves, the authors note this may have evened out differences between conditions relative to more typical, lower-effort daily use.

## Practical implications

For anyone building or deploying human-in-the-loop agent products — Magentic-UI itself, OpenAI's Operator, GitHub Copilot's coding agents, or similar CUAs — this paper is direct evidence that simply showing users a plan-and-action trace is not enough, and that summarization choices have real, measurable tradeoffs between reviewer speed, confidence, and actual error-catching. The authors' concrete recommendation is to combine an outcome-oriented overview (what was found/assumed) with easy navigation into the underlying execution detail, rather than forcing a choice between a wall of steps and a compressed summary — while cautioning that even a well-liked design can boost false confidence without boosting accuracy.

## Why you should care

This is one of the more methodologically careful entries in this collection on the "human oversight of agents" theme: three sequential real-user studies, a system genuinely capable of autonomous multi-step web/code/file actions, and a clean quantitative result that separates *feels more manageable* from *actually catches more errors*. As agentic tools proliferate, this paper is a concrete, evidence-based reminder that oversight interfaces need to be evaluated on whether they change what people actually get right — not just on whether people like using them or feel more confident afterward.
