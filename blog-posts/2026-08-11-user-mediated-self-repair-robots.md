# When Your Smart Home Breaks, Can It Talk You Through Fixing It?

**Authors:** Morten Roed Frederiksen (Data Systems and Robotics, IT University of Copenhagen, Denmark)
**Publication date:** 2026-08-11 (v1, per arXiv submission metadata) — note: the arXiv identifier itself (2609.26157) uses a "2609" prefix, which normally denotes a September 2026 submission; this date discrepancy could not be resolved in this session (see sourcing note below)
**Venue:** arXiv preprint (peer-review status not confirmed from sources used); a shorter, 4-page companion paper covering the same system and study also appears on arXiv as [2609.26155](https://arxiv.org/abs/2609.26155), "Toward Self-Repairing Ubiquitous Robots Using Goal-Oriented Agentic AI in Human-Robot Interactions"
**Paper link:** https://arxiv.org/abs/2609.26157
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-09-24

> **A note on sourcing:** this session's outbound network access to arxiv.org and its usual mirrors (Hugging Face, alphaXiv, Semantic Scholar, Pith) was blocked at the network egress layer, so this summary could not be built from a direct read of the full PDF. It is instead built from cross-checked excerpts surfaced by multiple independent web searches, including the paper's own abstract text and reported study design and results, which were consistent across several independent search queries. Facts that appeared consistently across independent searches are presented as such; anything that could not be corroborated this way is marked "Not available" or flagged as unconfirmed. Readers who need exact statistics, full result tables, participant demographics, architectural details, or direct quotations should consult the arXiv preprint directly.

---

## The problem the paper addresses

Robots and smart devices are increasingly meant to blend into everyday environments — a vacuum robot, a smart shelf, an ambient sensor unit — rather than sit behind a screen and menu system. The paper calls these "ubiquitous robotic systems." The catch: because they're designed to be invisible, most of them don't have a traditional visual interface (a screen, an app with diagrams, a troubleshooting wizard). So when something breaks, an ordinary person has no built-in way to figure out what's wrong or how to fix it. The paper's core question is: can an AI agent guide a non-expert, purely through natural spoken/typed conversation, to successfully carry out a real physical repair?

## Why this problem matters

As more of these ambient, interface-less robots enter homes and workplaces, routine hardware faults (a jammed part, a loose connector, a miscalibrated sensor) become a real, recurring friction point. Sending a technician for every small fault is expensive and slow; expecting users to consult a written manual defeats the purpose of an "invisible" device. A system that can diagnose and talk an ordinary person through the fix — adapting to however that person actually phrases things, asks questions, or goes off on tangents — could make self-service repair genuinely viable at scale, and is also a useful test case for how much unstructured, real-time human guidance a language-driven agent can reliably support.

## What makes the system agentic

This is not a chatbot that answers a single question. The system pursues an explicit goal (successfully complete a physical repair), plans over multiple steps, and directs a real-world, multi-turn interaction that adapts as it goes. According to the paper's own description, it uses a multi-layered architecture that separates **high-level strategic planning** (figuring out the overall repair goal and the sequence of sub-goals needed to get there) from **reactive conversational execution** (handling the live, turn-by-turn dialogue, including a user's questions, side comments, or unexpected phrasing). Unconstrained human instructions are converted into a structured hierarchy of goals that the system tracks and updates as the interaction unfolds — which is what makes it an agent carrying out a task, not a static FAQ or a fixed decision tree.

## How humans and the AI agent collaborate

The collaboration is physical and verbal at the same time: the AI agent does not have hands. It cannot open a panel, reseat a connector, or apply force to a stuck part. So the human is the one who does the physical work, while the agent is the one who has (or builds, through dialogue) a plan for the repair and communicates it step-by-step. This is a "user-mediated" repair, as the paper's own framing puts it — the robot guides, the human executes.

## What role the human plays

Non-expert study participants acted as the "hands" of the repair process. They interacted with the system through situated, real-time natural-language dialogue — describing what they saw, asking clarifying questions, and, per the reported results, sometimes diverging conversationally (going off-topic, rephrasing, or asking something unplanned) — while physically performing the repair steps on a hardware testbed as the agent guided them.

## What role the AI agent plays

The agent plays the role of diagnostician and instructor. It holds (or builds) the plan for the repair, decomposes an open-ended goal into a structured sequence of sub-goals, and translates that into live, adaptive spoken/text guidance — reacting to what the human says or does at each step, rather than reciting a fixed script.

## How control, initiative, and decisions are shared

Authority over the physical world is split cleanly: the agent effectively acts as the "supervisor" that plans and directs, while the human retains full control of physical action, and can question, redirect, or diverge from the flow of guidance at any point. The system's job, per the reported results, is to stay robust to that — adapting to conversational diversions and linguistic variation rather than requiring the user to follow a rigid script. This is a form of shared control organized around a division of labor: cognitive/diagnostic planning on the agent's side, physical execution and moment-to-moment judgment on the human's side.

