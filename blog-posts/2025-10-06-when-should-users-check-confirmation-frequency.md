# When Should Users Check? Modeling Confirmation Frequency in Multi-Step Agentic AI Tasks

**Authors:** Jieyu Zhou, Aryan Roy, Sneh Gupta, Daniel Weitekamp, Christopher J. MacLellan (Georgia Institute of Technology, Teachable AI Lab)
**Publication date:** 2025-10-06 (arXiv id 2510.05307, v1, cs.HC; camera-ready v3 posted 2026-05-07)
**Venue:** ACM CHI Conference on Human Factors in Computing Systems (CHI 2026), DOI 10.1145/3772318.3790655
**Paper link:** https://arxiv.org/abs/2510.05307
**Code link:** Not available (no repository confirmed from sources used)
**Project page:** Not available
**Date added:** 2026-09-04

> **A note on sourcing:** arXiv itself was unreachable from this research session's network (the fetch tool is blocked for that domain), so this summary is built from web-search-grounded excerpts of the paper's abstract, HTML body, and the CHI proceedings listing rather than a direct PDF read. Facts below reflect what those excerpts report; anything not confirmed is marked "not available," and interpretive statements are labeled as such.

---

## The problem the paper addresses

Picture an AI assistant that can carry out a whole multi-step chore for you — reorganize a folder of files, fill out a multi-page form, tidy up a virtual kitchen — and only shows you the result at the very end. That's how most agentic AI systems work today: they run autonomously and ask for your sign-off once, at the finish line. The paper's starting observation is that this "confirm-at-end" habit is **brittle**: if the agent makes a mistake early on, that mistake can cascade through every later step, and by the time you notice at the end, undoing it may mean starting over. The opposite extreme — asking you to approve every single step — avoids that trap but turns supervision into tedious, constant babysitting. Nobody has had a principled way to decide *when*, during a long agent run, a human should actually be interrupted to check in.

## Why this problem matters

This is a version of the classic oversight dilemma for autonomous systems: too little checking and small errors snowball into big failures; too much checking and the "assistant" becomes more work than doing the task yourself. As agentic AI moves into everyday tools — coding agents, computer-use agents, workflow automation — the placement of confirmation checkpoints stops being a minor interface choice and becomes the thing that determines whether people can actually trust and efficiently use these systems. Get it wrong, and users either get burned by silent cascading errors or abandon the agent because it's more exhausting to supervise than to do the job by hand.

## What makes the system agentic

The systems studied here are LLM-based agents that autonomously execute multi-step tasks across several application domains — the paper describes an "Office" domain, a "Daily Life" domain, a "Virtual Environment" domain, and a "Mixed Workflow" domain (exact task content beyond these labels is not confirmed from the sources used). The agents plan and carry out sequences of actions toward a goal, can make mistakes partway through, and are evaluated specifically as agents completing real multi-step jobs — not as a single question-and-answer exchange.

## How humans and the AI agent collaborate

The core of the paper is a **checkpoint-based confirmation system**: instead of confirming only at the end or at every single step, the agent pauses at a small number of *model-selected* points during its run to ask the human to check in. If the human's check reveals a problem, they diagnose it and correct or redo the affected step(s) before the agent continues. This is a direct, hands-on collaboration pattern — the human isn't just reviewing a finished product, they're periodically pulled into the loop at moments the system judges to be worth interrupting for.

## What role the human plays

In the study, participants played the role of a supervisor monitoring an AI agent's progress on a task. When a confirmation checkpoint came up, they inspected what the agent had done, decided whether it was correct, and — if not — diagnosed the error and corrected or redid the problematic step before letting the agent proceed. The authors describe this recurring behavior pattern as **Confirmation → Diagnosis → Correction → Redo (CDCR)**, identified from a smaller formative study before being used to inform the main system design.

## What role the AI agent plays

The agent autonomously executes the assigned multi-step task, occasionally making errors along the way (as designed into the study), and pauses execution at checkpoints determined by the researchers' underlying scheduling model rather than at fixed, arbitrary intervals.

## How control, initiative, and decisions are shared

Authority is split by design: the agent keeps the initiative to act by default, but the **system — not the human, and not a fixed rule — decides when to hand control back** for a check-in, based on a cost calculation about the value of catching an error now versus the cost of interrupting the user. The human then exercises full authority within that checkpoint (diagnose, correct, resume). This is a form of *system-scheduled, human-executed* shared control, distinct from both "human decides when to check" and "always check every step."

## The paper's main idea

**Claim by the authors:** the right way to think about confirmation placement is as a **minimum-time scheduling problem** — weighing the time cost of interrupting the user against the time cost of letting an undetected error run further before it's caught and has to be rolled back. Based on the CDCR pattern observed in their formative study, they built a decision-theoretic model that computes where to place confirmation checkpoints to minimize total expected time, rather than confirming at a fixed cadence.

