# HiLSVA: When Should a Scientific Visualization Agent Ask You First?

**Authors:** Kuangshi Ai, Patrick Phuoc Do, Chaoli Wang (Department of Computer Science and Engineering, University of Notre Dame)
**Publication date:** 2026-06-25 (v1); revised 2026-07-16 (v2) — arXiv id 2606.26614, cs.HC
**Venue:** arXiv preprint (formal venue/acceptance not confirmed in available sources)
**Paper link:** https://arxiv.org/abs/2606.26614
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-07-24

> **A note on sourcing:** the arXiv host was not directly reachable from this research session's network (outbound access to arxiv.org is blocked by network policy), so this summary is built from cross-checked search-engine excerpts of the paper's abstract, methods, and results rather than a direct read of the full PDF. Facts below that were corroborated across multiple independent search queries (authors, affiliation, dates, study design, participant breakdown, and the specific quantitative results reported) are presented as such; anything that could not be verified is marked "not available."

---

## The problem the paper addresses

Scientists who work with large, complex datasets — hurricane simulations, combustion models, medical scans — often rely on scientific visualization (SciVis) software to turn raw numbers into images they can actually reason about. Recent "agentic" tools promise to automate a lot of that work: describe what you want in plain language, and an AI plans and executes the visualization pipeline for you. But full automation creates a new problem — if the agent just does everything and hands you a picture, you lose the ability to catch its mistakes, understand why it made the choices it did, or steer it mid-task when something looks off. HiLSVA asks: can a visualization agent give you the benefits of automation while keeping you meaningfully in control of the process, not just the request?

## Why this problem matters

Scientific visualization isn't like asking a chatbot to summarize an email — a wrong parameter, a misread threshold, or an unnoticed artifact in the render can lead a scientist to a wrong conclusion about their data. That makes blind trust in an autonomous agent risky. At the same time, requiring a person to manually configure every rendering step defeats the purpose of using an AI assistant at all. The paper's stated goal is a system where "people derive meaningful insights... rather than being sidelined by automation" — a design tension that shows up in any domain where AI is meant to assist expert judgment rather than replace it.

## What makes the system agentic

HiLSVA is built as a **plan-first, multi-agent architecture**: rather than reacting to instructions one at a time, it constructs an explicit, stepwise plan for how to accomplish a visualization task, then executes that plan using visualization software tools inside a sandboxed environment for safety and reproducibility. It tracks its own execution history (stepwise provenance), can retrieve prior knowledge and adapt from user feedback at test time (what the authors call "learn-at-test-time," or LTT), and reflects on its own uncertainty to decide when to proceed versus ask for input. This combination — autonomous multi-step planning, tool use, environment interaction, and being evaluated on task completion rather than just conversational quality — is what makes HiLSVA an agentic system rather than a visualization chatbot.

## How humans and the AI agent collaborate

HiLSVA is explicitly designed around **mixed-initiative interaction**: both the human and the agent can take the lead at different points. The agent proposes and can execute a plan, but the human can review and approve steps before they run, jump in with natural language or direct manipulation of the visualization tools mid-task, and adjust how much autonomy the agent has. The paper frames this as "fluid hand-off" between human and agent control, rather than a fixed division of labor.

## What role the human plays

The human is a supervisor and active collaborator, not just an end recipient of a finished image. Depending on the autonomy setting, a person can: review and approve the agent's proposed plan before execution, intervene mid-workflow through natural language or by directly manipulating the visualization software, revisit earlier steps using the system's provenance record, and give feedback that the agent incorporates into how it behaves later in the session.

## What role the AI agent plays

The agent plans a sequence of visualization actions, executes them through tool calls to visualization software, tracks what it did at each step, and — in its more autonomous modes — proceeds without waiting for approval. In the system's richest mode, it also reflects on its own uncertainty and can proactively solicit feedback from the user rather than silently guessing, and it adapts within a session based on accumulated user feedback (the LTT mechanism).

## How control, initiative, and decisions are shared

The paper directly studies this by comparing **three autonomy configurations** with increasing degrees of shared initiative:

1. **Full-autonomous mode** — the agent executes with minimal user intervention.
2. **Half-autonomous mode (no LTT)** — the user can step in and provide input, but the agent doesn't adapt from that feedback over time.
3. **Mixed-initiative mode (with LTT)** — the agent can retrieve prior knowledge, reflect on its own uncertainty, and proactively ask the user for feedback, which it then incorporates going forward.

This gives the paper a controlled way to ask not just "does human involvement help," but "how much initiative should the human vs. the agent have, and does letting the agent learn from feedback change that trade-off."

## The paper's main idea

**Claim by the authors:** a human-in-the-loop agentic SciVis system that supports mixed-initiative interaction — explicit plans reviewed by the user, stepwise provenance, fluid control hand-off, and learning from feedback at test time — can preserve human oversight and understanding without giving up the productivity benefits of automation, and this holds across users with different levels of expertise (SciVis experts, domain scientists, and novices).

## How the approach works

HiLSVA combines a plan-first multi-agent design (the agent first builds an explicit, inspectable plan rather than acting step-by-step reactively) with a "human-in-the-loop user proxy" concept during execution: the user can seamlessly intervene through natural language or by directly manipulating the visualization tools, and control can pass fluidly back and forth. Every execution step, software state, and visualization output is logged for provenance, supporting undo, comparing alternative trajectories, and reusing validated workflows. The LTT mechanism lets the system retrieve and apply knowledge accumulated from earlier user feedback within a session.

## Human study or evaluation design

