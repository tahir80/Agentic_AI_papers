# Long-Horizon AI Research for Grothendieck Constant: A Case Study in Human–AI Mathematical Collaboration

**Authors:** Alan Li, Rahul Saha, Anton Xue, Swarat Chaudhuri, Adam Klivans (UT Austin), Pravesh K. Kothari (Princeton), Raghu Meka (UCLA)
**Publication date:** 2026-08-11 (arXiv v1)
**Venue:** arXiv preprint (cs.AI, cs.CC, cs.HC, math.FA); peer-reviewed venue not confirmed at time of writing
**Paper link:** https://arxiv.org/abs/2608.11195
**Code link:** https://github.com/trishullab/grothendieck-bounds (companion repository hosting scripts, certificates, and numerical outputs behind the math results; not confirmed to include the full AI research harness itself)
**Project page:** Not available
**Date added:** 2026-08-16

> **A note on sourcing:** this session's outbound network access to arxiv.org returned a blocked connection for direct fetches (organization egress policy, not a paywall — the paper is a public arXiv preprint), so this summary is built from cross-checked search-engine excerpts of the paper's abstract, methodology, and reported results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

Most demonstrations of "AI doing research" are short bursts: an agent gets a well-scoped question and produces an answer in one sitting. This paper is about something harder — mathematical research that takes days to weeks, where the "state" of the investigation (partial proofs, dead ends, half-formed conjectures) has to be carried forward across many work sessions, and where progress is slow and uncertain enough that there's rarely a clean reward signal telling the system whether it's on the right track. The authors ask a practical question: how should humans and an AI system actually work together over that kind of long horizon, so the system doesn't need constant babysitting but also doesn't run off unsupervised and unproductively?

## Why this problem matters

Most agentic-AI research is judged on tasks that finish in minutes. But real scientific and engineering problems often unfold over weeks, with humans able to check in only occasionally. If AI systems can't sustain useful autonomous progress over that kind of horizon — remembering what's been tried, incorporating human course-corrections without needing a human at the wheel constantly, and reporting back in a form a human can quickly audit — their usefulness for genuine research is limited to short, well-defined subtasks. Getting the human-AI division of labor right for long-horizon work is a prerequisite for AI being useful in open-ended research rather than only bounded chores.

## What makes the system agentic

