# When Developers Watch the Machine: How People Actually Oversee AI Coding Agents

**Paper title:** Human oversight of agentic systems in practice: Examining the oversight work, challenges, and heuristics of developers using software agents
**Authors:** Shipi Dhanorkar, Samir Passi (co-first authors, contributed equally), Mihaela Vorvoreanu — Microsoft
**Publication date:** 2026-06-03 (arXiv v1)
**Venue:** arXiv preprint. The paper repeatedly frames its contribution as feeding into ACM FAccT (Fairness, Accountability, and Transparency) research on agent oversight and cites many prior FAccT papers, but the manuscript itself does not state a confirmed acceptance/venue stamp — treat any specific "FAccT '26" attribution as unconfirmed.
**Paper link:** https://arxiv.org/abs/2606.05391
**Code link:** Not available (qualitative interview study; no code or dataset released)
**Project page:** Not available
**Date added:** 2026-07-17

*This post was revised after the author obtained and read the full PDF of the paper directly (rather than relying on secondhand search summaries). Facts below are drawn from the actual manuscript, including its appendices.*

---

## The problem the paper addresses

AI coding agents — Claude Code, Cursor, GitHub Copilot's agent mode, Cline, and similar tools — can now autonomously plan a task, edit multiple files, run commands, and iterate on their own work with only a starting instruction from a person. Everyone agrees a human should stay "in the loop." But the authors point out that almost everything written about that oversight is aspirational: laws like the EU AI Act mandate that humans "retain meaningful control," and academic frameworks describe what oversight *should* look like — yet almost no research had gone and actually watched what developers do, moment to moment, when they try to oversee an agent working on real code. The paper's two research questions are refreshingly direct: *How do developers oversee software agents in practice?* and *What oversight challenges do they face, and how do they cope?*

## Why this problem matters

The authors open with a blunt catalogue of what can go wrong: agents that misinterpret requests, silently corrupt production databases (they cite the widely reported Replit incident), get hijacked via prompt injection, or leak sensitive data. Automated safety nets like red-teaming and "agent-as-a-judge" evaluators exist, but the authors argue these remain limited by the scenarios and incentives they're built to catch. That leaves human oversight as a central line of defense — which makes it worth knowing whether that defense, as actually practiced, is anywhere close to what policy documents assume it is.

## What makes the system agentic

The paper studies coding agents as its subjects, not as something the authors built. It explicitly defines a "software agent" as one that "autonomously plans and acts to accomplish user goals by using tools and interacting with the environment," and deliberately excludes plain autocomplete tools from that definition. The 17 participants used real agentic coding tools in production and prototype work — Claude Code, Cursor, GitHub Copilot's agent mode, Cline, Gemini, OpenAI Codex, Amazon CodeWhisperer/Kiro, Aider, and others — across languages including Python, Java, Go, and C#.

## How humans and the AI agent collaborate

The paper's central move is to show that "oversight" is not one behavior but a bundle of activities spread across the entire lifecycle of a task — before an agent starts, while it plans, while it executes, and after it finishes.

## What role the human plays

Developers described actively:
- **Configuring agents before delegating anything** — setting deny lists, custom instructions, and scope boundaries.
- **Co-planning with the agent** — drafting and negotiating a plan together before execution starts, sometimes seeding partial code ("I bite the bullet... I write the crux of it," P11).
- **(Rarely) monitoring the agent in real time** — most participants said they almost never watched an agent's live reasoning trace.
- **Reviewing the finished output** — the most discussed activity by far, ranging from reading every line ("I read every single line. I approve every single line," P17) to relying on passing tests as a stand-in for correctness.

## What role the AI agent plays

In this study the agent is the object of observation: a tool that takes a delegated (often deliberately small) task, works largely on its own — sometimes for a "few dozen seconds to a minute," occasionally 15–25 minutes for prototype work — and reports back a plan, a set of edits, and a summary of what it did.

## How control, initiative, and decisions are shared

The paper's headline finding is that developers front-load a lot of their oversight *before* the agent ever starts working, rather than only reviewing at the end. It groups this into four forms:

1. **A priori control** — preventative — configuring agent autonomy, blocking specific libraries, and supplying project-wide context before delegating a task.
2. **Co-planning work** — proactive — jointly drafting a plan, decomposing the task into small testable chunks, and iterating on the plan with the agent before it executes.
3. **Real-time monitoring** — reactive — watching action logs or reasoning traces and intervening mid-task. The paper found participants did this rarely and mostly "perfunctorily" — glancing rather than vigilantly watching.
4. **Post hoc review** — evaluative — checking the finished code afterward using diff tools, test suites, or LLM-as-judge techniques.

Initiative shifts hands throughout: developers set the terms up front, then the agent takes the lead during execution (largely unsupervised, per the findings on real-time monitoring), and the developer resumes control during review.

## The paper's main idea

Existing discourse treats oversight as essentially "catch mistakes in the output." This paper argues oversight is instead a form of **bounded rationality** in action: faced with agents that are "too fast, too complex, and too much" to fully verify, developers have built a set of practical heuristics that trade thoroughness for efficiency — described in the paper as pursuing "efficient, not perfect" oversight.

## How the approach works

This is a qualitative, interview-based study, not a system-building or benchmarking exercise. Semi-structured, one-on-one interviews (~60 minutes on average) were conducted by the first author over video call, recorded, and transcribed. Analysis proceeded in three rounds of qualitative coding: (1) open coding of developer actions and challenges directly from participant quotes (e.g., "set deny lists," "co-plan with agents"); (2) axial coding into 13 recurring themes; (3) selective coding by the first two authors into the final two conceptual categories — the four forms of oversight work, and the heuristics used to cope with their challenges.

## Human study or evaluation design

The "study" is the qualitative interview process itself — there is no separate benchmark or synthetic user standing in for real people. Recruitment used criterion sampling (screening for developers who used agents at least weekly for professional work) combined with snowball sampling. One participant was excluded after a secondary screen revealed insufficient conceptual understanding of agents. The research was approved by the authors' organization's IRB, and participants received a $40 gift card. Interviews ran between July and August 2025.

## Participants and study setting

**17 experienced developers**, according to the paper's own appendix:
- 16 of 17 used agents several times a week for professional work (12 of those daily); 9 described themselves as "experienced," 4 "somewhat experienced," 4 "very experienced."
- 13 of 17 had 7+ years of programming experience.
- Roles: mostly software engineers/developers, plus a few engineering managers, one technical program manager, and one data scientist/ML engineer.
- Mostly based in the US, with one participant each in India and Brazil; 15 of 17 identified as male, 2 as female.
- **12 of the 17 participants worked at the same large tech company as the authors** (which the paper says happened unintentionally, due to recruitment difficulty — developers at other firms were hesitant to discuss proprietary agent workflows under NDA). The remaining 5 participants, from other organizations, reported similar experiences.
- The authors describe this explicitly as an "intensity sample" of power users at well-resourced organizations — early adopters likely to reveal emergent practices — not a representative cross-section of all developers.

## Experiments or benchmarks

There is none, and the paper does not claim one. Its evidentiary base is exclusively the coded interview transcripts. Readers looking for accuracy numbers, task-success rates, or a leaderboard will not find them; the contribution is a qualitative taxonomy and a catalogue of coping heuristics, grounded in direct quotes.

## Main results

**As reported by the authors:**

