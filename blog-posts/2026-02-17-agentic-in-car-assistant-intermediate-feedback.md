# "What Are You Doing?": Effects of Intermediate Feedback from Agentic LLM In-Car Assistants During Multi-Step Processing

**Authors:** Johannes Kirmayr (BMW Group Research and Technology; University of Augsburg), Raphael Wennmacher (LMU Munich), Khanh Huynh (BMW Group Research and Technology; LMU Munich), Lukas Stappen (BMW Group Research and Technology), Elisabeth André (University of Augsburg), Florian Alt (Universität der Bundeswehr München)
**Publication date:** 2026-02-17, revised 2026-03-03 (arXiv id 2602.15569)
**Venue:** ACM CHI 2026 (Proceedings of the 2026 CHI Conference on Human Factors in Computing Systems), DOI 10.1145/3772318.3790997
**Paper link:** https://arxiv.org/abs/2602.15569
**Code link:** Not available (no public code/data repository found)
**Project page:** Not available
**Date added:** 2026-09-15

> **A note on sourcing:** this session's network egress proxy blocks direct access to arxiv.org, doi.org, huggingface.co, and even general sites like Wikipedia under organizational policy (confirmed via the proxy status endpoint, which logs explicit 403 policy denials for these hosts). This summary is therefore built from web-search-indexed snippets of the abstract, the Hugging Face Papers listing, the ACM DOI record, and author-affiliation sources (LinkedIn, OpenReview, related co-authored papers), cross-checked across multiple independent queries rather than read directly from the primary PDF. The abstract text below is reproduced as it consistently appeared, near-verbatim, across search results. Anything that could not be corroborated this way is marked "Not available."

---

## The problem the paper addresses

Imagine asking your car's voice assistant to "find a coffee shop on the way and add it to my route" — a task that takes the assistant several steps (searching, filtering by detour time, checking your calendar, updating navigation) rather than one instant answer. While it works through those steps, should it stay silent until it's done, or narrate what it's doing along the way ("Searching nearby cafés... found three... adding the closest one to your route")? This paper studies exactly that question for agentic, multi-step LLM assistants operating in cars — a setting where the human's attention is supposed to be on the road, not on the assistant.

## Why this problem matters

As LLM-based assistants move from answering single questions to autonomously completing multi-step tasks, they take longer to finish and their internal "reasoning" becomes less visible to the user. In most digital contexts that's an inconvenience; in a moving vehicle it's a safety and trust issue — a driver who doesn't know whether the assistant is still working, stuck, or about to do something unexpected may glance at a screen, repeat a command, or simply stop trusting the system. The paper's authors (from BMW Group Research and Technology together with university HCI labs) are directly motivated by this real deployment context: in-car assistants are one of the first everyday settings where ordinary people will spend extended time next to an autonomously-acting LLM agent.

## What makes the system agentic

The assistant in this study doesn't just answer a question in one shot — it plans and executes a sequence of steps (e.g., searching, filtering, cross-referencing, and taking an action such as updating a route) to fulfill a driver's spoken request, and the paper's whole design hinges on that multi-step, autonomous execution. The object of study is explicitly the assistant's behavior *while it is agentically working through a task*, not the quality of a single generated reply — which is what pushes this squarely into agentic-AI territory rather than conversational-AI research.

## How humans and the AI agent collaborate

The collaboration studied here is about **communication during autonomous execution**, not joint task completion in the sense of the human doing part of the work. The AI agent carries out the multi-step task on its own; the variable the researchers manipulate is how much the agent tells the human about its own process while doing so — silence versus narrating its plan and intermediate results — and they measure how that choice shapes the human's trust, perceived speed, workload, and experience.

## What role the human plays

Forty-five participants sat in a dual-task setup that simulated the divided attention of real driving: they had to monitor a driving-related task with one hand while issuing requests to the in-car assistant and reacting to its behavior with the other. Participants judged how much they trusted the assistant, how fast it felt, how mentally taxing the interaction was, and — in follow-up interviews — described how much visibility into the agent's process they actually wanted, and when.

## What role the AI agent plays

The agentic assistant either works in silence and only announces a final result, or narrates its plan up front and then reports intermediate results as it executes each step — turning what would otherwise be an opaque multi-step process into a running commentary the human can follow (or ignore) while attention is divided.

## How control, initiative, and decisions are shared

The human never intervenes mid-task in this design — the agent retains full execution control throughout. What's shared instead is *information*: the agent's transparency setting determines how much insight the human has into the agent's ongoing decisions, and the paper's qualitative results show users wanting that transparency itself to be adaptive — high at first, while trust is still being established, then reduced once the system has proven reliable, and increased again for higher-stakes tasks. In other words, participants wanted the *level of shared visibility* to be dynamically calibrated to their evolving trust and the task's stakes, even though the underlying division of labor (agent executes, human doesn't) stayed fixed.

