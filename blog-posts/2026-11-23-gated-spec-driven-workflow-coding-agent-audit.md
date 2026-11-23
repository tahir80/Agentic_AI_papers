# Who's Really Checking the AI's Homework? A Hard Look at "Approval Gates" for Coding Agents

**Paper title:** A Gated Spec-Driven Workflow: An Audit-Trail Study of Coding-Agent Work
**Authors:** Rodrigo Figueiredo Abdo, Pedro Carvalho Brom
**Publication date:** 2026-11-03 (arXiv v1)
**Venue:** Accepted at the 19th IEEE/ACM International Conference on Utility and Cloud Computing (UCC 2026); currently an arXiv preprint (cs.SE)
**Paper link:** https://arxiv.org/abs/2611.05094
**Code link:** Not available (no repository was found during this session's research; check the paper directly for a possible link)
**Project page:** Not available
**Date added:** 2026-11-23

> **A note on sourcing and on why this paper, specifically:** this session's network access to arxiv.org and its usual mirrors was blocked by the environment's network policy, so the full PDF could not be opened directly. This summary is built from the paper's abstract and HTML excerpts as they surfaced across several web searches, cross-checked against each other for consistency. The paper itself is a freely available, open-access arXiv preprint. Numbers below are reported as they appeared in those excerpts; anything not independently confirmed against the full PDF is marked accordingly. Please check the arXiv preprint directly before citing specific figures.
>
> **Also important:** unlike most papers featured in this series, this one has **no study with external human participants**. The "audit trail" it analyzes comes from the paper's own two authors running the workflow on their own coding projects. It was selected anyway because it makes a focused methodological contribution to a question this blog cares about — how to structure human approval checkpoints over an AI coding agent's work — and because it is candid about where that approval structure breaks down. Treat its findings as a detailed case study/audit, not as evidence from a controlled study of how outside developers behave.

---

## The problem the paper addresses

AI coding agents like Claude Code can now take a short spec ("build me a Fortran solver for X") and turn it into a working, multi-file software feature with very little hand-holding. That's powerful, but it raises an uncomfortable question: if the agent plans its own work, writes its own code, and checks its own code, who is actually making sure it did the right thing? The paper studies a popular answer to that question — a **"spec-driven" workflow with human approval gates** — and asks whether the gates and checks actually hold up, or whether they just create the appearance of oversight.

## Why this problem matters

A lot of current best practice for working with coding agents boils down to: break the work into stages (spec → plan → tasks → code), and have a human sign off before each stage proceeds. This is appealing because it looks like real human-in-the-loop control. But if the "checks" that feed into that approval are themselves run by the same AI system being checked, the human's approval could be rubber-stamping something that was never really verified. As coding agents get folded into real engineering pipelines, this question — is the oversight real or theatrical? — has direct consequences for software safety and quality.

## What makes the system agentic

The system studied is built on Claude Code and is unambiguously agentic: an **orchestrator** agent plans and coordinates the work across stages; an **executor subagent** is dispatched to write code for a specific task, restricted to only the files that task declares it will touch; and a **reviewer subagent** checks each produced artifact against a fixed, stage-specific checklist of likely defects. After each block of tasks, an automated file-inventory check runs to catch any file changes nobody declared. This is multi-step planning, delegated execution, and tool use by multiple cooperating AI roles — not a single text response.

## How humans and the AI agent collaborate

The workflow is explicitly **gated**: a human user must approve each stage (e.g., the spec, then the plan, then each block of implementation tasks) before the agent system is allowed to move to the next one. The idea is that the human retains a checkpoint at every major transition, rather than only seeing the agent's work after everything is already done.

## What role the human plays

In this workflow design, the human's job is to **review and approve (or reject) each stage's output** before work continues — spec review, plan review, and review of completed implementation blocks. In the actual study, that human role was filled by the paper's own authors, who ran all nine features themselves and acted as both the people requesting the work and the people approving it at each gate.

## What role the AI agent plays

The AI side does essentially all of the generative and verification labor: the orchestrator breaks the feature into a plan and tasks; the executor subagent writes the code for each task within its declared file scope; and the reviewer subagent independently (in theory) checks the resulting artifacts against a defect checklist before the human sees them for approval.

## How control, initiative, and decisions are shared

On paper, control is split cleanly: the AI proposes and does the work, a semi-independent AI reviewer screens it, and the human holds a veto/approval right at each stage boundary. In practice, the paper's central finding is that this split is leakier than it looks — because the **orchestrator**, the same component directing the work, also ends up running and judging some of its own checks, which blurs the separation between "doer" and "checker" that the gate design depends on.

## The paper's main idea

The authors' main idea is to treat the gated, spec-driven workflow itself as an object of empirical study — not just a methodology to recommend, but a system whose logs and transcripts can be audited like evidence. By tracing exactly what the orchestrator, executor, and reviewer subagents did (and didn't) check at each gate across real projects, they surface specific, concrete failure modes in how "human oversight" actually plays out when most of the checking work is delegated to AI.