- Developers perform (at least) four distinct forms of oversight work — a priori control, co-planning, real-time monitoring, and post hoc review — not just the single after-the-fact "review the output" behavior emphasized in prior conceptual work.
- Real-time monitoring was the *least*-practiced form: most participants said they rarely or never proactively examined an agent's live reasoning ("I don't go through it line by line," P16), partly because tasks were deliberately decomposed into small, quick sub-tasks that made close monitoring feel unnecessary.
- Post hoc review was the *most*-discussed form, and its rigor varied by context — read every line for production/legacy code, but "let the agent run wild" (P01) for prototypes.
- The paper documents **four heuristics** developers use specifically to make post hoc review tractable:
  1. Treating the agent's *plan* as a faithful stand-in for its actual work, so reviewing the plan can substitute for reviewing every step.
  2. Treating *passing tests* as a guarantee of code correctness — one participant (P08) suggested that with sufficiently good test cases, the source code could be treated as "a complete black box" that developers never need to open.
  3. *Eyeballing* — quick spot-checks of method signatures, change summaries, or agent-generated visual diagrams (one participant, P07, asked agents to generate Mermaid data-flow diagrams specifically to speed up review of large pull requests).
  4. *Trusting the agent by default* in unfamiliar domains or languages the developer doesn't know well — including an informal "social proof" check where running the same prompt on two different agents and seeing agreement increased confidence.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's evidence here is descriptive, not measured: it documents what developers *say* they do and why, not independently verified error-catch rates. The authors' own claim is that this heuristic-driven style of oversight is a rational adaptation to genuine constraints (bounded rationality / "satisficing" rather than "optimizing," in their words) — but they also flag it as a real gap between the "meaningful, continuous human control" that policy frameworks like the EU AI Act assume and what is realistically happening on the ground.

**Interpretation (ours, not the paper's):** because the data is self-reported interview material, it tells us what practitioners believe they are doing and why — not how often heuristics like "tests passed, so it's fine" actually fail to catch real defects. That distinction matters for how much weight to put on the findings as a safety claim versus a description of current practice.

## What is genuinely new

Before this paper, discussion of "human oversight of AI agents" was largely normative — describing what oversight *should* involve. This paper's contribution is providing an early empirical anchor: a concrete four-part vocabulary for oversight work (a priori control, co-planning, real-time monitoring, post hoc review), evidence that oversight starts well before execution rather than only afterward, and a documented set of coping heuristics that developers have started using largely on their own.

## Limitations and open questions

The authors state these limitations directly:
- **Resource-privileged sample:** most participants worked at well-resourced tech firms with generous token limits and rich tool access, so monetary/computational cost barely factored into their oversight decisions — this may not generalize to resource-constrained settings.
- **Single-company concentration:** 12 of 17 participants worked at the same company as the authors, which the authors acknowledge "likely introduced some bias," even though the 5 participants from other firms reported similar experiences.
- **Small, well-bounded tasks:** participants mostly delegated small tasks to agents, which made real-time monitoring feel optional and post hoc review easier. The authors explicitly call for future work on oversight during longer-running, more complex agent tasks.
- **Self-report, not observation:** the findings describe what developers say they do, not directly observed behavior — and there is no measurement linking the heuristics to actual defect rates.

**Open question the paper raises:** if "efficient, not perfect" oversight is the realistic norm even among expert, motivated developers, what does that mean for regulations that assume thorough, continuous human review as a safety backstop?

## Practical implications

The authors translate each of the four oversight challenges into a concrete design suggestion for agent-tool builders: better configuration guides and visible custom-instruction affordances (for a priori control); context-aware prompting help and sub-task recommendations with resource-cost previews (for co-planning); reasoning panels and inline controls to fix mistakes (for real-time monitoring); and diff tools augmented with intent, reasoning, and proposed tests (for post hoc review). They also argue that the traditional "craftsman" developer role is shifting toward a "developer-manager" role, where architectural judgment and critique matter more than hands-on syntax, and where organizations face a growing tension between efficiency-driven heuristics and the EU AI Act's legal mandate for human oversight (specifically citing Article 14(4)(a) on the ability to detect anomalies and dysfunctions).

## Why you should care

This paper gives language to something many people who use coding agents have probably felt without naming: overseeing an AI agent is not one job, but several different jobs happening at different times — setting boundaries before it starts, negotiating a plan with it, occasionally glancing at what it's doing, and reviewing what it produced. And it is an honest, empirically grounded reminder — based on real developers' own accounts, not speculation — that this oversight quietly becomes a set of practical compromises under real time pressure, even among experienced engineers at well-resourced companies. That is exactly the kind of finding that should shape how the next generation of agent tools presents its work to the humans still nominally responsible for it.

---

*Claims attributed to "the authors" or "the paper" reflect what is stated in arXiv:2606.05391 (including its appendices); passages marked as interpretation are the summary writer's own reading and are not asserted by the paper itself.*
