# Can You Trust an AI Data Analyst? Giving Humans a Window Into What the Agent Actually Did

**Paper title:** BobFlow: Towards Human–Agent Collaborative Data Science Using Dataflows
**Authors:** Jiadong Bai, Yicong Huang, Chen Li
**Publication date:** 2026-11-04 (arXiv v1)
**Venue:** arXiv preprint (cs.DB, cross-listed cs.AI, cs.HC); a related demonstration paper, "Demonstration of BobFlow: Human-Agent Collaboration Using Dataflows on Data Science Tasks," appeared in PVLDB, Vol. 19, No. 12, pp. 4718–4721 (2026)
**Paper link:** https://arxiv.org/abs/2611.05761
**Code link:** https://github.com/Texera/bobflow (reported in the related VLDB demo paper; not independently confirmed from this session)
**Project page:** Not available
**Date added:** 2026-11-17

> **A note on sourcing:** this session's network access to arxiv.org and its usual mirrors (export.arxiv.org, alphaxiv.org, emergentmind.com, Semantic Scholar, Hugging Face, vldb.org) was blocked by the environment's network policy, so the full PDF could not be opened directly. This summary is built from the paper's abstract, HTML excerpts, and the related VLDB demo paper as they surfaced across several web searches, cross-checked against each other for consistency. The paper itself is a freely available, open-access arXiv preprint. Numbers and quotes below are reported as they appeared in those excerpts; anything not independently confirmed against the primary PDF is marked accordingly (e.g., participant demographics, recruitment process, and exact task wording were not available from the sources used). Please check the arXiv preprint directly before citing specific figures.

---

## The problem the paper addresses

When an AI agent writes a Python or SQL script to answer a data question — "which customers churned last quarter and why?" — the analyst on the other end usually just gets the final answer, plus maybe a wall of code. If the analyst wants to check whether the agent actually did the right thing, they have to read and mentally re-execute that script line by line. BobFlow's authors argue this is a bad medium for collaboration: scripts are opaque, hard to spot-check, and hard to partially correct. Their question is simple — what if the agent's work was represented not as code, but as something a human can visually follow, inspect, and edit at each step?

## Why this problem matters

As LLM agents increasingly take on real data-analysis work — cleaning data, running statistics, building dashboards — the stakes of getting it subtly wrong go up. A hallucinated filter, a mis-joined table, or a wrong aggregation can silently produce a confident but incorrect answer. If analysts can't easily verify *how* an agent reached its conclusion, they're left either blindly trusting the output or re-doing the analysis themselves, which defeats the purpose of delegating the work. The authors frame this as a core obstacle to real-world adoption of data-science agents: collaboration requires a shared artifact that both the human and the agent can reason about together, not just a human watching an agent work and getting a final answer.

## What makes the system agentic

BobFlow's core is a "Dataflow ReAct" agent: it follows the think–act–observe loop (the ReAct pattern) to pursue a data-science goal across multiple steps — choosing operators (e.g., filter, join, aggregate, visualize), executing them, observing the results, and deciding what to do next, rather than producing one static script or answer in a single pass. It is built on top of Apache Texera, an existing collaborative, interactive workflow engine for data analytics, so the agent's actions directly manipulate and extend a live, executable workflow graph rather than just emitting text.

## How humans and the AI agent collaborate

The central design idea is to make the **dataflow graph itself** — not code — the shared medium of collaboration. As the agent works, it builds out a visual pipeline of operators that a human analyst can see, step through, and inspect at any point, rather than only reviewing a finished script or a final answer. The claim is that a dataflow is closer to how analysts already think about a pipeline of operations, making it easier to follow and challenge than reading generated code line by line.

## What role the human plays

The human is a data **analyst** who inspects, verifies, and steers the agent-generated dataflow. The authors' user study specifically examines how well participants could understand what the agent had done, verify whether it was correct, and guide the agent (through further requests or corrections) during task completion and debugging — i.e., the human's job is oversight and correction of the agent's in-progress work, not just reading a final result.

## What role the AI agent plays

The agent is the one doing the analytical labor: proposing, configuring, and executing dataflow operators to work toward a data-science goal (e.g., answering an analytical question over a dataset), using the ReAct reasoning loop to decide its next action based on what it has observed so far.

## How control, initiative, and decisions are shared

This is best described as **human oversight with inspection-level intervention**: the agent initiates and drives the step-by-step construction of the analysis, while the dataflow representation gives the human a continuously visible, editable record of what's happened so far, so they can check, question, or redirect it without having to read through generated code. Control is shared at the granularity of individual dataflow operators rather than only at the start (prompt) or end (final answer) of the task.

## The paper's main idea

**The authors' claim:** dataflows — visual graphs of composable operators — are a better shared abstraction than scripts for human-agent collaboration in data science, because they are easier for analysts to follow, verify, and partially edit. Built on this idea, BobFlow combines the dataflow abstraction with a ReAct-style agent loop, so the agent's reasoning and the human's oversight both operate on the same artifact.

