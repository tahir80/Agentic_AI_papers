# Teaching an AI Agent Your Taste, One Task at a Time: Test-Time Adaptation Through Human-AI Interaction

**Authors:** Zora Zhiruo Wang, Apurva Gandhi, Rulin Shao, Aspen Chen, Jonas Mueller, Zhiqi Liang, Jett Chen, Michael Ryan, Qianou Ma, Luxi He, Zhoujun Cheng, Andre He, Seungone Kim, Jiayi Geng, Mingqian Zheng, Weiwei Sun, Zheyuan Zhang, Xinran Zhao, Yike Wang, Abe Hou, Liwei Jiang, Pang Wei Koh, Diyi Yang, Graham Neubig, Daniel Fried (25 authors; individual author-to-institution mapping not confirmed from sources used, but the project is reported as led out of Carnegie Mellon University)
**Publication date:** 2026-09-03 (arXiv v1)
**Venue:** arXiv preprint, cs.AI/cs.CL (peer-reviewed venue not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2609.04141
**Code link:** https://github.com/zorazrw/tahi-agent-adaptation
**Project page:** Not available
**Date added:** 2026-09-09

> **A note on sourcing:** this session's outbound network access to arxiv.org and every mirror/aggregator site tried (Hugging Face, Semantic Scholar, example.com as a control) returned a blocked connection at the network egress layer (organization policy, not a paywall — the paper is a public arXiv preprint with an open GitHub code repository). This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed," and readers who need precise numbers, full results tables, or participant demographics should consult the arXiv preprint directly.

---

## The problem the paper addresses

An LLM-based agent is trained on data from millions of people, so by design it behaves like an "average" collaborator. But on real, open-ended professional work — writing a document a certain way, designing a visual asset to a certain taste — success criteria are often personal, inconsistent across people, and never fully written down in the initial instructions. Two different writers asking an agent for "a tighter draft" may want very different things. The paper's authors argue that today's agents have no good way to absorb this kind of individual, hard-to-articulate expertise, even though the interactions a person has with an agent over repeated sessions — the edits they make, the corrections they give, the standards they hold the work to — contain exactly the signal needed to close that gap.

## Why this problem matters

Anyone who has used a general-purpose AI writing or design tool for real work knows the frustration: the tenth output is barely better-fitted to your taste than the first, even though you've corrected the same kind of mistake nine times. If agents could actually learn from that ongoing correction — not just within one conversation, but across sessions — they could progressively need less hand-holding from a given person. That has direct practical stakes for any product built around repeated human-agent collaboration: coding assistants, writing tools, design copilots. Getting personalization right could mean the difference between an agent that stays a generic tool forever and one that becomes a genuinely tailored collaborator.

## What makes the system agentic

The system under study is an LLM-based agent (built on a trainable backbone language model, reported as Qwen3.6-35B) that plans and executes multi-step, open-ended tasks in two domains — writing and visual creation — producing concrete deliverables rather than a single text reply. The agent maintains and updates both its working context (memory of facts and procedures) and its underlying weights (via preference-based fine-tuning) across sessions, and is evaluated on whether its output artifacts succeed by a given user's standards, not on generic benchmark accuracy. That combination — goal-directed multi-step task execution, tool/artifact production, persistent adaptation across sessions, and evaluation as an acting agent — fits the working definition of agentic AI used in this survey.

## How humans and the AI agent collaborate

The paper's framework, called **TAHI (Test-time Adaptation through Human-AI Interaction)**, is explicitly built around an ongoing interaction loop between a specific human and their agent. Rather than treating a person's feedback as a one-off correction, TAHI treats a whole history of a person's interactions with the agent as a stream of signal that the agent should learn from, session after session, so that later tasks need progressively less correction than earlier ones.

## What role the human plays

Each real participant works with the agent on their own real tasks (in writing or visual creation) across multiple sessions and, per the paper's reported interface, can intervene through three distinct channels: adjusting the agent's **plan**, specifying or verifying the evaluation **rubric** the output should be judged against, and directly **editing the deliverable** the agent produced. These interaction signals — not just a thumbs up/down — are what the agent draws on to personalize itself to that person.

## What role the AI agent plays

The agent autonomously plans and executes each task to produce a deliverable, then treats the human's plan adjustments, rubric edits, and deliverable edits from past sessions as adaptation signal: it updates its own working context (memory and procedural know-how) and, separately, updates its own weights via direct preference optimization (DPO) on LoRA adapters trained to prefer the human-guided final outputs. A companion "evolving rubric module" also uses this interaction history to build up an increasingly precise, person-specific checklist of what counts as success.

## How control, initiative, and decisions are shared

Within any single task, the agent has the initiative — it plans and produces the deliverable on its own. The human's initiative operates one level up: across sessions, they shape what the agent will do next by correcting its plans, tightening its evaluation rubric, and editing its outputs, and the agent is designed to fold those corrections back into how it behaves in future sessions. Control is therefore shared not turn-by-turn within a task, but session-by-session over the arc of a working relationship — a form of adaptive delegation where the amount of correction a person needs to give is meant to shrink as the agent learns their standards.

## The paper's main idea

**Claim by the authors:** the interaction history between a specific human and their AI agent — the plan tweaks, rubric refinements, and deliverable edits accumulated across sessions — is a rich, underused source of signal for closing the gap between an agent's average, population-trained behavior and the individualized standard a given professional actually needs; and this signal can be productively used both to adapt the agent's context and to adapt its weights at test time.

## How the approach works

TAHI processes a person's interaction history in a streaming, session-by-session fashion. Two complementary adaptation mechanisms are combined: **context adaptation**, where the agent induces reusable factual memory and procedural skills from past sessions and carries them into new tasks, and **weight adaptation**, where the agent's underlying LoRA-adapted weights are updated with direct preference optimization to favor outputs shaped like the human-guided final deliverables from earlier sessions. Alongside this, an **evolving rubric module** builds a person-specific evaluation checklist over time, intended as a scalable way to judge output quality that improves as more interaction data accumulates, rather than relying on a fixed rubric written once.

## Human study or evaluation design

The authors report a real human-participant evaluation — not a simulated-user study. Per available search excerpts, the study compares three conditions: **online context adaptation**, **online weight adaptation**, and an **offline** condition with no test-time adaptation, run across the two task domains. Participants were assigned to conditions and completed a fixed number of tasks each so that adaptation could be measured as it accumulated across sessions, rather than in a single one-off interaction. Full details of randomization, counterbalancing, and statistical testing were not independently confirmed from the sources available in this session.

## Participants and study setting

The paper reports **30 human participants** ("human experts" in the authors' own framing — people with individualized expertise exceeding what an average AI agent captures), working across **600 tasks total** in the writing and visual-creation domains (consistent with roughly 20 tasks per participant). Exact recruitment method, professional backgrounds, and demographic details were not confirmed from the sources available in this session; readers who need that information should consult the paper directly.

## Experiments or benchmarks

The evaluation is built around the 30-participant, 600-task human study described above rather than a pre-existing public benchmark, comparing the three adaptation conditions (online context, online weight, offline/no adaptation) against each other, and separately evaluating the evolving rubric module's ability to catch failures compared to rubrics written by language models alone or by humans alone.

## Main results

**Reported by the authors, per available search excerpts:**
- Adapted agents improved **solo task success by 4.5–20.9%** within only tens of tasks per person, relative to the non-adapted (offline) condition.
- Personalized agents also produced improvements in success of **up to 8.8% that generalized across users** — i.e., adaptation learned from one person's interaction history was reported to also help when applied for other users, not only the person who generated the signal.
- The evolving rubric module caught **16.0–22.3% more failures** than rubrics produced by language models alone or by humans alone.

Precise per-condition breakdowns, statistical significance, and full results tables could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's headline metric is task success of the agent's output as judged against each person's own standards, which is itself a proxy for whether the collaboration is meeting a real person's bar — but the search excerpts available did not surface separate, explicit measurements of participants' subjective trust, workload, or satisfaction. **This should be read as a gap in what could be confirmed from available sources, not necessarily as an absence in the paper itself;** readers interested in these outcomes specifically should check the full text for any user-experience surveys or qualitative feedback the authors may report.

## What is genuinely new

- **Cross-session, streaming personalization of an agent to one specific person**, rather than a single round of feedback used once and discarded.
- **Combining context adaptation and weight adaptation** (DPO on LoRA adapters) as two distinct, complementary levers for closing the gap between population-average and individual-expert behavior.
- **An evolving, interaction-derived rubric module** that appears to outperform both LM-only and human-only rubrics at catching failures, suggesting interaction history is a genuinely richer signal than either source alone.
- **A real 30-participant, 600-task human evaluation** in two live-work domains (writing, visual creation), rather than a synthetic or simulated-user benchmark.

## Limitations and open questions

- **Scale of the human study.** 30 participants and 20 tasks each is a real and meaningfully-sized study for this kind of research, but it is still modest next to population-scale claims about "individual expertise" — how well these findings generalize across a much broader and more diverse pool of professionals is untested here.
- **Domain scope.** Only writing and visual creation were studied; whether the same adaptation mechanisms transfer to domains with harder-to-verify success criteria (e.g., code, scientific research) is an open question the paper does not resolve.
- **Subjective human outcomes not confirmed.** As noted above, explicit measurements of trust, workload, or user satisfaction were not confirmed from the sources available in this session — it's unclear from what could be verified whether the paper reports these directly.
- **Peer-review status.** As of this writing, this appears to be a recent arXiv preprint with no confirmed peer-reviewed venue.
- **Sourcing caveat (this summary).** Because full-text access was blocked in this research session, exact study procedures, statistical detail, and any qualitative findings could not be verified beyond what surfaced in search excerpts.

## Practical implications

If the reported results hold up under closer scrutiny, they suggest a concrete, buildable pattern for any product pairing a person repeatedly with the same AI agent: treat every plan correction, rubric edit, and deliverable revision as reusable training signal, not just a one-time fix, and give the agent both a context-level and a weight-level mechanism to absorb it. The reported cross-user transfer effect (personalization to one person partly generalizing to others) is a particularly practical detail — it hints that personalization data may have value beyond the individual who generated it, which matters for how such systems could be built responsibly and efficiently at scale.

## Why you should care

Most human-AI collaboration research either studies one-shot feedback (a single correction, a single rating) or trains models before deployment and treats the deployed agent as behaviorally fixed. This paper's focus on continuous, cross-session adaptation *at test time*, driven by real people's ongoing corrections across genuinely open-ended creative work, is a step toward agents that plausibly get better at working with *you specifically* the more you use them — which is a meaningfully different, and more central, kind of human-AI collaboration than a single-turn "did you like this output?" signal.
