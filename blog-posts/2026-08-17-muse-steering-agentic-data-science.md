# When Your Data-Analysis Agent Goes Off the Rails, Can You Actually Fix It? Meet MUSE

**Authors:** Wei-Hao Chen, Weixi Tong, Yuan Tian, Tianyi Zhang (Purdue University, Human-Centered Software Systems Lab), Chenglong Wang (Microsoft Research)
**Publication date:** 2026-08-17 (arXiv v1)
**Venue:** Accepted to ACM UIST 2026 (39th ACM Symposium on User Interface Software and Technology), November 2–5, 2026, Detroit, MI, USA
**Paper link:** https://arxiv.org/abs/2608.16181
**Code link:** Not available (no public code/data repository found at time of writing)
**Project page:** https://www.microsoft.com/en-us/research/publication/muse-an-interactive-meta-agent-for-understanding-and-steering-llm-powered-data-science-systems/
**Date added:** 2026-09-12

> **A note on sourcing:** this session's outbound network access to arxiv.org and every mirror/aggregator tried (Hugging Face, Semantic Scholar, export.arxiv.org) was blocked at the network egress layer (organization policy, not a paywall — the paper is a public arXiv preprint). This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed," and readers who need precise numbers, full results tables, or participant demographics should consult the arXiv preprint directly.

---

## The problem the paper addresses

Modern "agentic" data science tools let you type something like "clean this dataset and tell me which factors predict churn" and the agent will write and run code, transform data, and produce an analysis — all on its own, in many steps. That's powerful, but it creates a new problem: when the agent's output looks wrong, or just looks *off*, how does a person figure out what happened? The agent's own record of what it did is usually a long, low-level execution log — a wall of tool calls, intermediate variables, and code snippets — that is exhausting to read and hard to connect back to "what actually went wrong in my analysis." And even once a person spots the problem, most interfaces only let them react by typing a brand-new prompt and waiting for the whole pipeline to run again from scratch.

## Why this problem matters

This is the everyday reliability gap in agentic tools: it's not that the agent is always wrong, it's that when it *is* wrong, ordinary users have no good way to notice, understand why, or correct it without starting over. That gap matters commercially and practically — nobody wants to blindly trust an agent's spreadsheet analysis before a big decision, but nobody wants to manually re-read thousands of lines of execution trace either. Getting this "middle layer" right — enough transparency to trust the result, without demanding an engineer's patience to get it — is a prerequisite for agentic data tools to be used seriously rather than treated as a novelty.

## What makes the system agentic

The system under study has two parts. First, there is an underlying LLM-powered data science agent that autonomously plans and executes multi-step workflows — loading data, transforming it, writing and running analysis code, and producing results — from a natural-language request, without a human writing the code itself. Second, sitting on top of that agent is **MUSE**, an interactive "meta-agent": a system that itself processes the underlying agent's behavior (its logs, its actions, its outputs) and produces new artifacts — restructured summaries, flagged warnings, verification scripts, and translated repair instructions — rather than just displaying raw text. Both layers plan, act, and produce outputs beyond a single reply, and both are evaluated as active systems (the underlying agent doing the data science, MUSE doing the mediation) rather than as one-shot chatbots.

## How humans and the AI agent collaborate

MUSE's core idea is to give a human a legible, actionable window into an otherwise opaque agent execution, and a direct way to reach in and redirect it mid-task rather than only after the fact. Instead of reading a flat trace or waiting for a whole run to finish before intervening, the user can move between a high-level overview of what the agent has done and low-level implementation detail, ask grounded questions about a specific step by referencing it directly, and — when something looks suspicious — have that step scaffolded for verification and repair on the spot.

## What role the human plays

According to the paper's description, a person using MUSE inspects the agent's evolving workflow at whatever level of detail they need, asks questions grounded in specific steps rather than the whole trace, verifies intermediate results using scaffolded verification plans and scripts MUSE prepares, and gives feedback or edits to redirect problematic steps — all without needing to manually dig through the raw execution history or leave the interface to check things in an external editor.

## What role the AI agent plays

Two agent-like roles are involved. The underlying data science agent does the actual work: it plans and executes the multi-step analysis autonomously in response to the original natural-language request. MUSE, the meta-agent, continuously restructures that agent's raw execution trace into multiple semantic levels, monitors the trace to flag potentially problematic ("suspicious") steps for the human's attention, and — once a person has reviewed and decided how to fix something — translates that repair intent back into a contextualized instruction the underlying agent can act on, closing the loop between human judgment and agent execution.

## How control, initiative, and decisions are shared

The underlying agent has the initiative to run the workflow autonomously step by step; the human doesn't write the code. But MUSE is explicitly designed for **mixed-initiative steering**: the system takes the initiative to flag suspicious steps for review, while the human takes the initiative to inspect, question, verify, and repair whichever steps they choose, at whatever point they choose — rather than only being able to act at fixed checkpoints or only after the entire run completes. Per the paper's reported comparison, this in-situ intervention is the key difference from baseline interfaces, where users had to wait for the full pipeline to finish before they could even write a corrective prompt.

## The paper's main idea

**Claim by the authors:** the reason agentic data science systems are hard to trust and correct isn't a lack of raw information — it's that raw execution traces are the wrong representation for a human collaborator. Reorganizing that trace into multiple semantic levels, proactively surfacing likely problem spots, scaffolding in-situ verification, and translating human repair intent into agent-usable instructions together let a person actually understand and steer an agentic workflow, rather than just watch it happen.

## How the approach works