## How the approach works

BobFlow's agent (described as a "Dataflow ReAct" system) reasons step by step about a data-science task, at each step selecting or configuring a dataflow operator, executing it within the underlying Apache Texera engine, and observing the result before deciding on its next action. Because this process happens inside Texera's existing collaborative workflow interface, a human analyst can watch the dataflow being built, inspect intermediate outputs at each node, and intervene (for example, by adjusting an operator or asking a follow-up question) rather than only seeing a final script or answer, as would happen with a conventional code-generating ("script-based ReAct") agent.

## Human study or evaluation design

The authors ran a **user study comparing BobFlow against a script-based ReAct baseline** (an agent that produces conventional code instead of a dataflow), evaluating how well each system supported analysts in **understanding, verifying, and guiding agent-generated analyses** during task completion and debugging. Based on the excerpts available, this reads as a **between-subjects design**: one group of participants used the script-based baseline and a separate group used BobFlow. This detail (between- vs. within-subjects) is based on secondary excerpts and was not independently confirmed from the primary PDF.

## Participants and study setting

**16 participants** took part, reportedly split with the first 9 using the script-based ReAct baseline and the remaining 7 using BobFlow. Participant background, recruitment process, and task domain expertise were **not available** from the sources used for this summary — check the full paper for details before citing.

## Experiments or benchmarks

- A **user study** on data-science tasks requiring participants to understand, inspect, verify, and guide/debug agent-generated analyses, comparing BobFlow to a script-based ReAct baseline.
- A separate **preliminary benchmark** (reported in the related VLDB demo paper) evaluating task accuracy: BobFlow reportedly reached **79% accuracy** on evaluated data-science tasks versus **68%** for the script-based ReAct baseline.
- The arXiv abstract additionally reports accuracy gains of **up to 18.6 points** over the script-based baseline at roughly **one-third of its inference cost**, and **1.1–62.3% fewer input tokens** than the script-based agent in most settings.

## Main results

**As reported by the authors (via secondary excerpts, not independently re-verified against the primary PDF):**
- In the user study, **all participants using BobFlow reached a correct answer on their first request**, while **about a third of participants using the script-based baseline needed additional follow-up requests** to get there.
- BobFlow reportedly helped analysts **understand, inspect, and verify** agent-generated analyses more effectively than the script-based baseline.
- On the separate benchmark, BobFlow's accuracy (79%) exceeded the script-based baseline (68%), while using substantially fewer input tokens in most settings.

## Effects on human performance, trust, workload, safety, or decision quality

*Based on the available excerpts, not a full read of the paper:* the clearest human-related outcome is a reduction in the number of follow-up requests analysts needed to reach a correct answer — a proxy for how much friction or back-and-forth the collaboration required. This suggests the dataflow representation reduced the effort analysts spent correcting or re-querying the agent, consistent with the authors' framing that it supports better understanding and verification. However, the excerpts available did not report standardized trust, workload (e.g., NASA-TLX), or satisfaction scales — if such measures exist in the paper, they were not surfaced in the sources used here, so this should be treated as an open item to confirm against the primary PDF.

## What is genuinely new

*Authors' framing, as surfaced in the sources used here:* rather than treating human-agent collaboration in data science as a code-review problem, BobFlow reframes the shared artifact itself — from a generated script to an interactive dataflow graph — as the key lever for making an agent's work legible and correctable to a human analyst, combined with a ReAct-style agent that operates natively on that graph via an existing collaborative workflow engine (Apache Texera).

## Limitations and open questions

- *My interpretation:* the user study is small (16 participants, apparently split roughly 9/7 across two groups), which is enough to show a directional effect but leaves open how robust the findings are, and whether results generalize to more complex, multi-stage analyses or to analysts with different levels of expertise.
- Participant background and task-domain details were not available from the sources used, so it's unclear whether participants were professional data analysts, students, or another population.
- No explicit trust/workload/satisfaction measures were found in the excerpts used here; the paper may or may not include them — this should be checked directly.
- The reported accuracy figures (79% vs. 68%) come from a separate "preliminary benchmark" in the related demo paper rather than the user study itself, so the two types of evidence (controlled benchmark vs. small user study) shouldn't be conflated.

## Practical implications

*My interpretation, following the authors' own stated motivation:* teams building data-science or analytics agents might get more effective human oversight by exposing the agent's work as an inspectable, editable workflow graph rather than only generated code or a final text answer — especially in settings (scientific research, business analytics, auditing) where an analyst must be able to verify, not just trust, what an automated pipeline did.

## Why you should care

As AI agents take on more of the mechanical work of data analysis, the format in which their work is shown to a human stops being a cosmetic detail — it may determine whether a person can actually catch a mistake before acting on it. BobFlow's small but concrete user study suggests that a shared, inspectable representation (a dataflow graph) can measurably reduce the number of corrective round-trips an analyst needs, offering early evidence that *how* an agent's reasoning is surfaced matters for genuine human oversight, not just how capable the agent is.