## The paper's main idea

**Claim made by the authors:** for agentic LLM assistants performing extended, multi-step operations in attention-critical settings, giving users planned-step and intermediate-result feedback is not a minor UX nicety but a lever that measurably improves trust, perceived speed, and user experience while reducing task load, compared to silent operation — and the ideal amount of that feedback should adapt over time as trust is established, rather than being fixed.

## How the approach works

The authors built an in-car voice assistant capable of agentic, multi-step task processing and implemented two feedback conditions: (1) **silent operation**, where the assistant works through its steps invisibly and only speaks once with the final answer, and (2) **planned-step and intermediate-result feedback**, where the assistant states its plan before acting and reports results as each step completes. Both conditions were tested across tasks of varying complexity within a controlled, mixed-methods, dual-task driving paradigm, combining quantitative ratings with semi-structured interviews.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, within/between (exact design not confirmed from available sources) mixed-methods experiment with a dual-task paradigm simulating divided driving attention, comparing the two feedback conditions across tasks of differing complexity, followed by qualitative interviews.

## Participants and study setting

**Real human participants: N = 45.** The study was conducted as a controlled lab experiment simulating an in-car interaction context (dual-task paradigm), rather than an on-road field study. Detailed demographic breakdowns, recruitment method, and compensation were **not available** from the sources this session could access.

## Experiments or benchmarks

Not a public benchmark. The "experiment" is the controlled comparison of the two feedback conditions (silent vs. planned-step/intermediate-result) across varying task complexities within the dual-task driving simulation, evaluated via both quantitative measures and interviews — no dataset or code release was found.

## Main results

**Demonstrated by the authors:** intermediate feedback significantly improved perceived speed, trust, and user experience, and significantly reduced task load, relative to silent final-only operation — and these effects held across the different task complexities and interaction contexts tested. **Demonstrated (qualitative):** interviews revealed that participants wanted an *adaptive* transparency policy — high verbosity early on to build trust, tapering off as the system proved reliable, with adjustments upward again for higher-stakes tasks or situations.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** this is the paper's central contribution — it directly measures and reports effects of an agentic assistant's communication style on driver-relevant trust, perceived speed, user experience, and task load, finding that transparency about an agent's ongoing multi-step work improves all of these relative to silence. **Our interpretation:** because the study used a simulated dual-task paradigm rather than an on-road or high-fidelity driving simulator study, the safety implications (e.g., effects on actual driving performance or eyes-off-road time) should be read as suggestive rather than directly demonstrated; the paper's measured outcomes are self-reported trust/UX/workload rather than driving safety metrics.

## What is genuinely new

- A controlled, human-subjects test of *agent transparency during multi-step execution* specifically for LLM-based agentic assistants, rather than for single-turn chatbots or non-agentic voice assistants.
- Evidence that the benefits of "narrating the plan while working" generalize across task complexity levels within the tested design.
- A concrete, user-derived design principle — start transparent, taper off as trust builds, and re-escalate for high-stakes tasks — that is more nuanced than a blanket "always explain" or "never explain" rule.

## Limitations and open questions

- The study uses a dual-task lab paradigm to simulate driving attention rather than a real or high-fidelity driving simulator, so effects on actual road safety are not directly measured.
- N = 45 is a solid but moderate sample for a single-lab HCI study; demographic and cross-cultural generalizability are **not available** from the sources this session could access.
- No code, prompts, or dataset release was found, limiting independent replication of the exact assistant behavior tested.
- The paper does not (as far as this session could confirm) test a system that dynamically adapts its own verbosity in real time — the adaptive-transparency idea comes from participants' stated preferences in interviews, not from a working adaptive system that was itself evaluated.

## Practical implications

For anyone building agentic LLM assistants in attention-constrained settings — in-car systems, but plausibly also wearables, smart-home hubs, or other hands-busy/eyes-busy contexts — this paper offers direct, human-tested guidance: don't let a multi-step agent work in silence, but also don't assume more narration is always better forever. Start transparent, and design a mechanism to reduce verbosity as trust is established, while retaining the ability to re-escalate transparency for higher-stakes actions.

## Why you should care

This is a rare controlled, real-participant study of a question every builder of agentic LLM products eventually hits: what should the agent say about itself while it's working? It's grounded in a concrete, safety-relevant deployment context (driving) and produces both a clear quantitative result (transparency helps trust, speed perception, UX, and workload) and an actionable, non-obvious design principle (transparency should be adaptive, not fixed) for human-agent collaboration more broadly.
