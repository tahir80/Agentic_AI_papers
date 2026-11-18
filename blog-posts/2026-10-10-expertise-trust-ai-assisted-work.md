# Why Experts and Novices Use the Same AI Agent So Differently

**Paper title:** Impact of Expertise and Trust on AI-assisted Work
**Authors:** Qianou Ma, Pranav Khadpe, Rock Yuren Pang, Kenneth Koedinger, Tongshuang Wu, Siddharth Suri, Shamsi Iqbal (Carnegie Mellon University and Microsoft Research; author name spellings vary slightly across secondary sources — e.g., "Pranav Khape"/"Khadpe", "Rock Pang"/"Rock Yuren Pang", "Siddarth"/"Siddharth Suri" — not independently verified against the primary PDF in this session)
**Publication date:** 2026-10-10 (arXiv v1)
**Venue:** arXiv preprint, cs.HC; no peer-reviewed venue confirmed from sources used
**Paper link:** https://arxiv.org/abs/2610.14660
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-11-18

> **A note on sourcing:** this session's network access to arxiv.org and its usual mirrors (export.arxiv.org, alphaxiv.org, emergentmind.com) was blocked by the environment's network policy, so the full PDF could not be opened directly. This summary is built from the paper's abstract, HTML excerpts, and secondary citations as they surfaced across several web searches, cross-checked against each other for consistency. The paper itself is a freely available, open-access arXiv preprint. Numbers and quotes below are reported as they appeared in those excerpts; anything not independently confirmed against the primary PDF is marked accordingly (exact task wording, full demographics, and the complete coding scheme were not fully available from the sources used). Please check the arXiv preprint directly before citing specific figures.

---

## The problem the paper addresses

When someone uses an AI agent to help with real work — not a toy demo, but an actual task with a real deadline and a real deliverable — how much should they hand over to the agent, and how much should they stay personally involved in? The authors set out to study this directly: they gave 20 working professionals, with a range of data-science backgrounds, the same agentic tool and the same real task, and watched what people with different levels of expertise and different levels of trust in AI actually did with it.

## Why this problem matters

Most studies of AI agents either measure whether the agent got the right answer, or ask people afterward how much they trusted it. This paper argues that neither view alone tells you what you need to know: a person can "complete" a task by mostly letting the agent do it, without ever understanding whether the result is actually correct. As agentic tools move into real jobs — hiring decisions, data analysis, software engineering — that gap between "looks done" and "is actually right, and the human can vouch for it" becomes a real risk. The authors frame their question as being about more than task success: whether people who delegate to an agent remain able to evaluate the work the agent produced.

## What makes the system agentic

Participants worked with what the paper describes as an "agentic tool" that could carry out a multi-step, real-world data-science assessment — the same one used for hiring evaluations at a major U.S. company — rather than answering a single one-shot question. The available excerpts do not fully detail the tool's internal architecture (e.g., exact planning loop or tool calls), so this summary treats it as described by the authors: an agent capable of taking on substantial chunks of a multi-step analytical task on a person's behalf, which the person could then let run, steer, or override.

## How humans and the AI agent collaborate

The core of the study is not a new interface or protocol — it's an observational account of how real collaboration unfolds when the division of labor is left up to the person. Across three workflow phases (planning, implementation, and review), participants chose, moment to moment, whether to do the work themselves, hand it to the agent, or something in between, and the authors tracked both what people said about this (self-reported, "stated" delegation) and what people actually did on screen ("observed" delegation).

## What role the human plays

The human is the one holding the task and the outcome: deciding how to break the assessment down, whether to let the agent run with a sub-task or step in, and whether to critically check what the agent produced before accepting it. The paper's central lens is on how a person's *expertise* in the task domain and their *trust* in the AI shape these moment-to-moment choices.

## What role the AI agent plays

The agent is the one available to absorb or carry out pieces of the task — planning steps, generating analysis, or producing partial solutions — at whatever level of delegation the human allows. It does not appear to adapt its own behavior to the person; rather, the paper studies how differently people use the *same* agent capability depending on who they are.

## How control, initiative, and decisions are shared

This is **human-directed delegation along a spectrum**, not fixed turn-taking or a shared plan negotiated with the agent. At the planning phase, people ranged from copying the task in and diving straight into agent-produced output, to exploring and decomposing the task into pieces themselves before engaging the agent. At the implementation phase, the range ran from manually steering the agent's work to simply delegating it. At review, people either gave the output a surface-level check or critically scrutinized and guided it. The human alone picks a point on that spectrum at each phase, and the paper's main interest is in what predicts where they land.

## The paper's main idea

**The authors' claim:** a person's task-relevant expertise and their trust in the AI jointly shape *how* they work with an agentic tool — not just whether they use it — and this shapes a real tradeoff between finishing more of the task and understanding/validating what was produced. Delegating more tends to get more of the task done, but increases the chance the result is actually wrong; retaining more control and scrutiny tends to produce more valid outcomes at the cost of finishing less.

## How the approach works

