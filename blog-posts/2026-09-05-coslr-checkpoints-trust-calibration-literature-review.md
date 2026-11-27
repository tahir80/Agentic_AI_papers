# Checkpoints Are Not Enough: Why "Click to Approve" Isn't the Same as Real Oversight

**Paper title:** Checkpoints Are Not Enough: Trust Calibration in CoSLR, a Human-AI System for Systematic Literature Reviews
**Authors:** MD Aidul Islam, Malik Abdul Sami, Muhammad Waseem, Zeeshan Rasheed, Kai-Kristian Kemell, Zheying Zhang, Pekka Abrahamsson
**Publication date:** 2026-09-05 (arXiv v1)
**Venue:** arXiv preprint (cs.CL, cross-listed cs.AI, cs.IR); peer-reviewed venue not confirmed
**Paper link:** https://arxiv.org/abs/2609.22248
**Code link:** Not available (no public repository found during this session's research)
**Project page:** Not available
**Date added:** 2026-11-27

> **A note on sourcing:** this session's network access to arxiv.org and its usual mirrors was blocked by the environment's network policy, so the full PDF could not be opened directly. This summary is built from the paper's abstract, HTML excerpts, and author-page summaries as they surfaced across several web searches, cross-checked against each other for consistency. The paper itself is a freely available, open-access arXiv preprint. Specific figures below (notably the 63-participant count and the 34.9% statistic) are reported as they appeared in those cross-checked excerpts; please verify against the full PDF before citing them elsewhere.

---

## The problem the paper addresses

A lot of today's advice for working safely with AI agents boils down to: insert a "human checkpoint" before anything important happens, and let a person approve or reject the agent's work. This paper asks a pointed question about that advice: does inserting a checkpoint actually produce real human oversight, or can it quietly become a box people click through without truly checking anything? The authors study this in the context of a very concrete, high-stakes task — doing a systematic literature review (SLR), the rigorous, multi-stage process researchers use to survey everything published on a topic — using a human-AI system called **CoSLR** that places mandatory approval checkpoints between the AI's work and its acceptance.

## Why this problem matters

Systematic literature reviews are foundational to how whole fields decide what is already known. Get the screening or the extracted data wrong, and every paper that cites the review inherits the error. AI tools that can search, screen, and summarize literature promise huge time savings, but only if the human reviewers "approving" each stage are actually catching the agent's mistakes rather than rubber-stamping them. This isn't just an SLR problem — it's the same question facing every tool that puts a "review and approve" button in front of an AI agent's output, from coding assistants to medical note-takers. If checkpoints turn out to be theater rather than substance, a lot of current human-oversight design may be giving people (and institutions) false confidence.

## What makes the system agentic

CoSLR is described as a modular, three-phase, multi-agent pipeline built on large language models combined with retrieval-augmented generation (RAG). Rather than answering one question in one shot, it autonomously works through the stages of an SLR workflow — searching the literature, screening and filtering candidate papers, and extracting/synthesizing data — producing outputs, logs, and a trace of its own actions as it goes. It only stops at specific points to request human sign-off before continuing, which is what makes it a genuine multi-step, tool-using, semi-autonomous agentic system rather than a single-turn chatbot.

## How humans and the AI agent collaborate

The collaboration is structured around **mandatory checkpoints**: at defined points in the three-phase pipeline, the system pauses and requires a human to review and approve (or reject/revise) what it has produced before it is allowed to proceed to the next stage. The intent is to keep a person in the loop at every major transition of the review process, not just at the very end when the whole review is "done."

## What role the human plays

The human is the reviewer who must inspect the AI's intermediate work — its search results, screening decisions, extracted data, or drafted summaries — and decide whether to accept it, reject it, or send it back, at each checkpoint gate. In the paper's study, this role was filled by real study participants performing SLR-related tasks with CoSLR, not by the system's own authors.

## What role the AI agent plays

The AI side performs essentially all of the generative and retrieval labor of the review: running searches, applying RAG to pull relevant literature, screening papers against inclusion/exclusion logic, and drafting extracted data and summaries — while logging its actions in a trace for transparency — and then waiting at each checkpoint for the human's decision before moving forward.

## How control, initiative, and decisions are shared

On paper, control is shared cleanly: the agent does the work, but it cannot proceed past a checkpoint without the human's explicit approval, so the human nominally holds veto power over every stage. The paper's central contribution, however, is showing that this formal division of control doesn't automatically translate into *substantive* shared decision-making — a checkpoint can be satisfied with a single, low-effort confirmation, regardless of how much is actually at stake at that stage.

## The paper's main idea

The authors' main argument, captured in the title, is that **checkpoints are necessary but not sufficient** for real human oversight. Simply placing a mandatory "approve" gate in an agentic pipeline doesn't guarantee that users will do the cognitive work of actually verifying the AI's output — oversight has to be *calibrated*, matching the effort a checkpoint demands to how much is riding on that decision, rather than treating every stage identically.

## How the approach works

CoSLR applies the same fixed, uniform checkpoint design to every user and every stage of the SLR pipeline: each one can, in principle, be satisfied by a single confirmation click, whether the stage is low-stakes (e.g., confirming a routine search query) or high-stakes (e.g., an inclusion/exclusion decision that determines which papers make it into the review). The system supports this with trace logs intended to aid transparency, validation, and reproducibility of the overall workflow.

## Human study or evaluation design

The paper reports a study with **63 participants** who used CoSLR to work through SLR-related tasks involving these checkpoints. The authors measured how participants engaged with the checkpoints and what it would mean for them to trust the AI's output — specifically, whether people said they would accept AI-generated summaries or reports without further independent checking.

## Participants and study setting

Available excerpts confirm a sample size of 63 participants but do not give further demographic detail (e.g., expertise level, recruitment method, or professional background) that could be independently verified during this session's research; this should be checked against the full paper text.

## Experiments or benchmarks

Rather than a standardized public benchmark, the evaluation centers on real usage of the CoSLR system by the 63 study participants across the pipeline's checkpoints, with the authors analyzing checkpoint interactions and self-reported trust/trust-calibration responses. No public dataset or benchmark release was confirmed during this session's research.

## Main results

The paper's main empirical finding is that a large share of participants treated the mandatory checkpoints as pro forma rather than as a substantive check: **22 of 63 participants (about 34.9%) reported that, after only limited interaction with the system, they would trust AI-generated summaries and reports without doing any further checking.** The authors frame this not as a reason to remove human checkpoints, but as evidence that checkpoint *design* — uniform, identical gates regardless of stakes — fails to calibrate how much effort a reviewer should invest at each stage.

## Effects on human performance, trust, workload, safety, or decision quality

The key human-related outcome concerns **trust calibration**: a sizeable minority of real users were, by their own report, willing to extend essentially unconditional trust to the AI's output at exactly the points designed to catch its mistakes. The paper does not report separate quantitative measures of workload or task-performance accuracy in the excerpts available; its central claim is about the mismatch between the *presence* of a human checkpoint and the *quality* of human scrutiny actually applied there.

## What is genuinely new

Authors' claim: that effective human-AI collaboration in review-heavy workflows requires checkpoints whose demanded effort is calibrated to the stakes of the decision, not uniform gates applied identically everywhere — and that this is a design problem distinct from simply deciding where to put a human-in-the-loop step. Demonstrated result: the 63-participant study showing a concrete, measured rate (34.9%) of participants willing to skip further verification after a mandatory checkpoint. My own interpretation: this is a useful, generalizable cautionary data point for any agentic system that relies on "approval gates" as its primary safety mechanism — it suggests the mere existence of a human-in-the-loop step is a weak proxy for genuine oversight, and that checkpoint design (how much effort it demands, how it's differentiated by stakes) deserves as much scrutiny as whether a checkpoint exists at all.