**Demonstrated in the paper:** the authors ran a controlled, within-subject user study in which the same twelve participants used HiLSVA across the three autonomy conditions (full-autonomous, half-autonomous without LTT, and mixed-initiative with LTT), completing tasks under each mode plus a final free-choice task where they picked their preferred mode. This design lets the paper compare autonomy levels for the same person rather than across different people, controlling for individual variation in expertise and preference.

## Participants and study setting

**Demonstrated in the paper:** twelve participants were recruited across three expertise bands — three SciVis experts, four domain scientists familiar with scientific datasets but with limited visualization-tool experience, and five novices with neither domain nor visualization expertise. All twelve completed the study. This is a real, hands-on lab study — not a simulated-user or synthetic-persona evaluation — though the sample is small, as is typical for controlled HCI studies of this kind.

## Experiments or benchmarks

There is no public, named benchmark here; participants worked through five case studies of varying complexity: two basic-action tasks (a "foot" dataset and a hurricane dataset), two visualization-workflow tasks (tornado and combustion datasets), and one scientific-analysis task (a half-cylinder dataset), plus domain-specific interpretation questions to check understanding of the resulting visualizations.

## Main results

**Demonstrated in the paper (per available descriptions):**
- **Task completion time** rose with the degree of mixed initiative: full-autonomous mode was fastest (9.83 ± 3.27 min), half-autonomous mode was in between (11.67 ± 4.44 min), and mixed-initiative mode was slowest (13.50 ± 4.46 min). A Friedman test found this difference was not statistically significant overall (χ²(2) = 5.09, p = 0.078), though the authors report a large effect size specifically between the full-autonomous and mixed-initiative conditions.
- **Comprehension:** participants answered domain-specific interpretation questions about the visualizations correctly on average 11.75 out of 12 — near ceiling — suggesting the system's outputs were broadly understandable across expertise levels regardless of mode.
- **User control and transparency ratings** (5-point scales) were high specifically in the mixed-initiative/provenance-supporting conditions: ability to review and approve actions rated 4.75 ± 0.60; ability to adjust autonomy levels 4.83 ± 0.37; clarity of system feedback 4.92 ± 0.28; usefulness of stepwise provenance for understanding system behavior 4.92 ± 0.28; ability to revisit previous steps 5.00 ± 0.00 (a perfect score across all twelve participants).
- **Learn-at-test-time** was rated as noticeably beneficial: participants rated the benefit of the agent's accumulated within-session knowledge at 4.50 ± 0.65.
- Overall, the authors report that mixed-initiative interaction improved task completion, user control, and workflow transparency across expertise levels, at the cost of some execution efficiency — a direct trade-off between speed and oversight.

## Effects on human performance, trust, workload, safety, or decision quality

The study's central human-related finding is this efficiency-versus-oversight trade-off: giving the agent more autonomy made tasks faster, but participants rated their sense of control, their understanding of what the system was doing (transparency), and their ability to review, approve, and revisit the agent's actions much more highly under the modes that preserved human involvement and provenance. Comprehension of the resulting visualizations stayed high (11.75/12) regardless of mode, suggesting the trade-off was mainly about process (control, transparency, time) rather than final understanding of the output. **This is the authors' framing of their own results**, based on the quantitative ratings and timing data described above.

## What is genuinely new

- A concrete, working system that operationalizes mixed-initiative SciVis as **three directly comparable autonomy configurations** on the same tasks with the same participants, rather than a single fixed design or a purely conceptual proposal.
- The **learn-at-test-time (LTT)** mechanism, letting the agent adapt its behavior within a session based on the specific feedback a specific user gives it — moving beyond a static, one-size-fits-all agent toward one whose behavior is shaped by the person it's currently working with.
- Combining stepwise provenance (undo, trajectory comparison, workflow reuse) with fluid human-agent hand-off, giving a fairly complete account of what "human oversight" can look like in a visualization pipeline, not just at the start (approving a plan) or the end (reviewing a picture), but throughout execution.

## Limitations and open questions

- **Small sample (n=12)**, typical of controlled HCI lab studies but limiting statistical power — the headline timing difference across autonomy modes did not reach conventional significance (p = 0.078).
- **Domain scope:** the case studies span a handful of SciVis datasets (foot, hurricane, tornado, combustion, half-cylinder); it's not established how well the findings generalize to other scientific domains or much larger/longer real-world analysis workflows.
- **Self-reported ratings:** the control/transparency/LTT scores are participants' own 5-point ratings, not independent behavioral or physiological measures, and some scores (e.g., a perfect 5.00 ± 0.00 on revisiting previous steps) may partly reflect a small, engaged sample rather than a broader population.
- We were unable to independently verify additional details (e.g., full statistical reporting, exact task instructions, or supplementary materials) since the full PDF could not be fetched in this session — readers who need precise details should consult the paper directly.

## Practical implications

If the results hold up under closer scrutiny, they offer a concrete design lesson for agentic tools in expert domains generally, not just SciVis: users seem willing to trade some execution speed for a system that keeps them able to review, approve, and revisit what an autonomous agent did — and letting the agent visibly adapt to a user's feedback within a session appears to be valued on its own, independent of raw speed. For builders of agentic tools in high-stakes analytical domains (science, engineering, medicine), this is evidence that investing in provenance, reviewability, and adjustable autonomy — not just faster automation — is something real users notice and rate highly.

## Why you should care

This paper is a useful data point precisely because it isolates the "how much should the agent do on its own" question and measures it directly, with the same people, across three concrete configurations. It gives a real (if small-scale) empirical answer to a question that comes up across every domain in this research log: full autonomy is faster, but people consistently rate systems that preserve their oversight, transparency, and ability to step in as better on exactly the dimensions — control, understanding, trust in the process — that matter when the AI's mistakes could actually cost something.
