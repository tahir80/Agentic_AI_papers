# Trust-Calibrated Code Review: A Participatory Design Study of Review Workflows for LLM-Generated Multi-File Changes

**Authors:** Lo Gullstrand Heander (Lund University), Agnia Sergeyuk (JetBrains Research), Ilya Zakharov, Emma Söderberg, Nikita Mukhortov
**Publication date:** 2026-06-01 (arXiv id 2606.01969, v1)
**Venue:** arXiv preprint; conducted in collaboration with JetBrains. Formal conference/journal acceptance not confirmed in available sources.
**Paper link:** https://arxiv.org/abs/2606.01969
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-07-23

> **A note on sourcing:** arXiv was unreachable from this research session's network (outbound requests to arxiv.org were blocked at the proxy level), so this summary was built from multiple, cross-checked search-engine excerpts of the paper's abstract and indexed HTML text rather than a direct PDF read. The facts below — research questions, method, participant counts, design constructs, and the quoted percentages/means — appeared consistently across independent queries. Anything not confirmed this way is marked "not available" rather than guessed.

---

## The problem the paper addresses

LLM-based coding agents (like AI pair-programming or "agentic" IDE tools) increasingly don't just suggest one line of code — they go off and edit several files at once to implement a feature or fix a bug. But the tools developers use to review that work were designed for a different era: a human writing one focused diff at a time. The paper's starting point is blunt: "no validated end-to-end workflow or IDE tooling design exists" for reviewing these multi-file, agent-generated changes. Developers are stuck reviewing a fundamentally new kind of output with fundamentally old tools.

## Why this problem matters

If review tools don't keep up with what agents can produce, developers face a bad choice: rubber-stamp changes they don't have time to truly verify, or grind through unfamiliar multi-file diffs with no support for figuring out where the risk actually is. Either way, the promised productivity gains of agentic coding tools are undercut — either by unsafe code slipping through, or by review becoming the new bottleneck. Getting this workflow right is a precondition for agentic coding tools to be used safely at scale.

## What makes the system agentic

The object under study is an LLM-based coding agent that autonomously plans and executes changes spanning multiple files in a codebase — not a single-shot code completion, but a multi-step, multi-file edit that a human then has to make sense of as a whole. The paper itself is not proposing a new autonomous agent; rather, its entire contribution is about designing and evaluating the human-facing review layer that sits between that agentic behavior and a developer's decision to merge it. This qualifies as agentic-AI research because the object of design and evaluation is precisely how humans oversee an agent that plans and acts across a codebase, not how they read isolated single-file suggestions.

## How humans and the AI agent collaborate

The collaboration here is structured as a **review gate**: the agent proposes a multi-file change, and the developer's job is to decide how much to trust it and whether to accept it. The paper's central contribution is a workflow for *how* that trust decision gets made — breaking the review into three levels of zoom (overview, file-level analysis, and code-snippet-level inspection) rather than forcing a single all-or-nothing read of a large diff.

## What role the human plays

The human is the reviewer, risk-assessor, and final approver. Across the study, practitioners were also active **co-designers**: 17 industry developers first described their real pain points reviewing agent-generated multi-file changes (Discover phase), 7 of them returned to help shape candidate solutions (Develop phase), and a separate group of 43 practitioners then evaluated a resulting prototype and reported how it would change their review effort and trust-assessment process (Deliver/validation phase).

## What role the AI agent plays

The coding agent is the one producing the multi-file change being reviewed — the "subject" of the review workflow rather than a participant that adapts to the human in real time. Within the proposed prototype, an AI-derived "Judge" construct also surfaces automated risk signals (e.g., risk-per-line, risk-per-file) that feed into the human's review, meaning the AI plays a secondary, assistive role inside the review process itself, not just as the author of the original change.

## How control, initiative, and decisions are shared

This is a **human oversight** setup: the agent has already acted (autonomously producing a multi-file change), and control sits with the human, who decides what to trust and what to accept. The paper's contribution is giving that human better instruments for exercising that control — a workflow that lets them scale their attention up and down (from whole-change overview to single-snippet inspection) rather than an interface where the agent and human jointly plan or negotiate the work as it happens.

## The paper's main idea

**Claim by the authors:** the central obstacle to reviewing LLM-generated multi-file changes is not just size or unfamiliarity — it's **trust calibration**: developers need help figuring out *how much* scrutiny each part of a change deserves, not just *what* changed. Their proposed answer is a three-level review workflow (overview → file-analysis → code-snippet review) built around seven design constructs distilled directly from developer feedback: chunk (grouping related changes), risk-per-line, risk-per-file, judge (an automated verdict/risk signal), walk-through (a guided narrative of the change), zooming in/out between levels, and a "security cage" metaphor that makes explicit what the agent was and wasn't allowed to do.

## How the approach works

