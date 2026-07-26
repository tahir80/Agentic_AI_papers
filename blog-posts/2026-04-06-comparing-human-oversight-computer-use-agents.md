# Comparing Human Oversight Strategies for Computer-Use Agents

**Authors:** Chaoran Chen, Zhiping Zhang, Zeya Chen, Eryue Xu, Yinuo Yang, Ibrahim Khalilov, Simret A. Gebreegziabher, Yanfang Ye, Ziang Xiao, Yaxing Yao, Tianshi Li, Toby Jia-Jun Li (affiliations include University of Notre Dame and collaborating institutions; full institutional list not independently confirmed from available sources)
**Publication date:** 2026-04-06 (arXiv id 2604.04918, cs.HC)
**Venue:** arXiv preprint; formal venue and peer-review/acceptance status not confirmed from available sources
**Paper link:** https://arxiv.org/abs/2604.04918
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-07-26

> **A note on sourcing:** arXiv is not reachable from this research session's network (outbound web fetches are blocked by the session's egress policy), so this summary is built from web-search-indexed excerpts of the paper's abstract and HTML text rather than a full read of the PDF. Claims below are flagged as authors' claims where the underlying numbers could not be independently verified; anything not confirmed through available sources is marked "Not available."

---

## The problem the paper addresses

Computer-use agents (CUAs) — AI systems that can click, type, and navigate a real computer on a person's behalf — are moving people from *doing* the work themselves to *supervising* an agent that does it. But according to the authors, most existing oversight mechanisms (approve-every-click dialogs, plan previews, risk flags, and so on) have been designed and studied one at a time, as isolated interface features. That makes it hard to answer a more basic question: considered as whole strategies, which ways of overseeing a CUA actually work better, and at what cost?

## Why this problem matters

If oversight is the thing that's supposed to keep a person in control of an autonomous agent, then the specific *shape* of that oversight — when it interrupts you, what level of detail it shows you, how much it asks you to approve — determines whether you actually catch a mistake before it happens, or only after the damage is done. Get the design wrong, and "human oversight" becomes a box-ticking exercise rather than a real safety net; over-design it, and it can bury people in low-value interruptions until they stop paying attention (a pattern documented in related work on oversight fatigue).

## What makes the system agentic

The paper studies LLM-powered computer-use agents operating in a live web environment — software that plans and executes multi-step actions (clicking, typing, navigating between pages) to complete a task on a real website, rather than just answering a question in text. Participants worked with these agents on real, multi-step tasks, and the paper's central concern is how people supervise that ongoing, autonomous execution — an agent-level question, not a language-model one.

## How humans and the AI agent collaborate

The authors frame CUA oversight along two dimensions that jointly define a "design space" of strategies:
- **Delegation structure** — how much the agent acts on its own before checking in, from *agent-led* (the agent acts by default and only escalates to the human under specific conditions) to *human-controlled* (the human must authorize every action before it proceeds).
- **Engagement level** — the level of the workflow at which the human's attention is organized, from low-level, step-by-step action traces up to high-level plans.

