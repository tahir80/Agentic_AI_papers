# From Chat Log to Flowchart: Helping People Actually Catch What an AI Agent Got Wrong

**Authors:** Zekun Wu, Anna Maria Feit (Saarland University, Saarland Informatics Campus); Xinru Wang (Singapore-MIT Alliance for Research and Technology); Rock Yuren Pang, Chenglong Wang (Microsoft Research)
**Publication date:** 2026-09-11 (arXiv v1)
**Venue:** arXiv preprint (peer-reviewed venue/acceptance not confirmed from sources used)
**Paper link:** https://arxiv.org/abs/2609.13136
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-09-18

> **A note on sourcing:** this session's outbound network access to arxiv.org and its usual mirrors (Hugging Face, alphaXiv, Semantic Scholar, Pith) was blocked at the network egress layer, so this summary could not be built from a direct read of the full PDF. It is instead built from cross-checked excerpts surfaced by multiple independent web searches, including the paper's own abstract text and reported study design and results. Facts that appeared consistently across independent searches are presented as such; anything that could not be corroborated this way is marked "Not available" or "not confirmed." Readers who need exact statistics, full result tables, participant demographics, or direct quotations should consult the arXiv preprint directly.

---

## The problem the paper addresses

When you ask an AI agent to "book this flight," "clean up this spreadsheet," or "reorganize these files," it doesn't just answer a question — it goes off and does a string of things: opens tools, clicks through apps, reads and writes files, calls APIs. When it's done, what you're usually left with to check its work is a long, linear chat transcript: a scroll of text messages, tool calls, and outputs in the order they happened. The paper argues that this transcript format is a poor match for the actual job a person needs to do afterward — figure out *what* the agent did, *whether* it did it correctly, and *whether* it's safe to reuse or hand off. Errors get buried in the scroll, and there's no easy way to see the shape of the process at a glance.

## Why this problem matters

As agents take on longer, more consequential multi-step jobs, the cost of a missed error goes up, and reading through an ever-longer chat log to catch it doesn't scale. This is the classic human-oversight bottleneck for agentic AI: it's not enough for an agent to be usually right, because someone still has to be able to check its work efficiently, catch the times it's wrong, and decide whether the result is trustworthy enough to keep or reuse. If review is too slow or too easy to get wrong, people either rubber-stamp agent output they haven't really checked, or they don't get the benefit of automation at all.

## What makes the system agentic

The AI agents studied here turn a single natural-language request into a genuinely multi-step process spanning tools, files, and applications — not a one-shot answer. The paper's own corpus-building step underscores this: the authors analyzed 10,803 real, publicly shared workflow templates from n8n (a popular workflow-automation platform) specifically to characterize what this kind of real-world, multi-tool agent automation actually looks like in practice, before designing their intervention around it.

## How humans and the AI agent collaborate

The collaboration happens *after* the agent has finished a task, not during it: this is a post-hoc human oversight design rather than real-time supervision. The agent runs its multi-step process to completion, and the human's job is to review what happened — to understand it, validate it (catch any errors), and decide whether to reuse it. The paper's central move is to change the *representation* the human reviews it through: instead of a chat transcript, the agent's completed execution trace is converted into an interactive, editable, graph-based workflow diagram.

## What role the human plays

Humans are the reviewers, validators, and decision-makers. In the study, participants were handed a completed agent execution — deliberately seeded with some errors — and asked to inspect it, catch problems, and judge whether it could be trusted and reused, using either the new graph-based workflow view or a conventional prompt/chat-only view.

## What role the AI agent plays

Two AI components are at work. First, the task-performing agent itself autonomously executes the multi-step job (using tools, files, and applications) that the human will later review. Second, a separate AI pipeline — the paper's "Trace2Flow" research probe — takes that agent's raw execution trace and translates it into a human-facing artifact: it grounds candidate workflow operations in the trace, has an LLM generate an intermediate workflow representation, and compiles that into an executable graph of operations and data dependencies for the person to inspect.

## How control, initiative, and decisions are shared

The agent takes the initiative to complete the task autonomously; the human retains full authority over review, validation, and reuse decisions afterward. The workflow diagram is explicitly framed by the authors as a **descriptive, not prescriptive** artifact — it explains what the agent did, but it doesn't tell the human what to conclude about it. All judgment about correctness and trustworthiness stays with the person.

## The paper's main idea

**Claim by the authors:** representing a completed agent execution as an editable, graph-based post-task workflow — rather than leaving the person to comb through a linear chat/prompt transcript — measurably improves a reviewer's ability to understand what an agent did and to catch the errors it made, and does so by supporting the kind of cross-checking across multiple pieces of evidence that effective validation seems to require.

