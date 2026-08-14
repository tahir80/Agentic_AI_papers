# A Framework of User Experience Principles for Human-AI Agent Interaction in the Workplace

**Authors:** Kathrin Paimann, Elizangela Valarini, Sebastian Juhl (SAP SE; Hochschule Fresenius, Heidelberg; University of Missouri)
**Publication date:** 2026-07-26 (arXiv v1, id 2607.19941) — exact day taken from secondary sources and not independently re-verified against the primary PDF (see sourcing note below)
**Venue:** To appear in the proceedings of Mensch und Computer (MuC) 2026, the German/Austrian/Swiss HCI conference (Duisburg, 30 Aug–2 Sep 2026); arXiv preprint in the meantime
**Paper link:** https://arxiv.org/abs/2607.19941 (HTML: https://arxiv.org/html/2607.19941v1)
**Code link:** Not available — this is a design-research/HCI paper, not a released software system
**Project page:** Not available
**Date added:** 2026-08-14

> **A note on sourcing:** This session's direct network access to arxiv.org (and mirrors such as Hugging Face, Semantic Scholar, alphaXiv, and other reader proxies) was blocked by organizational egress policy, so this summary could not be built from a first-hand read of the full PDF. It was instead assembled by cross-checking many independent web-search queries against snippets of the paper's abstract, HTML rendering, and secondary discussion. Facts that were consistent and specific across multiple searches (authors, venue, methodology types, the top-ranked principles, the study's framing) are reported as such. The full ordered list of all eight UX principles, the exact number of study participants, and some methodological details could **not** be independently confirmed from the sources available and are marked "Not available" or flagged as unconfirmed below, rather than invented. Readers who want exact figures should check the primary PDF directly.

---

## The problem the paper addresses

AI "agents" — software that doesn't just answer a question but goes off and *does* something in a business system on your behalf — are quickly becoming a normal part of office work: things like SAP's Joule agents, Microsoft Copilot agents, or similar assistants that can look things up, draft documents, or take actions across a company's software. But most guidance on how to *design* these agents so people actually trust and want to use them is either generic UX advice borrowed from ordinary software, or abstract AI-ethics principles that don't tell a product designer what to actually put on the screen. This paper asks a very practical question: when real business users and professionals interact with AI agents at work, what do *they* say actually matters for a good experience — and can that be turned into a concrete, validated checklist that designers and engineers can use?

## Why this problem matters

A workplace AI agent that quietly does the wrong thing, or that a user can't figure out how to stop, correct, or trust, doesn't just annoy someone — it can create real business, compliance, and safety problems, and it can also kill adoption of a genuinely useful tool. As companies race to embed autonomous or semi-autonomous agents into everyday workflows, decisions about how much control a human keeps, how transparent the agent is about what it's doing, and how a person can intervene are being made right now, often without much empirical grounding. This paper is explicitly aimed at giving designers and engineers something more solid to build on than intuition.

## What makes the system agentic

The paper doesn't build a brand-new agent from scratch; instead, its subject matter is real, deployed enterprise AI agents — the kind that plan and carry out multi-step tasks inside business software (the authors are SAP researchers, and the paper's framing and examples are grounded in agentic systems like SAP's Joule agents). These are goal-directed systems that act inside a live software environment (retrieving data, executing steps, taking actions across integrated business tools) rather than simply answering a one-off question, and it's exactly the *agentic* character of these systems — their autonomy, their ability to act without a human typing every step — that motivates the paper's focus on control, oversight, and trust.

## How humans and the AI agent collaborate

The paper studies collaboration one level up from a single task: rather than watching one person work through one workflow with one agent, it gathers structured input from business users, industry professionals, and UX/AI experts about what makes any interaction with a workplace AI agent feel trustworthy, controllable, and useful. That input — collected through a participatory design workshop, expert reviews, in-depth interviews, and a validation survey — is synthesized into a set of design principles meant to shape how future agent interactions should be built, so that oversight, intervention, and shared control are designed in rather than bolted on afterward.

## What role the human plays

Humans are the source of the paper's evidence and the intended beneficiaries of its output. Real business users and professionals took part in a participatory design workshop, sat for in-depth interviews about their expectations and concerns, and rated/validated the resulting principles in a survey; UX and AI experts contributed structured expert reviews. Within the design principles themselves, humans are also cast as active overseers of the agents they'll eventually use: the top-rated principle, "Human Control," is explicitly about people retaining final approval, using confirmation workflows, and having a reliable way to stop an agent — i.e., humans are meant to stay the ones who decide, not just the ones who watch.

## What role the AI agent plays

In the principles that emerged, the AI agent is framed as a capable but bounded actor: it should behave reliably and safely as a "non-negotiable baseline," respect data privacy and role-based access, tailor its outputs to the user's current role, task, and context ("Context-Awareness"), and be transparent enough about what it's doing and why that a user can verify and trust its output. In other words, the agent is expected to act autonomously within guardrails that keep it legible and interruptible to the human it's working with or for.

## How control, initiative, and decisions are shared

The clearest signal in the paper is that participants wanted control to stay with the human at moments that matter — final approval before consequential actions, explicit confirmation steps, and a working "stop" mechanism — while being comfortable letting the agent handle routine execution on its own the rest of the time. This is a form of adaptive, risk-sensitive delegation: initiative can shift toward the agent for low-stakes, well-understood work, but the paper's top-ranked principles push initiative back toward the human whenever reliability, privacy, or context sensitivity is in question.

## The paper's main idea

Rather than proposing a new algorithm or agent architecture, the paper's core contribution is a **validated framework of eight UX principles** (with underlying, more specific criteria) for designing human-AI agent interactions in the workplace — distilled directly from what real users, professionals, and experts said mattered, not derived purely from the authors' own reasoning or from prior chatbot-era UX guidance.

## How the approach works

The authors used a multi-method design-research process: a participatory design workshop to surface candidate principles collaboratively with users; a "paper-and-pencil" exercise; expert review by UX/AI specialists; a meta-analysis pulling together prior literature and inputs; and in-depth interviews to probe how people actually reason about control, risk, and trust with workplace agents. The resulting candidate principles were then validated and prioritized through a survey, producing a ranked, criterion-level framework rather than just a loose list of ideas.

## Human study or evaluation design

This is a qualitative-plus-survey human-subjects design-research study, not a controlled task-performance experiment with an actual working agent. It combines a workshop, expert reviews, interviews, and a validation survey — real people directly generating and rating the framework's content, rather than being observed performing tasks with a live agent under experimental conditions.

## Participants and study setting

The study drew on business users, industry professionals, and UX/AI experts, consistent with the authors' base at SAP (an enterprise software company) and their focus on agentic tools used in real business workflows. **The exact number of participants across the workshop, interviews, and survey could not be confirmed from the sources available for this summary** and is reported here as Not available; readers who need exact sample sizes should check the paper directly.

## Experiments or benchmarks

There is no benchmark or task-performance experiment in the traditional agentic-AI sense (no accuracy/success-rate numbers on a fixed task suite). The "evaluation" is the validation of the design framework itself: whether the eight principles, once proposed, were rated as relevant, complete, and correctly prioritized by study participants.

## Main results

The study produced and validated eight core UX principles (with supporting criteria) for human-AI agent interaction in the workplace. Confirmed from multiple independent sources, the top-ranked principles were:

1. **Human Control** (ranked #1) — meaningful oversight at critical decision points, emphasizing final approval, confirmation workflows, and stop mechanisms.
2. **Reliability, Safety, and Robustness** (ranked #2) — treated by participants as a non-negotiable baseline; unstable or misleading outputs were seen as disruptive and trust-eroding.
3. **Data Privacy and Governance** (tied #3) — especially important in regulated or client-facing contexts, with access needing to stay role-sensitive.
3. **Context-Awareness** (tied #3) — agent outputs should reflect the user's role, current task, and situation to be genuinely useful.

A fifth principle, **Transparency** (sometimes described alongside explainability), was also identified as important for trust and verification, with its importance varying by task complexity and user experience level. **The paper defines eight principles in total; the remaining three could not be verified with confidence from the sources available for this summary and are therefore not listed here** — see the primary paper for the complete, authoritative list.

## Effects on human performance, trust, workload, safety, or decision quality

The paper does not report a controlled comparison of task performance, workload, or trust scores between an agent designed around these principles and one that ignores them — that kind of head-to-head evaluation is explicitly flagged (per secondary sources) as future work, since the authors note that most existing evidence in this space comes from controlled lab settings and that longitudinal, real-world data on how such designs affect productivity, accountability, and user experience is still scarce. What the study does show is *which* design concerns real users and experts rate as most important for trust and adoption — with human control over consequential decisions rated as the single most important factor.

## What is genuinely new

The paper's contribution is a **framework of design principles grounded in a real, multi-method human study** (workshop, interviews, expert review, survey validation) specifically about agentic AI in the workplace, rather than a general human-AI or chatbot UX framework repurposed for agents. Positioning "Human Control" as the top-ranked principle — ahead of reliability, privacy, and context-awareness — is a concrete, actionable data point for anyone designing oversight mechanisms into enterprise agents today.

## Limitations and open questions

By the authors' own framing (as reflected in secondary sources), the principles have not yet been validated through longitudinal, real-world deployment data — the evidence base is still workshop-, interview-, and survey-based rather than drawn from people using agents built around these principles over time in production. It's also, by design, a general framework rather than a study of one specific agent's behavior, so it doesn't tell you exactly how to implement "Human Control" or "Context-Awareness" in a given product. This blog post is additionally limited by not having direct access to the full PDF; some specifics (participant counts, the complete list of all eight principles, fine-grained criteria under each principle) are not confirmed here and should be checked against the source paper.

## Practical implications

For teams building enterprise or workplace AI agents, this paper offers a concrete, user-validated starting checklist: prioritize meaningful human control (final approval, confirmation steps, a real stop button) as the top design concern, treat reliability/safety as non-negotiable table stakes, take data governance and role-based access seriously, make agent behavior context-aware, and be transparent enough that users can verify what the agent did and why. It's a useful reference point for product and UX teams currently deciding how much autonomy to give an agent and how to surface oversight controls to end users.

## Why you should care

If you're designing, deploying, or simply going to be asked to trust a workplace AI agent in the near future, this paper is a rare case of "what do the actual users want" being asked directly and turned into a ranked, checkable list — and the answer, echoed across the highest-priority principle, is that people want to stay meaningfully in control, not just be informed after the fact. That's a useful, evidence-grounded counterweight to the industry's general push toward more autonomous agents.

---

*Author's interpretation note: statements above describing what participants said, felt, or prioritized reflect the paper's own reported findings (as far as they could be verified through secondary sources); the framing of "why this matters" and the practical-implications section reflect this summary's own interpretation and are not verbatim claims from the paper.*