## Limitations and open questions

The authors themselves note that CoSLR's checkpoints are uniform across stages and users, and they explicitly leave the design and evaluation of stakes-calibrated checkpoints (e.g., requiring a more effortful check, such as opening and inspecting a cited source, specifically at high-stakes stages like inclusion/exclusion decisions) to future work. The paper is a single arXiv preprint with no confirmed peer-reviewed venue at the time of this summary, and details on participant background, task duration, and statistical analysis could not be independently confirmed given this session's restricted access to the full text. An open question the paper raises but doesn't resolve: how would trust and checkpoint engagement change if the system varied the effort required by stage, rather than keeping every gate equally lightweight?

## Practical implications

For anyone building or deploying human-in-the-loop checkpoints on top of agentic systems — whether for literature reviews, coding agents, or any other AI pipeline — the practical takeaway is to resist treating "there's a human approval step" as self-evidently sufficient oversight. The design of that step matters: a uniform, low-friction confirmation risks becoming a formality, especially once users build up confidence in the system over repeated, mostly-correct interactions. Matching the effort a checkpoint demands to the actual stakes of the decision — and perhaps instrumenting checkpoints to detect when they're being rubber-stamped — looks like a more promising direction than simply adding more gates.

## Why you should care

This paper is a useful reality check for the whole "human-in-the-loop" design pattern that underlies much of today's thinking about agent safety: putting a person in front of an "Approve" button is not the same thing as that person actually catching the agent's mistakes. With a real 63-person study behind it, CoSLR's finding — that roughly a third of users were ready to trust AI output unconditionally right at the checkpoint meant to prevent exactly that — is a concrete warning for designers tempted to treat checkpoints as a solved problem rather than something that itself needs careful, stakes-aware design.

