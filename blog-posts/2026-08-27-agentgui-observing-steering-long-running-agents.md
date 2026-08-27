# AgentGUI: An Interface for Observing and Steering Long-Running AI Agents

**Authors:** Xuan Zhao, Jiwoong Sohn, Qinyue Zheng, Michael Moor (ETH Zürich, ETH AI Center)
**Publication date:** 2026-07-28 (arXiv id 2607.26300, v1, cs.HC)
**Venue:** arXiv preprint (not yet confirmed as peer-reviewed)
**Paper link:** https://arxiv.org/abs/2607.26300
**Code link:** Not available (a project/code repository was referenced in web summaries but could not be independently verified from the paper itself; marked "Not available" rather than risk an incorrect link)
**Project page:** Not available
**Date added:** 2026-08-27

> **A note on sourcing:** arXiv itself was unreachable from this research session's network (the fetch tool is blocked for that domain), so this summary is built from web-search-grounded excerpts of the paper's abstract, HTML body, and results rather than a direct PDF read. Facts below reflect what those excerpts report; anything not confirmed is marked "not available," and interpretive statements are labeled as such.

---

## The problem the paper addresses

AI agents built on large language models are increasingly left to run on their own for long stretches — writing and debugging code, training small models, iterating on a task over many steps — often with several such sessions going at once. The paper's starting observation is that **human oversight of these agents is falling behind their growing autonomy**, largely because the tools people have for watching and correcting a running agent are primitive: raw logs, scattered terminal output, or dashboards not built for the job. If you can't easily tell what a long-running agent is actually doing, you can't meaningfully supervise it.

## Why this problem matters

The "human-in-the-loop" promise behind agentic AI depends on humans being able to loop in effectively. If overseeing an agent takes as much effort as just doing the task yourself, or if problems only surface after an agent has spent hours going down the wrong path, oversight becomes theater rather than a real safety and quality mechanism. As more people run multiple agents concurrently — the paper's framing is that this is becoming normal working practice — the interface for watching and steering them stops being a minor UX detail and becomes central to whether human oversight can scale at all.

## What makes the system agentic

The agents studied here are long-running, multi-step LLM agents operating inside isolated Docker sandboxes (referred to as "desks" in the paper), each pursuing a concrete task — for example, training a small image classifier or iteratively refining a system prompt for a question-answering benchmark. They plan and take sequential actions, use tools, write and execute code, and produce artifacts over time, and the paper's own automated "manager" component treats the agent's trajectory as something to be audited step by step. This is squarely agent-level behavior — sustained, autonomous task execution — not a single prompt-response exchange.

## How humans and the AI agent collaborate

AgentGUI is the interface layer sitting between the person and one or more running agents. It gives the human two ways to intervene: reading rich visualizations of what an agent has done so far (its "trace"), and steering it — either by sending a message that interrupts and redirects the agent's current turn, or by relying on an automated LLM-powered "manager" that periodically audits idle or long-running sessions and nudges the agent back on track if it has drifted from the task. This is a case of **human oversight paired with automated assistance for that oversight** — the human isn't in the loop on every action, but has both manual and automated levers for catching and correcting problems.

## What role the human plays

A person using AgentGUI monitors one or several concurrently running agents through the trajectory visualizations, decides when something looks wrong or off-track, and — when they choose to intervene — sends a corrective message that interrupts the agent's current step. They can also simply trigger an audit on demand rather than writing a correction themselves.

## What role the AI agent plays

The agent carries out the assigned task autonomously (e.g., training a model, iterating a prompt) inside its sandboxed environment. Separately, an **automated manager** — itself an LLM-driven component — periodically or on-demand decomposes the task into verifiable criteria, gathers evidence from the agent's transcript and workspace files, judges whether each criterion is met, and either marks the session solved or resumes the working agent with corrective feedback describing what still needs fixing.

## How control, initiative, and decisions are shared

Initiative is split three ways: the working agent acts on its own by default; the human can seize control at any moment with a manual interruption; and an automated manager can also seize control on the human's behalf, either on a schedule or when asked. This is a form of **adaptive, tiered autonomy** — the system is designed so that oversight doesn't have to come exclusively from a human watching constantly, but the human retains the ability to step in directly whenever they want.

## The paper's main idea

**Claim by the authors:** the core bottleneck in scaling human oversight of agents isn't necessarily the agents' capabilities but the interface — without good trajectory visualization and low-friction steering, people can't identify or fix problems in a running agent efficiently, especially when running several concurrently. AgentGUI is presented as a concrete answer: a locally hosted GUI combining trace visualization, manual and automated steering, and compatibility with multiple existing agent frameworks.

## How the approach works