The researchers used a **double-diamond participatory design process** (Discover → Define → Develop → Deliver) run in collaboration with JetBrains:
- **Discover (N=17 practitioners):** interviews/workshops surfacing real pain points reviewing agent-generated multi-file changes; identified trust-calibration as the central challenge.
- **Define:** author-led synthesis of these pain points into design goals.
- **Develop (N=7, drawn from the Discover group):** co-design sessions converging on the three-level workflow and its seven supporting constructs.
- **Deliver:** the team built a high-fidelity, semi-interactive prototype embodying the workflow, then validated it with a follow-up survey of 43 practitioners who viewed a walkthrough/demonstration of the prototype and reported expected changes to their review and trust-assessment effort.

## Human study or evaluation design

**Demonstrated in the paper:** a mixed-methods participatory design study with real industry practitioners at every phase — not a single lab experiment, but iterative co-design followed by a separate quantitative validation survey. The validation survey asked 43 practitioners to rate each of the three workflow levels on a five-point scale and to estimate whether the workflow would reduce their overall review effort and their trust-assessment effort compared to their current tools.

## Participants and study setting

67 unique industry practitioner-slots across the study: 17 in the Discover phase, 7 (a subset of the 17) in the Develop phase, and 43 separate practitioners in the Deliver-phase validation survey. The work was carried out in partnership with JetBrains, suggesting a mix of professional software developers with real experience reviewing code, including (per the study's premise) LLM-agent-generated changes.

## Experiments or benchmarks

There is no public leaderboard-style benchmark here — this is a design-research study, not a model evaluation. The "experiment" is the validation survey: practitioners viewed a video/walkthrough demonstration of the semi-interactive prototype (not hands-on use in a live review task) and then rated it.

## Main results

**Demonstrated in the paper (per available sources):**
- All three workflow levels (overview, file-analysis, code-snippet review) scored above the neutral midpoint, with means between 3.50 and 3.91 on a five-point scale.
- 63% of the 43 survey respondents expected the workflow to reduce their **overall review effort** compared to their current tools.
- 52% expected it to reduce their **trust-assessment effort** specifically — a more modest number, but notable given that, per the authors, none of the participants' current tools explicitly surface trust signals at all.
- Trust-calibration emerged as the dominant theme developers raised unprompted when describing what's hard about reviewing agent-generated multi-file changes.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper:** the validation survey measured practitioners' *self-reported expectations* of reduced review effort and reduced trust-assessment effort after seeing the prototype — it did not measure actual review accuracy, actual time spent, or safety outcomes in a live task. **Our interpretation:** this is a real signal that a workflow explicitly designed around trust-calibration resonates with practitioners' stated needs and expected effort, but — as with many participatory-design validation studies — it is evidence of anticipated benefit from a demonstration, not measured behavioral change from hands-on use.

## What is genuinely new

- A workflow **explicitly organized around trust-calibration** as the design target, rather than around generic diff navigation — distilled directly from what developers said was hardest about reviewing agent-generated multi-file changes.
- Seven concrete, named design constructs (chunk, risk-per-line, risk-per-file, judge, walk-through, zooming, security cage) that give IDE and tooling builders a shared vocabulary for this problem, developed and refined by real practitioners rather than proposed top-down.
- A rigorous double-diamond participatory-design process — spanning discovery, co-design, and validation with 67 distinct practitioner-slots in collaboration with an actual IDE vendor (JetBrains) — applied specifically to the emerging problem of multi-file agentic code review, an area with little prior validated tooling design.

## Limitations and open questions

- The validation survey evaluated the prototype via a **video/demonstration walkthrough, not hands-on use in a realistic review task** — so the reported effort reductions are practitioners' expectations, not measured performance.
- Several respondents suggested the fixed three-level structure might be too rigid, proposing free navigation between levels instead — whether the leveled scaffolding actually helps or constrains expert reviewers is an open, flagged question.
- Respondents also suggested integrating test-coverage data into the "Judge" construct, which the authors note as unaddressed in the current design.
- The authors themselves identify **hands-on, longitudinal evaluation** — actually using the prototype on real review tasks over time — as necessary future work, implying the current validation is an early, expectation-based signal rather than a demonstrated efficacy result.
- No code, dataset, or interactive prototype link was found in available sources, limiting independent verification or reuse.

## Practical implications

For IDE vendors and teams building agentic coding tools, this paper offers a concrete, developer-validated vocabulary and workflow structure (levels + the seven constructs) for building review tooling that treats trust-calibration as the central problem, rather than bolting agent-review features onto diff viewers built for human-authored, single-file changes. The "security cage" construct in particular — making explicit what an agent was and wasn't permitted to do — offers a practical mechanism connecting oversight design to agent permissioning.

## Why you should care

Most of the papers in this collection study agents that already exist and ask how well humans can supervise them after the fact. This one instead asks *how the supervision tooling itself should be designed*, using real developers as co-designers rather than only as evaluators. As agentic coding tools push more autonomous, multi-file changes into everyday development, the specific finding that "trust-calibration," not just navigation or diff size, is what developers say they're missing is a useful, human-grounded reframing of what review tooling for agents needs to solve — even though, by the authors' own account, it still awaits hands-on validation beyond a demonstration survey.
