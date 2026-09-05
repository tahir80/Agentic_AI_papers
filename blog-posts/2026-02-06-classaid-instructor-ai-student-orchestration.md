# ClassAid: A Real-time Instructor-AI-Student Orchestration System for Classroom Programming Activities

**Authors:** Gefei Zhang, Guodao Sun, Ronghua Liang (Zhejiang University of Technology), Meng Xia (Texas A&M University)
**Publication date:** 2026-02-06 (arXiv id 2602.06734, cs.HC)
**Venue:** ACM CHI Conference on Human Factors in Computing Systems (CHI 2026), Barcelona, Spain, April 13–17, 2026; DOI 10.1145/3772318.3790824
**Paper link:** https://arxiv.org/abs/2602.06734
**Code link:** Not available (no public repository could be confirmed from sources used)
**Project page:** Not available
**Date added:** 2026-09-05

> **A note on sourcing:** arXiv itself, along with essentially every other external domain, was unreachable from this research session's network (only github.com/raw.githubusercontent.com were reachable), so this summary is built entirely from web-search-grounded excerpts of the paper's abstract, HTML body, and reported results rather than a direct PDF read. Facts below reflect what those excerpts report; anything not confirmed through this method is marked "Not available," and interpretive statements are labeled as such.

---

## The problem the paper addresses

Generative-AI coding assistants are now common in programming classrooms, but they create a tension: give students unrestricted access to an AI helper and some will lean on it for ready-made answers instead of learning to reason through problems themselves, undermining the whole point of the exercise. Take the AI away and instructors lose a scalable way to give each student individualized, timely feedback in a room full of learners coding at different paces and hitting different obstacles. The paper's core problem is how to let an AI teaching assistant help at scale in real time, without the instructor losing the ability to see what it's doing or steer it when it isn't doing the right thing for a particular student in the moment.

## Why this problem matters

Class sizes make one-on-one instructor attention scarce, and unmonitored AI coding help is already a documented risk for shallow learning and overreliance. But swinging to the opposite extreme — locking the AI down to rigid, one-size-fits-all behavior — throws away the main advantage of having an AI assistant at all: the ability to adapt help to the individual student's needs, in real time, as the class actually unfolds. Getting this balance right matters for anyone deploying LLM tutoring or teaching-assistant tools at scale, not just in programming courses — it's a concrete instance of a much broader question in human-AI collaboration: who should decide how autonomous an AI helper is allowed to be, and how quickly can that decision change as circumstances change?

## What makes the system agentic

ClassAid's core component is a "TA Agent" that continuously monitors each student's ongoing interaction with the system (their code, their questions, and their prior activity), diagnoses the student's likely cognitive/metacognitive state using a Bloom's-taxonomy-based classification, weighs multiple possible responses, and selects and delivers one of several intervention types — all without a human writing that specific response. In its "automatic" mode the agent autonomously decides, turn by turn, whether to give a direct technical answer or a Socratic hint based on its read of the student's need. This is multi-step, tool-supported, environment-embedded behavior (reading code and interaction history, classifying, choosing among actions, intervening) evaluated as agent performance in its own right — not a single question-answering exchange — which is what makes it agentic AI rather than a plain chatbot.

## How humans and the AI agent collaborate

The paper's central design idea is a live, adjustable division of labor between an instructor and a fleet of TA Agents (one operating per student or small group), mediated by a real-time dashboard. The instructor can watch what every agent is doing across the whole class at once and change, on the fly, how much autonomy each agent has — from fully autonomous ("automatic feedback"), to constrained-but-active (fixed to "technical" or "heuristic" feedback only), to silenced entirely. This is a direct, running example of **adaptive delegation**: the human doesn't set the AI's autonomy level once and walk away; they renegotiate it continuously as the classroom situation changes.

## What role the human plays

