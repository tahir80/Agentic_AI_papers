# Reading the Code Isn't Enough: Why Careful Developers Still Wave AI Agents Through on Risky Actions

**Paper title:** From Delegation to Action Approval: An Exploratory Study of Developers' Practices in Collaborating with AI Coding Agents
**Authors:** Yinan Wu, Dominik Wermke, Ze Shi Li, Kathryn T. Stolee, Bowen Xu
**Publication date:** 2026-11-06 (arXiv v1)
**Venue:** arXiv preprint, cs.SE; peer-reviewed venue not confirmed
**Paper link:** https://arxiv.org/abs/2611.10058
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-11-14

> **A note on sourcing:** this session's network access to arXiv and its mirrors (arxiv.org, ar5iv, alphaXiv, Hugging Face) was blocked by the environment's network policy, so the full PDF could not be opened directly. This summary is built from the paper's abstract and results excerpts as they surfaced across several web searches, cross-checked against each other. The paper is a freely available, open-access arXiv preprint. Numbers and quotes below are reported as they appeared in those excerpts; anything not independently confirmed against the primary PDF is marked accordingly. Please check the arXiv preprint directly before citing specific figures.

---

## The problem the paper addresses

When a developer uses an AI coding agent, there's an old, familiar step: read the code it wrote before you accept it. But modern coding agents don't just write code anymore — they run shell commands, read and write files, call external tools, and take other actions as part of doing the work. Those actions often ask for a separate kind of approval, a quick "allow this?" prompt, that's different from reviewing a diff. This paper asks a simple but under-studied question: when developers already review code carefully, do they *also* scrutinize those separate action-approval prompts carefully — or does careful code review quietly substitute for action oversight that never actually happens?

## Why this problem matters

A shell command or a file read can do things a code diff never shows you. Deleting a file, exfiltrating data, modifying something outside the project, or hitting a production system are all examples of effects that leave no trace in the code the agent eventually produces — by the time you're looking at the generated code, the risky action already happened or didn't. If developers assume that reviewing code is "enough" oversight, they may be leaving a whole category of agent behavior essentially unsupervised, even while feeling diligent. As coding agents are given more autonomy and more tool access, this gap between "I reviewed the code" and "I approved the actions" becomes a real safety and trust question, not a theoretical one.

## What makes the system agentic

