# AgentForge: An Immersive Role-Playing Platform for Learning Agentic Software Engineering

**Authors:** Zihan Fang, Yueke Zhang, Yu Huang (Vanderbilt University, based on cross-checked author profiles and search-engine excerpts — not independently confirmed from the paper's own author/affiliation block)
**Publication date:** 2026-08-04 (arXiv v1)
**Venue:** arXiv preprint (cs.SE / cs.AI / cs.HC; peer-review status not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2608.04148
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-09

> **A note on sourcing:** this session's outbound network access to arxiv.org (and several other research-hosting domains, including semanticscholar.org and the authors' personal/lab pages) returned a blocked connection for direct fetches — an organization egress policy in this sandboxed environment, not a paywall; the paper is a public arXiv preprint. This summary is therefore built from cross-checked search-engine excerpts of the paper's abstract and reported methodology/results, plus circumstantial cross-referencing of author profiles, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed." Readers who need precise statistical detail should consult the arXiv preprint directly.

---

## The problem the paper addresses

Agentic AI coding tools don't just autocomplete a line of code anymore — they plan a fix, write a patch, review it, and run tests, often coordinating several AI "agents" to do it. That's powerful, but it's also opaque: a novice developer watching this happen has no easy way to see *why* the AI planned the fix it did, or whether the patch it wrote is actually sound. The paper's premise is that novices learning to work with agentic AI have to learn three things at once — how the agentic system works internally, how to actually collaborate with it, and how to critically evaluate what it produces — and most tools give them no structured way to practice any of that.

## Why this problem matters

As agentic coding tools spread from personal experiments into classrooms and entry-level jobs, the people who will supervise them are, increasingly, people who have never had to build a mental model of how they work. If novices only ever *use* these tools passively — accept the suggestion, move on — they risk becoming poor overseers of exactly the systems they're meant to be checking. This is the same concern that shows up elsewhere in this repository's coverage of human oversight of coding agents (e.g., the "How Coding Agents Fail Their Users" and "Human oversight of agentic systems in practice" entries): oversight is a skill, and skills usually need deliberate practice, not just exposure.

## What makes the system agentic

AgentForge's core is a **multi-agent code-repair pipeline** with four distinct roles — Task Planner, Patch Author, Code Reviewer, and Test Runner — each performing a genuine step in a multi-step workflow (decompose the bug → write a patch → review it → run tests) on real single-file bug-repair tasks. In any given practice session, three of these four roles are filled autonomously by LLM agents while a human occupies the fourth, and the system exposes the intermediate artifacts each role produces (plans, patches, review comments, test results) rather than only a final answer. That combination — goal-directed, multi-step, tool-using agents acting inside a real code-repair environment, evaluated as collaborating teammates rather than single-turn generators — is what puts this squarely in agentic AI territory.

## How humans and the AI agent collaborate

The collaboration is structured as **role rotation inside a shared pipeline**: according to search-indexed descriptions of the paper, each participant completed practice sessions across all four roles in turn, occupying one role per session while AI agents autonomously filled the other three. This is a genuinely shared workflow rather than a simple "AI suggests, human approves" loop — the human's output in their assigned role becomes an input to the next AI-run stage, and vice versa, so both sides are actually acting inside the same pipeline rather than one merely reviewing the other's finished work.

## What role the human plays

In each session, the novice takes on exactly one of the four roles: deciding how to decompose a bug and plan the fix (Task Planner), writing the actual patch (Patch Author), reviewing a patch produced by the AI agents for correctness (Code Reviewer), or running and interpreting tests (Test Runner). Across roles, the human is also asked to monitor and evaluate the AI agents' intermediate outputs, and can issue **"reroutes"** — a human-initiated correction that redirects the workflow when it's going off track. The platform's scaffolding and "metacognitive support" are described as deliberately prompting the human to reflect on both the software-repair task and their own collaboration with the agents, rather than just clicking through.

## What role the AI agent plays

Three LLM agents run the remaining stages of the pipeline autonomously for whichever role the human isn't occupying that session — planning the fix, authoring the patch, reviewing it, or running tests — and hand their output forward to the next stage (whether that next stage is another agent or the human). The system is designed to make this agent coordination and the artifacts it produces visible to the human, rather than hiding them behind a single chat-style response.

## How control, initiative, and decisions are shared

Initiative shifts by pipeline stage rather than sitting with one side throughout: for three of the four stages in a given session, the AI agents act independently; for the fourth, the human acts, informed by whatever the agents before them produced. The human additionally holds a standing override — the "reroute" mechanism — that lets them intervene when they judge the pipeline is heading the wrong way, and the frequency with which participants used this mechanism was itself treated as a measurable signal of collaboration friction, differing significantly by which role the human held.

## The paper's main idea

**Claim by the authors (as reported in search-indexed summaries of the paper):** letting novices rotate through each role in a real multi-agent code-repair pipeline — with the intermediate agent artifacts made visible and reroute/correction affordances built in — helps them learn both practical software-repair skills and how to collaborate critically and effectively with agentic AI, rather than treating the agentic pipeline as an opaque black box.

## How the approach works

AgentForge decomposes bug repair into the same four stages a multi-agent coding pipeline would use in production — planning, patching, reviewing, testing — and lets a human step into any one of them while AI agents handle the rest. Because the roles rotate across sessions, the same person experiences the pipeline from multiple vantage points: as the one who sets the plan the AI patches against, as the one whose patch the AI reviews, as the one reviewing the AI's patch, and as the one interpreting the AI's test results. The scaffolding surfaces what each AI agent decided and produced at each stage, and the reroute mechanism gives the human a concrete way to act on that visibility rather than just observing it.

## Human study or evaluation design

**Demonstrated in the paper (per available search-indexed descriptions):** 37 novice developers used AgentForge, each completing practice sessions across the four roles on a suite of real, single-file bug-repair tasks. The study logged behavioral interaction measures — turns, reroutes, and completion time — per role, alongside self-reported task-completion outcomes and perceived difficulty, and collected participants' self-reported gains in understanding of software repair and of agent collaboration. Exact procedural details (within-subject vs. between-subject ordering, session length, number of bugs per session) were **not available** from the sources accessible in this session.

## Participants and study setting

37 novice developers (real human participants, not simulated). Their exact background (students vs. early-career professionals), recruitment method, and the physical/remote setting of the study were **not confirmed** from the sources available in this session.

## Experiments or benchmarks

No public benchmark was identified; the study uses a custom suite of single-file bug-repair tasks built for this platform. The authors reportedly note this as a scope limitation and describe planned future work extending to multi-file refactoring tasks.

## Main results

**Demonstrated in the paper (per available search-indexed descriptions):**
- Participants achieved **high task-completion rates** with AI-agent support (exact percentage not available from accessible sources).
- **Interaction demands differed significantly by role:** the Code Reviewer role required significantly more interaction turns, reroutes, and completion time than the other three roles (reported statistic: p_adj = .004), and was also rated as the most challenging role.
- Participants reported **significant self-reported gains** in their understanding of both software repair and of collaborating with agentic AI.

No comparison against a non-agentic or solo (no-AI-teammate) baseline condition was confirmed from the sources accessible in this session, so it is not established how much of the reported learning gain is attributable specifically to the multi-role/rotation design versus practicing bug repair generally.

## Effects on human performance, trust, workload, safety, or decision quality

The clearest human-centered finding is a **workload/difficulty asymmetry across roles**: the oversight-style role (Code Reviewer) demanded significantly more interaction and was perceived as hardest — a pattern that echoes findings elsewhere in this repository (e.g., in "Overseeing Agents Without Constant Oversight" and "How Coding Agents Fail Their Users") that reviewing/verifying an agent's work is often more demanding than producing work alongside it. This is reported as a **demonstrated result** (p_adj = .004), not just an author claim. The self-reported learning gains in software-repair and agent-collaboration understanding are also demonstrated (survey-based) outcomes, though the exact instrument and numeric scores were not available from accessible sources. No trust, workload (beyond interaction counts), or safety measures beyond these were confirmed.

## What is genuinely new

- A platform that puts a novice **inside** a real multi-agent coding pipeline, in a rotating role, rather than only letting them prompt or observe a single AI assistant.
- Empirical, role-by-role measurement of collaboration burden (interaction turns, reroutes, completion time) within a human-AI multi-agent team — showing this burden is not uniform across roles, with the reviewer/verifier role standing out as most demanding.
- Framing critical, effective collaboration with agentic AI as a **learnable skill** with its own scaffolding and metacognitive design, rather than an assumed byproduct of tool exposure.

## Limitations and open questions

- **Small sample:** 37 novice participants; generalizability to professional developers or to production agentic coding tools (Claude Code, Copilot CLI, etc.) is untested.
- **Narrow task scope:** the authors reportedly restrict evaluation to single-file bugs; real-world engineering involves cross-file changes and ambiguous requirements not yet covered — the authors describe multi-file refactoring as future work.
- **No confirmed baseline comparison:** it is not established from available sources whether the reported learning gains are specific to the rotating multi-role design versus simply practicing bug repair with any AI assistance.
- **Unconfirmed procedural and demographic detail:** participant background, recruitment, study setting, and exact statistics (completion-rate percentages, means/SDs, survey instrument) could not be independently verified in this session because the full PDF could not be fetched — this is a limitation of this summary's sourcing, not necessarily of the paper itself.
- **Peer-review status:** appears to be an arXiv preprint at the time of writing; no peer-reviewed venue was confirmed.

## Practical implications

For teams building or teaching agentic coding tools, this paper points toward a concrete training design: let people practice **every** role in a human-AI coding pipeline, not just the one they'll hold in production, and give them a visible trail of what each agent did plus an explicit way to interrupt or redirect it. The finding that the reviewer/oversight role was the most demanding role is a useful, actionable signal for anyone designing onboarding or workload expectations around human review of agentic code — it suggests review capacity, not just tool access, may be the bottleneck to plan for.

## Why you should care

If you expect to supervise, review, or collaborate with agentic coding tools at work — which is increasingly likely for anyone in software — this paper's underlying premise is worth sitting with: knowing how to *use* an agentic pipeline is not the same skill as knowing how to *oversee* one, and the second skill may need to be practiced deliberately rather than picked up by osmosis. The specific finding that reviewing was the hardest role to inhabit is a small, concrete data point in favor of investing training time there specifically, rather than assuming familiarity with an agent's outputs is enough.
