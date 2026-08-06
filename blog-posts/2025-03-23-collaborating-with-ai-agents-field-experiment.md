# What Actually Happens When You Put an AI Agent on a Human Team

**Paper title:** Collaborating with AI Agents: Field Experiments on Teamwork, Productivity, and Performance
**Authors:** Harang Ju (Johns Hopkins Carey Business School), Sinan Aral (MIT Sloan School of Management)
**Publication date:** 2025-03-23 (arXiv v1); revised 2025-08-15 (v2) and 2026-02-05 (v3)
**Venue:** Working paper, MIT Initiative on the Digital Economy (not confirmed as peer-reviewed at a conference/journal from available sources)
**Paper link:** https://arxiv.org/abs/2503.18238
**Code link:** Not available (no public repository found)
**Project page:** Not available (the "Pairit" experimentation platform is described in the paper but no public project site was found)
**Date added:** 2026-08-06

*Transparency note: this session's network policy blocked direct fetches to arxiv.org and every other external host tested (including a plain connectivity check to a non-arXiv site), so this summary was not built from a direct read of the primary PDF. It is compiled from the paper's abstract and multiple independent, cross-checked search-engine-surfaced excerpts (including MIT Sloan and MIT Initiative on the Digital Economy coverage of the study). Several secondary sources report slightly different specific numbers for the same quantities — likely reflecting differences between the v1 and v3 versions of the paper — and those discrepancies are flagged explicitly below. Readers should verify exact figures against https://arxiv.org/abs/2503.18238 before citing them elsewhere.*

---

## The problem the paper addresses

Companies are increasingly told to put AI "agents" — not just chatbots you ask one-off questions, but systems that can act inside a shared workspace — directly onto teams alongside human employees. But almost all of the evidence for "AI makes people more productive" comes from studies where one person uses one AI tool by themselves. This paper asks a more specific and less-studied question: when an AI agent is dropped into an actual *team* workflow — sending messages, writing copy, editing images, alongside real coworkers on a real deliverable — what actually changes about how the team works, and does the output get better?

## Why this problem matters