The subject of the study isn't a single tool the authors built — it's the real AI coding agents developers already use day to day (the kind built on large language models that can plan multi-step work, call tools, execute shell commands, read/write files, and take actions in a developer's environment rather than just emitting a text suggestion). These agents are evaluated here in their natural habitat: real developers' real workflows, where the agent proposes actions and the human has to decide, action by action, whether to let it proceed.

## How humans and the AI agent collaborate

The collaboration happens through a two-layer gate: first the agent proposes code and/or an action; then the human either reviews the generated code, approves/rejects the specific action (running a command, touching a file, calling a tool), or — as the paper finds — does some mix of both with very different levels of care. The agent's job is to keep working within whatever boundary the human sets; the human's job is to set and enforce that boundary, action by action, across a session that may include many such approval requests.

## What role the human plays

The human developer is the gatekeeper for both the *output* (the code) and the *process* (the actions the agent takes to get there). In practice, this paper shows those are two distinct jobs that the same person has to do, and that doing one well doesn't guarantee doing the other well.

## What role the AI agent plays

The agent proposes and, once approved, executes actions with real side effects — not just code suggestions. It also, per the authors' framing, can request approval in ways that make the human's job easier or harder: showing (or not showing) what the action will actually do before asking for a green light.

## How control, initiative, and decisions are shared

This is human oversight of a semi-autonomous agent, exercised through a stream of discrete approval decisions rather than one big up-front delegation. The agent takes the initiative to propose actions; the human retains a veto at each step — but the paper's central finding is that this veto is exercised unevenly: rigorously for code, more loosely for actions, and with scrutiny that erodes further as a session goes on.

## The paper's main idea

**The authors' claim:** careful code review does not reliably carry over into careful action approval. These are separable forms of oversight, and developers' survey-reported behavior shows many of them are strong on one and weak on the other — specifically, strong on code review while being comparatively lax on approving actions that never show up in the code at all.

## How the approach works

The authors surveyed developers who use AI coding agents (reportedly recruited through a mix of a developer community channel and the Prolific platform) about their habits: how carefully they review generated code, how carefully they review and approve different categories of agent actions (e.g., running shell commands, reading files, and other action types), what safeguards they rely on, and what would make them trust an agent with more autonomy. They then related self-reported code-review carefulness to self-reported action-approval carefulness within the same respondents, and looked at how approval behavior varied by developer, by action type, and over the course of a session.

## Human study or evaluation design

This is a **self-report survey study**, not a controlled lab experiment with randomized conditions or logged behavioral telemetry. It is exploratory — the authors are mapping out a largely undocumented practice (action approval) rather than testing a specific intervention against a baseline. That framing matters: the numbers below describe what developers say they do, not independently observed behavior.

## Participants and study setting

**203 developers** who use AI coding agents in their own work, reportedly recruited via a developer community channel and Prolific. Further demographic detail (experience level, agent tools used, industry) was not confirmed from the sources used here — check the full paper for the complete participant breakdown.

## Experiments or benchmarks

There is no public benchmark or dataset here in the usual agentic-AI sense; the "experiment" is the survey instrument itself, applied across real developers' self-reported practices with several action types (e.g., shell commands, file reads/writes) and contrasted with their self-reported code-review habits.

## Main results

**As reported by the authors (surfaced via search excerpts, not independently re-verified against the primary PDF):**
- 61% of developers who said they carefully reviewed most or all generated code also said they often approved at least one type of agent action without close review.
- Overall, roughly 64% (130 of 203) of respondents often approved at least one action type without close review.
- Requiring approval before risky actions was the most common safeguard developers said they used (around 63%).
- Autonomy preferences and approval behavior varied more between individual developers than between different kinds of development activity — i.e., who you are seems to matter more than what task you're doing.
- Approval requests that preview an action's likely effects before the human decides were associated with closer review and reportedly better decisions, not just with developers feeling more confident.
- Developers who said they mainly "monitor and step in when needed" (rather than reviewing every request up front) reported reviewing approval requests less closely.
- Scrutiny of approval requests reportedly declined as the number of such requests within a session increased — a pattern consistent with approval fatigue.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's main human-related finding is about **oversight quality and safety**, not performance or productivity: it suggests that a sizable share of developers who believe they are exercising careful oversight (because they review code carefully) are in fact leaving a meaningful category of agent behavior — actions with side effects outside the code — only loosely supervised. It also points to a workload/attention effect: approval fatigue, where scrutiny drops as the number of approval prompts in a session rises, suggesting that current approval UX may not sustain careful human oversight over longer agentic sessions. These are the authors' reported associations from self-report data, not causally demonstrated effects from a controlled experiment.

## What is genuinely new

*Authors' framing, as surfaced in the sources used here:* explicitly separating "code review" from "action approval" as two distinct oversight behaviors in human-agent coding collaboration, and showing empirically (via a sizable developer survey) that being careful at one does not imply being careful at the other — along with early evidence that *how* approval requests are presented (e.g., previewing effects) measurably changes how carefully humans engage with them.

## Limitations and open questions

- *My interpretation:* this is self-reported survey data, not logged or observed behavior — developers' actual approval habits in the moment could differ from what they report about themselves.
- It is an exploratory, correlational study; no controlled comparison (e.g., randomizing which developers get preview-style approval prompts) is reported, so causal claims about "previews improve review" should be treated as suggestive, not proven.
- Recruitment mixed a community channel and Prolific, which may skew the sample toward particular kinds of agent users; broader demographic and generalizability details were not available from the sources used in this summary.
- Exact figures (percentages, action-type breakdowns, statistical tests) should be checked against the primary PDF before being cited precisely, since this summary relies on secondary search excerpts rather than a direct reading of the paper.

## Practical implications

*My interpretation, following the authors' own stated design directions:* agent-tool builders should treat action approval as its own design problem, separate from code review — concretely, by confirming intent before acting, setting approval defaults based on an action's risk level rather than treating all actions alike, showing what an action will actually change before asking for a go-ahead, and making actions recoverable/reversible where possible. For anyone deploying or using coding agents today, the practical takeaway is blunt: reviewing the code an agent produces is not the same as supervising what it does to produce it, and assuming otherwise is itself a risk.

## Why you should care

As coding agents are given more tool access and more autonomy — running commands, touching files, calling external services — the gap this paper documents (careful code reviewers who are loose action approvers) is exactly the kind of blind spot that turns into a real incident: not a bad suggestion in a diff, but an action nobody really looked at. This is a timely, concrete, human-centered look at where current human-oversight practice for agentic coding tools is actually weak, from a survey of real developers using real agents — not a hypothetical about future AI risk, but a documented gap in how people are supervising agents they're already using.
