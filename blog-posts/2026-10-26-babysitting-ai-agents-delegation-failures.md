# When "Just Delegate It to the AI Agent" Goes Wrong

**Paper title:** Babysitting AI Agents: A User-Centered Taxonomy and Study of Agentic Delegation Failures
**Authors:** Shravika Mittal, Sunnie S. Y. Kim, Scott Counts, Jennifer Neville, Debarati Das, Philippe Laban
**Publication date:** 2026-10-26 (arXiv v1)
**Venue:** arXiv preprint; venue/acceptance not yet confirmed
**Paper link:** https://arxiv.org/abs/2610.34748
**Code link:** Not available (no repository or dataset release was found during this session's research; check the paper directly for a possible link)
**Project page:** Not available
**Date added:** 2026-11-25

> **A note on sourcing:** this session's direct network access to arxiv.org and related mirrors (alphaxiv, export.arxiv.org, etc.) was blocked by the environment's network policy, so the full PDF could not be opened directly. This summary is built from the paper's abstract and HTML excerpts as they surfaced across several targeted web searches, cross-checked against each other and against secondary write-ups (including a FourWeekMBA summary and a Substack "journal club" post) for consistency. The paper itself is a freely available, open-access arXiv preprint. A few specific numbers below (marked explicitly) come only from secondary summaries and could not be independently confirmed against the full PDF — treat those as reported-but-unverified, and check the arXiv preprint directly before citing them.

---

## The problem the paper addresses

People are increasingly handing real tasks — not just questions, but entire jobs like "fix this bug," "book this trip," "clean up this spreadsheet" — over to AI agents that act on their own for multiple steps. Sometimes that works great. Often, something goes wrong partway through: the agent gets stuck, does the wrong thing, or quietly "completes" a task without actually finishing it. This paper asks a simple but under-studied question: *what actually goes wrong when people delegate tasks to AI agents, in the real world, and how do users notice and recover from it?*

## Why this problem matters

Most agent research measures success rates on benchmarks. Far less attention goes to the messier, more common experience of a real person watching an agent fail at a real task they care about. If agent builders don't know the full range of ways delegation breaks down — or which failures users barely notice until it's too late — they can't design better handoffs, warnings, or recovery tools. This paper is explicitly trying to fill that gap with evidence from actual agent users, not just lab benchmarks.

## What makes the system agentic

The paper doesn't build a new agent; it studies agents already in wide use — coding assistants (the data skews heavily toward r/ClaudeAI and r/Cursor communities), browser/computer-use agents, and general-purpose task agents — all of which plan multi-step actions, call tools, and operate with some autonomy on a user's behalf rather than just answering a single question. The object of study is exactly the "agentic" behavior: planning, acting, and sometimes going off the rails over multiple steps without the user watching every move.

## How humans and the AI agent collaborate

The collaboration pattern here is **delegation under uncertainty**: a person hands a task to an agent, steps back to some degree, and only re-engages when something seems off — or, worse, after the fact, when a failure has already happened. The paper is centrally about this hand-off relationship: how users decide to delegate, what they notice (or fail to notice) about how it's going, and how they intervene or adjust afterward.

## What role the human plays

In the real-world scenarios the paper documents, humans are the ones who initiate delegation, monitor (often imperfectly) while the agent works, notice (or miss) failures, and then respond — through immediate remediation of a specific failure and/or longer-term changes to how they use agents going forward. In the companion study, 73 people with real agent-delegation experience were asked to recall and describe a specific delegation episode and reflect on how severe and how noticeable the failure was, and what they did about it.

## What role the AI agent plays

The agents are the ones doing the delegated work — writing code, browsing the web, executing multi-step tasks — and, crucially, the ones whose failures are the paper's subject. The paper is not about what a well-behaved agent does; it's a catalog of the many ways these agents fall short while nominally "handling" a task on a person's behalf.

## How control, initiative, and decisions are shared

Control here is lopsided by design: the user largely hands off initiative to the agent for the duration of a delegated task, which is exactly what creates the problem space the paper studies. There's no shared real-time control loop (no co-piloting or step-by-step approval in the failures described) — the tension the paper documents is precisely what happens *between* the moment of delegation and the moment the human re-engages, and how that gap lets failures go undetected or unaddressed for a while.

## The paper's main idea

The authors argue that agent failure needs a **user-centered** taxonomy — not just "did the agent get the right answer," but what the person delegating the task actually experienced: how common different failure types are, how severe users judge them to be, how easy or hard they are to notice, and what people actually do in response. They call this taxonomy **MANDATE**, built from a large corpus of real user-reported experiences rather than from lab observations alone.

## How the approach works

The study has two linked parts. First, the authors mined a large corpus of **163,487 Reddit posts** describing people's experiences delegating tasks to AI agents, and identified **4,367 posts that described at least one failure**, covering **6,623 individual failure instances**. From this, they built MANDATE bottom-up: a taxonomy of **23 failure categories organized into 7 higher-level groups** (for example, failures around an agent making no real progress on a task were flagged as common but under-studied). Second, they ran a **follow-up study with 73 experienced AI-agent users**, recruited through a screening survey, who described a specific past delegation experience in a scenario-based online survey and reported how severe and how noticeable that failure was, along with what they did to fix or work around it, immediately and over the longer term.

## Human study or evaluation design

The 73-person study is a **self-report, recall-based survey**, not a controlled task where researchers watched people delegate work and fail in real time. Participants were screened for prior experience delegating tasks to AI agents, then asked to recall and describe a specific delegation episode (its failure, its severity, how noticeable it was, and their response to it) in a structured online questionnaire.

## Participants and study setting

73 participants with self-reported experience delegating tasks to AI agents, recruited via a screening process (exact recruitment channel and demographic breakdown not confirmed from available excerpts). According to the search excerpts available, only about half of participants (36 of 73) were able to describe a sufficiently specific failure episode; the rest gave vaguer or more general accounts — itself a finding about how hard these failures can be to pin down after the fact.

## Experiments or benchmarks

There is no benchmark or controlled experiment in the usual agentic-AI sense. The "experiment" is the large-scale corpus analysis (163k+ Reddit posts) used to build and populate the MANDATE taxonomy, paired with the 73-person recall survey used to connect taxonomy categories to perceived severity, noticeability, and user response.

## Main results

The authors report that failures cluster heavily around certain agent types in the corpus — most visibly coding agents (r/ClaudeAI and r/Cursor were the most failure-heavy communities in the data) — and that some of the most frequently reported failure types, such as an agent running without making real progress, have received comparatively little attention in prior agent-evaluation research. *Reported only in secondary summaries, not independently confirmed against the full paper:* one write-up claims a negative correlation between a failure category's severity and how easily it's noticed (reported as Spearman's ρ ≈ -0.61); treat this figure with caution until verified against the source PDF.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's framing strongly implicates user trust and safety — failures that are severe but hard to notice are exactly the kind that could erode trust unpredictably or let real harm slip through unaddressed — but the available excerpts do not show the authors running a separate, quantified measurement of trust, workload, or decision quality as outcome variables. The main human-related evidence is the self-reported severity/noticeability ratings and the recall difficulty itself (only half of participants could pin down a specific episode), which is itself informative about how agent failures register, or fail to register, with real users.

## What is genuinely new

Two things stand out as novel, demonstrated contributions: (1) a **large-scale, bottom-up taxonomy of agent delegation failures grounded in real users' own words** rather than researcher-constructed failure scenarios, and (2) empirically connecting failure *type* to perceived *severity* and *noticeability* through a dedicated user study — moving the conversation from "does the agent complete the benchmark task" to "what does this failure feel like, and how would a person even know it happened."

## Limitations and open questions

The authors themselves flag that Reddit posters are self-selected and likely skew toward particular communities (notably coding-agent power users), so MANDATE's category frequencies may not represent the broader population of agent users or use cases. The 73-person follow-up study drew on people who already delegate frequently to agents, which limits how far its findings generalize to more casual or first-time users. The recall-based design also means the study captures what people remember and choose to report well after the fact, not failures observed as they happened — and the fact that over a third of participants couldn't describe a specific episode suggests the method itself may undercount subtler or harder-to-articulate failures.

## Practical implications

For teams building or deploying agents, the practical takeaway is to design explicitly for the failure modes users report experiencing — especially ones that are severe but easy to miss — rather than assuming benchmark success translates into a safe real-world delegation experience. That could mean better progress-visibility signals (directly addressing the "agent isn't actually making progress" failure type), clearer indicators of when a task has silently stalled, or prompts that help users notice and recall failures more concretely than "it just didn't feel right."

## Why you should care

This paper is a useful corrective to agent hype: it's a reminder, grounded in thousands of real reported experiences, that handing a task to an agent and walking away is not a solved problem. Even for people who already use agents regularly, noticing when delegation has gone wrong — and knowing what to do about it — is itself hard, which matters directly for anyone thinking about how much to trust, supervise, or hand off to an AI agent in their own work.

---

### Candidate comparison and selection rationale

As part of this run's search process, the following candidates were compared before selecting this paper (scored 0–5 unless noted, per this project's rubric: Human–AI collaboration relevance / Strength of real human evaluation / Agentic AI relevance / Methodological quality / Practical relevance / Recency 0–3):

1. **"Babysitting AI Agents: A User-Centered Taxonomy and Study of Agentic Delegation Failures"** (arXiv 2610.34748, Oct 26 2026) — **Selected.** Agentic: clearly yes — studies real-world coding, browser, and task agents performing multi-step delegated work. Human–AI collaboration: 4/5 — centrally about how users delegate, monitor, notice failures, and recover/adapt (calibrated trust, repair after breakdown). Real human evaluation: 3/5 — a real 73-participant study with real agent users, though self-report/recall-based rather than a controlled task; paired with a large real-user-generated corpus (163k Reddit posts). Methodological quality: 4/5 (mixed-methods: large corpus + structured taxonomy + targeted user study). Practical relevance: 5/5. Recency: 3/3 (within the last 30 days, and not previously in this repository's table).
2. **"Human-in-the-Loop Runbook Improvement with Agentic Support Automation"** (arXiv 2611.28441, arXiv-posted Nov 21 2026) — Rejected. Real deployment data (232 production incidents over 17 weeks) and genuine human-agent collaboration (an agent guides operators through incident mitigation and proposes runbook edits), but the work was originally published at IEEE CogMI 2025 and only recently mirrored to arXiv, creating an unreliable "recency" signal; the authors also report their core metric (whether the system drove more/better runbook updates) as inconclusive, weakening methodological strength relative to candidate 1.
3. **"When AI Agents Act on Our Behalf: A Taxonomy of Human-Agent Interaction Failure"** (arXiv 2611.00291, Oct 30 2026) — Rejected. Relevant topic (a taxonomy of human-agent interaction failure across autonomy levels) but built from 695 documented incident reports via qualitative coding by the paper's two authors, not from a study with real human participants reacting to or using agents; weaker on "strength of real human evaluation" than candidate 1.
4. **"Principled Human-AI Collaboration in Agentic Workflows"** (arXiv 2611.01566, Nov 2026) — Rejected. A statistical framework (stat.ML) for deciding which AI-generated outputs can skip human review while meeting expert-quality guarantees; evaluated only via synthetic experiments, with no real human participants and a system (generate-verify content release) that is only marginally "agentic" in the multi-step, tool-using sense this project requires.
5. **"Puzzles to Paradigms: A Survey of Human-Agent Collaboration in Scientific Innovation"** (arXiv 2611.09917, Nov 2026) — Rejected. On-topic by title, but it is a literature survey built from a targeted (non-systematic) search of prior work, not a paper reporting a new system, study, or experiment of its own.

Candidate 1 was selected as the strongest combination of a real, non-duplicate human-involvement study, clear agentic-AI relevance, and recency, while being transparent that its human evaluation is a recall-based survey rather than an observed, controlled interaction study.