---

### Candidate comparison and selection rationale

Five candidates were compared before selecting this paper (scored 0–5 unless noted, per this project's rubric: Human–AI collaboration relevance / Strength of real human evaluation / Agentic AI relevance / Methodological quality / Practical relevance / Recency 0–3):

1. **"Checkpoints Are Not Enough: Trust Calibration in CoSLR..."** (arXiv 2609.22248, Sept 5 2026) — **Selected.** Agentic: yes, a multi-agent LLM+RAG pipeline executing a multi-stage SLR workflow with checkpoint gating (4/5). Human–AI collaboration: checkpoints are the entire research question — a central, directly studied mechanism of oversight and shared control (5/5). Real human evaluation: a genuine 63-participant study measuring trust/checkpoint behavior, not a simulated or self-run case study (4/5). Methodological quality and practical relevance both strong (4/5 each), though recency is modest (preprint from roughly 12 weeks before this run, 1/3). Clears both minimum thresholds (collaboration ≥4, agentic ≥3) with the highest combined score of the candidates compared.
2. **"Is That Clear? The Impacts of Clarifying Questions on Human-LLM Interaction"** (arXiv 2611.01087, ~Nov 2026) — Rejected. Strong, recent, genuine human study (n=180, controlled online experiment: clarifying questions raised perceived understanding/satisfaction but reduced scrutiny of answers, including wrong ones). However, the system is a single-turn conversational LLM doing preference elicitation, not a multi-step, tool-using agent evaluated as an agent. Agentic AI relevance assessed well below the required 3/5 threshold.
3. **"The Work Behind Delegation: A Framework for Supervising AI Coding Agents"** (arXiv 2609.24234, Sept 2026) — Rejected as the top pick, though a strong runner-up. Real humans (19 experienced developers) and clearly agentic (Sheridan's supervisory-control framework applied to coding agents across plan/monitor/review/teach stages), but the "study" is grounded-theory-style observation and workflow diagramming rather than a controlled or outcome-measuring evaluation, and it is a less direct test of a specific collaboration mechanism than CoSLR's checkpoint study.
4. **"DoubleAgents: Human-Agent Alignment in a Socially Embedded Workflow"** (arXiv 2509.12626, Sept 2025; HCOMP 2026) — Rejected primarily on recency. A genuine, well-designed human study (longitudinal use of a coordination agent + review dashboard + policy module, showing rising comfort/reliance over time alongside persistent demand for control at uncertain edge cases), but the preprint is roughly 14 months old at the time of this run, far outside the preferred recency window, which several newer, non-duplicate candidates could clear.
5. **"AI Agents Push Humans Out of the Loop"** (arXiv 2608.23642, Aug 2026; NeurIPS 2026 Position Paper Track) — Rejected. Directly relevant theme (degradation of human oversight under heavy agentic-AI use) but it is a position/argument paper with no system built, no human study conducted, and no concrete methodological contribution to supervision/intervention design — it does not meet the bar this project sets for papers without a human-subjects evaluation.

Several other strong candidates surfaced during search — "Auditable Human-Agent Teams for Autonomous X-ray Experimentation," "AgentPanel," "Comparing Human Oversight Strategies for Computer-Use Agents," "How to Steer Your Multi-Agent System," "Human-AI Collaboration at Scale," and "Understanding the Effects of Multi-Agent Deliberation for Human-AI Decision-Making" — but all were already present in this repository's paper table from earlier runs and were excluded as duplicates. CoSLR was the strongest paper clearing both minimum thresholds that had not already been logged.