The authors ran a **think-aloud study**: each of the 20 participants narrated their reasoning out loud while completing the same data-science hiring assessment with the same agentic tool. Sessions were analyzed through a coding scheme anchored to three workflow phases — plan, implement, review — with the specific strategy within each phase (e.g., "copy-paste" vs. "explore and decompose" at planning; "manual steering" vs. "delegate to AI" at implementation; "surface review" vs. "critical guidance" at review) emerging inductively from the transcripts and screen recordings. They then related these behavioral codes, plus a self-report AI-delegation-trust scale (4 items, reported Cronbach's alpha = 0.82) and measures of in-domain expertise, to outcomes including task completion, solution validity, participants' sense of understanding, and self-rated success.

## Human study or evaluation design

A within-group, think-aloud observational study: all 20 participants used the identical tool on the identical task, with expertise and trust treated as measured individual differences rather than experimentally manipulated conditions. Data sources reportedly included think-aloud narration, screen recordings, and post-task self-report scales (trust/delegation comfort, cognitive load, satisfaction, self-rated success).

## Participants and study setting

**20 professionals** with varying levels of data-science expertise, each completing the same real-world data-science assessment (described as one actually used for hiring at a major U.S. company) using the same agentic tool. Detailed demographics (job titles, years of experience, recruitment process) were **not available** from the sources used for this summary — check the full paper before citing specifics.

## Experiments or benchmarks

There is no separate automated benchmark; the "experiment" is the single think-aloud study described above, analyzed through behavioral coding plus correlational statistics relating expertise, trust, delegation behavior, and outcomes. Reported statistics include:
- In-domain expertise and AI-delegation trust were moderately correlated (r = 0.48).
- The AI-delegation-trust scale was positively associated with satisfaction with AI use (β/r ≈ +0.53, p = .017) and self-rated success (≈ +0.45, p = .048), and marginally negatively associated with cognitive load (≈ −0.39, p = .087).
- **Stated** (self-reported) delegation showed weak relationships with outcomes, but **observed** (behavioral) delegation significantly negatively correlated with solution completeness (ρ = −0.59, p = .006) and positively correlated with participants' sense of understanding.
- Strategies associated with more human engagement and less delegation (exploring/decomposing at planning, manually steering at implementation, critically guiding at review) were each associated with roughly 62–65% validity of the resulting artifact in the reported breakdown — figures that should be treated as approximate pending a check against the primary PDF, since the full comparison table (i.e., validity rates for the more-delegated strategies) was not fully recoverable from the sources used.

## Main results

**As reported by the authors (via secondary excerpts, not independently re-verified against the primary PDF):**
- **Experts** more often decomposed the task up front, manually steered the agent during implementation, and critically reviewed its output — strategies oriented toward maintaining understanding.
- **Novices** more often copy-pasted the task straight to the agent, delegated implementation to it, and did only a surface-level review — strategies oriented toward finishing quickly.
- Across the sample, delegating more got more of the task *completed*, but increased the likelihood that the final solution was actually *invalid*.
- Experts were more willing to accept a lower completion rate in exchange for being able to scrutinize and vouch for the agent's work; novices tended to prioritize completion over verification.

## Effects on human performance, trust, workload, safety, or decision quality

The clearest human-related finding is the **trust–experience link**: higher self-reported trust in/comfort with delegating to the AI was associated with higher satisfaction and higher self-rated success, and (marginally) with lower cognitive load — but trust was tied to how people *felt* about the interaction, not to whether their final output was actually correct. Separately, how much people *actually* delegated (observed behavior, not stated intent) was the variable that tracked real task outcomes: more observed delegation predicted lower completeness of a valid solution and less reported understanding of the result. In other words, feeling good about delegating and getting a good outcome from delegating were not the same thing in this study — a genuine calibration concern if trust judgments don't track actual solution quality.

## What is genuinely new

*Authors' framing, as surfaced in the sources used here:* the paper's distinctive move is tracing a full chain — from who someone is (expertise, trust) to what they actually do moment-to-moment with an agent (planning, implementation, and review strategies) to what results (task and human outcomes) — rather than treating "delegation" as a single global dial, or treating self-reported trust as a stand-in for real reliance. The split between *stated* and *observed* delegation, and the finding that only the observed version predicted real outcomes, is presented as a key empirical contribution.

## Limitations and open questions

- The authors themselves describe the work as **hypothesis-generating and exploratory** rather than a definitive causal test — with 20 participants and no experimental manipulation of expertise or trust, the correlations reported (e.g., r = 0.48, ρ = −0.59) describe associations among people who differ in many ways, not a controlled contrast.
- *My interpretation:* because every participant used the same single task and tool, it's unclear how much the specific findings (e.g., the ~62–65% validity figures) would generalize to other domains, other agentic tools, or longer-horizon work.
- The authors reportedly flag the need for follow-up work that systematically varies agent and task characteristics, and that examines how different kinds of "understanding" trade off against task outcomes — suggesting they view this study as a first look rather than a settled answer.
- Full demographic detail, the complete behavioral coding scheme, and code/data availability were not confirmed from the sources used in this session; these should be checked against the primary PDF.

## Practical implications

*My interpretation, following the authors' own stated motivation:* organizations deploying agentic tools for real work may want to separate two different questions — "did people like using it / did they feel successful" versus "did the people who used it most heavily actually produce correct, verifiable work" — because this study suggests those can diverge, especially for less-expert users who tend to delegate more and check less. It also suggests that supporting novices in decomposing tasks or scrutinizing agent output, rather than simply handing them a capable agent, may matter for getting trustworthy results, not just good feelings about the tool.

## Why you should care

As agentic AI tools move from demos into actual hiring pipelines, analyst workflows, and other consequential tasks, this paper is a reminder that the *person* using the tool, not just the tool itself, determines whether the outcome can be trusted. Two people can use the identical agent on the identical task and land in very different places — one with a faster, less-verified answer, another with a slower, better-understood one. The paper's evidence that self-reported trust tracked the human's experience but not the task's actual correctness is the kind of calibration gap that matters most as these tools get deployed on work that counts.
