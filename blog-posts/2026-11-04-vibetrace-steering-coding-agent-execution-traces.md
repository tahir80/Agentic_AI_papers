# From Watching to Steering: Enabling Human–Coding Agent Collaboration through Execution Traces

**Authors:** Xiaoke Yan, Jiaying Lei, Danqing Shi, Zichen Wang, Nan Cao (Nan Cao's affiliation is confirmed as Tongji University / iDVx Lab via the project's GitHub organization; other authors' affiliations could not be independently confirmed from the sources available to this summary)
**Publication date:** 2026-11-04 (arXiv id 2611.04466, v1, cs.HC) — the exact day is inferred from the position of this arXiv ID among neighboring IDs with confirmed timestamps, not read directly off the paper, so treat it as approximate
**Venue:** arXiv preprint (no peer-reviewed venue confirmed)
**Paper link:** https://arxiv.org/abs/2611.04466
**Code link:** https://github.com/idvxlab/VibeTrace
**Project page:** Not available
**Date added:** 2026-11-20

> **A note on sourcing:** arXiv, alphaxiv, Semantic Scholar, and similar mirrors were all unreachable from this research session's network (outbound fetches to those domains are blocked at the network level). This summary is therefore built entirely from web-search-grounded excerpts of the paper's abstract, HTML body, and reported results, not a direct read of the PDF. Facts below reflect what those excerpts report; anything not confirmed is marked "not available" or "not independently confirmed," and interpretive statements are labeled as such.

---

## The problem the paper addresses

Modern coding agents (the kind behind tools like Claude Code, Codex, or OpenCode) don't just answer a question — they run for many steps, writing files, running commands, reading error output, and deciding what to do next on their own. The paper's starting problem is that once such an agent is running, a person has almost no good way to see *what it actually did* or to *fix one specific mistake* without starting over. The usual option is a raw, scrolling log, which the authors treat as the status quo baseline. If something goes wrong three steps in, a person typically can't just rewind to that point and nudge the agent back on track — they either let it keep going or scrap the whole run.

## Why this problem matters

"Vibe coding" — letting an agent write and run code somewhat autonomously while a person checks in periodically — is spreading quickly, but trust in that workflow depends on people being able to understand and correct what the agent did, not just accept or reject the final diff. If the only way to fix a bad agent decision is to restart the whole task, people either over-supervise (watching every step, defeating the point of delegating) or under-supervise (accepting flawed work because re-doing it is too costly). Giving people a way to see *into* an agent's run and selectively repair just the part that went wrong is what makes delegating real, non-trivial coding work to an agent practical rather than risky.

## What makes the system agentic

The system being studied is a long-running coding agent built on **OpenCode**, an existing open agent framework. It plans multi-step work, chooses and calls tools (editing files, running shell commands, executing tests), observes the results, and decides what to do next across many turns in pursuit of a coding goal — this is squarely agent-level, multi-step autonomous behavior, not a single prompt-and-response exchange. VibeTrace itself is not the agent; it is the collaboration layer that sits on top of the agent's run.

## How humans and the AI agent collaborate

VibeTrace frames the collaboration as a loop: **observe → understand → intervene → evolve**. The agent executes a coding task step by step inside OpenCode; VibeTrace renders that execution as a navigable, interactive trace — actions, intermediate states, and failures — instead of a flat log. When a person spots a problem, they can **fork the execution from an earlier step**, correct it, and let the agent continue from that point, without discarding the validated work that came before. The corrections and traces people produce are then **distilled into reusable "skills"** that the agent can draw on in future runs, so the human's one-time intervention has a lasting effect on the agent's future behavior.

## What role the human plays

The person watches the agent's trace to understand what it has done and why, diagnoses where and why something went wrong, and — when needed — forks execution at the point of failure to supply a targeted correction rather than restarting the whole task. Across repeated use, the human's corrections and feedback feed into a growing library of skills the agent can reuse.

## What role the AI agent plays

The agent (OpenCode-based) autonomously plans and executes the coding task: writing and editing code, running commands, and iterating on results. After a human intervention, it resumes execution from the forked point using the corrected state. The agent also draws on previously distilled "skills" — representations learned from past traces and human feedback — to avoid repeating past mistakes and to work more efficiently (reported, on a separate benchmark, to use fewer tokens and succeed more often).

## How control, initiative, and decisions are shared

The agent has default initiative — it runs multi-step work on its own. The human's control is **targeted and historical rather than constant**: instead of approving or steering every step in real time, the person can reach back into the trace at the specific point something broke, intervene there, and let the agent proceed unaided from the next step onward. This is a form of **selective, retrospective human correction** layered onto an otherwise autonomous agent, combined with a mechanism (skill distillation) that lets individual human corrections generalize to future agent runs rather than being a one-off fix.

## The paper's main idea

**Claim by the authors:** the real bottleneck in human-coding-agent collaboration is not that agents make mistakes, but that conventional execution logs make it hard for people to *inspect* those mistakes and *correct* them surgically. VibeTrace is presented as an answer: a trace-visualization and intervention system that makes an agent's run inspectable and "forkable," paired with a mechanism that turns human corrections into reusable agent skills, evaluated through a mix of benchmark experiments, a controlled comparison study, and expert interviews.

## How the approach works

VibeTrace connects to a local OpenCode HTTP server and renders the agent's execution as an interactive trace view: a navigable record of the agent's actions, intermediate states, and failures, rather than scrolling text. From any point in that trace, a person can fork execution — effectively rewinding to that step while keeping everything validated before it — make a correction, and resume the agent from there. Separately, the system distills patterns from accumulated traces and human corrections into "skills": reusable representations the agent can call on in later tasks, which the authors evaluate for effects on cost and accuracy on the SWE-bench Verified benchmark (an automated coding-agent benchmark, not a human study).

## Human study or evaluation design

**Demonstrated in the paper (per available excerpts), across three evaluation components:**
1. A **benchmark experiment** on SWE-bench Verified testing whether skills distilled from traces/corrections improve the agent's own performance (no human participants in this component).
2. A **controlled user study** comparing VibeTrace's trace visualization against OpenCode's conventional logs, where participants completed two "vibe-coding" tasks and were assessed on execution understanding and error diagnosis.
3. An **expert study** with eight participants who used VibeTrace on real-world coding tasks after a short introduction to both the VibeTrace and OpenCode interfaces, including cases drawn from participants' own projects.

The available excerpts do not make clear whether the "controlled user study" and the "eight-expert study" are the same study described twice or two distinct studies with separate samples — this is flagged as **not independently confirmed** rather than assumed either way.

## Participants and study setting

At least eight participants described as experts took part in hands-on evaluation, using VibeTrace on real coding tasks (including, for some, their own projects) after a brief onboarding to the tool. Demographic details (seniority, industry vs. academic background, programming experience) are not available from the sources used for this summary. This is a small, non-representative sample, consistent with an early-stage HCI system evaluation rather than a large-scale deployment study.

## Experiments or benchmarks

- **SWE-bench Verified** (automated, no human subjects): used to test whether skills distilled from traces and human feedback improve agent performance and efficiency.
- **Two vibe-coding tasks** in the controlled comparison between VibeTrace and conventional logs.
- **Real-world coding tasks**, including some drawn from participants' own projects, in the expert study.

No public dataset or benchmark specific to the human-facing trace/intervention evaluation is reported as released; the code repository is public (see Code link above).

## Main results

**Demonstrated in the paper (per available excerpts):**
- On SWE-bench Verified, using distilled skills **raised the agent's pass rate from 65.0% to 68.0%**, while **cutting input tokens by 23.0% and inference cost by 15.5%** — an agent-capability result, not a human-outcome result.
- In the controlled comparison, participants using VibeTrace's trace visualization reportedly understood agent execution better and diagnosed errors more easily than with OpenCode's conventional logs — reported qualitatively/directionally in the excerpts available; exact effect sizes or statistical tests were not found and should be treated as **not independently confirmed**.
- In the expert study, participants gave positive feedback on VibeTrace's **observability, explainability, and controllability**, reportedly using example cases from their own projects.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper (qualitatively, per available excerpts):** improved self-reported or observed understanding of agent execution and easier error diagnosis when using trace visualization versus raw logs; positive qualitative feedback on observability, explainability, and controllability from expert users. **Not demonstrated in the available excerpts:** no quantified trust scores, workload measures (e.g., NASA-TLX), task-completion-time comparisons, or safety outcomes were found in the sources used for this summary — these may exist in the full paper but could not be confirmed here. **Our interpretation:** the human-facing evidence here is real but currently qualitative and small-sample; it supports the *direction* of the authors' claim (trace visualization plus fork-based intervention helps people understand and fix agent runs) without yet offering the kind of quantified, statistically tested effect sizes that would make the result easy to generalize.

## What is genuinely new

- A concrete mechanism — **forking execution at an arbitrary trace step** — that lets a person correct one specific point in an agent's run without discarding everything that came before or restarting from scratch, which is a more surgical form of intervention than "stop and redirect" or "approve/reject the final diff."
- A **feedback-to-skill pipeline** that turns individual human corrections into reusable agent capability, so that human oversight effort compounds over time rather than being spent once per task.
- A combination of an automated capability benchmark (SWE-bench Verified) with a human-facing comparison study and expert interviews, evaluating both whether the mechanism helps the agent and whether it helps the person.

## Limitations and open questions

- Human evaluation samples are small (at least eight participants) and evaluation details (whether the controlled study and expert study are the same or different participant pools, exact task counts, and statistical analysis) are not fully confirmed from the sources used here.
- No quantified trust, workload, or decision-quality metrics were found in the available excerpts, despite plausible relevance to a system explicitly about human oversight of agent execution.
- The strongest quantitative results (pass-rate and cost improvements on SWE-bench Verified) come from an automated benchmark of the skill-distillation mechanism, not from the human studies, and should not be conflated with the human-collaboration evaluation.
- No peer-reviewed venue is confirmed; this is currently an arXiv preprint.
- This summary itself relies on secondary, search-indexed excerpts rather than a direct read of the full PDF, because arXiv was unreachable from this session's network — readers should verify specifics against the paper directly.

## Practical implications

For anyone building or using long-running coding agents (CLI agents, IDE copilots, autonomous coding bots), this paper suggests a concrete design pattern worth borrowing: don't just show a log of what an agent did — make the execution trace navigable and "forkable" so a person can correct a specific misstep without throwing away the rest of a run, and treat human corrections as training signal (via a skill library) rather than disposable one-off fixes. If the qualitative benefits reported here hold up under more rigorous, larger-scale testing, this kind of surgical, trace-based intervention could reduce the all-or-nothing choice between blind trust in an agent's output and restarting from zero.

## Why you should care

As coding agents take on longer and more consequential tasks, the way humans inspect and correct their work — not just the raw capability of the agent — determines whether delegating to them is actually safe and efficient. This paper is a timely (November 2026), concrete example of research aimed squarely at that problem: giving people a precise way to see into an agent's run, fix exactly what went wrong, and have that fix make the agent better going forward. The evidence so far is promising but preliminary — small human samples and qualitative results — so it's worth watching for a more rigorous follow-up rather than treating it as a settled result.
