# InterDeepResearch: Enabling Human-Agent Collaborative Information Seeking through Interactive Deep Research

**Authors:** Bo Pan, Lunke Pan, Yitao Zhou, Qi Jiang, Zhen Wen, Minfeng Zhu, Wei Chen (affiliation not confirmed from available sources)
**Publication date:** 2026-03-13 (arXiv id 2603.12608)
**Venue:** arXiv preprint (cs.IR / cs.HC); the paper is formatted with ACM-style conference metadata, suggesting a submission to an ACM venue, but acceptance/venue could not be confirmed from available sources
**Paper link:** https://arxiv.org/abs/2603.12608 (PDF: https://arxiv.org/pdf/2603.12608)
**Code link:** https://github.com/bopan3/InterDeepResearch
**Project page:** Not available separately (the GitHub repository doubles as the project page/demo)
**Date added:** 2026-07-18

> **A note on sourcing:** the arXiv host was not directly reachable from this research session's network, so this summary is built from the paper's publicly circulated abstract, the arXiv HTML rendering, and the project's GitHub README, rather than a direct, complete read of the typeset PDF. Facts that could be cross-confirmed across these sources (authors, study design, participant counts, and the quantitative usability ratings) are reported as such; anything we could not verify — exact benchmark scores, venue/acceptance status, author affiliation, and study logistics such as session length or setting — is marked "not available" or "not confirmed" rather than invented.

---

## The problem the paper addresses

"Deep research" agents — the kind that take a query, then autonomously search the web, filter what they find, and stitch it into a report — have become a popular way to offload complex research tasks to an LLM. But the paper argues that almost all of these systems follow a rigid "query-to-report" pattern: you type a question, the agent disappears for a while, and it comes back with a finished write-up. In between, you're a bystander. You can't tell it "actually, focus on this angle instead," can't feed in something you already know, and can't easily check *why* the agent believes a particular claim once the report is done.

## Why this problem matters

As people increasingly rely on these agents for real work — literature reviews, market research, due diligence, technical investigation — the report they get back is only useful if it reflects what the person actually needed to know, and if its claims can be checked. A system that only takes a query at the start and hands back a black-box report at the end has no way to absorb a user's evolving understanding of the problem, and gives the user little basis for trusting (or catching errors in) what comes out.

## What makes the system agentic

InterDeepResearch is built around an LLM-based agent that performs the classic "deep research" loop autonomously and iteratively: issuing searches, retrieving and filtering web content, and synthesizing findings into intermediate and final outputs, all without a human writing each step. It is evaluated as an agent, not just as a chat model — the paper reports its performance on established deep-research benchmarks (Xbench-DeepSearch-v1 and Seal-0), alongside a dedicated sub-agent that the system launches on demand to trace whether an earlier piece of retrieved evidence actually supports a later claim. That combination — autonomous multi-step retrieval/synthesis, tool use (web search), and agent-level benchmarking — is what puts this squarely inside our working definition of agentic AI, rather than a single-turn Q&A tool.

## How humans and the AI agent collaborate

The paper's core move is to make the agent's ongoing research process visible and interactable instead of hiding it behind a single "generate report" button. The interface exposes the agent's research session as a structured, navigable space — a chat-style timeline of what the agent has done, a graph showing how pieces of information depend on earlier search/synthesis actions, and a card view of the retrieved content — so a person can drop in at any point, see what the agent has found and why, and redirect it.

## What role the human plays

According to the paper, the human contributes exactly what the "query-to-report" paradigm discards: personal knowledge, context, and an evolving sense of what they're actually trying to find out. Concretely, they can read the agent's in-progress research trace, inject new context or redirect the agent mid-task, and select any piece of generated text to trigger a "context backtrace" — asking the system to verify what upstream evidence, if any, actually supports that statement.

## What role the AI agent plays

The agent carries out the research work itself: running retrieval and synthesis actions, and maintaining a hierarchical model of its own research context (organized into information, action, and session levels) so it can manage what to keep and what to compress as the research session grows, without exhausting its context window. When a user asks it to justify a claim, the system dispatches a separate LLM-based sub-agent specifically to check the Action Dependency Graph for supporting evidence and report back.

## How control, initiative, and decisions are shared

This is a mixed-initiative design: the agent runs autonomously by default (it doesn't wait for step-by-step instructions), but the human retains the ability to observe the process at any granularity and to steer it in real time, rather than only being able to accept or reject a finished report. The paper frames this explicitly around three needs its formative study identified as missing from existing systems: **process observability** (can the user see what's happening and why), **real-time steerability** (can the user redirect the agent as their understanding changes), and **context navigation efficiency** (can the user find, revisit, and verify specific pieces of prior research without losing their place).

## The paper's main idea

**Claim by the authors:** existing deep research agents under-collaborate with their users because they only accept input at the start and only deliver output at the end. The authors argue that meaningfully supporting human-agent collaboration in this setting requires purpose-built infrastructure for managing and exposing the agent's evolving research context — not just a friendlier chat window — and they present InterDeepResearch's context-management framework and multi-view interface as one way to do this.

