# Code Got Cheap. Judgment Didn't: A 12-Week Field Study of Governing an AI Coding Agent

**Paper title:** Cheap Code, Costly Judgment: A Case Study on Governable Agentic Software Engineering
**Authors:** James C. Davis, Paschal C. Amusuo, Tanmay Singla, Berk Çakar, Kirsten A. Davis (Purdue University)
**Publication date:** 2026-07 (arXiv v1; exact day not independently confirmed — sources vary between 2026-07-01 and 2026-07-04)
**Venue:** arXiv preprint (cs.SE); peer-review status not confirmed
**Paper link:** https://arxiv.org/abs/2607.01087
**Code link:** Not available (no public repository confirmed from available sources)
**Project page:** Not available
**Date added:** 2026-08-23

*Note on sourcing: direct access to the arXiv PDF was not possible from this environment (arxiv.org is blocked by the network policy in place here). This summary is built from the paper's abstract and from multiple independent secondary descriptions of its content and framework (including tech-press coverage of the paper). Specific quotes, numeric breakdowns, and the full limitations section that would normally come from a direct PDF read are not available — anything not explicitly confirmed is marked as such below. Readers who want the primary source should consult the paper directly.*

---

## The problem the paper addresses

For most of software engineering history, writing code was the expensive, slow part. Reviewing, testing, and maintaining it was comparatively cheap by comparison — you only had so much code to check because a human could only write so much of it. Frontier AI coding agents (the Claude Code / Cursor / GitHub Copilot agent-mode family of tools) just broke that assumption: a single engineer can now direct an AI agent to produce code far faster than any team of humans typing by hand. The paper's core question is not "can AI generate useful code?" — that's now assumed — but a much harder one: once code is nearly free to produce, how do engineers organize their tools, processes, and evidence so that all of that AI-generated work stays *inspectable, correctable, and maintainable* rather than turning into an unmanageable pile that nobody, human or AI, can safely touch?

## Why this problem matters

Cheap, abundant code sounds like a pure win until you ask who is accountable when it breaks, who can explain why it works the way it does, and who can safely change it six months later. If code production outpaces an organization's ability to govern it — to review it, test it, document it, and hold someone responsible for it — then speed becomes a liability rather than an asset. This is especially high-stakes in the paper's own case study domain: the system built during the study is a *document accessibility remediation* tool, i.e., software meant to help make digital documents usable for people with disabilities. Governance failures in that kind of system have direct human consequences, not just abstract "technical debt."

## What makes the system agentic

The subject of this case study is not a demo agent solving toy benchmarks — it's frontier AI coding agents used the way an expert engineer actually works day-to-day: autonomously planning implementation steps, writing and editing files across a large codebase, running tests and lints, and iterating over an extended real project. Over 12 weeks this produced 420,000 lines of production code plus 1.16 million lines of tests, lint configuration, documentation, and supporting agent tooling — a genuinely large, real-world, multi-step body of agentic work, not a single prompt-and-response exchange.

## How humans and the AI agent collaborate

This is a first-person case study: one of the paper's authors is the expert software engineer who did the work, using frontier AI coding agents as his day-to-day implementation partner across the full 12-week project. The collaboration was continuous and hands-on rather than a one-off "delegate and check back later" arrangement — the engineer directed the agents, watched what they produced, and had to decide, incident by incident, how to respond when agentic output created a governance problem (an inconsistency, an untested edge case, an architectural drift, an unclear rationale for a change, and so on).

## What role the human plays

The engineer supplies judgment: deciding what to build, evaluating whether agent-produced code is trustworthy, catching and diagnosing recurring failure patterns, and — critically — converting each recurring failure into a durable safeguard (a new test category, a stricter lint rule, a documentation requirement, a changed workflow) rather than just patching the same problem over and over. The paper frames this as the scarce resource in the new equation: code got cheap, but the judgment needed to keep that code governable did not.

## What role the AI agent plays

The AI agents are the high-velocity implementers: generating the bulk of the 420 KLOC of production code and much of the surrounding test/documentation scaffolding, at a pace no human-only team could match. In the paper's framing, the agents are not passive tools waiting for instructions at every step — they carry out substantial chunks of implementation independently, which is exactly what creates the governance challenge the paper studies: fast, largely autonomous output that a human still has to keep inspectable and correctable.

## How control, initiative, and decisions are shared

The paper's central theoretical contribution — a candidate "middle-range theory" the authors call **governance conversion** — is essentially a model of how initiative shifts back and forth between agent and engineer over time. The agent takes the initiative during implementation, moving fast and producing large volumes of code and tests. When that speed surfaces a recurring structural failure (a class of problem that keeps showing up across incidents, not a one-off bug), the human engineer takes the initiative to convert that discovered failure into a lasting governance mechanism — a rule, a test, a check, a piece of tooling — that then constrains and shapes how future agentic work happens. Reported secondary descriptions of the paper indicate this framework rests on thirteen cross-incident themes organized into four clusters, three of which ground the core theory (abundant implementation but scarce judgment; governance relocated into the technical "substrate" itself; and the practice of engineering the system to be legible to the agent working on it) and a fourth that characterizes the first-person, reflexive nature of the study method itself.

## The paper's main idea