## How the approach works

The workflow proceeds in stages (e.g., specification, planning, task-by-task implementation), with a human approval gate between major stages. Within implementation, work is broken into small, declared-scope tasks; an executor subagent is restricted to editing only the files its task names. A reviewer subagent then checks the resulting artifact against a fixed, stage-specific list of likely defects. After each block of tasks finishes, an automated file-inventory check compares the files actually touched against what was declared, to catch any undeclared or out-of-scope changes before the human's next approval decision.

## Human study or evaluation design

There is **no study with external human participants or developers**. The evaluation is an **audit-trail / case-study analysis**: the authors ran the gated workflow themselves on nine software features across seven of their own projects and then systematically examined the resulting logs and transcripts — looking at how often declared scopes were respected, how reviews were conducted, how often work was fully completed, and where the review process broke down.

## Participants and study setting

None in the human-subjects sense. The "participants" acting as the human approver at each gate were the paper's two authors, working on their own codebases. The authors are explicit that this is a small, self-selected sample run by the people who built the workflow, not an independent or blinded evaluation.

## Experiments or benchmarks

Instead of a benchmark, the paper analyzes **nine real coding features spread across seven projects** (one example mentioned in search excerpts is a Fortran numerical solver), tracking metrics like task completion rates, file-scope compliance by the executor subagent, reviewer token usage, and instances where review was re-run unnecessarily.

## Main results

According to the excerpts available: five of the nine features were completed with every planned task done; across all nine features, 288 of 581 planned tasks were completed. The file-scope restriction largely worked — the executor subagent mostly stayed within its declared files, and in at least one case where it didn't, the automated file-inventory check caught the undeclared change. The paper's headline finding, however, is that the **orchestrator is the weak link**: because it both runs and judges some of its own checks, the "independent" review isn't always independent. The authors also report that unnecessary re-reviews consumed a large share of reviewer effort — one figure reported is that, across three of the projects, re-reviews the workflow didn't actually need to request used roughly 75% of the reviewer subagent's tokens.

## Effects on human performance, trust, workload, safety, or decision quality

The paper does not measure these with human participants, so there are no trust, workload, or decision-quality outcomes to report in the usual sense. What it does provide is an argument about **safety and reliability of the oversight structure itself**: if the component responsible for orchestrating the work can also, in effect, grade its own homework before the human sees it, the human's "approval" at the gate may be based on an incomplete or biased signal. That's a finding about the trustworthiness of the human-oversight mechanism, not about how a human using it actually felt or performed.

## What is genuinely new

The novelty here is less a new AI capability and more a **diagnostic audit of a widely-used human-oversight pattern** (stage gates plus an AI reviewer) using real transcripts rather than only a description of the design. Identifying the specific failure mode — orchestrator self-review contaminating the gate — and quantifying wasted reviewer effort from redundant re-reviews are the paper's concrete, demonstrated contributions.

## Limitations and open questions

The authors' own case-study design is the paper's biggest limitation: nine features, seven projects, and the authors themselves as both requesters and approvers means the findings may not generalize to other developers, teams, or codebases, and there's no control condition (e.g., an ungated workflow, or a genuinely independent human or AI reviewer) to compare against. The reviewer subagent's token counts are reported as a lower bound, not a precise measurement. It's also an open question how these findings would change with real external developers approving the gates, under time pressure, across unfamiliar codebases — exactly the setting a future human-subjects study would need to test.

## Practical implications