## The paper's main idea

**Claim by the author:** a goal-oriented agentic architecture that separates strategic planning from reactive dialogue execution can successfully guide non-expert users through real, physical hardware repairs via natural-language conversation alone — even when users phrase things unpredictably or interrupt the flow of guidance with questions or tangents.

## How the approach works

Per the reported description, the architecture has (at least) two layers: a strategic layer that maintains the overall repair goal and a structured hierarchy of sub-goals, and a reactive layer that handles live conversational execution — parsing what the user says, responding, and adjusting the guidance in real time. This decoupling is presented as the key design choice that lets the system stay on-task at the planning level while remaining flexible and responsive at the conversational level, rather than treating every user utterance as a potential derailment of a fixed script.

## Human study or evaluation design

The system was evaluated with real, non-expert human participants performing an actual physical repair task on a hardware testbed, guided end-to-end by the agent through dialogue. The study measured whether participants could complete the repair (a behavioral outcome) and also collected participants' self-reported sense of self-efficacy after the interaction.

## Participants and study setting

**Twenty participants (N = 20)**, described as non-expert users, took part in the study using a **physical hardware testbed** (a real repair task, not a simulation). Reported results indicate 19 of the 20 participants successfully completed the task. Further demographic detail (recruitment method, professional background, prior technical experience, compensation) could not be confirmed from the sources available in this session.

## Experiments or benchmarks

There is no public benchmark here — this is a single custom study built around one physical hardware repair scenario and one experimental system. No dataset or benchmark release could be confirmed from the sources available.

## Main results

**Reported across cross-checked search excerpts:** the architecture achieved a **95% task completion rate** (19 of 20 participants successfully completed the physical repair guided by the agent). Participants reported **positive self-efficacy** after the interaction, and the system's real-time guidance reportedly adapted successfully to conversational diversions and variation in how participants phrased things. Exact statistical tests, effect sizes, and full result tables could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central human-outcome measures, as reported, are **task completion** (did the user succeed at the physical repair) and **self-efficacy** (did the user come away feeling capable/confident). Both are reported positively: a 95% completion rate and positive self-reported self-efficacy. This session could not confirm whether standardized trust or workload instruments (e.g., NASA-TLX) were additionally used, or whether a non-agentic baseline (e.g., a static manual or fixed decision-tree guide) was tested for comparison.

## What is genuinely new

- A concrete architecture that explicitly decouples strategic goal planning from reactive, real-time conversational execution for a physical, human-executed repair task.
- A demonstrated case of an LLM-based agent guiding a real physical intervention it cannot itself perform, with the human as the sole physical actor — a distinct division of labor from most "agent does the task, human reviews it" setups common in software-agent oversight research.
- Evidence, from a real (if small) physical-world study, that this kind of guidance can remain robust to unconstrained human conversational behavior — questions, phrasing variation, and topic diversions — rather than requiring users to follow a fixed script.

## Limitations and open questions

- **Small, single-study sample.** Twenty participants (one author, one venue, one task) is a modest basis for generalizing across repair types, robot form factors, or user populations.
- **Single task/testbed.** The study evaluated one physical hardware repair scenario; it's unclear how the architecture would generalize to more complex, higher-stakes, or more physically demanding repairs.
- **No confirmed baseline comparison.** It could not be confirmed from available sources whether the study compared the agentic-dialogue condition against a non-AI alternative (e.g., a written manual), which would clarify how much of the benefit comes from the AI-specific adaptivity versus simply having any real-time guidance at all.
- **Sourcing caveat (this summary).** Because full-text access was blocked in this research session, architectural details beyond the high-level two-layer description, full participant demographics, exact statistics, and the apparent discrepancy between the paper's reported "11 Aug 2026" submission date and its "2609" arXiv identifier prefix could not be independently resolved. Readers should verify against the primary source.
- **Peer-review status.** Not confirmed from sources used; this is presented here as an arXiv preprint.

## Practical implications

For designers of ambient, screen-free robots and smart devices, this is a concrete data point that natural-language, agent-guided repair is viable as a self-service support channel — potentially reducing the need for in-person technician visits or reliance on written manuals for routine hardware faults. More broadly, for human-AI collaboration design, it's a worked example of a "supervisor agent, human hands" division of labor, distinct from the more commonly studied "autonomous agent, human reviewer" pattern — useful for any setting where an AI can reason and plan but cannot physically act (accessibility support, remote expert assistance, field maintenance).

## Why you should care

Most agentic-AI human-oversight research studies humans reviewing or approving what a software agent already did. This paper flips that relationship: the AI plans and talks, but a person does the physical work, and the AI has to stay useful and adaptive across all the unpredictable ways real people communicate — questions, digressions, imprecise language — while that person's hands are on real hardware. It's a small, single-author study, so the results should be read as an early, encouraging signal rather than a settled result — but it's a genuinely different and practically relevant shape of human-AI collaboration worth watching as ambient and interface-less robotics become more common.