The system described is squarely agentic: it pursues a long-running research goal (tightening bounds on a specific mathematical constant), and it does so through many rounds of autonomous multi-step work — proposing mathematical approaches, writing and running code, checking whether results hold, and deciding what to try next — rather than answering a single prompt. It maintains its own memory across sessions (so work doesn't restart from scratch each time), employs an internal verification step to catch its own mistakes, and — according to the reported figures — executed over 240 sessions and more than 2,000 reasoning-model calls across roughly five and a half weeks (June 16 to July 24, 2026) with only intermittent, asynchronous human input. That combination of a standing goal, sustained autonomous multi-step action, persistent memory, and tool use (a coding agent that writes and verifies programs) is what puts it in agentic-AI territory rather than a single long chat response.

## How humans and the AI agent collaborate

The collaboration is asynchronous and non-blocking by design. Rather than a human approving every step or holding a live back-and-forth conversation with the system, the human operators — the paper's own authors — periodically read the system's self-produced progress notes and post steering instructions to a shared file the system checks on its own schedule. The system keeps working in the meantime; it isn't paused waiting on the human. This is a "supervisor who checks in" model of collaboration rather than a "co-pilot in the loop for every action" model.

## What role the human plays

The human operators — domain-expert mathematicians and computer scientists — set the initial research direction, periodically review the system's accumulated progress, and inject redirection, domain intuition, or new leads by writing instructions the system picks up asynchronously. Per the reporting available, they are not approving individual computational steps; their role is higher-level: steering the overall trajectory of a long-running investigation and, crucially, validating that the system's claimed mathematical insights are actually novel and correct.

## What role the AI agent plays

The system does the sustained work between human check-ins: proposing approaches, translating them into executable code via a coding agent (reported to be Claude Code, running Opus 4.7/Fable), running and checking that code, and — importantly — writing up its own progress into a persistent "session report" that serves as the system's long-term memory. This report is what lets the next work session (and the human reviewer) pick up where the last one left off, without re-deriving everything or overflowing the model's working context.

## How control, initiative, and decisions are shared

Initiative sits mostly with the AI system between check-ins — it decides what to try next within the current research direction — while the humans hold direction-setting and validation authority: they can redirect the investigation at any point via the asynchronous steering channel, and they are the ones who ultimately judge whether a claimed result is a genuine mathematical advance. Control is therefore shared on a coarse timescale (steering messages, periodic review) rather than a fine one (no step-by-step approval), which is a distinctive point on the human-AI collaboration spectrum compared to systems that require confirmation before each action.

## The paper's main idea

**Claim by the authors:** with the right collaboration scaffolding — a persistent memory that survives across many work sessions, an internal verification step, and a channel for humans to steer the system asynchronously without halting it — a long-horizon AI research system can make genuine, expert-validated progress on a hard open mathematical problem, and the paper documents both the successes and the friction points of running such a system for real. The companion result: new bounds on the Grothendieck constant, a quantity that has been studied for roughly 70 years.

## How the approach works

The reported architecture divides labor between a reasoning model (which proposes mathematical ideas and strategies) and a coding agent (which implements, runs, and checks those ideas computationally). A file called the "bulletin" is how human operators send steering instructions into the system without stopping it. A separate "session report" file is the system's own running memory — code, partial proofs, and prose explaining the mathematics accumulated so far — so that progress compounds across sessions instead of being lost or having to be re-fed into every new reasoning call. An internal verification protocol is used to check claimed results before they're reported as progress.

## Human study or evaluation design

**Important distinction:** this is not a controlled, multi-participant human-subjects study with recruited participants and standardized measurement instruments (like trust or workload scales). It is a first-person case study / research log: the paper's own authors were the human operators, and the "evaluation" is a detailed account of how the collaboration unfolded over roughly five and a half weeks, including the authors' own reflections on what worked and what didn't when steering the system. Readers should weigh the paper accordingly — it demonstrates a real, extensive, and consequential human-AI collaboration, but not one measured with the kind of controlled experimental design used in HCI user studies.

## Participants and study setting

**Demonstrated in the paper (per available descriptions):** the human operators were the authors themselves — domain-expert mathematicians and computer scientists from UT Austin, Princeton, and UCLA — rather than independently recruited study participants. The setting was the authors' own long-horizon research effort on the Grothendieck constant, run continuously from June 16 to July 24, 2026, comprising more than 240 system sessions and over 2,000 reasoning-model calls.

## Experiments or benchmarks

There is no public benchmark or dataset here — the "experiment" is the single, real research campaign on one hard open problem (bounding the Grothendieck constant), not a repeatable benchmark task with multiple trial runs or comparison systems.

## Main results

**Demonstrated in the paper (per available descriptions):**
- The system-assisted research tightened the known bounds on the Grothendieck constant K_G to **6π/11 ≤ K_G ≤ π/(2·log(1+√2)) − 10⁻⁴**, which pins down the previously unknown tenths digit of K_G as **7** (i.e., K_G ≈ 1.7…).
- The lower-bound argument reportedly takes a different approach from prior work — establishing limits on a class of optimal rounding schemes rather than constructing explicit counterexamples — and the upper bound reportedly comes from the first asymptotic (rather than only low-dimensional) construction of a certain rounding scheme.
- The authors state that the system arrived at insights that domain experts judged to be genuinely novel, not just re-derivations of known results.

## Effects on human performance, trust, workload, safety, or decision quality

The paper does not report a quantified measurement of human trust, workload, or decision quality in the standardized sense used in HCI trust/workload studies — there is no survey instrument, no comparison condition, and no independently recruited participant pool. What it does offer, per the available descriptions, is the authors' own qualitative account of the collaboration process: what kinds of steering were useful, where the system needed human intuition to get unstuck, and how the memory and verification design affected how much oversight was needed. **This is the authors' own interpretation of their experience, not a demonstrated experimental effect on human outcomes measured against a control.**

## What is genuinely new

- A concrete, reusable architecture for long-horizon human-AI research collaboration — asynchronous steering via a "bulletin," persistent cross-session memory via a "session report," and an internal verification protocol — described in enough detail to be a template for other long-horizon AI-assisted research efforts.
- A rare instance of an AI-assisted research effort producing a result (tightened Grothendieck constant bounds) on a problem that has been open for about seven decades, with the paper explicitly framing this as a case study in *how* the collaboration was structured, not just reporting the math result on its own.
- An explicit design stance — voiced by the authors on social media accompanying the release — that the collaboration should be structured to keep the research "fundamentally human," i.e., a deliberate argument against treating this as a demonstration of full automation.

## Limitations and open questions

- **Single case study, not a controlled study:** the "human-AI collaboration" evaluation is the authors' own account of their own process on one problem; there is no comparison against alternative steering designs, no multiple independent research teams, and no standardized measurement of the human side of the collaboration.
- **Generalizability is unconfirmed:** whether this bulletin-plus-session-report architecture works as well for other research domains, other problems, or other human operators (with different expertise or steering styles) is not established by a single case.
- **Peer-review status:** as of this writing, this appears to be an arXiv preprint; a peer-reviewed publication venue was not confirmed.
- We were unable to independently verify additional details (e.g., the exact contents of a "bulletin" message, how disagreements between operators were resolved if more than one was involved, or the full verification protocol) since the full paper could not be fetched in this session — readers who need precise details should consult the arXiv preprint directly.

## Practical implications

For teams considering AI-assisted long-horizon research or engineering work, this paper offers a concrete architectural pattern to borrow: separate the system's persistent "memory" of accumulated progress from the live reasoning process, give humans an asynchronous (not blocking) channel to redirect the work, and build in an internal verification step before treating any claimed result as real progress. The core practical lesson the authors appear to draw is that useful long-horizon autonomy doesn't require choosing between "human approves every step" and "AI runs fully unsupervised" — an asynchronous, periodic-check-in model can let an AI system sustain weeks of autonomous work while still keeping a human's judgment as the final arbiter of what counts as genuine progress.

## Why you should care

This is a case where an agentic AI system's output isn't a benchmark score but a verified new bound on a nearly 70-year-old open mathematical question — and the paper is explicit that this happened through a specific, documented form of human-AI collaboration rather than either full automation or constant human supervision. It's a useful data point for anyone designing agent systems meant to run over long horizons: the interesting design problem isn't just "how capable is the model," but "what memory, verification, and steering scaffolding lets a human stay meaningfully in control of a process they can't watch continuously." Just keep the caveat in view: what's demonstrated here is one detailed, real case, not a controlled study of how this collaboration pattern performs across people or problems.
