# How Much Should a Human Do? A New Benchmark Dials Human Involvement Up and Down to Find Out

**Authors:** Yaozu Wu, Wei-Chieh Huang, Jizhou Guo, Dongyuan Li, Renhe Jiang, Henry Peng Zou, Chunyu Miao, Shanghao Li, Weizhi Zhang, WeiWei Ye, Yankai Chen, Meng Zhang, Xue Liu, Philip S. Yu (The University of Tokyo, University of Illinois Chicago, MBZUAI, McGill University, Zhejiang University — author-to-institution mapping not individually confirmed)
**Publication date:** 2026-07-05 (arXiv v1)
**Venue:** arXiv preprint, cs.AI/cs.MA (peer-reviewed venue not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2607.04329
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-25

> **A note on sourcing:** this session's outbound network access to arxiv.org and mirror/aggregator sites (Hugging Face, Semantic Scholar, ar5iv) returned a blocked connection for direct fetches (organization egress policy, not a paywall — the paper is a public arXiv preprint). This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported findings, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way — including exact metric definitions and the full results tables — is marked "not available" or "not confirmed," and readers who need precise numbers should consult the arXiv preprint directly.

---

## The problem the paper addresses

Most benchmarks for AI agents test them alone: give the agent a task, let it work uninterrupted, and score the result. But that isn't how most real agentic systems will actually be used. A customer-service agent, a coding assistant, or a research assistant is usually paired with a person who can jump in — to answer a question, approve a risky step, or correct a mistake. The trouble is, we have no good, systematic way to test *how* that human involvement should be configured: how much say should the human get, through what channel, and at what point in the task? This paper's authors argue the field has been evaluating agents as if humans are optional extras, when in practice the human's role is a design choice that can be tuned — and that choice needs its own benchmark.

## Why this problem matters

If you're building a product with an AI agent — a travel-booking bot, a coding copilot, an automated research assistant — you have to decide how much autonomy to give it and how the human gets involved: full autonomy with occasional check-ins? A human who can be consulted but not overruled? A human who must approve every step? Right now those design decisions are mostly guesswork, because there's no shared way to systematically vary "how much human" a system gets and measure what changes. Getting this wrong has real costs: too much autonomy risks safety failures and eroded trust; too much human involvement burns the very time and attention savings the agent was supposed to provide. A benchmark that treats human participation as a dial you can turn, rather than a fixed afterthought, is aimed squarely at helping designers find the right setting for a given task.

## What makes the system agentic

The systems under test are LLM-powered agents that plan and execute multi-step tasks across six different domains (arXiv abstract excerpts identify these as including tasks like airline customer service, retail, telecom support, coding, research assistance, and negotiation/bargaining — domain names corroborated via search excerpts but not independently verified against the full paper). These agents hold explicit **roles, permissions, and action authority** within a task graph, use tools, and are evaluated on whether they actually complete the task and recover from failures — not just on the quality of a single response. That qualifies them as agentic under this survey's working definition: goal-directed, multi-step, tool-using, and evaluated as agents rather than as chatbots.

## How humans and the AI agent collaborate

The paper's central contribution, **HAS-Framework**, models a human-agent system as a graph in which both the human and the LLM-powered agent are "first-class participants" — each with their own role, permissions, communication paths, and authority to act. Built on top of that framework, **HAS-Bench** lets researchers *configure* how much and what kind of human participation is present in a given run, and then measures what happens. Three configurable dimensions control this: **agency levels** (how much decision-making power the human retains versus delegates to the agent), **interaction channels** (how the human and agent communicate — e.g., clarification requests, feedback, approvals), and **persona policies** (behavioral scripts that determine how the "human" role responds during a run).

## What role the human plays

Important caveat up front: **the "human" in HAS-Bench's experiments is not a real person.** The benchmark's "persona policies" are LLM-driven scripts that stand in for a human collaborator — asking clarifying questions, giving feedback, granting or withholding approval, according to a configurable policy — rather than recruited human participants making live decisions. In other words, the paper studies *simulated* human participation, systematically varied, rather than *real* human behavior observed in the wild.

## What role the AI agent plays

The AI agent is the task-executing party: it plans, calls tools, and carries out the steps of tasks in each of the six domains, deciding — depending on the configured agency level — how much to act independently versus defer to, consult, or wait on the simulated human participant.

## How control, initiative, and decisions are shared

This is exactly what the benchmark is built to vary rather than fix. By turning the "agency level" and "interaction channel" dials, the researchers can instantiate systems ranging from mostly-autonomous agents that only loop in the human for edge cases, to systems where the human retains tight, continuous control. The paper's headline claim is that these different configurations produce measurably different collaboration behavior — the degree of human involvement is not just a autonomy/safety trade-off in the abstract, but something with concrete, measurable effects on outcomes.

## The paper's main idea

**Claim by the authors:** human participation in an agentic system is not simply "more is better" or "less is better" — its benefit is conditional on *when*, *how*, and *by whom* it's exercised, and a graph-based framework (HAS-Framework) plus a configurable benchmark (HAS-Bench) can make that conditionality visible and measurable for the first time, rather than leaving it to case-by-case product intuition.

## How the approach works

HAS-Framework represents a task as a graph of participants (human and agent nodes) with explicit roles, permissions, and communication edges. HAS-Bench then instantiates this graph under different configurations — varying the human's agency level, the channel(s) through which the human and agent interact, and the persona policy governing the simulated human's responses — across six task domains. For each configuration, the benchmark measures both **whether the task got done** (task outcomes) and **how the collaboration unfolded along the way** — process-level measures the authors report include clarification quality, feedback utilization, control calibration, safety, initiative, and interaction cost (exact operational definitions of each metric were not independently confirmed from available sources).

## Human study or evaluation design

**This is not a human-subjects study.** No real human participants were recruited or observed; "human participation" is implemented and varied entirely through LLM-driven persona policies acting as a proxy for a person. The authors present this as a deliberate design choice that allows systematic, repeatable variation of human involvement across many configurations and domains — something a live human study could not easily do at this scale — but it means the paper's findings describe how *simulated* human involvement affects agent behavior, not how *real* people actually behave when paired with these agents, and the paper's own framing (per available excerpts) does not claim otherwise.

## Participants and study setting

Not applicable — no real human participants. The "participants" in every reported experiment are the LLM-powered agent and one or more LLM-driven simulated human personas, run across the six task domains under different agency-level and interaction-channel configurations.

## Experiments or benchmarks

HAS-Bench itself is the benchmark contribution: six task domains, multiple configurable dimensions of human participation (agency level, interaction channel, persona policy), and a battery of task-outcome and process-level metrics applied across those configurations. Search excerpts referencing the paper's results also surfaced a set of domain-level pass-rate figures (Airline 91.7%, Retail 94.4%, Telecom 86.7%, Coding 93.8%, Research 87.5%, Bargaining 90.0%, overall 91.1%) that are plausibly tied to a human-verification or data-quality check on the benchmark's task suite rather than the paper's main collaboration-effect results — this attribution could not be independently confirmed from available sources, so it is reported here with that caveat rather than presented as a headline finding.

## Main results

**Reported by the authors, per available search excerpts:** across the six domains, human participation can substantially improve task completion and failure recovery compared to a fully autonomous agent baseline — but the size (and possibly the direction) of that improvement depends on *when* in the task the human is involved, *how* (which interaction channel and agency level), and *by whom* (which persona policy). This is presented as evidence against a one-size-fits-all approach to human-in-the-loop design: the same nominal amount of "human involvement" can help or fail to help depending on how it's configured. Precise effect sizes, statistical tests, and full per-domain, per-configuration results tables could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

Because no real humans were involved, the paper cannot and does not report effects on real human trust, workload, or experience. What it does report — per available excerpts — is effects on **agent-side and system-level outcomes** under varying simulated-human configurations: task completion, failure recovery, and process measures explicitly named "safety," "control calibration," and "interaction cost." These are proxies for concepts that matter to real human-AI collaboration (safety, how well control is calibrated, how costly interaction is) but are measured here entirely within a simulated environment, not validated against real people's actual experience.

## What is genuinely new

- **A graph-based framework (HAS-Framework)** that treats a human collaborator as a structured, first-class participant in an agent's task graph — with explicit roles, permissions, and communication paths — rather than an unstructured external interrupt.
- **A configurable benchmark (HAS-Bench)** that lets researchers systematically dial human participation up and down along multiple independent axes (agency level, interaction channel, persona policy) and observe the effect, across six domains, rather than testing one fixed human-in-the-loop design.
- **Process-level collaboration metrics** (clarification quality, feedback utilization, control calibration, safety, initiative, interaction cost) that go beyond simple task-success rates to characterize *how* a collaboration unfolded, not just whether it worked.

## Limitations and open questions

- **No real human participants.** This is the paper's most consequential limitation for anyone specifically interested in human-AI collaboration: every finding describes simulated-persona behavior, not verified real-world human behavior. The paper does not claim to have run a human-subjects study (per available excerpts), and this digest treats that claim boundary as firm.
- **Simulated personas may not represent real human variability.** LLM-driven persona policies are a scalable way to vary "human" behavior systematically, but whether they capture the noisiness, inconsistency, expertise gaps, and situational pressure of real people interacting with an agent is an open question the paper does not resolve.
- **Exact metric definitions and full results not independently confirmed.** Precise operational definitions for metrics like "control calibration" or "initiative," and complete per-domain, per-configuration results tables, could not be verified from the sources available in this session; readers who need those details should consult the arXiv preprint directly.
- **Peer-review status:** as of this writing, this appears to be an arXiv preprint with no confirmed peer-reviewed venue.

## Practical implications

If this framework's core claim holds up — that the benefit of human participation depends heavily on its specific configuration, not just its amount — the practical takeaway for people building agentic products is that "add a human in the loop" is not a single design decision but a multi-dimensional one: which agency level, which interaction channel, at which points in the task. A framework and benchmark like this could eventually help teams *test* different human-participation configurations against their specific task before shipping, rather than picking one by intuition. That said, because the underlying "human" here is simulated, any specific numeric configuration this benchmark recommends would still need real human validation before being trusted in a live product.

## Why you should care

Human-AI collaboration research has largely proceeded along two separate tracks: benchmark papers that ignore the human almost entirely, and human-subjects studies that test one specific interface or task deeply but can't easily explore the huge space of possible human-participation designs. This paper's contribution is a bridge of sorts — a framework and benchmark explicitly built to make "how much and what kind of human involvement" a first-class, systematically testable variable. That is a genuinely useful methodological tool for the field, even though — and the paper's own framing appears to acknowledge this by construction — it is a step *before* the real-human validation that would be needed to know whether its simulated findings hold up with actual people.
