# When You Manage a Team of AI Coworkers, You Still Have to Be the Boss

**Paper title:** Understanding Human–Multi-Agent Team Formation for Creative Work
**Authors:** Hyunseung Lim (KAIST), Dasom Choi (National University of Singapore), Sooyohn Nam (KAIST), Bogoan Kim (Chungbuk National University), Hwajung Hong (KAIST) — affiliations per indexed/secondary sources, not independently confirmed from the primary PDF
**Publication date:** 2026-01-20 (arXiv v1); presented at CHI 2026 (April 13–17, 2026, Yokohama, Japan)
**Venue:** ACM CHI Conference on Human Factors in Computing Systems (CHI '26); DOI 10.1145/3772318.3791166
**Paper link:** https://arxiv.org/abs/2601.13865
**Code link:** Not available (no public repository found)
**Project page:** Not available
**Date added:** 2026-08-04

*Transparency note: outbound web access in the environment that produced this post could not reach arxiv.org or general web pages directly (the network gateway returned HTTP 403 on every external host tested, including a plain connectivity check). This summary is therefore built entirely from the paper's publicly indexed abstract, the ACM listing, and search-engine-surfaced excerpts, cross-checked across multiple independent queries — not from a direct read of the full PDF. Any number or quote below should be treated as coming from secondary/indexed sources, and verified against https://arxiv.org/abs/2601.13865 before being cited elsewhere.*

---

## The problem the paper addresses

If you're going to work with one AI assistant, you just talk to it. But what if you're handed an entire *team* of AI agents — a researcher agent, a sketch-generator agent, a critic agent — and you have to decide how many of them to use, what each one's job is, and how they relate to each other and to you? This paper asks a simple but under-studied question: when ordinary people (not AI researchers) are given the tools to assemble their own team of AI agents for a creative task, how do they actually go about it — and what goes wrong?

## Why this problem matters

Most human-AI collaboration research studies one human paired with one AI. But real creative and knowledge work increasingly involves multiple specialized AI agents at once — a drafting agent, a fact-checking agent, a design agent — and someone has to decide how those agents are organized. Get the team structure wrong and you don't just get a worse answer from one model; you get agents talking past each other, duplicating effort, or nobody being responsible for judgment calls. The authors argue that "team formation" — a well-studied problem in human management — has been largely skipped over in agentic AI research, which tends to assume the agents' roles and structure are fixed by the system designer rather than shaped by the person actually using them.

## What makes the system agentic

The object of study is **CrafTeam**, a technology probe (a working research prototype, not a polished product) that lets a person assemble a **Human-Multi-Agent Team (HMAT)**: multiple LLM-based agents, each given a distinct role, that work together — and with the human — toward a shared creative goal (generating and developing design ideas). This fits the agentic definition used in this repository: the agents are goal-directed, they coordinate with each other and the human across multiple steps of an ideation process (not a single prompt-response turn), and the paper evaluates them as a *team* of acting agents rather than as a single-turn chatbot.

## How humans and the AI agent collaborate

CrafTeam's core idea is to expose **team formation itself** as something the human configures, rather than something baked into the system. Before and during each ideation session, participants could adjust:

1. **Team size** — how many agents to include
2. **Structure** — how agents relate to each other and to the human (e.g., hierarchical vs. flat)
3. **Role allocation** — what job each agent has (e.g., idea generator, critic, researcher)
4. **Member composition** — which specific agent personas/capabilities to include
5. **Shared mental models** — what context or framing all the agents (and the human) hold in common

The system then automatically assembled a working agent team based on those settings, and the human ideated with that team, watching it work and stepping in as needed.

## What role the human plays

The human is the **team architect and active collaborator**, not a passive requester. Participants repeatedly cycled through: (1) forming a team by setting the five dimensions above, (2) actually ideating with that team on a design task, and (3) reflecting on how well the team worked — then used that reflection to reconfigure the team for the next round. According to indexed findings, participants didn't settle for handing off ideation to the agents; over the course of the study they moved toward **directly orchestrating** the agents' work themselves — stepping in to make calls the agents weren't good at.

## What role the AI agent plays

The AI agents are specialized teammates, each carrying a role the human assigned (for example, an agent tasked with leading the team's direction, or one tasked with generating raw ideas). Per indexed findings, when an agent was set up to *lead* the team — i.e., to be the one deciding what direction the ideation should take — it struggled: agents had trouble making the kind of value judgments (what's a *good* idea, what's worth pursuing) that leading a creative process requires.

## How control, initiative, and decisions are shared

This is a **mixed-initiative, human-configurable** setup: the human doesn't just approve or reject agent output turn by turn — they design the very shape of the team's decision-making authority before work even starts, and can redesign it between rounds. Initiative can, in principle, sit with an agent (if it's assigned a leading role) or with the human — but the paper's central finding is about which of these arrangements people actually gravitated toward once they tried both.

## The paper's main idea

**Team formation is itself a design problem that deserves explicit support**, not an implementation detail decided by whoever builds the agentic system. The authors' framing: as multi-agent AI moves from single specialized agents into teams, the question of *how a human should assemble and structure that team* — like a manager staffing a project — is at least as important as how capable any individual agent is.

## How the approach works

CrafTeam operationalizes team formation as five configurable dimensions (listed above) and turns each configuration into a working agent team the human can actually use for a task, rather than asking people to describe an ideal team in the abstract. The three-step cycle (form → ideate → reflect), repeated multiple times per participant, was designed specifically so participants could learn from a bad team formation and try a different one — closer to how a real manager iterates on a team's composition over time.

## Human study or evaluation design

**A real, hands-on user study**, not a simulation. Twelve design practitioners currently working in design teams at IT companies used CrafTeam in what indexed sources describe as a roughly three-hour session, cycling through the form/ideate/reflect loop multiple times (reported as three iterations), each time carrying insights from the previous round into how they reconfigured their team.

## Participants and study setting

**12 real design practitioners** (not simulated personas, not crowdworkers answering a survey) recruited from design teams at IT companies — people whose day job involves the kind of creative ideation work the study task was built around. The study was a controlled, single-session lab study using the CrafTeam probe on design-ideation tasks; it was not a live workplace deployment.

## Experiments or benchmarks

There is no public benchmark here — this is a qualitative/exploratory HCI study, not a leaderboard comparison. The "experiment" is the repeated form–ideate–reflect cycle itself: each of the 12 participants went through this loop multiple times, generating a trajectory of team-formation choices researchers could analyze for patterns.

## Main results

The headline finding, per indexed sources: participants **started out trying to let agent teams operate autonomously** (including assigning an agent to lead), but **shifted toward directly orchestrating the agents themselves**. The reported reason is specific and important: agents assigned a leadership role struggled to make the value judgments and set the direction that creative idea development requires — the kind of "is this actually a good idea, and where should we take it" calls that, in this study, people were not comfortable leaving to the AI.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's outcome is best described as **qualitative and design-oriented** rather than a standardized quantitative trust/workload score. Based on available sources, the contribution is a set of **design considerations** for how HMAT-formation tools should work — informed by watching where the 12 practitioners' team structures succeeded or broke down — rather than a numeric trust/NASA-TLX-style workload measurement. We could not confirm specific statistics (e.g., satisfaction scores, time-on-task figures) from available indexed sources; readers should check the primary PDF for any such numbers.

## What is genuinely new

Most human-agent collaboration research either studies a single human-agent pair or treats a multi-agent system's internal structure as fixed by its designers. This paper is distinctive in treating **team formation as something the human user actively designs**, iteratively, and in showing — with real practitioners rather than a simulated study — a concrete behavioral pattern: people default toward wanting some autonomy from their agent team, but pull back toward direct orchestration once they see that agents can't reliably make the judgment calls a creative "lead" role requires.

## Limitations and open questions

- **Small sample and single domain:** 12 practitioners, one ~3-hour session, one kind of creative task (design ideation). It's unclear whether the same pull toward orchestration would hold for longer-horizon, non-creative, or higher-stakes agentic teamwork (e.g., software engineering or operations).
- **Exploratory, not confirmatory:** this is a technology-probe study meant to surface design considerations, not a controlled experiment isolating which of the five dimensions matters most.
- **No standardized quantitative human-factors metrics** (trust, workload, cognitive load) are confirmed from available sources — the findings are primarily qualitative/behavioral.
- This summary could not independently verify exact statistics, the full discussion section, or fine-grained methodology against the primary PDF, due to network restrictions in the environment that produced it. Verify against https://arxiv.org/abs/2601.13865 before citing specifics.

## Practical implications

For anyone building tools that let people assemble teams of AI agents (multi-agent copilots, agent "staffing" interfaces, orchestration dashboards), this paper's practical suggestion is: **don't assume users want to hand a team an autonomous leader.** Build in easy, iterative ways for people to reconfigure team structure and step into a direct-orchestration role — because based on this study, that's where practitioners actually converge once they've tried the alternative.

## Why you should care

As agentic AI moves from "one assistant" to "a team of specialized agents," the unglamorous question of *who's in charge of the team, and how it's structured* turns out to matter a lot — and this paper is one of the few to study that question with real practitioners actually trying to manage such a team, rather than assuming the answer in advance. Its central, human-observed finding — that people try full autonomy first and then pull the team back under their own direction once an AI "lead" can't make good creative judgment calls — is a useful, concrete data point for anyone designing how humans and multi-agent AI teams should share control.

---

*Author's note on selection: this paper was chosen after comparing it against several 2026 candidates, including a benchmark evaluating "configurable human participation" via simulated personas rather than real people (excluded per this repository's criteria), a participatory-design UX-principles study that did not evaluate a specific working agentic system, a randomized controlled trial of clinician-AI collaboration that used a single-turn diagnostic-synthesis tool rather than a multi-step agentic system, and a methodological paper whose only "human" role was expert annotators labeling risk levels. This paper was the strongest candidate found with both a real, hands-on human-participant study and a clearly agentic (multi-agent, goal-directed, multi-step) system at its center, even though its arXiv v1 predates the last-30-days window; no comparably strong very-recent candidate was found in this run's search.*