MUSE is structured as four layers. The **Summarization Layer** transforms the underlying agent's raw execution logs into a structured, multi-level semantic representation of the workflow — so a user can navigate between a high-level overview and low-level implementation detail rather than reading one long flat log. The **Monitoring Layer** highlights potentially problematic steps for inspection. The **Verification Layer** supports in-situ checking of intermediate results through scaffolded verification plans and targeted verification scripts, so a person doesn't need to independently re-derive whether a step's output is trustworthy. The **Steering Layer** lets users give feedback and revise specific problematic steps, and translates that repair intent into contextualized instructions that are fed back to the underlying data science agent — allowing correction without restarting the whole workflow.

## Human study or evaluation design

The authors ran a **between-subjects study with real human participants** (not simulated users) comparing three interface conditions on data science tasks: a baseline condition, a stronger baseline the paper reports as inspired by prior work ("DiLLS"-style) that explains agent behavior via three-layered summaries but does not support in-situ action — meaning users had to manually recover context and switch to an external editor to inspect, verify, or modify the workflow — and the full MUSE condition. Participants completed a post-task questionnaire using 7-point Likert-scale items covering understanding, error localization, verification, trust, and control, alongside a measure of task completion time.

## Participants and study setting

Per available search excerpts, the study involved **15 participants** in a between-subjects design (i.e., each participant used only one of the three interface conditions). Detailed demographics, recruitment method, and participants' professional backgrounds were not confirmed from the sources available in this session; readers who need that information should consult the paper directly.

## Experiments or benchmarks

There is no standard public benchmark here; the evaluation is built around the 15-participant lab study described above, comparing the MUSE condition against the two baseline interface conditions on researcher-designed data science tasks performed with an LLM-powered data science agent backend.

## Main results

**Reported by the authors, per available search excerpts:**
- Participants using MUSE completed tasks in about **17 minutes on average**, which the authors report as roughly **35% and 9% faster** than the two baseline conditions respectively.
- Post-task confidence ratings differed significantly across the three conditions (reported means of 4.20, 2.60, and 5.80 across the conditions, with the MUSE condition scoring highest), with an ANOVA showing this difference was statistically significant (**p = .0265**).
- Participants reported that it was easier to exert control over the agent with MUSE than with either baseline; in the baseline conditions, they described having to wait for the entire pipeline to finish before they could write a prompt to steer the agent, whereas MUSE allowed in-situ intervention.

Full results tables, effect sizes, and per-item Likert breakdowns (understanding, error localization, verification, trust, control) beyond what is summarized above could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The confirmed, reported effects are on **task efficiency** (faster completion with MUSE) and **subjective confidence/control** (significantly higher self-reported confidence and a reported sense of easier in-situ control with MUSE). These are directly relevant proxies for trust and decision quality in a human-agent collaboration setting, though the paper's own emphasis appears to be on confidence and controllability specifically, rather than on downstream outcomes like the correctness of participants' final data-analysis conclusions or their long-term reliance behavior — those effects, if measured, were not confirmed from the sources available in this session.

## What is genuinely new

- **A meta-agent layer purpose-built for human oversight of an agentic system**, rather than a better chat interface bolted onto the same agent.
- **Multi-level semantic restructuring of execution traces**, letting a person move fluidly between overview and detail instead of being stuck at one level of granularity.
- **In-situ steering with intent translation**: the system doesn't just show a problem, it scaffolds verification and turns a person's repair decision directly into an instruction the underlying agent can execute, closing the loop without a full restart.
- **A real controlled human study (n=15) directly comparing MUSE against a serious prior-work-inspired baseline**, not just against no tooling at all — the DiLLS-style comparison condition specifically isolates the value of in-situ steering versus "better explanation alone."

## Limitations and open questions

- **Small sample size.** A between-subjects study with 15 participants (roughly 5 per condition, if evenly split) is a real human evaluation, but it is a modest sample for statistical robustness — the reported p = .0265 result should be read in that light.
- **Lab tasks, not real-world workflows.** The tasks were researcher-designed for the study; how MUSE performs on messier, longer-horizon, real-world data science work by practitioners on their own data was not confirmed from the sources available in this session.
- **Generalization across backend agents and domains.** It's unclear from available excerpts whether MUSE's approach was tested with more than one underlying data science agent, or whether the same design would transfer to other agentic domains (e.g., coding agents, research agents) beyond data science.
- **Explicit limitations/future-work discussion.** The paper's own stated limitations, threats to validity, and future-work section could not be retrieved from the sources available in this session — this summary's "limitations" above are the reviewer's own reading of what is and isn't confirmed, not a restatement of the authors' own caveats.
- **Peer-review status at time of writing.** The paper is reported as accepted to UIST 2026, a top-tier, peer-reviewed HCI venue, though this session could not independently confirm the final camera-ready details.

## Practical implications

If the reported results hold up, they point to a concrete, reusable design pattern for anyone building agentic tools that ordinary users are meant to trust and correct: don't just expose the agent's raw trace, and don't just summarize it better — actively monitor it for likely problem spots, scaffold verification so people don't have to manually re-derive correctness, and make repair a first-class, in-situ action that feeds directly back into the agent's execution. That pattern plausibly extends well beyond data science, to any domain where an LLM agent takes many autonomous steps that a non-expert user needs to be able to supervise and fix.

## Why you should care

A huge amount of "human-in-the-loop" agent design boils down to giving people a chat box to type follow-up requests into and hoping that's enough. MUSE is a useful example of what happens when a research team instead treats *legibility and repairability of an agent's own execution* as a first-class design problem, then tests the result against a serious baseline with real users rather than just describing the design. The headline finding — that a genuinely different way of presenting and interacting with agent behavior measurably increased people's confidence and shaved meaningful time off task completion — is a small but concrete data point that how you let a person see and touch an agent's reasoning matters as much as how good the underlying agent is.