Four concrete oversight strategies were placed in this space and compared head-to-head: **Risk-Gated** (the interface surfaces the agent's current focus and reasoning and only interrupts when it detects a risky action), **Supervisory Co-Execution** (the human maintains ongoing oversight via coordinated views — a plan-review panel, a hierarchical execution trace, and explicit approval controls), **Action-Confirmation** (every individual action requires per-action human approval regardless of risk level), and a fourth, more plan/structure-oriented condition (its exact name could not be independently confirmed from available sources).

## What role the human plays

Depending on the condition, the human ranges from an approval gate who signs off on each click, to a supervisor monitoring a running plan and stepping in only when flagged, to a reviewer working mainly at the level of the agent's overall plan rather than its individual actions. Across all conditions, the human's core job is the same: notice when the agent is about to do (or has done) something problematic, and intervene to correct it.

## What role the AI agent plays

The CUA is the one actually doing the work — interpreting the task, deciding on and executing a sequence of on-screen actions in a live web environment — while surfacing varying amounts of information about its reasoning, plan, and individual steps depending on which oversight strategy is active.

## How control, initiative, and decisions are shared

This is a direct study of **human oversight of a semi-autonomous agent**, manipulated experimentally: the same underlying agent is paired with four different oversight regimes that shift where control sits along the delegation-structure and engagement-level axes — from tight, per-action human control to looser, plan-level supervision with agent-initiated escalation. That makes it one of the more systematic attempts in this literature to compare oversight *strategies* as coordination structures, rather than testing one interface design against a single baseline.

## The paper's main idea

**Claim by the authors:** oversight strategy, considered as a whole, matters most for *whether a person is ever exposed to* a problematic agent action in the first place — not necessarily for whether they're able to fix it once they see it. Plan-level, more agent-led strategies tended to reduce how often problematic actions occurred at all, but didn't produce equally large gains in a person's ability to successfully intervene once a problem became visible. In other words, prevention and correction are separate capabilities that different oversight designs trade off differently.

## How the approach works

The authors built a live web environment in which a CUA carries out real multi-step tasks, then instrumented four distinct oversight interfaces corresponding to the four strategies described above (Risk-Gated, Supervisory Co-Execution, Action-Confirmation, and the fourth plan-oriented condition). Participants used the same underlying agent under each condition and were measured on both objective outcomes (did a problematic action occur, and was it caught/corrected) and subjective outcomes (trust and other self-reported measures), in a mixed-methods design combining quantitative comparison with qualitative feedback.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, mixed-methods, within- or between-subjects comparison (exact design not confirmed from available sources) of four oversight strategies, run with real participants completing real multi-step tasks with a live CUA — not a simulated-user or benchmark-only evaluation.

## Participants and study setting

**Confirmed:** 48 participants completed tasks in a live web environment. Further demographic and recruitment details (e.g., professional background, compensation, session length) are **not available** from the sources accessible in this session.

## Experiments or benchmarks

No public leaderboard-style benchmark is used; the evaluation is a custom, study-specific live web environment built to let a real CUA complete multi-step tasks under each of the four oversight conditions.

## Main results

**Authors' claims (exact statistics not independently confirmed from available sources):**
- Oversight strategy shaped **exposure** to problematic agent actions more reliably than it shaped people's **ability to correct** those actions once they became visible.
- Plan-based (more agent-led, higher-engagement-level) strategies were associated with **fewer** problematic actions occurring in the first place, but did not translate into correspondingly large improvements in successful runtime intervention once such an action did surface.
- On subjective measures, **no single strategy was uniformly best** — the strategies produced distinct tradeoffs, and the clearest, most context-sensitive differences between strategies showed up specifically in participants' **trust**.

## Effects on human performance, trust, workload, safety, or decision quality

**Authors' claims:** the study's core dependent variables are (a) the rate at which problematic agent actions occurred, (b) whether/how successfully participants intervened once such an action was visible, and (c) subjective measures including trust. The headline finding is a dissociation between prevention and correction — a strategy that keeps people safer by reducing problems upstream is not automatically the same strategy that best equips them to catch and fix problems that do slip through. **Our interpretation:** this echoes a theme surfacing elsewhere in this collection (e.g., trace-design studies of post-hoc verification) — that "more oversight" or "better-designed oversight" does not move safety and correction-capability in lockstep, and product designers may need to pick a strategy based on which failure mode (prevention vs. correction) matters more for a given task's stakes.

## What is genuinely new

- A design-space framing (delegation structure × engagement level) that lets oversight strategies for CUAs be compared as coherent wholes rather than one interface feature at a time.
- A head-to-head, same-agent comparison of four named oversight strategies (Risk-Gated, Supervisory Co-Execution, Action-Confirmation, and a fourth, plan-oriented condition) in a live web environment with real users.
- Evidence that exposure to problems and the ability to correct them are separable outcomes that different oversight strategies affect differently — a more fine-grained result than a single "did the human catch the error" metric would show.

## Limitations and open questions

- Exact quantitative results (rates, effect sizes, statistical tests), participant demographics, task domain(s), and session structure could not be confirmed from the sources accessible in this session; readers should consult the paper directly for these details.
- As with any lab-based live-environment study, findings may not generalize to longer-horizon, higher-stakes, or field-deployed CUA use.
- The paper itself reportedly frames existing oversight research as fragmented across isolated interface features — its own four-strategy comparison, while broader, is still a bounded slice of the much larger space of possible oversight designs.

## Practical implications

For teams building computer-use agent products (browser agents, OS-level assistants, enterprise workflow agents), this paper's core practical suggestion is that oversight strategy should be chosen deliberately based on which risk matters more for the deployment context: strategies that front-load prevention (reducing how often bad actions happen) are not necessarily the same strategies that best support in-the-moment correction once something does go wrong — so a single "add an approval dialog" pattern may not be the right answer for every product.

## Why you should care

As CUAs move from demos into everyday tools, the design of the oversight layer around them — not just the underlying model — will shape how safe and trustworthy these systems feel and actually are in practice. This paper offers one of the more structured, real-user comparisons of oversight *strategies* (rather than single features) in this collection, and its central finding — that preventing problems and correcting them are not the same thing, and no single strategy wins at both — is a concrete, actionable caution for anyone choosing how much and what kind of human oversight to build into an agentic product.
