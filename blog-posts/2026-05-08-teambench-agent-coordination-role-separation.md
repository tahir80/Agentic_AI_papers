# TeamBench: Evaluating Agent Coordination under Enforced Role Separation

**Authors:** Yubin Kim, Chanwoo Park, Taehan Kim, Eugene Park, Samuel Schmidgall, Salman Rahman, Chunjong Park, Cynthia Breazeal, Xin Liu, Hamid Palangi, Hae Won Park, Daniel McDuff
**Publication date:** 2026-05-08 (arXiv id 2605.07073)
**Venue:** arXiv preprint — no peer-reviewed conference/journal venue confirmed as of this writing
**Paper link:** https://arxiv.org/abs/2605.07073 (PDF: https://arxiv.org/pdf/2605.07073)
**Code link:** https://github.com/ybkim95/TeamBench
**Dataset:** https://huggingface.co/datasets/ybkim95/teambench
**Project page:** https://teambench.github.io
**Date added:** 2026-09-14

> **A note on sourcing:** this session's network could not directly fetch arxiv.org, its HTML/PDF mirrors, Hugging Face, or the project's GitHub Pages site (all blocked by the outbound network policy). This summary is built from (1) the paper's abstract and description as it recurs consistently, near-verbatim, across many independent web searches and citation aggregators, and (2) the project's `README.md`, which this session *could* retrieve directly (via `raw.githubusercontent.com`) and which independently confirms the benchmark's structure (roles, task counts, ablation conditions, license). The human-study section in particular — including exact participant demographics and recruitment details, and the precise wording of results — could not be independently verified against the full paper text, since the PDF itself was not fetchable. What is reported below about the human study reflects the consistent description found across multiple independent search results; anything not corroborated this way is marked "Not available."

---

## The problem the paper addresses

When you give an AI agent a big task, a natural fix for reliability is to split the job across a team of agents with different roles — one plans, one does the work, one checks the work — the same division of labor a human software team might use. But does splitting roles across separate agents actually make outcomes more reliable, or does it just add coordination overhead without a real safety benefit? And critically: if you swap a *human* into one of those roles — say, as the checker verifying an AI's work — does that person actually behave like a careful reviewer, or do they just wave things through? TeamBench is built to answer both questions with hard evidence rather than intuition.

## Why this problem matters

"Add a verification step" and "put a human in the loop" are two of the most common reflexive answers to "how do we make AI agents safer." Both are being adopted widely, in coding agents, business-process automation, and beyond. But if the verification step is easy to route around, or if the human placed in that step just rubber-stamps the AI's output instead of actually checking it, then the safety mechanism is theater rather than substance. Before organizations lean on "add a reviewer" as a safety strategy, it is worth knowing whether that reviewer — human or AI — actually catches the failures they're meant to catch.

## What makes the system agentic

TeamBench evaluates teams of LLM-based agents that are assigned to one of three roles — **Planner**, **Executor**, or **Verifier** — and made to complete real, multi-step software and data tasks (851 task templates spanning 19 categories, with 931 seeded task instances). Each role runs in its own Docker container with a *different, deliberately restricted* view of the problem: the Planner can read the full task specification but cannot edit any files; the Executor can edit the workspace but cannot see the full specification (only a user-facing symptom description); and the Verifier can read the specification and the (read-only) workspace but cannot modify anything. This "OS-enforced role separation" — access control implemented at the level of the operating system and filesystem mounts, not just a prompt asking an agent to "stay in its lane" — forces genuine multi-agent coordination through communication rather than one agent silently doing everyone else's job. Every task ships a deterministic, automated grader, and agent teams are evaluated end-to-end on whether they actually solve the task, not on how they say they solved it — this is what makes it an agentic-AI evaluation rather than a language-quality benchmark.

## How humans and the AI agent collaborate

TeamBench's core benchmark evaluates all-AI teams. Its human-relevant contribution is a companion **40-session human study run under the identical role-separation rules**, comparing three conditions on the same tasks: (1) a single human working through a task alone with no role restrictions, (2) a human placed into the Verifier (or another) role while an AI agent occupies the remaining role(s), and (3) an all-human team distributed across the same Planner/Executor/Verifier split the AI teams use. This design directly probes how a human behaves once they are made to collaborate with an AI teammate under the same information and access constraints an AI verifier would face — rather than studying humans and AI agents as entirely separate populations.

## What role the human plays

In the study's mixed condition, a human is placed in a supervisory or checking role — most notably as the Verifier — reviewing and certifying work produced by an AI Planner and/or Executor operating with only partial visibility into the task, exactly as an AI verifier would.

## What role the AI agent plays

The AI plays the complementary role(s) in the mixed condition — for example, acting as Planner and/or Executor — producing a plan or a code/data change under its own restricted view of the specification, which is then subject to the human's review and certification before the task is considered complete.

## How control, initiative, and decisions are shared

This is a **role-based division of authority**: the Planner has information but no ability to act, the Executor has the ability to act but incomplete information, and the Verifier holds a checkpoint gate — final certification — without editing power. In the human-in-the-loop condition, that final say sits with the human, structurally similar to a human approving or rejecting an AI's proposed change. The paper's central human-relevant finding is about what actually happens at that checkpoint in practice — see Main results below.

## The paper's main idea

**Claim made by the authors:** enforcing role separation at the level of the operating system — rather than trusting agents to just follow instructions about what they should and shouldn't touch — surfaces coordination behaviors and failure modes that simple pass/fail scoring on a shared-workspace benchmark would otherwise hide, and the same holds for human participants dropped into those same enforced roles alongside AI teammates.

