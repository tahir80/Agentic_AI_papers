# When an AI Lab Team Runs the Experiment, Who Made the Call? Auditing Human–Agent Science at a Synchrotron

**Paper title:** Auditable Human–Agent Teams for Autonomous X-ray Experimentation
**Authors:** Gunik Luthra, Ronald J. Pandolfi, Benjamin T. Diroll, Ricky Ronquillo, Ruipeng Li, Christopher B. Murray, Marcus M. Noack, Kevin G. Yager, Esther H. R. Tsai
**Publication date:** 2026-11-06 (arXiv v1)
**Venue:** arXiv preprint, cs.AI (cross-listed cs.MA); peer-reviewed venue not confirmed
**Paper link:** https://arxiv.org/abs/2611.12933
**Code link:** https://github.com/CFN-softbio/VISION-CC
**Project page:** Not available (builds on the earlier "VISION" project at Brookhaven National Laboratory's Center for Functional Nanomaterials, https://www.bnl.gov/newsroom/news.php?a=122449)
**Date added:** 2026-11-13

> **A note on sourcing:** this session's network access to arXiv and its mirrors was blocked, so the full PDF could not be opened directly. This summary is built from the paper's abstract, HTML-version excerpts, and related institutional coverage of the predecessor project, cross-checked across several searches. The paper itself is a freely available, open-access arXiv preprint with openly released code and sample data. Numbers and quotes below are reported as they surfaced in those excerpts; anything not independently confirmed is marked accordingly. Please check the arXiv preprint directly before citing specifics.

---

## The problem the paper addresses

Scientific instruments like synchrotron X-ray beamlines are starting to be run not just by humans, and not just by a single AI assistant, but by *teams* of AI agents that plan measurements, analyze data, and decide what to do next — while a human scientist sets the goals and can step in at any time. That raises a question that didn't used to need an answer: when something goes right or wrong during an experiment, who actually decided it? The human? One particular agent? A chain of agents handing off to each other? This paper is about building a system where that question has a traceable answer.

## Why this problem matters

If an autonomous experiment produces a great result — or wastes expensive beamtime — "the AI did it" isn't good enough. Scientists, lab managers, and funders need to know whose judgment to trust, whose process to fix, and whether the human was still meaningfully in control. This is the same problem as a flight-data recorder on an airplane: you want to reconstruct exactly how a decision was reached, not just what happened. Without that, it's hard to improve the system responsibly or to know when human oversight is actually working.

## What makes the system agentic

The system, called **VISION-CC** (Virtual Scientific Companion with Claude Code), is built on Claude Code's "Agent Teams" feature. It isn't a single chatbot answering questions — it's a coordinated team of AI agents ("cogs") that plan and execute real, multi-step scientific work: controlling a synchrotron beamline, running X-ray scattering measurements on physical nanoparticle samples, analyzing the resulting data, and deciding what measurement to run next, over hours of continuous operation. One agent (reportedly a "Team Lead") coordinates the others, and a dedicated "Audit-cog" keeps a full transcript of everything everyone — human and agent — says and does.

## How humans and the AI agent collaborate

A human scientist sets the high-level scientific objective for the experiment and can change that objective mid-experiment as results come in. Rather than issuing one instruction and walking away, the scientist can message individual agents in the team directly — not just the team as a whole — while the agents carry out the actual measurement-analysis-decision loop largely on their own. Every exchange, human-to-agent and agent-to-agent, is logged by the Audit-cog, which the researchers later used to reconstruct who made which calls.

## What role the human plays

The human is the scientific director: defining and revising the goals of the experiment, communicating directly with specific agents when needed, and occasionally correcting course. According to the reported findings, human involvement wasn't just supervisory in name — the audit trail shows the human made genuine, substantive contributions to decisions and corrections alongside the lead agent, not merely a rubber-stamp approval role.

## What role the AI agent plays

The agent team runs the experiment loop itself: translating scientific intent into beamline operations, collecting X-ray scattering data, analyzing it, and deciding the next measurement step, largely autonomously between human check-ins. The Audit-cog's separate job is bookkeeping for accountability, not experimentation — it exists purely to make the team's and the human's reasoning traceable after the fact.

## How control, initiative, and decisions are shared

This is shared control with the human holding goal-setting authority and the agents holding execution authority day-to-day. Initiative flows both ways: the human can jump in and redirect at any point (and did), while the agents act independently between those interventions. The paper's distinctive move is to treat this division of labor as something to be *measured* after the fact, via the audit log, rather than assumed from the system's design.

## The paper's main idea

**The authors' claim:** that autonomous agent-run science needs to be *auditable* — the full record of human–agent and agent–agent interaction should be preserved so that decision provenance (who decided what, and why) can be reconstructed, and that this kind of audit can surface practical lessons about how human and AI effort actually divided up during real experiments.

## How the approach works

The team built VISION-CC on top of Claude Code's multi-agent "Agent Teams" infrastructure, assigning different agents to different roles in the experimental workflow (measurement, analysis, decision-making, and auditing), with the human scientist able to address any agent directly. The reported case study ran the system on **transmission small-angle X-ray scattering (SAXS)** experiments on nanoparticle superlattice samples at the NSLS-II 11-BM CMS beamline (Brookhaven National Laboratory), across **three beamtime sessions totaling more than 50 active hours and two scientifically relevant samples**. Afterward, the researchers used the Audit-cog's transcripts to reconstruct, turn by turn, which decisions and corrections came from the human versus from which agent.

## Human study or evaluation design

This is best described as a **real-world operational case study**, not a controlled experiment with multiple randomly assigned participants or a comparison condition. The "study" is the audit itself: a retrospective, transcript-based analysis of how one human scientist and the VISION-CC agent team actually behaved and divided decisions across real beamtime. *This is a limitation to flag clearly: the paper does not appear to report a multi-participant human-subjects study with statistical comparisons — it is a single deployment, carefully instrumented and audited.*

## Participants and study setting

As far as could be confirmed, the human side of the collaboration involves (at minimum) one scientist-operator working with the VISION-CC agent team in a real scientific facility — not a lab simulation and not crowdworkers. Broader recruitment or demographic details are **not available** from the sources used here, and it's unclear whether multiple scientists across the three sessions contributed, or the same person throughout.

## Experiments or benchmarks

There is no public benchmark here in the usual sense. The "experiment" is the real scientific workflow itself — three live beamtime sessions running SAXS measurements on nanoparticle superlattices — plus the audit analysis of the resulting interaction logs. The authors released, via GitHub, the VISION-CC agent-team code, an "audit codebook" defining the categories and prompts used for the analysis, a subset of SAXS data frames from one experiment, and a sanitized excerpt of the audit ledger itself — which is unusually transparent for this kind of operational case study.

## Main results

**Reported by the authors (as surfaced in search excerpts):**
- The agent team sustained closed-loop operation (measure → analyze → decide → repeat) across the three sessions without the human needing to drive every step.
- When the audit reconstructed where errors occurred, the human's errors were mostly described as "slips" — small things like misreading an instrument status or giving an inaccurate estimate — rather than substantive scientific misjudgments.
- The human rarely needed to personally apply a fix; the one human-initiated fix reported in the first experiment concerned the software bridge connecting the agent team to the beamline hardware, not a scientific decision.
- Both the lead agent and the human are reported to have made significant, genuine contributions to corrections and decisions over the course of the sessions.
- The authors state that using the agent team reduced the engineering effort needed to run these experiments, compared with doing so without it.

*Exact statistics (error counts, time breakdowns, inter-rater agreement on the audit coding, etc.) were not independently verified in this session — treat the bullet points above as reported findings, not verified figures.*

## Effects on human performance, trust, workload, safety, or decision quality

The clearest demonstrated effect is on **accountability and traceability**, not on classic human-factors measures like trust surveys or workload scales — this paper doesn't appear to run those. What it does show is that it's *possible* to reconstruct, after a real autonomous experiment, which decisions were human-driven versus agent-driven, and that the human's role was substantive (not just nominal) even though agents handled most of the moment-to-moment work. No controlled comparison (e.g., audited vs. non-audited operation, or with vs. without human override ability) is reported.

## What is genuinely new

*Authors' framing, not independently assessed:* applying a full, dedicated audit-agent architecture — logging every human–agent and agent–agent exchange specifically to support after-the-fact decision-provenance analysis — to a real, physical scientific instrument run by a multi-agent coding-agent team, and then actually using that log to characterize how work and correction responsibility were really split between the human and the agents.

## Limitations and open questions

- *My interpretation:* this is a single deployment / case study rather than a multi-subject experiment, so findings about human behavior (e.g., "errors were mostly slips") describe this specific scientist and setup, and may not generalize to other operators, labs, or instrument types.
- The system depends on a particular commercial product (Claude Code's Agent Teams), which may make independent replication or adaptation to other agent frameworks harder.
- There's no reported comparison against a non-audited or non-agentic baseline, so it's hard to say how much the *auditability* specifically — versus the agent team generally — changed outcomes.
- Full statistical detail, inter-coder reliability for the audit categories, and broader participant information were not available from the sources used to write this summary.

## Practical implications

*My interpretation:* for labs or organizations deploying agent teams to run real-world processes — scientific experiments, but plausibly other operational settings too — this paper is a template for building accountability in from the start: give every agent a role, keep one agent (or process) whose sole job is logging for audit, and treat "who decided this" as a question you can answer, not a mystery you shrug off. That matters most exactly where human oversight of autonomous or semi-autonomous agents is the whole point of keeping a human in the loop.

## Why you should care

As AI agent teams take on more real operational work — not just answering questions but running instruments, pipelines, and processes — the ability to reconstruct *who actually decided what* becomes a basic safety and trust requirement, not a nice-to-have. This paper is a concrete, real-world (if small-scale) demonstration that such auditability is achievable today, using off-the-shelf agent infrastructure, on a genuinely autonomous scientific process. It's a case study, not a controlled trial — but it's a useful existence proof that "human oversight" doesn't have to mean "trust us."
