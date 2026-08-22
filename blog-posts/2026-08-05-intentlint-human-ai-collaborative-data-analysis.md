# When Your AI Coding Agent Doesn't Know What Your Teammate Already Told It: IntentLint and the Problem of Shared Intent

**Authors:** Felicia Li Feng, Jian Zhao, Anamaria Crisan (University of Waterloo, School of Computer Science)
**Publication date:** 2026-08-05 (arXiv v1)
**Venue:** arXiv preprint (peer-reviewed venue not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2608.04331
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-22

> **A note on sourcing:** this session's outbound network access to arxiv.org (and to several other paper-hosting mirrors, including Semantic Scholar, Hugging Face, and alphaXiv) returned a blocked connection for direct fetches — an organizational egress policy on this session, not a paywall; the paper itself is a public arXiv preprint. This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported system design, and reported study findings, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

Picture two data analysts sharing a Jupyter notebook, both also prompting an AI coding agent (the kind built into tools like GitHub Copilot or Claude Code) to write and run analysis code for them. One analyst tells the agent "exclude outliers above the 99th percentile." Two hours later, their teammate — who never saw that instruction — prompts the same agent to "recalculate the summary stats," and the agent quietly applies a filtering assumption nobody agreed to check with them first. Nothing crashed. No error appeared. But the shared understanding of *what the analysis is actually doing* has quietly drifted apart. This paper is about that specific failure mode: as human-AI data analysis sessions evolve rapidly, the artifacts that are supposed to capture "what we've decided and why" — chat logs, code comments, notebook cells — become incomplete or hard to interpret, leading to undocumented assumptions, misaligned intent between collaborators, under-specified prompts, and AI actions nobody actually wanted.

## Why this problem matters

Data analysis has always been a team sport, but adding an AI agent that can write and execute code on anyone's behalf multiplies the ways a team's shared understanding can silently fracture. A single analyst working with an AI agent can at least keep the whole conversation in their own head; a group of analysts sharing a notebook and an agent cannot. Most existing tools for AI-assisted coding focus on making a single person's prompt-to-code loop faster, not on keeping several humans and an AI agent mutually aware of each other's goals, assumptions, and constraints. Left unaddressed, this is exactly the kind of quiet coordination failure that produces analyses nobody fully trusts and errors nobody catches until much later — a genuine, practical cost in any team that has adopted AI coding agents for real analytical work.

## What makes the system agentic

The AI collaborator in this setting is not a single-turn chatbot — it is an LLM-based coding agent (the paper's design connects to tools such as GitHub Copilot and Claude Code) embedded directly in a shared computational notebook. Given a natural-language prompt, it generates and executes code, reads and writes to the shared notebook state, and its outputs persist and compound across a session — one agent action becomes the foundation the next prompt (from the same person or a different teammate) builds on. That combination of a goal-directed loop, multi-step code generation and execution, and a persistent, shared environment it can act on is what makes this an agentic system rather than a simple autocomplete assistant.

## How humans and the AI agent collaborate

The paper frames the collaboration as **multi-human, single-(or multiple-)agent** work inside a shared notebook: several analysts, each free to prompt the AI agent independently, are all editing and building on the same evolving analytical artifact. IntentLint, the system the authors build, sits as a coordination layer between the humans and the agent — it does not replace either human judgment or the agent's code generation, but tries to make the *intent* behind each contribution visible to everyone (including, implicitly, to the agent's next invocation) before code gets written and run.

## What role the human plays

Humans are the **analysts driving the work and the ultimate arbiters of intent**: they issue the prompts that trigger the agent, they make analytical decisions (what counts as an outlier, which subset of data is in scope, what assumption is safe to make), and — critically for this paper — they are the ones who review, edit, and approve or reject the structured "rules" that IntentLint infers about what the team is trying to do. In the study, participants also directly evaluated whether the system helped them understand what their *human* collaborators (not just the AI) were trying to accomplish.

## What role the AI agent plays

The AI agent is the **code-generating collaborator**: given a prompt, it infers what to do, writes and runs code inside the shared notebook, and produces results that become part of the shared analytical record. IntentLint additionally uses AI/LLM-style inference itself, as a *meta*-layer: it reads the notebook's code, dependencies, data flow, and prior results, together with a user's new prompt, and infers likely goals, assumptions, and rationale — surfacing these as editable, structured rules rather than leaving them buried in code or chat history.

## How control, initiative, and decisions are shared

This is a case of **human-initiated prompting with a shared, inspectable coordination layer in between**: any analyst can still prompt the agent at any time (the agent has no autonomy to act unprompted), but before a prompt reaches the agent, IntentLint's prompt-time linting checks it against the team's currently active rules and flags potential conflicts — a lightweight, automatic checkpoint rather than a full approval gate. Analysts retain the final call on whether to proceed, revise the rule set, or override a flag; the system's job is to make the moment of potential misalignment visible in time for a human to catch it, rather than to block or arbitrate on its own.

## The paper's main idea

**Claim by the authors:** the core coordination failure in multi-human, AI-assisted data analysis is that analytic intent — the goals, assumptions, and decision rationale behind each step — is rarely made explicit anywhere, so it becomes invisible to both other human collaborators and to the AI agent generating the next round of code. The authors argue this can be addressed with a rule-based coordination layer offering two concrete mechanisms: **intent scaffolding** (surfacing inferred intent as structured, editable rules the team can review) and **prompt-time linting** (checking new prompts against those rules and flagging conflicts before code is generated).

## How the approach works

IntentLint is implemented as a proof-of-concept system (reported as a VS Code extension) that observes a shared computational notebook, extracting context from code, cell dependencies, data flow, and prior analytic results. Combining that context with a user's incoming prompt, it infers likely goals, assumptions, and rationale and represents them as structured, editable rules that any team member can inspect, revise, or discard. When a new prompt is submitted — by any analyst, to an AI coding agent such as Copilot or Claude Code — IntentLint checks it against the currently active rules and flags the prompt if it appears to conflict with something the team has already established, before the agent generates and executes new code.

## Human study or evaluation design

**Demonstrated in the paper:** the authors report first conducting a formative study to characterize the coordination challenges of multi-person, AI-assisted notebook analysis (using a Jupyter notebook as a technology probe, with attention to asynchronous workflows where analysts must interpret changes made earlier by themselves, teammates, or the AI). They then built IntentLint based on those findings and evaluated the resulting system in a follow-up study with real data analysts.

## Participants and study setting

**Demonstrated in the paper:** a study involving 16 data analysts. The exact recruitment method, task design, and whether the evaluation was a single structured session or an extended engagement were not independently confirmed from the sources available in this session; readers who need those specifics should consult the full paper.

## Experiments or benchmarks

There is no public benchmark; this is a qualitative/mixed-methods system evaluation rather than a quantitative leaderboard-style comparison. The "experiment" is analysts using IntentLint (and, implicitly, comparing it against their existing unaided workflow) while working on collaborative data-analysis tasks in shared notebooks alongside an AI coding agent.

## Main results

**Demonstrated in the paper (per available descriptions):**
- IntentLint **improved participants' awareness of what their collaborators — human and, indirectly, AI-driven — were doing and intending**, compared to working without the tool.
- The **intent scaffolding mechanism encouraged participants to make their own analytical strategies explicit** and to revisit those strategies over time, rather than leaving them implicit in code alone.
- **Prompt-time linting surfaced real conflicts** between a newly issued prompt and goals or constraints the team had previously established, catching misalignments earlier than they otherwise would have been caught.
- Participants also raised a clear limitation: some **wanted finer-grained control over the rule set itself**, including ideas like role-based permissions over who can create, edit, or override which rules — suggesting the current one-size-fits-all rule-sharing model doesn't fit every team's needs.

## Effects on human performance, trust, workload, safety, or decision quality

This is a **demonstrated result on collaboration awareness and reflection**, not a controlled trial with performance or trust metrics: the paper reports that using IntentLint helped analysts better understand collaborators' activities and intent and prompted deeper reflection on their own analytical choices, and that it helped surface misalignments earlier. What is **not established** from the sources available here is any quantitative measurement of task accuracy, completion time, workload (e.g., NASA-TLX-style scores), or calibrated trust — the reported evidence is qualitative/perception-based (participant reflections and reported experience), not a benchmarked before/after comparison on those dimensions.

## What is genuinely new

- A **coordination layer purpose-built for the specific failure mode of multi-human, AI-assisted analysis** — most prior human-AI coding-assistant work targets a single user's prompt-to-code loop, not a team's shared, evolving intent across both human and AI contributions.
- **Prompt-time linting** as a concrete, lightweight mechanism for catching misalignment *before* an AI agent acts on a conflicting prompt, rather than after the fact when the resulting code or output has to be manually caught and untangled.
- Treating **analytic intent as a first-class, structured, editable artifact** (a set of rules) rather than something left implicit in code comments, chat scrollback, or people's memory.

## Limitations and open questions

- **Small, qualitative study:** 16 participants is enough to surface rich, real design feedback but not to establish statistically robust claims about how much IntentLint improves outcomes, or how it performs at team scales larger than a handful of analysts.
- **No quantitative outcome metrics reported** in the sources available here (e.g., task accuracy, time-to-detect-a-misalignment, workload, or trust scores) — the demonstrated benefits are about awareness and reflection, not measured task performance.
- **Participants wanted more control** over the rule system itself (e.g., role-based permissions), which the authors themselves flag as an open direction rather than a solved problem.
- **Rule inference is itself AI-driven** and therefore imperfect; the paper does not (per available sources) report how often IntentLint's inferred rules were themselves wrong or needed significant correction, which matters for whether the coordination layer could introduce its own new source of noise.
- **Single organization/lab-style evaluation, single toolchain assumptions:** the system is described as integrating with specific AI coding tools (e.g., Copilot, Claude Code) inside a notebook/VS Code environment; how well the approach generalizes to other agentic tools, non-notebook analysis environments, or larger, more distributed teams is not established.
- **Peer-review status:** as of this writing, this appears to be an arXiv preprint; a peer-reviewed publication venue was not confirmed from the sources available in this session.

## Practical implications

For any team that has started letting multiple people prompt the same AI coding agent inside a shared analysis artifact — a increasingly common pattern as agentic coding tools spread from individual to team use — this paper is a concrete reminder that "the AI wrote correct-looking code" is not the same as "the AI did what the team actually intended." IntentLint's two mechanisms point to a practical, low-friction design pattern other tool builders could adopt: make an AI-assisted workflow's inferred assumptions visible and editable, and check new instructions against them automatically before the agent acts — a pattern that generalizes well beyond data analysis to any setting where multiple people delegate work to the same AI agent over a shared, evolving artifact.

## Why you should care

Most human-AI collaboration research on coding and analysis agents still studies a single person working with a single assistant. This paper is a useful corrective: it looks at what happens once an AI agent becomes a *shared* collaborator across a team, and identifies a specific, underappreciated coordination cost — the silent erosion of shared intent — that emerges only in that multi-person setting. Even without large-scale quantitative validation yet, the problem it names and the two mechanisms it proposes (make intent explicit; check new prompts against it before the agent acts) are a genuinely useful lens for anyone building or using AI agents as a *team* resource rather than a personal one.