Existing models of software governance typically start from known obligations (compliance requirements, security policies) and derive controls from them in advance. This paper argues that agentic development needs something different: a way of discovering necessary controls *from failures that only become visible once you're actually doing high-velocity agentic work* — you can't fully anticipate them ahead of time. Governance, in this account, isn't a static checklist applied before development starts; it's a conversion loop that runs continuously, turning newly discovered failure patterns into new durable safeguards as the project goes.

## How the approach works

The methodology is a first-person, autoethnographic case study: as the engineer worked, they kept 88 contemporaneous field notes documenting incidents, decisions, and reasoning in real time (not reconstructed afterward from memory). The authors then analyzed this record — together with the resulting 420 KLOC of production code and 1.16 MLOC of tests, lints, documentation, and agent tooling — to inductively derive the recurring themes and the resulting governance-conversion process model. This is qualitative, theory-building research in the software-engineering case-study tradition, not a controlled experiment or benchmark evaluation.

## Human study or evaluation design

There is no separate recruited-participant study here; the "human" being studied is the author-engineer themselves, and the evaluation is the real, 12-week construction of a real production system rather than a lab task. This makes the human evidence genuine and richly documented (contemporaneous field notes over an extended real project) but drawn from a single individual, which the paper's own case-study framing openly treats as its unit of analysis rather than something it disguises.

## Participants and study setting

**One expert software engineer** (a co-author of the paper), working over **12 weeks** to build a real document accessibility remediation system using frontier AI coding agents. This is a single-subject, real-world field setting — not a lab study with multiple recruited participants, and not a simulated task.

## Experiments or benchmarks

None in the sense of a leaderboard or a benchmark suite. The "data" is the empirical record of the project itself: 88 field notes, 420 KLOC of production code, and 1.16 MLOC of tests/lints/documentation/tooling, analyzed to build the governance-conversion theory.

## Main results

**As reported by the authors (via the abstract and secondary descriptions; the full results section was not directly accessible from this environment):**
- Agentic implementation velocity reliably surfaces recurring, cross-incident *classes* of governance failure — not just isolated one-off bugs.
- Sustained engineering judgment is what converts those recurring failures into durable governance mechanisms (tests, lints, documentation practices, tooling changes), allowing the project to keep its high implementation velocity without losing inspectability or maintainability.
- The resulting "governance conversion" process model is offered as a candidate middle-range theory — the authors' own words frame it as a *candidate* theory, i.e., an initial, evidence-grounded proposal meant for further testing, not a settled, universally validated finding.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's contribution here is process-level and qualitative rather than a measured before/after comparison: it documents *how* one expert engineer's judgment work evolved and what governance mechanisms emerged, rather than quantifying, for example, time saved, defect rates avoided, or a trust score. **Interpretation (ours, not the paper's):** because this is a single-subject account, it should be read as rich, detailed evidence of what governance work with agentic coding tools can look like in the hands of an expert — not as a generalizable measurement of typical outcomes across engineers or organizations.

## What is genuinely new

Most existing discussion of "AI coding agent governance" is either aspirational (frameworks describing what oversight *should* look like) or focused on whether the agent's output is correct in the moment. This paper's contribution is a grounded, empirically derived process model of how governance *itself gets built* over time, incident by incident, as a byproduct of sustained real-world use — reframing the challenge from "is this code correct?" to "how do engineers keep a fast-moving agentic system correctable and accountable as it evolves?"

## Limitations and open questions

The most obvious limitation, which the case-study design makes unavoidable, is that the evidence comes from a single expert engineer on a single project in a single domain (document accessibility tooling). The theory is explicitly offered as a *candidate* middle-range theory rather than a validated, generalizable one — an invitation for other researchers and practitioners to test whether the same governance-conversion pattern holds for other engineers, teams, domains, and agentic tools. A specific, detailed limitations/threats-to-validity section may exist in the full paper but was not independently accessible from this environment; readers should consult the primary source for the authors' own stated caveats.

## Practical implications

For engineering teams adopting AI coding agents at scale, the paper's framing offers a concrete lesson: don't expect governance to be something you fully design up front and then apply. Expect instead to run a continuous loop — watch for recurring failure patterns as agentic velocity increases, and treat each one as a signal to build a new, durable safeguard (a test category, a lint rule, a documentation habit, a piece of tooling) rather than a one-off fix. That reframes the job of a senior engineer working with agentic tools as much more about judgment, pattern recognition across incidents, and governance design than about hands-on code authorship.

## Why you should care

This paper is a rare thing: a detailed, real-world, extended account of what it actually takes for one skilled engineer to keep a genuinely fast-moving AI-agent-built system safe, inspectable, and maintainable — not a lab experiment, and not a speculative framework. If your own work involves directing coding agents on real projects, the "governance conversion" idea — that the failures you hit along the way are themselves the raw material for the safeguards you should build — is a practical mental model worth testing against your own experience, even though it comes from an n=1 case study rather than a large trial.

---

*Claims attributed to "the authors" or "the paper" reflect what is stated in arXiv:2607.01087's abstract and in independently cross-checked secondary descriptions of its content; passages marked as interpretation are the summary writer's own reading and are not asserted by the paper itself. Because the full PDF could not be directly fetched in this environment, some paper-level detail (exact limitations wording, specific incident examples, any numeric breakdowns beyond the codebase-size figures in the abstract) could not be independently verified and has been omitted rather than guessed.*