## How the approach works

The formative study (8 participants) was used to characterize how people actually notice and fix agent errors — surfacing the CDCR pattern as the typical unit of "checking work." The authors then built a decision-theoretic model treating checkpoint placement as an optimization over expected task time, balancing the cost of an interruption against the expected cost of a missed error compounding. This model was compared against two standard baselines: confirm-at-end (the industry-standard pattern) and confirm-every-step.

## Human study or evaluation design

**Demonstrated in the paper:** a two-part, real-participant evaluation — (1) a formative study with 8 participants used to derive the CDCR behavior pattern, followed by (2) a **within-subjects study with 48 participants**, who monitored AI agents and repaired the agents' mistakes while the agents executed multi-step tasks, comparing the model-based intermediate-confirmation approach against confirm-at-end and confirm-every-step baselines.

## Participants and study setting

56 real human participants in total (8 formative + 48 main study). Specific demographic details, recruitment channel, and compensation were not confirmed from the sources used for this summary. The main evaluation used a within-subjects design across the paper's four task domains (Office, Daily Life, Virtual Environment, Mixed Workflow), with errors evidently injected into agent runs so that participants had real mistakes to catch and fix.

## Experiments or benchmarks

No public benchmark was used; the tasks and error-injection setup appear to be custom-built for this study across the four domains described above. The comparison conditions were: confirm-at-end, confirm-every-step, and the paper's decision-theoretic intermediate-confirmation model.

## Main results

**Demonstrated in the paper:**
- **81% of participants preferred** the model-based intermediate-confirmation approach over the confirm-at-end approach used by existing systems.
- Task completion time was **reduced by 13.54%** relative to the baseline(s) (exact baseline-by-baseline breakdown not confirmed from sources used).

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper:** a clear preference result (81%) and a measured efficiency gain (13.54% less task completion time) when people supervised agents using model-scheduled checkpoints instead of confirm-at-end. **Not confirmed from the sources used:** whether the study also measured standardized trust or workload instruments (e.g., NASA-TLX), error-catch rate differences, or long-term reliance effects — these specific quantitative breakdowns could not be verified. **Our interpretation:** a strong preference plus a meaningful time savings is a solid signal that smarter checkpoint placement reduces supervision burden without the brittleness of confirm-at-end, but the published excerpts available to us don't let us confirm whether it also changed how many real errors were actually caught (accuracy of oversight), as opposed to purely how participants felt about the process and how fast they finished.

## What is genuinely new

- A concrete behavioral pattern (**CDCR**) describing how people actually check and repair agent work, derived from real observation rather than assumed.
- Reframing "when should the agent ask for confirmation" as a **minimum-time scheduling / decision-theoretic optimization problem**, rather than a fixed heuristic (every step, or only at the end).
- A real, within-subjects human study (48 participants) directly comparing this model-based approach against both standard industry patterns, with a quantified time savings and a strong stated preference.

## Limitations and open questions

- **Authors' own stated limitations (as reported in search excerpts):** the model currently operates at the *population* level rather than being personalized to individual users' checking speed or risk tolerance; it doesn't yet incorporate multi-dimensional cost functions (e.g., money, emotional cost, safety risk) beyond time; and the authors flag that future systems should consider mandatory checkpoints for high-stakes, hard-to-reverse actions regardless of what the time-cost model recommends.
- The tasks were custom-built across four domains rather than a shared public benchmark, and specific participant demographics/recruitment were not confirmed from the sources used, which limits our ability to assess generalizability.
- It is not confirmed whether the study measured decision accuracy (did the model-based schedule help people catch *more* real errors, not just finish faster) or trust/workload with standardized instruments.

## Practical implications

This work offers a concrete, tested design pattern for anyone building agentic AI products — coding agents, computer-use agents, workflow or RPA-style automation: don't default to a single end-of-task confirmation, and don't force users into confirming every step either. Instead, treat checkpoint placement as an optimization problem that weighs interruption cost against the cost of letting an error propagate, and consider reserving hard-coded mandatory checkpoints for genuinely high-stakes actions.

## Why you should care

Confirm-at-end is the default in most agentic AI tools shipping today, and this paper is direct evidence that this default is a real cost to users — not just a hypothetical risk. A tested alternative (model-scheduled intermediate checkpoints) was preferred by a large majority of real participants and measurably faster in a controlled study. For a research agenda centered on human–AI collaboration, this is a rare case of a genuinely human-centered mechanism for shared control — where the system decides *when* to hand back control, and the human decides *what to do* with it — evaluated with real people rather than left as a design suggestion.
