# Giving Humans and AI Agents a Shared, Reshapeable Map of the Work Itself

**Paper title:** Working Through Representation: Malleable Workspaces for Human-Agent Knowledge Work
**Authors:** Nan Chen, Long Ling, Luna K. Qiu, Zilong Wang, Yuqing Yang (Microsoft Research Asia affiliation reported in secondary sources; not independently confirmed from the primary PDF)
**Publication date:** 2026-10-22 (arXiv v1)
**Venue:** arXiv preprint, cs.HC; peer-reviewed venue/acceptance not confirmed
**Paper link:** https://arxiv.org/abs/2610.30893
**Code link:** Not available (the paper reportedly includes MalleableSpace's source code as supplementary material; no public code repository was found)
**Project page:** Not available
**Date added:** 2026-11-26

> **A note on sourcing:** this session's network access to arxiv.org and its usual mirrors (export.arxiv.org, alphaxiv.org, Semantic Scholar's API, Hugging Face) was blocked by the environment's network policy, so the primary PDF could not be opened directly. This summary is built from the paper's abstract and HTML/PDF excerpts as they surfaced across several targeted web searches, cross-checked against each other for consistency. The paper itself appears to be a freely available, open-access arXiv preprint. Figures, quotes, and design details below are reported as they appeared in those excerpts; anything not independently confirmed against the full PDF is marked accordingly. Please check the arXiv preprint directly before citing specific details.

---

## The problem the paper addresses

When you work with an AI agent over hours, days, or weeks on a real project — research, writing, planning — the agent's understanding of "what we're doing" tends to live only in the chat transcript. But a transcript is a timeline of messages, not a map of the work. It doesn't capture how your goals, documents, open questions, and completed steps relate to each other, or how that structure evolves as the project moves forward. The authors argue that this mismatch — a flat conversation history standing in for what should be an evolving, structured picture of the work — makes it hard for both the human and the agent to act consistently as a project matures.

## Why this problem matters

As people increasingly lean on AI agents for sustained knowledge work rather than one-off questions, the thing that actually needs to stay coherent isn't any single answer — it's the shared understanding of the project: what's been decided, what's still open, which documents matter, and why. If that understanding only exists implicitly, scattered across a chat log, both the human and the agent end up repeating context, losing track of earlier decisions, or working at cross-purposes. The authors frame this as a structural gap in how human-agent systems are currently designed, not just a UI inconvenience.

## What makes the system agentic

The paper studies MalleableSpace, a prototype built around a canvas that holds heterogeneous "units" — notes, text, PDFs, webpages, images, and videos — connected by labeled relationships and grouped into "Frames." Agent behavior isn't single-shot text generation: when a person issues a request through an "Agent Node," the system has to decide which nearby, connected, or co-located units are relevant, inspect them, and then — in "Agent mode" — actually modify unit content, edit relationships, and reorganize parts of the canvas, rather than just replying in a chat box. The built-in agent is reportedly based on an existing LLM agent framework ("pi-agent," not independently confirmed), so it is carrying out multi-step, tool-using, environment-modifying actions on a persistent workspace, not producing one isolated response.

## How humans and the AI agent collaborate

The central idea is that humans and the agent don't just exchange messages — they jointly build and revise a shared **Work Representation**: a structured, visible, editable organization of the project's documents, questions, goals, and operations. Both parties can read this structure to decide what to do next, and both can change it. The authors describe this as a two-way relationship: representation organizes action, and action (by either the human or the agent) in turn reshapes the representation.

## What role the human plays

The human arranges and curates the canvas, defines Frames and relationships between units, issues requests to the agent through Agent Nodes, and — critically — reviews whatever the agent changed. According to the available excerpts, users could keep or revert any edit the agent made to content or relationships, which is the paper's built-in mechanism for human oversight of agent-driven changes. Over the three-month field study, participants also evolved their own habits for how much structure to impose and when.

## What role the AI agent plays

The agent inspects the units it's been given access to (nearby, connected, or Frame-co-located with the request), reasons about them, and can both answer requests and directly edit the workspace: revising the content of existing units, changing relationships between them, and reorganizing how units are grouped. This goes beyond "the agent writes text I paste in somewhere" — the agent is described as acting on the same persistent representation the human is working in.

## How control, initiative, and decisions are shared

This is best described as **shared, reviewable control over a common artifact**: the human sets up and curates the Work Representation and can request agent help at any point; the agent can make consequential, structural changes to that representation (not just append outputs); and the human retains a review-and-revert checkpoint over what the agent changed. The authors' comparison of 58 prior systems found that most existing tools let agents *add* outputs locally (e.g., append a new note) but far fewer let agents *reorganize* existing structure, and fewer still supported agent-driven changes with lasting consequences for the representation — positioning MalleableSpace's deeper read/write access as a deliberate departure from the norm.

## The paper's main idea

**The authors' claim:** generative-AI knowledge work needs an explicit, shared, and malleable "Work Representation" — not just a conversation log — as the medium through which both humans and agents organize, interpret, and act on a project, and this representation must itself be revisable by both parties as understanding of the work evolves. They develop this as a conceptual model (grounded in analysis of 58 related systems) and instantiate it in a working prototype, MalleableSpace, to see how it holds up in real, sustained use.