## How the approach works

The system organizes everything the agent produces into a three-level hierarchy (information → actions → sessions), which supports dynamic context reduction so the underlying LLM doesn't run out of context as a research session grows, and lets the system reconstruct, for any piece of information, the chain of actions that produced it (the Action Dependency Graph). Three coordinated interface views sit on top of this: a linear chat-style view of the session, a graph view of action dependencies, and a card view of retrieved information. When a user backtraces a claim, a dedicated LLM agent walks the dependency graph to check for supporting evidence.

## Human study or evaluation design

**Demonstrated in the paper (per available sources):** the authors ran a two-stage, real-participant HCI study. First, a **formative study with 8 participants (P1–P8)** — people who use or build deep research systems — was used to surface concrete pain points with existing "query-to-report" tools; this directly produced the paper's three design goals (observability, steerability, navigation efficiency). Second, a **formal evaluation with 15 participants** drawn from frequent users and developers of deep research agents had people use InterDeepResearch and rate it on five-point Likert scales, explaining their ratings and giving open-ended feedback.

## Participants and study setting

Both studies recruited real human participants with direct, relevant experience — people who already use or build deep research tools, rather than general crowdworkers or simulated personas. Exact recruitment method, session length, and setting (remote vs. in-person, task-based vs. free exploration) are **not available** from the sources we could access in this session.

## Experiments or benchmarks

Beyond the human study, the paper evaluates the underlying agent's raw research capability on two existing deep-research benchmarks, **Xbench-DeepSearch-v1** and **Seal-0**, reporting that it performs competitively with other state-of-the-art deep research systems. We could not confirm the exact benchmark scores from the sources available to us, so we do not report specific numbers here.

## Main results

**Demonstrated in the paper (per available sources):** in the 15-participant evaluation, participants rated the system favorably on the specific collaboration dimensions it was designed to address: support for clearly comprehending the agent's research process (mean 4.8/5), usefulness of the Action Dependency Graph (mean 4.7/5), flexibility of steering the agent (mean 4.4/5), and efficiency of navigating prior context (mean 4.27/5). These are self-reported usability ratings on the system in isolation; the sources available to us do not describe a controlled comparison against a baseline "query-to-report" system on these same measures.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's evaluation centers on **self-reported usability and perceived support for collaboration** (comprehension, steerability, navigation), not on independent measures like task completion time, decision accuracy, trust scales, or workload instruments such as NASA-TLX. **This is our interpretation, based on the available sources:** the consistently high Likert ratings (4.27–4.8 out of 5) suggest participants who already work with deep research tools found the added observability and steering mechanisms genuinely useful, but we could not confirm from available sources whether the study measured, or found, effects on objective task outcomes or trust relative to a baseline system — readers who need that should consult the full paper directly.

## What is genuinely new

- A concrete architectural answer (hierarchical research-context management plus an Action Dependency Graph) to a specific human-agent collaboration failure mode — losing the ability to inspect or verify an agent's intermediate reasoning as a "deep research" session grows long.
- An on-demand, agent-driven evidence-backtracing mechanism that lets a user ask *why* the system believes something and get an automated check against the actual chain of retrieval/synthesis actions that produced it, rather than just re-reading the final report.
- Grounding the design directly in a formative study of real deep-research users/builders (8 participants) before building the system, then validating the resulting design goals with a second, independent group of real users (15 participants) — a research-then-build-then-validate pipeline with people at both ends.

## Limitations and open questions

- **Small samples skewed toward power users.** Both studies recruited people who already use or build deep research systems; the findings may not generalize to less technical or first-time users of such tools.
- **No confirmed baseline comparison.** The formal evaluation reports Likert ratings of the system itself; we could not confirm from available sources that these were compared against a matched baseline (e.g., a standard query-to-report system) on the same tasks, which limits how strongly "better collaboration" can be claimed versus "rated positively in isolation."
- **Self-reported measures only.** The available sources describe usability ratings and qualitative feedback, not objective outcomes (accuracy, time, verified trust calibration), so claims about real-world collaboration benefits should be treated as preliminary.
- Exact benchmark numbers, participant demographics, session protocol, and venue/peer-review status could not be confirmed from the sources reachable in this session.

## Practical implications

If the paper's findings hold up, they point to concrete building blocks — a layered research-context model, a dependency graph over agent actions, and an on-demand evidence-verification sub-agent — that teams building "deep research" or agentic search products could adopt to move users from passive report-recipients to active collaborators who can redirect the agent and check its work mid-process, not just after the fact.

## Why you should care

Deep research agents are one of the most widely deployed categories of LLM-based agentic AI right now, and this paper is a direct, HCI-grounded attempt to fix their most common complaint: you hand over a query and get back a black box. It's a useful, concrete data point in the broader human-AI collaboration question this log tracks — not "should a human supervise a research agent," but "what specific interface and context-management mechanisms actually let them do it well," backed by a real (if modest-sized) study of the people who'd actually use such a system.
