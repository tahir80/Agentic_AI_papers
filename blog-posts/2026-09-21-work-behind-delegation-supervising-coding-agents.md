# Delegating Code to an AI Agent Doesn't Mean the Work Disappears — It Changes Shape

**Paper title:** The Work Behind Delegation: A Framework for Supervising AI Coding Agents
**Authors:** Yeon Su Park, Nadia Arvi, Hae Ri Lee, Sehoon Lim, Qianou Ma, Juho Kim (KAIST School of Computing affiliation reported in secondary sources; not independently confirmed from the primary PDF)
**Publication date:** 2026-09-21 (arXiv v1)
**Venue:** arXiv preprint (cs.HC); a secondary source (a co-author's personal publications page) lists it as accepted to EMNLP Findings 2026 — not independently confirmed from the paper itself
**Paper link:** https://arxiv.org/abs/2609.24234
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-11-28

> **A note on sourcing:** this session's network access to arxiv.org and its usual mirrors (export.arxiv.org, alphaxiv.org, Semantic Scholar, Hugging Face) was blocked by the environment's network policy, so the primary PDF could not be opened directly. This summary is built from the paper's abstract, introduction, and HTML excerpts as they surfaced across several targeted web searches, cross-checked against each other for consistency. The paper itself is a freely available, open-access arXiv preprint. Any detail not independently confirmed against the full PDF is flagged as such below. Please check the arXiv preprint directly before citing specific details.

---

## The problem the paper addresses

When a developer hands a coding task to an AI agent — "add this feature," "fix this bug," "refactor this module" — the common assumption is that the human's job shrinks to writing a prompt and reading a diff. This paper argues that assumption hides a lot of real work. Developers still have to plan what to delegate and how, decide when to step in while the agent runs, review what it produced, correct it when it goes wrong, sometimes fix things by hand, and figure out how to avoid repeating the same corrections next time. The paper's core claim is that there wasn't, before this work, a clear framework for *where* all that supervisory effort actually goes.

## Why this problem matters

AI coding agents are being adopted fast, and the pitch is usually "delegate and save time." If the real supervisory burden is invisible or badly understood, two things can go wrong: tool builders design for the wrong bottleneck (e.g., polishing the final diff review, when the costly work is actually upfront planning or mid-task correction), and developers underestimate how much ongoing attention delegation still requires. Understanding the full shape of "supervision work" matters for anyone designing agent tooling, anyone managing engineers who use these tools, and anyone trying to decide how much to trust an agent with.

## What makes the system agentic

The paper doesn't introduce a new coding agent — it studies how developers supervise the AI coding agents already in wide use (the kinds of tools built around products like Cursor, Claude Code, or Copilot-style assistants). These agents plan multi-step changes, write and edit code, and often execute commands, across a session, with only partial human attention — which is exactly the "goal-directed, multi-step, tool-using" behavior that makes them agentic rather than single-shot text generators. The paper's contribution is a framework for the *human* side of working with that kind of system.

## How humans and the AI agent collaborate

The authors reframe coding-agent supervision using Thomas Sheridan's classic human supervisory control model — originally built for people overseeing automated machinery — and adapt it to coding agents. Collaboration here isn't a single hand-off; it is a recurring cycle. According to the available excerpts, the authors reconfigure Sheridan's five stages (Plan, Teach, Monitor, Intervene, Learn) into seven coding-agent-specific stages: **Plan, Monitor, Wait, Review, Teach, Manual Fix, and Update Assets**, connected by loops that developers move between as a task unfolds.

## What role the human plays

The developer plans what to delegate and how to scope it, monitors the agent while it works, waits during stretches where little oversight is possible or needed, reviews the agent's output, teaches the agent (through corrections, instructions, or examples) when it's off track, sometimes fixes problems manually rather than re-delegating, and updates reusable assets — rules, templates, prompts — so similar guidance doesn't have to be repeated next time.

## What role the AI agent plays

The agent is delegated a coding task and executes it with a meaningful degree of autonomy — planning and carrying out multi-step changes to a codebase without the developer dictating each step. It is also the thing being taught: it's expected to incorporate corrections and, ideally, retain updated rules or assets so supervisory effort invested once pays off on future tasks.

## How control, initiative, and decisions are shared

Control is not fixed — it shifts across the seven stages. At points like Wait and Monitor, the agent effectively holds the initiative while the human observes (or deliberately doesn't). At Teach, Review, and Manual Fix, the human reclaims control to correct or redo work. At Plan and Update Assets, the human is shaping the conditions under which the agent will act autonomously later. The paper's framing is that supervision is this whole rotating cycle, not a single checkpoint at the end.

## The paper's main idea

Supervising a delegated coding agent is itself a distinct, multi-stage body of work, and understanding it requires a framework broader than "the user reviews the output." The authors propose that framework by adapting an established human-supervisory-control model from automation research into one specifically shaped around how developers actually work with coding agents.

## How the approach works

The authors built the framework from observations of real developers' practices and workflow diagrams drawn from **19 experienced developers** (secondary sources indicate roughly 20 were initially recruited, with one excluded for being unable to use their regular agent setup during the study). Using that data, they adapted Sheridan's five-stage model into the seven coding-agent-specific stages and loops described above. They then checked the framework's fit against a second, independent source of evidence: public developer discussions about coding agents on Reddit, treating that corpus as a way to see whether the stages and loops showed up in how developers describe their own experiences "in the wild."

## Human study or evaluation design

This is a qualitative, formative HCI study, not a controlled experiment. The primary data collection involved observing developers' existing supervisory practices and having them produce workflow diagrams of how they actually work with their coding agents. The secondary validation step — analysis of Reddit discussions — is text analysis of real practitioners' public accounts, not a second participant study with recruited subjects.

## Participants and study setting

**19 experienced developers** who already use AI coding agents in their regular work (with their own existing agent setups, rather than a lab-assigned tool), studied through observation and workflow-diagramming sessions. Further demographic detail (recruitment platform, seniority, industry, geography) is not available from the sources used for this summary. The secondary Reddit corpus draws on real, self-selected public developer commentary rather than a recruited sample.

## Experiments or benchmarks

There is no public benchmark or standardized dataset here, and none is confirmed as released. The "evaluation" is the framework-fit check against the Reddit discussion corpus rather than a quantitative experiment with conditions and metrics.

## Main results

According to the authors, supervisory demands are spread across all seven stages rather than concentrated at the review step that gets the most attention in casual discussion of "AI code review." They report that developers cope with this spread-out burden in three main ways: concentrating effort heavily into the Plan stage upfront, delegating some supervisory work to other agents (having one agent help oversee or check another), and converting recurring corrections into reusable assets — rules, templates, or standing instructions — so the same guidance doesn't need to be re-taught each time.

## Effects on human performance, trust, workload, safety, or decision quality

This paper does not run a controlled before/after comparison and, from the sources used here, does not report a standardized trust or workload instrument (e.g., no NASA-TLX-style score was found). Its "human-related outcome" is qualitative: a description of where developers' supervisory effort goes and which coping strategies they adopt. The authors' design implication — stated as their own recommendation, not as a measured effect — is that agent builders should prioritize preserving developer intent throughout execution, since (in their account) supervisory demand spikes specifically when an agent drifts from the goals, constraints, or scope the developer originally intended.

## What is genuinely new

*Authors' claim:* a framework that reconfigures a well-established human-supervisory-control model (built originally for overseeing automated machinery) into one tailored to AI coding agents, naming seven distinct supervisory stages rather than treating "supervision" as a single undifferentiated activity.
*Demonstrated:* the framework was built from real developers' described practices and checked, after the fact, against independent public discussion data from a different population of developers.
*My interpretation:* the main value here is conceptual and diagnostic — it gives practitioners and tool designers a shared vocabulary for which specific kind of supervisory work is becoming a bottleneck (e.g., "this is a Teach problem" vs. "this is a Plan problem"), which is a different contribution than proving any particular tool or technique improves outcomes.

## Limitations and open questions

The study sample is small (19 developers) and self-selected toward people already experienced with coding agents, which limits how far the framework generalizes to novices or to less common agent setups. There's no controlled baseline or comparison condition — this is formative, descriptive research. The secondary validation relies on public Reddit discourse, which is self-selected and may not represent typical usage. The reported peer-review venue (EMNLP Findings 2026) comes from a secondary source rather than the paper itself, so it should be treated as unconfirmed. No quantitative trust, workload, or productivity metrics are reported in the material available for this summary.

## Practical implications

For developers: the framework offers a way to notice which stage is actually consuming your time with a given agent setup — if you're constantly in "Teach" or "Manual Fix," that's a signal to invest more in "Plan" or "Update Assets" instead. For teams building or buying coding-agent tools: the paper suggests that review-step polish alone won't address the real supervisory burden, and that supporting reusable, persistent guidance (so correction effort isn't repeated) may matter as much as improving the agent's raw output quality.

## Why you should care

If your research interest is human–AI collaboration, this paper is useful less as a study of *outcomes* and more as a vocabulary for *where the human labor in "delegation" actually lives*. It pushes back on the narrative that agentic coding tools simply remove work from the human side, and instead maps out the specific, recurring forms that human oversight takes when the thing being overseen is a semi-autonomous coding agent rather than a single AI-generated answer.