AgentGUI provides a dashboard of concurrent agent "desks," each an isolated Docker sandbox. For each desk, it renders a structured, navigable view of the agent's trajectory (its trace of actions, outputs, and artifacts) rather than raw logs. On top of this, the automated drift-prevention manager works in the background: it breaks the task down into checkable criteria, inspects the transcript and files produced so far, and — if it judges the agent to have drifted from the goal — automatically resumes the agent's session with specific corrective feedback instead of waiting for a human to notice.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, within-participant user study (N=8, MSc/PhD students in quantitative fields, not co-authors of the paper) comparing AgentGUI against a baseline dashboard (a "Hermes Dashboard," a native visualization tool from the underlying agent framework the authors built on). The study used a counterbalanced design — four participants saw AgentGUI first and four saw the baseline first — across two research-style tasks: training a small CNN on the OrganSMNIST dataset against a frozen scorer, and iteratively refining a system prompt for answering MedXpertQA (a medical question-answering benchmark) questions.

## Participants and study setting

Eight graduate students (MSc/PhD level) in quantitative fields took part, working with real, running agent sessions rather than simulated or pre-recorded traces. This is a small, non-representative sample drawn from a technical population, not domain-expert practitioners (e.g., not professional ML engineers or clinicians), and not a large-scale field deployment.

## Experiments or benchmarks

Two components were evaluated: (1) the human user study just described, using OrganSMNIST (a medical image classification dataset) and MedXpertQA (a medical QA benchmark) as the underlying task content; and (2) a separate, non-human-subject experiment testing the automated drift-prevention manager's effect on task completion rates across a "model ladder" of small local LLMs (roughly 0.8B to 9B parameters), run 50 times per model.

## Main results

**Demonstrated in the paper:**
- In the human study, participants using AgentGUI identified key elements in an agent's trace **38% faster** than with the baseline dashboard, a statistically significant difference (p = 0.023).
- In the separate automated-manager experiment (no human participants), the drift-prevention feature raised task completion rates for small local agents by as much as **34 percentage points** across the tested model sizes.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper:** the one human-performance metric directly measured is speed of identifying key elements in an agent's trace, which improved significantly with AgentGUI. **Not demonstrated in the paper (based on available excerpts):** the study does not appear to report effects on decision accuracy, self-reported trust, workload, or longer-term reliance patterns — the reported human-subject result is specifically about review/identification speed, not about whether people made better oversight decisions or felt more confident doing so. **Our interpretation:** a faster time-to-identify-key-elements is a meaningful proxy for reduced oversight burden, but on its own it doesn't establish that people caught more real problems or trusted the system more appropriately — a distinction other papers in this space (e.g., work on Magentic-UI trace design) have shown really matters, since faster and more confident isn't the same as more accurate.

## What is genuinely new

- A working, open interface specifically designed for the emerging practice of running and overseeing **multiple concurrent, long-running LLM agents**, rather than a single agent doing one short task.
- An automated "manager" that performs LLM-based audits of an agent's own trajectory against decomposed task criteria and can autonomously resume/redirect a drifting agent — effectively automating part of the oversight role itself, alongside (not instead of) the human.
- A real, controlled human-subjects comparison (even if small) showing a statistically significant efficiency gain for a concrete oversight interface, plus a separate quantitative demonstration that automated drift correction helps smaller, weaker local models complete tasks more often.

## Limitations and open questions

- The human study had only 8 participants, all graduate students in quantitative fields — not professional ML engineers, domain experts, or a demographically broad user base, which limits how far the 38%-faster result generalizes.
- Only two tasks were tested (a CNN training task and a prompt-iteration task), both fairly technical and ML-specific; it's unclear whether the interface's benefits hold for other kinds of long-running agent work (e.g., web browsing, business workflows).
- The human study measured speed of identifying trace elements, not decision accuracy, trust calibration, or workload — so it's not yet established whether faster review also means better oversight outcomes.
- The automated drift-prevention results (34pp improvement) come from a separate experiment on small local models with no human participants involved, so they shouldn't be read as part of the human-collaboration evaluation.
- Code and project page availability could not be confirmed from the sources used for this summary.

## Practical implications

For teams building or operating agentic AI systems — especially ones running several agents at once for coding, data science, or research-style tasks — this paper offers a concrete design pattern: pair rich, navigable trajectory visualization with both a manual "interrupt and redirect" control and an automated background auditor that can catch and correct drift without waiting for a human to notice. The reported efficiency gain suggests that investment in oversight tooling itself, not just in agent capability, can measurably reduce the human effort needed to keep tabs on autonomous systems.

## Why you should care

As agentic AI moves from single short tasks toward long-running, semi-autonomous work streams, the practical question of *how a person actually watches and corrects an agent in real time* becomes as important as how capable the agent itself is. This paper is a useful, recent data point showing that purpose-built oversight interfaces can produce a measurable, statistically significant improvement in how quickly a human can make sense of what an agent has been doing — while also being honest, in what's available of the paper, about testing this on a small, technical sample and a narrow set of tasks.