## How the approach works

MalleableSpace is implemented as an Electron desktop application with local, per-Space persistence. Its canvas hosts mixed-type units (notes, PDFs, webpages, images, videos) that users can position, group into Frames, and connect via labeled edges. When a person invokes the agent through an Agent Node, the system scopes the agent's visibility to units that are spatially nearby, explicitly linked, or grouped in the same Frame, and the agent can then read, answer about, or (in Agent mode) directly revise those units and their relations. Changes the agent makes are inspectable and reversible by the user.

## Human study or evaluation design

The authors' empirical grounding is a **three-month longitudinal field deployment** of MalleableSpace with real users, rather than a short lab task. This is a formative, qualitative field study (not a controlled A/B experiment with a baseline condition), aimed at observing how representational structure, agent involvement, and personal workflows actually evolve over sustained real-world use — complementing the conceptual model built from the 58-paper literature comparison.

## Participants and study setting

**Seven experienced agent users** took part in the three-month deployment. Beyond "experienced agent users," further demographics (occupation, domain, recruitment method) were **not available** from the sources used for this summary — check the full paper for details before citing.

## Experiments or benchmarks

- A **structured comparison of 58 related human-agent and knowledge-work systems**, used to characterize how (and how little) existing tools support agents reorganizing shared representations versus merely appending outputs to them.
- A **three-month longitudinal field study** of the MalleableSpace prototype with seven participants, used to observe real, sustained human-agent use rather than short, artificial tasks.
- No standardized public benchmark or dataset is involved; this is a systems/design-research paper rather than a benchmark paper.

## Main results

**As reported in the available excerpts, not independently re-verified against the primary PDF:**
- Across the 58 compared systems, agent-driven changes that *reorganize* existing representation structure (versus simply adding new content) were substantially less common, and changes with *lasting structural consequences* for the representation were rarer still — a gap the authors position MalleableSpace as addressing.
- In the field deployment, participants' use of representational roles and organization reportedly developed and shifted over the three months as they worked, rather than staying fixed from day one.
- The authors describe refining their conceptual model based on these field observations — i.e., the study fed back into the Work Representation / Work Environment framework itself, not only into the prototype's feature list.

## Effects on human performance, trust, workload, safety, or decision quality

*Based on the available excerpts, not a full read of the paper:* the study does not appear to report standardized, quantitative measures of trust, workload (e.g., NASA-TLX), task performance, or decision quality — the evaluation is qualitative and observational, tracking how participants' representational practices and agent-delegation habits changed over three months of real use. The clearest human-related signal surfaced in the excerpts is behavioral and structural (how people organized and re-organized their work, and how much they let the agent restructure versus only append), rather than a measured outcome like error rate or satisfaction score. If the full paper reports additional quantitative measures, they were not found in the sources used here, and this should be treated as an open item to confirm against the primary PDF.

## What is genuinely new

*Authors' framing, as surfaced in the sources used here:* most human-agent knowledge-work tools treat the agent's contribution as something to append onto existing material (a new note, a new paragraph), while leaving the deeper organization of the work to the human. This paper's distinct contribution is (1) naming and modeling this gap explicitly via a 58-paper comparison, and (2) building and field-testing a system where the agent is given — and humans can review/revert — real authority to reorganize the shared representation itself, not just add to it, and tracking what happens when real users live with that arrangement for months rather than minutes.

## Limitations and open questions

- *My interpretation:* seven participants over three months is a genuine longitudinal commitment for a design study, but it is still a small, self-selected sample of "experienced agent users," so findings about how representational practices evolve may not generalize to novice users or to teams (versus individuals).
- The evaluation is qualitative/formative rather than a controlled comparison against a baseline (e.g., a plain chat interface or a non-malleable canvas), so the paper cannot isolate how much of any benefit comes specifically from agent-driven reorganization versus the canvas/Frame interface itself.
- No quantitative trust, workload, or performance metrics were found in the sources used — it's unclear whether the authors view this as future work or out of scope for this paper.
- The review-and-revert mechanism for agent edits is described as the paper's safeguard against unwanted structural changes, but the excerpts used here don't report how often participants actually needed to revert agent actions, which would be a useful indicator of how well-calibrated the agent's reorganization behavior was in practice.

## Practical implications

*My interpretation, following the authors' own stated motivation:* builders of agent-based productivity tools (research assistants, planning tools, writing environments) might consider giving agents real, reviewable write-access to the *structure* of a shared workspace — not just the ability to append new content — if they want agents to meaningfully participate in organizing long-running, multi-session projects. The paired human review/revert step is presented as the key safety valve that makes this deeper agent authority tolerable.

## Why you should care

Most discussions of human-AI collaboration focus on what the agent says or does in a single turn. This paper asks a quieter but arguably more consequential question: what should the *shared record of the work itself* look like, and who gets to change its structure? Its three-month field study is a reminder that the interesting effects of giving agents more structural authority over shared work may only show up over sustained, real use — not in a 20-minute lab task — and that a deliberate human review-and-revert step may be what makes that authority workable rather than risky.
