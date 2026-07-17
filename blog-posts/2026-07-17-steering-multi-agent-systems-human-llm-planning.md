# How to Steer Your Multi-Agent System: Human-LLM Collaborative Planning

**Authors:** Zeyu He (Pennsylvania State University), Hannah Kim, Dan Zhang, Estevam Hruschka (Megagon Labs)
**Publication date:** 2026-05 (arXiv id 2605.23023; exact day of first posting not confirmed from available sources)
**Venue:** ACM Conference on AI and Agentic Systems (ACM CAIS '26), May 26–29, 2026, San Jose, CA, USA (DOI: 10.1145/3786335.3813144)
**Paper link:** https://arxiv.org/abs/2605.23023 (PDF: https://arxiv.org/pdf/2605.23023)
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-07-17

> **A note on sourcing:** the arXiv host was not directly reachable from this research session's network, so this summary is built from the paper's publicly circulated abstract, conference listing, and secondary descriptions rather than a direct read of the full PDF. Facts below that could be cross-confirmed across multiple independent sources (authors, venue, DOI, study design, participant count, sampling method, and qualitative findings) are reported as such; anything that could not be verified is marked "not available" or flagged as uncertain rather than invented.

---

## The problem the paper addresses

When you ask a "multi-agent" AI system to do something complicated — say, answer a question that needs some math, a bit of code, and a lookup of facts — the system doesn't just answer in one shot. Internally, it builds something like a project plan: agent A does the calculation, agent B writes the code, agent C checks the facts, and so on. Today, most of these systems only show you two things: the final answer, or a flat, high-level to-do list. What actually happens in between — how the plan branches, where one agent's output feeds into another's task — stays hidden.

That's a problem when the plan is wrong. If a user can only critique the finished answer, or nudge a simple bullet-point list, they have no way to say "this middle step is off" without either accepting a bad answer or throwing out the whole plan and starting over.

## Why this problem matters

As multi-agent LLM systems get deployed for real work — research assistants, coding helpers, data-analysis pipelines — mistakes tend to hide in the connective tissue between agents, not just in the final output. A wrong assumption made early by one agent can silently corrupt everything downstream. If humans are expected to supervise these systems responsibly (rather than just trust them or reject them wholesale), they need a way to look at and adjust the plan while it's still being built — not just grade it after the fact.

## What makes the system agentic

The system studied here is a genuine multi-agent LLM setup, not a single chatbot: an LLM-based planner decomposes a task into a structured plan made up of interdependent sub-tasks, and separate LLM-based execution agents carry out those sub-tasks (things like numerical computation, coding, information retrieval, and commonsense reasoning) using tools. The paper describes the prototype as using one LLM configuration for planning and a separate, faster LLM configuration for execution. Multiple agents have to coordinate — the tasks in the study were deliberately designed so that no single agent could solve them alone. That combination — decomposition, delegation across agents, tool use, and multi-step execution rather than a single text reply — is what makes this an agentic AI system under our working definition, not just a chat interface.

## How humans and the AI agent collaborate

This is the heart of the paper. Instead of treating human oversight as "approve or reject the final answer," the system lets a person inspect the plan's intermediate structure — the graph of sub-tasks and how they connect — and intervene at that level: giving feedback on a specific piece of the plan, or directly editing its structure, before execution finishes.

## What role the human plays

According to the paper, the human is a process-level supervisor and co-planner: reading the plan the LLM planner proposes, deciding whether and where it needs correction, and then either giving targeted feedback on a sub-part of the plan or making a structural edit themselves (adding, removing, or rewiring steps). The human is not just a downstream grader — they can act mid-plan, before any execution agent has run.

## What role the AI agent plays

The LLM planner proposes an initial plan and is responsible for turning human feedback (whether a comment on part of the plan or a structural edit) back into a coherent, executable plan — a step the authors call "reintegration." The execution agents then carry out the finalized sub-tasks using tools. The planner also has to reconcile a human's local edit with the rest of the plan, which the paper shows is not always trivial.

## How control, initiative, and decisions are shared

Authority is explicitly shared and configurable rather than fixed: the paper compares several feedback/control conditions, ranging from a person giving high-level ("global") feedback that causes the planner to regenerate the whole plan, to more surgical options — targeted feedback on one part of the plan, targeted feedback given together with the full plan for context, and direct structural edits made by the human. This lets the paper study a genuine trade-off: more targeted human control costs more effort and carries more risk of botched reintegration, while coarser control is safer for the system to absorb but gives the human less precision. The authors describe this as an "effort-control-risk" trade-off that determines when fine-grained supervision is actually worth doing.

## The paper's main idea

**Claim by the authors:** meaningful human oversight of multi-agent LLM systems should happen at the process level — during planning, at the level of individual sub-tasks and their connections — not only at the outcome level (approving/rejecting a finished answer). The paper argues, and tries to demonstrate, that people can do this kind of process-level steering effectively if given the right interaction primitives (targeted feedback and structural editing), and that the “right” level of human involvement depends on the situation, not a single fixed policy.

## How the approach works

The prototype system (built as a web application with an LLM-based planner and separate LLM-based execution agents) exposes the plan as an inspectable, editable structure rather than a black box or a flat checklist. A user can zoom into any sub-task, comment on it, or restructure the plan by hand; the planner then reconciles that input with the rest of the plan before handing finalized sub-tasks to the execution agents. The paper frames this as one instance of a broader design space of "hybrid human-AI planning patterns," rather than a single fixed workflow.

## Human study or evaluation design

**Demonstrated in the paper (per available descriptions):** the authors ran a within-subject user study in which each participant used two versions of the system — a baseline interaction mode and the richer steering prototype — across two sessions, so that the same people could be compared under both conditions. Participants worked through curated task sets designed in matched pairs of similar difficulty and planning complexity, each requiring genuine multi-agent collaboration (not solvable by a single agent). The paper reports separately measuring the mechanics of feedback: how often global feedback, targeted feedback, targeted feedback with full-plan context, and direct structural edits each produced a valid, successfully reintegrated plan.

## Participants and study setting

Based on cross-checked secondary descriptions of the paper, **13 participants (labeled P1–P13)** were recruited in-house, via convenience sampling, from a U.S.-based industry research lab (consistent with the authors' Megagon Labs affiliation). This is a real-human, hands-on study — participants actually used the prototype to steer live multi-agent plans — but it is a small, single-organization convenience sample, which the authors themselves would be expected to flag as a limitation (see below).

## Experiments or benchmarks

There is no public, named benchmark here; the evaluation is a custom, purpose-built task set (four sets of matched question pairs spanning numerical computation, coding, retrieval, and commonsense reasoning) combined with an ablation-style comparison of feedback conditions (global feedback vs. targeted feedback vs. targeted feedback with full-plan context vs. structural editing).

## Main results

**Demonstrated in the paper (per available descriptions):**
- Global feedback (regenerating the whole plan from a human comment) reliably produced a valid, coherent revised plan in effectively all cases.
- More targeted interventions — revising just one part of the plan — succeeded less often, because a locally revised sub-plan can create mismatches with the rest of the plan when it's reintegrated.
- Among the targeted approaches, giving the model the full plan as context alongside the targeted feedback improved reintegration success compared to targeted feedback alone.
- Direct structural editing by the human (adding/removing/reordering plan steps) had the lowest reported success rate among the conditions studied, since later edits depend on the plan state left by earlier ones — small sequencing mistakes compound.
- Overall, the authors describe a genuine trade-off: targeted, fine-grained human control improves plan stability/alignment with intent but is more fragile to reintegrate correctly than coarse, whole-plan regeneration.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central empirical contribution is about *how* humans supervise multi-agent plans, not a headline trust/workload score. Per available descriptions, the authors report that participants could meaningfully use process-level supervision — inspecting, commenting on, and editing intermediate plan structure — and that different feedback types have measurably different success/failure characteristics, which the authors connect to an "effort-control-risk" trade-off: finer-grained control demands more human effort and carries more risk of an inconsistent plan if mishandled, while coarse feedback is cheaper for the human but less precise. **This is our interpretation, based on the available summaries** — we could not confirm specific quantitative trust, workload (e.g., NASA-TLX), or task-completion-time figures from the sources available to us, and we are not asserting numbers we could not verify.

## What is genuinely new

- Reframing human oversight of multi-agent LLM systems around **process-level** intervention (the plan's internal structure) rather than only pre-task configuration or post-hoc output review — a step beyond prior interview-based findings (like the "Human oversight of agentic systems in practice" paper already in this repository) that developers rarely monitor agents in real time.
- A direct, controlled comparison of specific feedback mechanisms (global vs. targeted vs. targeted-with-context vs. structural edit) and their differing success/failure modes when reintegrated into a live multi-agent plan — a concrete, mechanistic account of *why* fine-grained human control is harder to execute reliably, not just that it exists.
- Framing the choice of supervision granularity as an explicit effort-control-risk trade-off that a system (or its interface) could, in principle, be designed to adapt to.

## Limitations and open questions

- **Small, non-representative sample.** Thirteen participants recruited by convenience sampling from a single industry research lab is not a broad or demographically diverse pool; findings about how "humans" steer plans may not generalize to other user populations, expertise levels, or task domains.
- **Custom task set.** The four question-pair sets were purpose-built for this study rather than drawn from an established, independently validated benchmark, which makes it harder to compare results against other multi-agent steering work.
- **Reintegration failures are a real weakness.** The paper's own results show that the more precise/targeted forms of human control are also the ones most likely to fail to reintegrate cleanly — this is presented as a finding, but it is also an open engineering problem the paper does not claim to have solved.
- We were unable to independently verify exact quantitative results, statistical tests, or full details of the two interaction conditions from the sources available in this session, since the full PDF could not be fetched — readers who need precise numbers should consult the paper directly.

## Practical implications

If the paper's findings hold up under closer reading, they suggest that agentic system builders shouldn't only invest in "final answer" review UIs — exposing the intermediate plan graph and letting users comment on or restructure specific sub-tasks appears to be usable and valuable, but the reintegration step (folding a human's local edit back into a consistent global plan) is a real technical bottleneck worth solving well, since it currently seems to be where fine-grained human control is most likely to break down.

## Why you should care

This paper targets a very concrete, practical version of a big question this research log keeps returning to: not just "should a human oversee an AI agent," but "at what level of granularity, through what interface, and at what cost?" It's a useful, hands-on data point — the more control you hand a person over a multi-agent plan's internals, the more valuable but also the more failure-prone that control becomes unless the underlying system is built to reconcile human edits carefully. That's a concrete design lesson, not just a philosophical stance on "humans in the loop."