Whether AI helps or hurts a team isn't just about how smart the underlying model is — it's about how work gets divided, who talks to whom, and what people stop doing themselves once an AI teammate can do it for them. Getting this wrong at scale (across a whole marketing department, a whole newsroom, a whole engineering org) could mean shipping worse work faster, or missing where AI actually helps versus where it quietly makes something worse (here, the paper's account suggests images). Understanding the mechanism — not just "productivity went up X%" but *why* — is what lets organizations design better human-AI workflows instead of guessing.

## What makes the system agentic

The AI "teammate" in this study is not a single-turn chatbot. According to the paper, it operates inside a shared, real-time collaborative workspace called **Pairit** (an experimentation platform the authors built, previously referred to in an earlier draft as "MindMeld") and can take the same range of actions a human teammate can: sending chat messages, drafting and editing ad copy, and generating images (reportedly by calling DALL·E 3 as a tool). It acts across a full multi-step work session rather than answering a single prompt, coordinates with a human partner toward a shared deliverable, and is evaluated as a working teammate — not as a standalone language model — which is why it fits this repository's definition of agentic AI.

## How humans and the AI agent collaborate

Participants were randomly assigned into two-sided teams working in real time inside Pairit's chat-and-editing workspace: some teams paired two humans together, others paired one human with the AI agent. Both team types had access to the same workspace features — real-time chat, synchronized text editing, image editing, and the ability to generate new images — and worked on the same task under the same time constraints, so the only systematic difference between conditions was whether the "other" teammate was human or AI.

## What role the human plays

The human is a working teammate with full access to the shared workspace: proposing ideas over chat, writing and revising ad copy, and directly editing images. According to the paper's reported findings, when paired with an AI teammate, humans shifted part of their effort — communicating more and doing less hands-on text editing themselves — rather than the AI simply replacing their work outright.

## What role the AI agent plays

The AI agent — built on a GPT-4o snapshot according to reported methodology details — acts as a full teammate rather than a tool the human operates: it can chat, propose and write ad copy, edit copy, and generate images on its own initiative within the shared workspace, working toward the same shared deliverable as its human counterpart.

## How control, initiative, and decisions are shared

This is a **peer-teammate** arrangement rather than a supervisor/assistant or approval-gated setup: both the human and the AI agent can initiate messages, propose content, and make edits inside the same shared workspace, with no reported mechanism requiring the human to approve each AI action before it takes effect. Reported findings suggest the *balance* of who does what shifted — humans reportedly communicated more and left more of the direct content editing to the AI — but initiative was not formally restricted to one party.

## The paper's main idea

**Authors' claim:** AI agents don't uniformly improve every part of collaborative work — they reshape *how* teams divide labor, and the resulting gains (and losses) are uneven across task types. The paper frames this as a "jagged frontier" of AI-agent capability within a single collaborative task: according to the abstract, human-AI teams produced better *text* output while human-human teams produced better *image* output, rather than AI improving (or hurting) everything at once.

## How the approach works

The authors built Pairit specifically to run this kind of experiment: a controlled but realistic collaborative workspace where teams (human-human or human-AI) jointly produce marketing ad content — chat, shared text editing, shared image editing, and image generation — while the platform logs every message and edit. This design lets the researchers compare not just final output quality but the *process* by which teams of each type reached their output.

## Human study or evaluation design

**Authors' claim, based on the abstract:** a randomized field experiment. Participants were randomly assigned to human-human or human-AI teams and asked to produce real display ads for a real client (a think tank) over a working session, with output evaluated via independent human ratings; a subset of the ads produced were then run as an actual paid ad field experiment on X (formerly Twitter).

## Participants and study setting

**Reported in the abstract:** 2,234 participants (one secondary source states 2,310, a discrepancy this summary could not resolve without the primary PDF), reportedly recruited via Prolific, randomly assigned to human-human or human-AI teams, producing a reported 11,024–11,138 ads in total for a real think tank's year-end report campaign. This is a real-participant, real-deliverable field experiment — not a simulated study, and not a lab exercise with throwaway output.

## Experiments or benchmarks

There is no academic benchmark here; the "test" is the field experiment itself, plus a secondary real-world field test: a sample of the ads produced by each team type was run as live paid advertising on X, reportedly gathering approximately 5 million impressions, letting the authors observe real click-through and cost-per-click outcomes rather than only lab-based quality ratings.

## Main results

**Demonstrated / authors' reported findings:**
- Human-AI teams reportedly produced about 50% more ads per worker than human-human teams.
- Human-AI teams reportedly produced higher-*text*-quality ad copy; human-human teams reportedly produced higher-*image*-quality output — the paper's central "jagged frontier" finding.
- In the live X field test, higher image quality (human-human teams) reportedly improved cost-per-click, while higher text quality (human-AI teams) reportedly improved click-through and view-through rates — reportedly netting out to broadly similar overall ad performance between the two team types, despite the different *kind* of quality each produced.
- Team communication reportedly increased and humans reportedly did substantially less direct hands-on text editing when paired with an AI agent — secondary sources give different specific percentages for this shift (e.g., roughly 60–70% less direct editing in some reports vs. roughly 20% in others), which this summary cannot resolve without the primary PDF; the qualitative direction (less direct editing, more delegation of drafting to the agent) is consistent across sources even where exact figures differ.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the paper reports a measurable shift in *how* humans spent their effort — communicating more, editing less by hand — when working with an AI teammate rather than a human one, alongside a reported increase in output volume per worker. **Not measured, as far as this summary could confirm:** standardized trust, workload (e.g., NASA-TLX), or safety metrics; the study's human-outcome evidence is behavioral (what people did) and productivity/quality-based (what got produced), not self-reported trust or workload scores.

## What is genuinely new

Most human-AI collaboration studies compare a single person's output with vs. without an AI tool. **Authors' claim (and this summary's assessment):** this paper is distinctive in running a real, randomized field experiment that puts an AI agent into the *same structural role* as a human teammate — same workspace, same available actions, same task — which lets the researchers isolate how team composition itself (not just AI availability) changes both the process (communication, division of labor) and the outcome (uneven quality gains across text vs. images), and then validates the output quality difference with a real paid-advertising field test rather than lab ratings alone.

## Limitations and open questions

- **Authors' own caveat (reported):** findings come from a marketing/advertising context specifically; the authors note the pairing/collaboration dynamics observed here may not generalize to other collaborative task types such as coding or data analytics.
- **Numeric discrepancies across secondary sources:** this summary found inconsistent figures across independent search results for participant count (2,234 vs. 2,310), total ads produced (11,024 vs. 11,138), and the size of the communication/editing shift — likely reflecting differences between paper versions (v1 vs. v3) rather than errors, but unresolved without direct access to the current primary PDF.
- **No confirmed standardized trust/workload measurement:** it's unclear from available sources whether the paper measured subjective trust or perceived workload, as opposed to only behavioral and output-quality metrics.
- This summary could not independently verify the full methodology, discussion, or exact statistics against the primary PDF due to network restrictions in the environment that produced it.

## Practical implications

If the reported findings hold up on direct reading, the practical takeaway for organizations deploying AI teammates (not just AI tools) is: expect AI agents to change *who does what* within a team, not just how fast the team works — and expect that change to help some parts of the output (here, text) more than others (here, images). That argues for evaluating AI-agent teammates task-by-task rather than assuming a single blanket productivity multiplier, and for specifically watching for capability gaps (the "jagged frontier") that a team's usual quality-control process might not catch if everyone assumes the AI teammate is uniformly as good as a human one.

## Why you should care

This is one of the more rigorous field tests to date of what happens when an AI agent is treated as an actual teammate — with its own initiative inside a shared workspace — rather than a tool one person operates alone, and it's validated with real paid advertising outcomes rather than lab ratings alone. Its central claim, that AI's benefit to a team is uneven across task types even within one project, is a concrete, human-tested counterpoint to the more common "AI just makes teams faster" narrative, and a useful reminder that adding an AI teammate changes team dynamics in ways worth measuring directly rather than assuming.

---

*Author's note on selection: this paper was compared against several other 2026 candidates, including a CHI 2026 platform paper for running human-agent CSCW experiments (strong theoretical fit but a smaller-scale demonstration study, ~16-32 participants across sub-studies), a short workshop paper documenting declining human scrutiny of AI-agent-authored code over time (highly relevant to human oversight/trust calibration, but a brief 5-page observational study), a large-scale observational mining study of human-AI code review conversations (strong agentic fit but topically close to two code-review papers already in this repository), a 48-participant study of humanlike vs. machinelike interaction cues in AI-assisted writing (weak on the agentic-AI criterion — closer to a proactive suggestion tool than a goal-pursuing multi-step agent), and a very recent (July 2026) multi-agent deliberation benchmark that had no real human participants at all. This paper was selected as the strongest candidate on balance: a real, randomized field experiment with over 2,000 real participants and real deliverables, an AI agent acting with genuine multi-step initiative inside a shared workspace, and both lab-based and live-market (paid social ad) validation of its findings — even though its arXiv v1 predates the last-30-days window; no comparably rigorous very-recent candidate with a real human-participant study was found in this run's search.*
