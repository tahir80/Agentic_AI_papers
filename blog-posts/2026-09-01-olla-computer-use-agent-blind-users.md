# Are We There Yet? Assessing Computer-Use Agents for Blind Users' Accessible Interaction with Desktop Applications

**Authors:** Satwik Ram Kodandaram, Monalika Padma Reddy, Xiaojun Bi, Jiawei Zhou, I. V. Ramakrishnan (Stony Brook University); Vikas Ashok (Old Dominion University)
**Publication date:** 2026-09-01 (arXiv id 2609.00524)
**Venue:** Accepted, EMNLP 2026 Main Conference
**Paper link:** https://arxiv.org/abs/2609.00524
**Code link:** Not available (no code or data repository could be found or verified)
**Project page:** Not available (no project page could be found or verified)
**Date added:** 2026-09-08

> **A note on sourcing:** arXiv was unreachable from this research session's network (the fetch tool is blocked network-wide for arxiv.org in this environment), so this summary is built from web-search-grounded excerpts of the paper's abstract and reported findings, cross-checked across multiple independent search queries, rather than a direct PDF read. Facts below reflect what those excerpts report; anything not confirmed is marked "Not available," and interpretive statements are labeled as such. Readers should verify details against the arXiv page directly before citing this paper.

---

## The problem the paper addresses

Computer-use agents (CUAs) — AI systems that look at a screen, decide what to click or type, and carry out multi-step actions in real desktop applications — are usually built and judged for sighted users who can watch the agent work and step in visually if something goes wrong. Blind users, who rely on screen readers to navigate a computer by sound and keyboard rather than sight, have a fundamentally different relationship to that same interface. This paper asks a very direct question: when you actually hand a screen-reader-accessible CUA to blind users and let them use it for their own real work over weeks, does it hold up — and where exactly does it fail?

## Why this problem matters

Screen-reader users already do more work than sighted users to operate the same software, because a screen reader exposes a website or application one linear, spoken element at a time rather than as a glanceable visual layout. An AI agent that could reliably operate a desktop application on a blind user's behalf — booking a form, formatting a spreadsheet, navigating a settings menu — could meaningfully reduce that burden. But if the agent fails silently, gets confused about what's on screen, or can't explain what it's doing, it risks making a user's task-completion experience worse, not better, especially since the user often can't independently double-check the agent's work by glancing at the screen the way a sighted user could. Getting this right — or clearly documenting where it currently goes wrong — has direct, practical stakes for real people's independence and daily computer use.

## What makes the system agentic

