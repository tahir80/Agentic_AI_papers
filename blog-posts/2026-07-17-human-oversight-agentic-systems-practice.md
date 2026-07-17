# When Developers Watch the Machine: How People Actually Oversee AI Coding Agents

**Paper title:** Human oversight of agentic systems in practice: Examining the oversight work, challenges, and heuristics of developers using software agents
**Authors:** Shipi Dhanorkar, Samir Passi, Mihaela Vorvoreanu (Microsoft Research / Aether)
**Publication date:** 2026-06-03 (arXiv preprint)
**Venue:** ACM Conference on Fairness, Accountability, and Transparency (FAccT '26)
**Paper link:** https://arxiv.org/abs/2606.05391
**Code link:** Not available (qualitative interview study; no code repository)
**Project page:** Not available
**Date added:** 2026-07-17

---

## The problem the paper addresses

Autonomous coding agents — tools that can read a codebase, plan a series of edits, write code, run tests, and even open pull requests with only a starting instruction from a person — are spreading fast through software teams. Everyone agrees that a human should "keep an eye on" these agents. But the paper's authors point out that almost all of the guidance on what that oversight should look like is written from the top down: policy documents, ethics frameworks, and regulations that describe oversight in the abstract. Very little research had actually gone and watched what developers do, moment to moment, when they supervise an agent working on real code.

That is the gap this paper fills: not "what should oversight look like," but "what does oversight actually look like, in practice, for people who do it every day?"

## Why this problem matters

If coding agents keep gaining autonomy, the quality of human oversight becomes one of the main safety nets standing between a plausible-looking but wrong piece of code and something that ships into production. Design guidelines, company policies, and regulation (the EU AI Act and similar frameworks are mentioned as context) increasingly assume that "a human in the loop" will catch problems. But if nobody has documented how real oversight happens — when developers step in, what they actually check, and where their attention naturally fails — then those policies are being built on an assumption nobody has tested. This paper is meant to give that assumption an empirical foundation.

## What makes the system agentic

The systems under study are the software coding agents developers already use at work — tools that go beyond autocomplete by taking a task description, forming a multi-step plan, editing multiple files, running commands or tests, and iterating on the result largely on their own before reporting back. The paper does not introduce a new agent architecture; instead, it studies how professional developers work *around* and *with* these already-agentic tools in their daily jobs.

## How humans and the AI agent collaborate

This is the heart of the paper. Rather than treating oversight as one single behavior ("the human checks the output"), the authors found that developers weave oversight into every stage of working with an agent — before it starts, while it plans, while it works, and after it finishes.

## What role the human plays

The developer is not a passive approver waiting at the end of the pipeline. Across the interviews, developers described actively:
- Setting up guardrails before the agent even starts (a priori control).
- Shaping and negotiating the agent's plan before execution begins (co-planning).
- Watching the agent's actions unfold and intervening mid-task (real-time monitoring).
- Reviewing the finished artifact afterward (post hoc review).

## What role the AI agent plays

The agent is the one doing the multi-step work — proposing a plan, writing and editing code, and often invoking tools such as test runners on its own. In this paper the agent is treated as the object of study rather than something the authors built: its job is to execute a coding task with a meaningful degree of autonomy, which is precisely what makes the human oversight work necessary and interesting to examine.

## How control, initiative, and decisions are shared

According to the authors, control is distributed unevenly across the task lifecycle rather than concentrated at a single checkpoint. Developers try to front-load control by constraining the agent's scope and permissions in advance, then shift toward a more collaborative, plan-shaping mode, then toward watchful monitoring once the agent is actually executing, and finally toward evaluative review once it is done. The paper's central claim is that this makes oversight **preventative and proactive**, not just the reactive, after-the-fact review that earlier conceptual work on "human-in-the-loop" tended to assume.

## The paper's main idea

The authors argue that oversight of coding agents is not one activity but an emergent bundle of at least **four distinct forms of oversight work**, each with its own timing and purpose:

1. **A priori control** — instructing and constraining the agent *before* delegating a task, e.g., configuring what level of autonomy it gets, blocking it from certain libraries, or supplying project-wide context so it doesn't go astray.
2. **Co-planning** — working with the agent to shape or negotiate its plan before it starts executing, rather than simply accepting whatever plan it proposes.
3. **Real-time monitoring** — watching the agent as it works and stepping in during execution if something looks off.
4. **Post hoc review** — checking the finished code afterward, the classic "review the diff" style of oversight that most prior discussions of human-in-the-loop focus on.

## How the approach works

This is a qualitative, interview-based study rather than a system-building or benchmarking exercise. The researchers conducted semi-structured interviews with experienced developers who use agentic coding tools in their real work, then analyzed the transcripts to surface recurring patterns — an exploratory, grounded approach common in human-computer interaction research, rather than a controlled experiment with a treatment and control group.

## Human study or evaluation design

The "study" here *is* the human evaluation: there is no separate benchmark or synthetic user standing in for people. The authors interviewed developers about their lived experience overseeing agents on real coding tasks and inductively derived the four-category framework, along with the challenges and heuristics described below, directly from what those developers reported doing.

## Participants and study setting

**17 experienced developers** who use autonomous/semi-autonomous software agents as part of their actual jobs were interviewed. The paper is explicit that this is a real-world, professional-practice setting — developers describing genuine oversight behavior on genuine coding tasks — rather than a lab task built for the study.

## Experiments or benchmarks

There is no quantitative benchmark, leaderboard, or task-success metric in this paper — and it does not claim to have one. Its contribution is the qualitative framework of four oversight forms, plus a catalog of the challenges developers face and the heuristics they use to cope, drawn from the interview data. Readers looking for accuracy numbers or pass/fail rates on a benchmark will not find them here; the paper's evidence is thematic analysis of what practitioners said.

## Main results

As reported by the authors:
- Developers perform (at least) four distinct forms of oversight — a priori control, co-planning, real-time monitoring, and post hoc review — not just the single after-the-fact "review the output" behavior that much prior conceptual work assumes.
- Reviewing agent-generated code is genuinely difficult in practice, and developers face concrete, situated challenges doing it well.
- Developers cope by adopting heuristics — for example, treating a passing test suite as a stand-in "guarantee" for code correctness — rather than exhaustively verifying everything the agent produced.
- The paper's framing is that developers pursue **efficient, not perfect, oversight**: they consciously trade thoroughness for practicality, which the authors describe as a disconnect between idealized notions of human supervision and how oversight actually gets done under real time and workload pressure.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's own evidence here is descriptive rather than measured: it documents *how* oversight is practiced and *why* developers say they cut corners (heuristics like "tests passed, so it's probably fine"), rather than measuring, say, error-detection rates or time-on-task with numbers. The authors' claim — not an independently quantified result — is that this heuristic-driven, "good enough" oversight style creates a gap between what policy frameworks expect of human overseers and what is realistically happening on the ground, which has direct implications for whether relying on "a human will catch it" is a sound safety assumption.

**Interpretation (ours, not the paper's):** because this is an interview study, it cannot tell us how often the heuristics actually fail to catch real bugs — it tells us that experienced developers *believe* they are cutting corners and *why* they do so. That distinction matters when deciding how much weight to put on the findings.

## What is genuinely new

Before this paper, discussions of "human oversight of AI agents" were largely normative — describing what oversight *should* involve — with comparatively little empirical grounding in what practitioners actually do. This paper's contribution is providing that empirical anchor: a concrete, four-part vocabulary for oversight work (a priori control, co-planning, real-time monitoring, post hoc review) built from real practitioners' accounts, plus documentation of the specific coping heuristics they use.

## Limitations and open questions

- **Sample size and method:** 17 interviews is a modest, qualitative sample; the findings describe recurring patterns in what people say they do, not a statistically representative or causally validated account of oversight effectiveness.
- **Self-report:** because the data comes from interviews, it reflects developers' descriptions and perceptions of their own oversight behavior, which may not perfectly match what they would do if directly observed.
- **No outcome measurement:** the paper does not measure whether the heuristics developers use (like trusting passing tests) actually correlate with catching more or fewer real defects — that link is asserted as a concern, not tested.
- **Open question the paper raises:** if "efficient, not perfect" oversight is the realistic norm, what does that mean for policies and regulations that assume thorough human review as a safety backstop for agentic systems?

## Practical implications

For teams deploying coding agents, the paper is a useful reality check: assuming that "a developer will review it" is equivalent to rigorous, uniform scrutiny at every stage may be optimistic. The four-category framework is a useful checklist for tool builders — it suggests that agent tooling should support oversight *before* a task starts (permissions, scoping, context), *during* planning (letting a person shape the plan, not just approve it), *during* execution (surfacing what the agent is doing in real time), and *after* completion (review), rather than only building a good "review the diff" experience at the end.

## Why you should care

If you use, manage, or build around coding agents, this paper puts language and structure around something you have probably felt but not named: that "watching an AI agent work" is not one job but several different jobs happening at different times, each with its own blind spots. It is a reminder — grounded in real developers' own accounts, not speculation — that oversight quietly becomes a set of practical compromises under time pressure, which is exactly the kind of finding that should shape how the next generation of agent tools presents its work to the humans still responsible for it.

---

*Claims in this summary attributed to "the authors" or "the paper" reflect what is reported in the arXiv preprint (2606.05391); passages marked as interpretation are the summary writer's own reading and are not asserted by the paper itself.*