For teams adopting spec-driven, gated workflows with coding agents, the practical lesson is: don't assume a "reviewer subagent" step gives you independent verification just because it's a separate role in the prompt. If the same orchestrating agent also controls or influences that review, the gate can look rigorous while quietly offering weaker protection than intended, and the resulting rubber-stamp approvals from a human reviewer could let undetected issues through. Builders of these workflows may want to enforce stronger separation (e.g., a reviewer with no visibility into the orchestrator's running narrative) and watch for wasted review cycles that eat into any efficiency gains.

## Why you should care

This paper is a useful reality check for anyone relying on "human approval gates" as their main safety mechanism for AI coding agents: a gate is only as good as the information the human sees at it, and this audit shows a concrete, plausible way that information can be compromised by how the agent system itself is wired — even when, superficially, a human is "in the loop" the whole time.

---

### Candidate comparison and selection rationale

As part of this run's search process, the following candidates were compared before selecting this paper (scored 0–5 unless noted, per this project's rubric: Human–AI collaboration relevance / Strength of real human evaluation / Agentic AI relevance / Methodological quality / Practical relevance / Recency 0–3):

1. **"A Gated Spec-Driven Workflow: An Audit-Trail Study of Coding-Agent Work"** (arXiv 2611.05094, Nov 3 2026) — **Selected.** Agentic: clearly yes (orchestrator + executor + reviewer subagents, multi-stage planning, tool/file actions). Human-AI collaboration: approval gates at every stage are a direct, central mechanism (feedback/approval/oversight), scoring 4/5. Real human evaluation: 1/5 — no external participants, authors ran it themselves; this is disclosed explicitly throughout the post and table. Selected under this project's stated exception for papers "without a real human–AI collaboration study" that "make a major methodological contribution specifically intended to support human oversight... intervention": the gated, multi-subagent review architecture and its audited failure mode (orchestrator self-review) is exactly that kind of contribution. Recency: 3/3 (within the last 30 days).
2. **"Is That Clear? The Impacts of Clarifying Questions on Human-LLM Interaction"** (arXiv 2611.01087, ~Nov 2026) — Rejected. Strong real human study (n=180, controlled experiment; clarifying questions raised perceived understanding but reduced scrutiny of errors), but the system studied is a single-turn conversational recommender, not a multi-step, tool-using agent. Agentic AI relevance assessed below the required 3/5 threshold.
3. **"What to Delegate, What to Preserve: Human Preferences for Agentic AI Across Everyday Life and Work"** (arXiv 2611.09730, Nov 6 2026) — Rejected. Real human respondents (a survey across 45 use cases/9 life domains), but no actual LLM agent system is built or evaluated; it measures stated preferences about hypothetical future delegation, not an agent "evaluated as an agent." Fails the agentic-system criterion.
4. **"Knowing When to Intervene: Causal Evaluation of AI Agents"** (arXiv 2611.09792, Nov 2026) — Rejected. Agentic (evaluated on τ-bench Retail, ToolSandbox, ImpossibleBench) and squarely about when human/automated intervention is warranted, but human review appears only as motivating context, not as an actual human-in-the-loop experimental condition. Human–AI collaboration relevance assessed below the required 4/5 threshold.
5. **"Requesting Expert Reasoning: Augmenting LLM Agents with Learned Collaborative Intervention" (AHCE)** (arXiv 2602.22546, Feb 2026) — Rejected. Agentic, and designed around a learned policy for when to call on a "human expert," but (a) it is roughly nine months old, well outside the preferred recency window, and (b) available excerpts could not confirm the "human expert" in its experiments was a real person rather than a scripted/simulated role.
6. **"AgentPanel," "Auditable Human-Agent Teams for Autonomous X-ray Experimentation," "BobFlow," "From Watching to Steering" (Vibetrace), and "From Delegation to Action Approval"** — All strong candidates with real human studies, but all were already present in this repository's paper table from earlier runs, so excluded as duplicates.

No paper found in this run combined (a) a genuine human-subjects evaluation, (b) clear agentic-AI status, and (c) novelty relative to the existing table within the preferred 30-day recency window — the strongest papers meeting (a) and (b) were already logged. This paper was chosen as the best non-duplicate option that still clears the agentic and collaboration-relevance bars, with its lack of a human-subjects study stated plainly rather than glossed over.