The paper's object of study, OLLA, is a computer-use agent: it combines language-model reasoning with multimodal interface grounding (interpreting screenshots and UI structure) to autonomously decide and execute sequences of GUI actions — clicks, keystrokes, navigation steps — needed to carry out a user's stated goal inside real, unmodified desktop applications. It is not answering questions about an interface; it is operating one, across multiple steps, using tools (the OS's own UI) to pursue a goal, and it is evaluated on whether the resulting chain of actions actually accomplishes real tasks in the 12 applications tested — the paper's own criteria for a genuine agentic system.

## How humans and the AI agent collaborate

Blind users issued natural-language commands to OLLA to accomplish tasks in real desktop applications they use in their everyday lives, over a three-week diary study, rather than a short one-off lab task. The system executed the requested multi-step action sequence, and users experienced (and, per the interviews, reported on) the agent's successes, partial successes, and failures across a large number of real commands. This is genuine deployment-in-the-wild collaboration: users bring their own tasks, the agent acts on real applications, and the resulting interaction data plus follow-up interviews are what the paper analyzes.

## What role the human plays

Eight blind participants used OLLA as their own assistive tool for three weeks, issuing 1,258 real commands of their own choosing across 12 different desktop applications. Beyond simply using the system, they were the direct source of the study's evidence: their commands, the agent's screenshots/UI-tree state, and its responses and action traces were logged, and participants were interviewed afterward about their experience — including where the agent fell short of what they actually needed from an assistant.

## What role the AI agent plays

OLLA is the acting party: it receives each spoken/typed command, reasons about the current screen state (via screenshots and UI trees), plans a sequence of GUI actions, and executes them inside the real application. The underlying models were evaluated during live deployment and, afterward, five different models (with GPT-5 performing best) were re-run against the same logged commands to compare task success rates and analyze exactly how and where each model's action traces broke down.

## How control, initiative, and decisions are shared

The human retains task-level initiative throughout — every session begins with a user-issued command reflecting their own real goal — while the agent has full execution-level autonomy for how it carries that command out. There is no fixed division of labor beyond that: the study specifically investigates what happens *within* the agent's autonomous execution (where it succeeds, where and why it fails) and what users say they'd want beyond simple command-and-execute automation, rather than testing an explicit shared-control or hand-off protocol.

## The paper's main idea

Instead of evaluating computer-use agents only on synthetic, pre-scripted benchmark tasks, the authors argue the field needs field data from the population that most needs reliable non-visual computer assistance. They built and deployed OLLA specifically to be screen-reader accessible, then combined (a) quantitative model-comparison analysis on real user commands and (b) qualitative interview analysis of what users actually wanted from the tool, to characterize both where today's best CUAs fail technically and where they fall short of blind users' actual collaboration needs.

## How the approach works

OLLA logs each command together with the on-screen state (screenshots and UI-tree representations), the model's response, and the resulting action trace. After the three-week deployment, the authors re-executed the same 1,258 logged commands against five different underlying models, scoring task success and then manually analyzing failed traces to categorize the kinds of errors involved (e.g., misidentifying an on-screen element, losing track of a stated constraint mid-task, or not recognizing that a task was actually finished). Semi-structured interviews with the same participants were analyzed to surface what kinds of help users wanted that went beyond the agent simply executing a command.

## Human study or evaluation design

A three-week diary/field study: participants used OLLA for their own real tasks in their own desktop environments over an extended period, rather than in a single lab session on tasks assigned by the researchers. This was followed by post-study interviews, and by an offline re-evaluation of the logged real commands across multiple models for controlled comparison.

## Participants and study setting

8 blind users, screen-reader users of real desktop applications, participating in their own everyday computing contexts over three weeks. Recruitment details, demographics, and screen-reader software used were **Not available** from the sources consulted for this summary.

## Experiments or benchmarks

Not a synthetic benchmark: the evaluation set is the 1,258 real, user-generated commands collected during the field deployment, spanning 12 real desktop applications. These logged commands were then re-run against five different models (GPT-5 and four others) to compare success rates on identical, real-world-sourced tasks — arguably a stronger ecological-validity test than typical synthetic CUA benchmarks, though drawn from only 8 users' task distributions.

## Main results

GPT-5 achieved the highest task success rate among the five models tested, reported at 52.5%. Trace-level analysis of failures identified recurring categories: grounding failures (misreading or misidentifying on-screen elements), planning failures, constraint-tracking failures (losing track of task requirements mid-execution), and termination failures (not correctly recognizing task completion or incompletion).

## Effects on human performance, trust, workload, safety, or decision quality

The paper reports, via its interviews, that blind users' needs go beyond simple automation — they describe wanting the agent to do things like troubleshoot when something isn't working, explain the current UI state, and help them learn an application, not just silently execute commands. This points to trust and usability gaps: a roughly-50%-success-rate agent, operating for users who often cannot independently visually verify its actions, creates real friction and a need for the agent to be more transparent and explanatory about what it is doing and why. Specific quantitative measures of trust, workload, or safety (e.g., survey instruments or Likert-scale ratings) were **Not available** from the sources consulted for this summary — this account should be treated as the authors' qualitative characterization until the full text can be verified.

## What is genuinely new

This appears to be among the first studies to deploy a computer-use agent with real blind users for real tasks over an extended (three-week) field period, rather than in a single lab session or on synthetic accessibility benchmarks — combining that field-collected command set with a controlled, multi-model re-evaluation on the exact same real tasks, plus interview-derived insight into collaboration needs that a pure success-rate benchmark would miss.

## Limitations and open questions

Based on available sources: a small participant sample (8 users), a best-model success rate around half of attempted commands (meaning failures were common during the actual field deployment, not just in retrospective analysis), and reliance on interview self-report for the "beyond automation" needs rather than a separate controlled comparison of alternative, more collaborative agent designs. Whether the findings generalize across different screen readers, operating systems, or a broader population of blind users is **Not available** from the sources consulted.

## Practical implications

The paper's failure taxonomy (grounding, planning, constraint-tracking, termination) gives concrete engineering targets for anyone building accessible computer-use agents. Its interview findings suggest that accessible CUA design should not stop at "execute the command correctly" — it should also support explanation, troubleshooting help, and teaching, which are collaboration needs distinct from raw automation and likely require different interaction design (e.g., the agent narrating its own state and uncertainty) rather than only improving raw task success rate.

## Why you should care

This is a rare case of an agentic AI system being handed to a population with a direct, high-stakes practical need for it, then studied in real use over weeks rather than in a lab demo — and the honest result is a roughly coin-flip success rate on real tasks, with users wanting more than automation from their AI assistant. It's a useful corrective to benchmark-driven optimism about computer-use agents: real deployment with real users surfaces both concrete technical failure modes and collaboration needs that synthetic evaluations are unlikely to reveal.

---

*Distinguishing claims from results: the 52.5% GPT-5 success rate, the 1,258-command/12-application/8-participant/three-week study design, and the four named failure categories are reported findings from the paper (via secondary sources). The characterization of "beyond-automation" interview themes and their implications for collaboration design reflects the authors' qualitative reporting as summarized in available excerpts. Framing of practical implications and the "why you should care" take are this summary's own interpretation, not direct quotes from the paper.*