## How the approach works

The authors first mined 10,803 public n8n workflow templates to ground their understanding of how real multi-tool agent automations are structured. They then built **Trace2Flow**, a pipeline that: (1) grounds candidate workflow operations in an agent's raw execution trace, (2) uses an LLM to generate an intermediate workflow representation from those grounded operations, and (3) compiles that representation into an executable graph — nodes as operations, edges as symbolic data dependencies — that a person can inspect and edit after the task is done.

## Human study or evaluation design

A within-participant controlled study: each participant reviewed agent executions under two conditions — the new **post-task workflow (graph) condition** built by Trace2Flow, versus a **prompt-only / chat condition** showing the same underlying execution as a conventional transcript. The executions reviewed contained a mix of five staged errors (reported as two "prompt errors" and three "agent errors") for participants to try to catch.

## Participants and study setting

**20 participants (N = 20)** took part in a controlled, within-subject lab-style study. Further demographic detail (recruitment method, professional background, compensation) was not confirmed from the sources available in this session.

## Experiments or benchmarks

There is no public benchmark here — this is a custom within-subject comparative study built on real agent execution traces, plus a separate, large-scale descriptive corpus analysis of 10,803 public n8n automation templates used to inform the design of the workflow representation itself.

## Main results

**Reported across cross-checked search excerpts:** correct detection of the staged errors rose from about **30% of sessions in the prompt-only condition to about 65% in the workflow condition** — roughly doubling successful error detection. The paper also reports that post-task workflows improved participants' general understanding of what the agent had done, not just their error-catching rate, and that successful validation happened mainly when participants **cross-checked across multiple sources of evidence** in the workflow (rather than trusting any single piece of information in isolation). Exact statistical tests and full result tables could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The study's central human-performance outcome is **validation/error-detection accuracy** — whether a reviewer correctly catches a planted error — which roughly doubled under the workflow condition versus the prompt-only baseline. The paper also reports improved subjective **understanding** of the agent's completed process under the workflow condition. This session could not confirm whether standardized workload (e.g., NASA-TLX) or trust instruments were additionally used.

## What is genuinely new

- A large-scale, real-world grounding step (10,803 public n8n templates) used specifically to inform how a *review* artifact for agent output should be structured, rather than to train or evaluate the acting agent itself.
- **Trace2Flow**, a concrete pipeline that turns a completed agent's raw execution trace into an editable, graph-based workflow for human review, positioned explicitly as descriptive rather than prescriptive.
- A controlled, quantified demonstration that changing *how* a completed agent run is presented — not what the agent does — can roughly double a reviewer's error-detection rate.
- An explicit empirical link between successful human validation and **cross-checking across multiple evidence sources** within the workflow view, rather than a single explanation or summary.

## Limitations and open questions

- **Small sample.** Twenty participants in a within-subject study is enough to detect a fairly strong effect but leaves open questions about generalization across task types, error types, and reviewer expertise levels.
- **Post-hoc review only.** The design and study address reviewing a *completed* agent run; the paper does not (per sources used) evaluate real-time, mid-execution human oversight or intervention.
- **Staged errors in a lab setting.** The five planted errors were designed by the researchers, which may not capture the full diversity or subtlety of errors real agents produce in the wild.
- **Sourcing caveat (this summary).** Because full-text access was blocked in this research session, exact statistical tests, full demographic details, and direct participant quotations could not be verified beyond what surfaced in cross-checked search excerpts.

## Practical implications

For anyone building tools around agentic AI — coding agents, browser/computer-use agents, workflow-automation agents like those built on n8n — this is a concrete, testable design pattern: don't just hand reviewers a chat log of what an agent did; convert the completed execution into a structured, graph-based, editable artifact that supports cross-checking. The reported near-doubling of error-detection accuracy suggests this kind of representational choice may matter as much for safe agent oversight as the underlying agent's raw capability.

## Why you should care

As agentic AI takes on longer and more consequential multi-step jobs, the practical bottleneck increasingly isn't "can the agent do the task" but "can a person tell, efficiently and correctly, whether it did the task right." This paper offers direct, controlled evidence that a specific, buildable change — turning a linear trace into a reviewable, editable workflow graph — meaningfully improves that human oversight capability, at least in this study's setting. It's a useful, concrete data point for anyone designing the review layer that sits between an autonomous agent and the person who has to trust (or not trust) its output.
