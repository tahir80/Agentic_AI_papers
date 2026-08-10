# ArtAnno: Annotating Implicit Semantics in Artworks through LLM Agent-Driven Bidirectional Human-AI Augmentation

**Authors:** Xiaoyan Gu, Yifang Wang, Wenqing Zheng, Haozhong Liu, Yixia Zheng, Peiyi Jiang, Wenjie Ning, Wei Zhang, Wei Chen (State Key Lab of CAD&CG, Zhejiang University, with some co-authors reportedly affiliated with Florida State University and Hangzhou City University — exact per-author affiliation mapping not independently confirmed from the paper's own author block)
**Publication date:** 2026-08-05 (arXiv v1)
**Venue:** arXiv preprint (cs.HC / cs.AI); peer-review status not confirmed at time of writing
**Paper link:** https://arxiv.org/abs/2608.05026
**Code link:** Not available (no public repository found at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-10

> **A note on sourcing:** this session's outbound network access to arxiv.org (and several other research-hosting domains, including semanticscholar.org, huggingface.co, and publisher sites) returned a blocked connection for direct fetches — an organization egress policy in this sandboxed environment, not a paywall; the paper is a public arXiv preprint. This summary is therefore built from cross-checked search-engine excerpts of the paper's abstract, methodology, and reported results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed." Readers who need precise statistical detail should consult the arXiv preprint directly.

---

## The problem the paper addresses

A lot of what makes an artwork meaningful isn't visible on the surface. A dragon isn't just a dragon in a Chinese painting — it can signal imperial authority, a particular dynasty's iconography, or a specific myth, depending on posture, color, and context that only someone steeped in art history would recognize. Computational art research needs this kind of "implicit semantic" annotation — the culturally grounded meaning behind an image, not just its visible objects — but producing it is slow and expertise-hungry, and general-purpose AI tools aren't built to capture or reuse that kind of specialist judgment.

## Why this problem matters

Digitizing and annotating cultural heritage at scale (museum collections, archives, teaching materials) is bottlenecked by the small number of people who actually hold the relevant expertise. If an AI tool could genuinely absorb an expert annotator's reasoning as they work — not just log their labels — it could help that expertise go further, both by speeding up the expert's own work and by helping less experienced annotators approximate expert-level judgments. Get this wrong, though, and you either get an AI that produces shallow, surface-level labels no better than object detection, or a tool that dumps unreliable suggestions on annotators and adds review burden instead of removing it.

## What makes the system agentic

ArtAnno is built as a **multi-agent LLM system**, organized into two coordinating modules that each perform multi-step work rather than a single text response: a *Proactive Agentic Support Module* that mines an artwork for candidate semantics and proactively generates label suggestions with multimodal justifications (not just a label, but a rationale drawing on visual and textual evidence), and an *Interaction-Driven Evolution Module* that distills what happens during each annotation session into a reusable **Skill Library** and **Knowledge Base** the agents draw on in future sessions. That combination — autonomous multi-step reasoning over an artwork, persistent memory that accumulates across sessions, and a system evaluated on an ongoing collaborative task rather than a single benchmark question — is what makes this an agentic system rather than a one-shot labeling model.

## How humans and the AI agent collaborate

The paper frames this as **Bidirectional Human-AI Augmentation (BiHAA)**: a closed loop in which the AI augments the human's annotation work (by proactively surfacing candidate semantics and explanations), and the human's expertise — corrections, confirmations, and reasoning captured during annotation — augments the AI in turn, being distilled into the shared Skill Library and Knowledge Base that shape how the agents behave in later rounds and later sessions. Collaboration isn't a single hand-off; it's designed to run continuously, round after round, with each side's contribution changing what the other does next.

## What role the human plays

Human annotators bring the domain judgment the system can't originate on its own: they inspect the AI's proposed labels and multimodal justifications, verify or correct them, and (per the formative study) contribute the deeper cultural/contextual knowledge — such as iconographic symbolism — that the system is designed to internalize. In the initial formative study, this loop was partly run as a **Wizard-of-Oz** setup, with a human operator manually collecting participants' annotation knowledge between rounds and feeding it back into the prototype to simulate the bidirectional evolution the full system later automates.

## What role the AI agent plays

The agentic system reduces the annotator's "cold start" and search burden: rather than the human starting from a blank canvas, the Proactive Agentic Support Module mines the artwork for candidate implicit semantics and proactively suggests labels with supporting multimodal explanations up front. As sessions accumulate, the Interaction-Driven Evolution Module is reported to internalize both domain knowledge (e.g., recurring cultural symbols) and the annotator's procedural strategies, so the agents' suggestions are meant to get more targeted and less generic over time and across domains.

## How control, initiative, and decisions are shared

Initiative is genuinely mixed: the AI acts first and proactively (it doesn't wait to be asked before proposing semantics), but the human retains final judgment — verifying, correcting, or rejecting what the agent proposes — and it is specifically the human's corrective/expert input that gets folded back into the system's evolving knowledge, rather than the AI's output being taken as ground truth. Per the authors' reported formative findings, participants wanted this initiative to shift over the course of a task: proactive AI suggestions mattered most at the start (to cut down exploration effort), while interactive, explainable AI output mattered more in a later verification phase.

## The paper's main idea

**Claim by the authors:** annotating implicit semantics in artworks is best supported not by a one-way AI assistant (suggest once, human accepts or rejects) but by a closed **bidirectional** loop, where the AI's proactive suggestions reduce the human's search effort and the human's corrections and domain expertise are continuously captured and reused to make the AI's future suggestions better — including across different art domains.

## How the approach works

The authors first ran a formative study to understand what annotators actually need from such a system, then built ArtAnno's two-module architecture around those findings: the Proactive Agentic Support Module handles the "AI helps human" direction (semantic mining, proactive label suggestion, multimodal justification), and the Interaction-Driven Evolution Module handles the "human helps AI" direction (distilling annotation trajectories — the record of what the annotator confirmed, corrected, and reasoned through — into a persistent Skill Library and Knowledge Base). The system was then evaluated with two case studies and a follow-up user study built on the working prototype.

## Human study or evaluation design

**Demonstrated in the paper (per available search-indexed descriptions):** a two-phase formative study with 20 real artwork annotators from diverse backgrounds, using a Wizard-of-Oz prototype in which participants identified cultural semantics in Traditional Chinese Painting while a human operator manually simulated the bidirectional evolution process between rounds. Findings from this phase directly shaped ArtAnno's design. The authors then validated the resulting system through two case studies plus a separate user study on the working prototype.

## Participants and study setting

- **Formative study:** 20 real artwork annotators (backgrounds not further specified in accessible sources), Wizard-of-Oz methodology, Traditional Chinese Painting as the task domain.
- **User study:** 12 real, paid volunteers (each compensated $15), all with prior experience using annotation tools (self-reported proficiency, mean 3.67/5). Exact recruitment method and demographic breakdown were **not available** from sources accessible in this session.

Both are real human participants, not simulated personas — though the formative study's "bidirectional evolution" step in phase 1 was itself simulated by a human operator (Wizard-of-Oz) rather than run by the finished automated system.

## Experiments or benchmarks

No public benchmark was identified; the evaluation uses custom artwork-annotation tasks (Traditional Chinese Painting in the formative study; domains for the two case studies and user study not fully confirmed from accessible sources, though the authors report the system supporting cross-domain transfer).

## Main results

**Demonstrated in the paper (per available search-indexed descriptions):**
- In the user study, annotation time with ArtAnno dropped to a reported mean of **15.75 minutes**, versus a baseline mean of **30.92 minutes** — roughly a **49% reduction**.
- The system is reported to improve knowledge accumulation and reuse across sessions, and to support transferring accumulated knowledge/strategies across different artwork domains.
- Formative-study findings indicated a phase-dependent preference: annotators wanted **proactive recommendations** early in a task (to cut exploration overhead) and **interactive, multimodal explanations** later, for verification.

Exact statistical tests (significance, effect sizes, variance) for the time-reduction result and other reported outcomes were **not available** from the sources accessible in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The clearest demonstrated human-centered outcome is **efficiency**: participants completed annotation substantially faster with ArtAnno than with the baseline (≈49% less time, per the reported means above). The formative study also surfaced qualitative preferences that function as an early trust/workload signal — annotators explicitly wanted the AI's role to shift from "propose options for me" (reducing early-stage workload) to "explain and justify so I can verify" (supporting confidence in accepting or correcting a suggestion) as they moved through a task. No standardized trust, workload, or safety instrument (e.g., a validated Likert scale) was confirmed from the sources accessible in this session, so these should be read as reported efficiency and preference findings rather than fully instrumented trust/workload measurements.

## What is genuinely new

- A **bidirectional** framing of human-AI augmentation for a knowledge-intensive annotation task — the AI helps the human up front, and the human's real-time corrections/expertise are structurally captured (via a Skill Library and Knowledge Base) to improve the AI, rather than treating human feedback as a one-off input.
- Splitting the collaboration into two purpose-built modules (proactive support vs. interaction-driven evolution) that map onto two different moments in the task — the AI act as initiator early and as an explainer/verifier partner later — informed directly by a formative study rather than assumed by design.
- A concrete measured efficiency gain (annotation time roughly halved) tied to a real, paid user study, not only a benchmark score.

## Limitations and open questions

- **Small samples:** 20 formative-study participants and 12 user-study participants; generalizability beyond these groups and beyond the studied art domain(s) is untested.
- **Wizard-of-Oz element:** part of the formative study's bidirectional-evolution process was manually simulated by a human operator rather than run by the finished automated system, so that phase demonstrates the concept but not the fully automated pipeline.
- **Domain scope:** demonstrated primarily on Traditional Chinese Painting (formative study); the extent and rigor of the claimed cross-domain transfer is not fully confirmed from sources accessible in this session.
- **Unconfirmed statistical detail:** significance tests, variance, and full case-study results could not be independently verified because the full PDF could not be fetched in this session — a limitation of this summary's sourcing, not necessarily of the paper itself.
- **Peer-review status:** appears to be an arXiv preprint at the time of writing; no peer-reviewed venue confirmed.

## Practical implications

For anyone building AI tools for expert-in-the-loop knowledge work (museum/archive annotation, cultural-heritage digitization, or other domains where labels depend on deep contextual expertise), ArtAnno's design is a concrete template: front-load AI initiative to cut early search effort, shift toward explanation-heavy AI behavior as the human moves into verification, and treat the human's corrections as data that should durably reshape the system's future suggestions — not just a one-time accuracy check.

## Why you should care

This paper is a useful, recent example of "human-AI collaboration" that goes beyond a chat window: the AI proactively does real work (mining and suggesting), the human's expert judgment visibly and durably changes what the AI does next, and the whole loop was tested with real paid annotators completing a real task faster than a baseline. If your interest is in agentic systems that genuinely learn from ongoing human correction rather than agents that merely execute commands, this is a small but concrete data point for what that can look like in practice — alongside a reminder that even here, the fully automated bidirectional loop was demonstrated at modest scale (12–20 participants), not yet at production scale.