## How the approach works

For the all-AI evaluation, TeamBench runs each task across five ablation conditions — including a single "oracle" agent with full access as a baseline, a role-restricted single agent, and full multi-agent teams with and without the Planner or Verifier present — across a 27-configuration cross-provider grid (multiple underlying LLMs), then compares deterministic pass rates and partial credit, plus behavioral logs of, e.g., whether a Verifier tries to edit code it isn't supposed to touch. For the human study, the same 851-task-template environment and role-separation infrastructure is reused with real people substituting for one or more AI roles, under the same deterministic graders, enabling direct behavioral comparison between all-AI, human-AI, and all-human conditions on matched tasks.

## Human study or evaluation design

**Demonstrated in the paper (as consistently described across independent sources):** a 40-session pilot study comparing solo human performance, humans paired with an AI agent under enforced role separation, and all-human teams under the same role separation, on tasks drawn from the same benchmark used for the AI-only evaluation.

## Participants and study setting

Real human participants completed 40 sessions total under controlled, role-separated conditions mirroring the AI benchmark's setup. Exact participant count, recruitment method, and demographic details were **not available** from the sources this session could access (the full paper text could not be fetched directly); what is corroborated across multiple sources is the session count (40) and the three-way comparison design (solo / human-with-agent / human team).

## Experiments or benchmarks

TeamBench itself: 851 task templates, 931 seeded instances, 19 task categories, a 90-task stratified leaderboard subset, 5 ablation conditions, and a 27-configuration cross-provider grid, all under OS-enforced Planner/Executor/Verifier role separation with deterministic shell-script grading (independently confirmed via the project's public GitHub repository).

## Main results

**Demonstrated by the authors (per consistently reported summaries):**
- Prompt-only role separation (asking agents nicely to respect roles) and OS/sandbox-enforced role separation reach statistically indistinguishable task pass rates — but prompt-only setups produce **3.6× more cases** where the Verifier oversteps its role and directly edits the Executor's code, i.e., the enforcement mostly changes *how* teams reach similar scores, not whether they succeed.
- AI Verifiers **approve 49% of submissions that actually fail** the deterministic grader — a substantial false-approval rate for the role explicitly meant to catch failures.
- Removing the Verifier role entirely *improves* mean partial score in the ablation — evidence that, as implemented, the verification step was net-negative rather than a safety net.
- Multi-agent teams help when a single agent already struggles with a task, but can hurt performance when a single agent would have done fine alone.
- In the human study: **humans paired with an AI agent under the same role-separated setup tended to collapse into quick approval** rather than sustained, effortful checking, whereas all-human teams spent more time and effort actively coordinating to fill in missing information across roles.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the human study's central human-relevant finding is a behavioral one — when a human is placed in a verification/oversight role alongside an AI teammate under restricted information, the natural tendency observed was toward fast, low-effort approval rather than the more effortful, information-seeking coordination behavior seen in all-human teams. **Our interpretation:** this mirrors, in a controlled multi-agent-style task setting, the well-known "automation complacency" or rubber-stamping failure mode long documented in human-automation interaction research — an AI teammate's confident output appears to invite less scrutiny from a human reviewer than a human teammate's would, which is directly relevant to how much genuine safety value a "human-in-the-loop verifier" role actually adds if left unaddressed by interface or process design.

## What is genuinely new

- A benchmark that enforces role separation at the operating-system/sandbox level (disjoint filesystem mounts, restricted tool access per role) rather than only via prompting, making it possible to directly compare "asked nicely" versus "actually can't" role boundaries.
- A concrete, quantified failure mode for AI-verifier safety nets: verifiers approving roughly half of grader-failing submissions, and removing the verifier sometimes helping rather than hurting.
- A same-infrastructure human study that puts real people through the identical role-separated task environment as the AI agents, allowing direct, apples-to-apples comparison of solo, human-AI, and all-human coordination behavior — including evidence that people paired with an AI teammate default toward quick approval rather than deeper verification.

## Limitations and open questions

- The human study's participant count, recruitment, and demographic details were not confirmed from the sources available to this session; readers should consult the full paper for those specifics before drawing statistical conclusions.
- Not yet peer-reviewed as of this writing.
- The "quick approval" finding is a described behavioral pattern from a 40-session pilot rather than, as far as could be confirmed here, a large-scale, high-powered controlled trial with formal statistical tests of the human-condition differences.
- Findings are specific to the coding/data-task domain the benchmark covers (drawn from public GitHub issue trackers and UCI datasets per the project's license notes); how far the verifier-complacency pattern generalizes to other domains (e.g., higher-stakes decisions) is untested here.

## Practical implications

For anyone designing "human-in-the-loop" or "AI-verifies-AI" safety architectures for agentic systems — coding agents, workflow automation, multi-agent pipelines — this paper is direct evidence that adding a verification role is not automatically a safety improvement: both AI verifiers and, per the human study, human verifiers paired with an AI teammate can approve output too readily unless the role is specifically designed (through interface, incentives, or task structure) to sustain real scrutiny rather than default to quick sign-off.

## Why you should care

This is a rare instance where the same rigorously controlled task environment is used to study *both* all-AI team coordination *and* real human behavior when paired with an AI teammate in a checking role — rather than treating "have a human review it" as a self-evidently safe design choice. Its headline result (verifiers, AI and apparently human alike, approving things they shouldn't) is a concrete, actionable warning for anyone currently relying on a review step, human or automated, as their main safety mechanism for agentic AI.