The instructor (supported by teaching assistants, in the study's deployment) supervises the whole class through the orchestration dashboard, watches for alerts the system surfaces (the paper reports the system raising 15 such alerts during the deployment, covering agent-behavior, process, and code issues), and makes classroom-wide or per-student decisions about which feedback mode each TA Agent should use. In the reported classroom session, the instructional team made eight such classroom-wide mode adjustments over the course of the activity — for example, starting all students in restrictive "heuristic" (hints-only) mode to encourage independent thinking, then switching to "automatic" mode after ten minutes with no task completions, and later moving specifically the students who were still stuck into direct "technical" mode.

## What role the AI agent plays

Each TA Agent handles the moment-to-moment work of actually helping a given student: reading their code and question, estimating their cognitive level, and generating or selecting a response that matches the feedback mode the instructor currently has it set to. In "automatic" mode, the agent additionally takes on a delegated judgment call that would otherwise fall to the instructor or a human TA — deciding, per question, whether the student needs a hint or a direct answer.

## How control, initiative, and decisions are shared

Control is explicitly layered and dynamic rather than fixed at design time: the instructor holds standing authority to raise or lower each agent's autonomy at any moment, the agent exercises whatever autonomy it has been granted within that window, and the dashboard's alerts give the instructor the situational awareness needed to know when to intervene. Initiative can come from either side — the system proactively surfaces alerts that prompt the instructor to act, and the instructor can also act unprompted based on their own observation of class progress. This is a mixed-initiative, human-supervised multi-agent arrangement: many TA Agents running semi-autonomously in parallel, under one human's adjustable, real-time oversight.

## The paper's main idea

The authors argue that the right way to deploy AI teaching assistance at scale isn't to pick a single fixed level of AI autonomy in advance, but to build the *infrastructure for continuously renegotiating that autonomy* — instructor-facing controls plus system-generated alerts — so a human can keep the AI's behavior aligned with pedagogical goals as a real class actually plays out, moment to moment.

## How the approach works

ClassAid consists of (1) TA Agents, one instantiated per student, that monitor the student's coding activity and questions, classify the student's apparent cognitive/metacognitive level (drawing on Bloom's taxonomy) and current obstacle, and generate a feedback response in one of four modes set by the instructor: **technical** (direct coding solutions), **heuristic** (hint-based, Socratic guidance), **automatic** (the agent autonomously chooses between technical and heuristic per question), or **silent** (no AI support); and (2) an instructor-facing real-time dashboard that visualizes student–AI interaction across the whole class, surfaces alerts about agent behavior/process/code issues, and lets the instructor change any student's (or the whole class's) feedback mode instantly.

## Human study or evaluation design

The evaluation combined three parts: (1) a classroom deployment in which real students used the system to complete programming tasks while an instructor and teaching assistants used the orchestration dashboard live; (2) an expert-rated assessment of TA Agent output quality, in which two instructors with data-visualization teaching experience independently scored a sample of the agent's real classroom responses (roughly half of the 274 student questions collected, plus a separate ~106-question sample of "automatic"-mode decisions) on a three-point correctness scale, judging the accuracy of the agent's cognitive-level classification, the correctness of its feedback, the appropriateness of its automatic mode-selection, and its classification of question type (critical-thinking vs. answer-seeking); and (3) semi-structured interviews with eight external programming educators who were shown the system and asked for their professional assessment.

## Participants and study setting

The classroom deployment involved 54 students and one instructor (with teaching-assistant support) in a live class session using the ClassAid student interface, working through two sequential programming tasks over 50 minutes; performance did not count toward students' grades, which the authors note was meant to encourage natural engagement rather than test-taking behavior. The separate interview study recruited eight programming educators. Further demographic detail (student year/major, institution, instructor background) was not confirmed from the sources used.

## Experiments or benchmarks

This is a real classroom field deployment and an expert content-rating exercise rather than an evaluation on a public agent benchmark; there is no third-party leaderboard or standardized dataset involved. The "benchmark," such as it is, is the live classroom session itself plus the authors' own expert-coded sample of real TA Agent transcripts.

## Main results

During the live session, the system surfaced 15 alerts (a mix of agent-behavior, process, and code-related issues), and the instructional team responded with eight classroom-wide feedback-mode changes over the course of the activity — starting the whole class in heuristic-only mode, escalating to automatic mode after a stretch with no completions, and later moving specifically struggling students into technical mode. In post-session feedback, about 80% of students said ClassAid was better suited to classroom learning than a general-purpose chatbot, while acknowledging general chatbots were faster for quick answers; about 70% said they preferred the heuristic/proactive style of feedback (reasoning support and problem decomposition) over being simply handed an answer. The eight interviewed educators were broadly positive, specifically praising the system's controllability and flexibility and describing the real-time mode-adjustment capability as reinforcing rather than displacing the instructor's central role in the classroom. Exact numerical results from the expert accuracy-rating exercise (e.g., precise agreement or correctness percentages for the agent's cognitive-level and mode-selection judgments) were not confirmed from the sources used.

## Effects on human performance, trust, workload, safety, or decision quality

The reported evidence here is primarily perception- and interview-based rather than a controlled comparison against a no-AI or fixed-autonomy baseline. Educators reported (per the authors' thematic analysis) that dynamic orchestration helped them align AI support with pedagogical goals, manage overall class progress, and reduce the burden of manually providing individualized feedback to many students in a programming-intensive setting — this is the paper's claim, drawn from interview themes, rather than a measured workload metric like NASA-TLX. Students' self-reported preference for reasoning-oriented feedback over direct answers is the closest the paper comes to a learning-quality signal, but the study did not report a controlled measure of learning gains, and no baseline (e.g., no-AI or always-automatic classroom) condition was tested against it.

## What is genuinely new

**Authors' claim:** a live, instructor-adjustable autonomy dial applied *per TA Agent, per student, in real time*, rather than a fixed configuration chosen before class starts, combined with system-generated alerts that actively prompt instructor attention rather than requiring the instructor to constantly watch every agent. **Demonstrated:** the deployment shows this dial actually being used mid-class — heuristic → automatic → technical transitions driven by observed student progress — which is a concrete, if single-session, existence proof of adaptive human-AI task delegation happening live rather than only in concept. **Our interpretation:** this is a useful, transferable design pattern (a supervisory dashboard plus a graduated, instructor-controlled autonomy spectrum) for any setting where one human oversees many parallel semi-autonomous AI helpers, beyond programming education specifically.

## Limitations and open questions

The evaluation is a single classroom deployment with 54 students and one instructor, plus a separate 8-educator interview panel — a useful but modest-scale, single-session field study without a controlled baseline comparison (e.g., against fixed-mode or no-AI classrooms), so causal claims about learning or workload benefits should be read cautiously. The expert content-rating relied on two raters drawn specifically for that task, and the numerical accuracy/agreement results were not available from the sources used for this summary. It's also unclear from available sources how well a single instructor can keep adjusting settings for many concurrent TA Agents as class size grows well beyond the 54-student pilot, or how the approach generalizes outside programming instruction.

## Practical implications

For builders of AI teaching assistants, coding copilots, or any assistant deployed to a group under one supervisor's watch, the paper offers a concrete pattern: expose a small number of discrete autonomy levels (not just "on/off"), let the supervising human change them per-recipient at any time, and add system-driven alerts so the human doesn't have to poll every agent constantly to know when to step in. This design pattern — a supervisory dashboard with a graduated, live-adjustable autonomy dial — is directly reusable in other settings with one human overseeing many parallel semi-autonomous LLM agents (e.g., customer support, code review, or moderation queues), not just classrooms.

## Why you should care

This paper is a rare thing: a real classroom deployment (not a lab study with paid crowdworkers, and not a benchmark) of exactly the kind of human-AI arrangement — a supervisor continuously renegotiating how much autonomy to grant a fleet of semi-autonomous AI helpers — that is becoming central to how agentic AI actually gets used in workplaces and classrooms alike. If you're designing or deploying LLM agents that operate under human supervision at any scale, ClassAid is a concrete illustration of what "adjustable autonomy" can look like as software, and what actual users (students and educators) said about it.
