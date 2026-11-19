**Paper title:** Foundations of Proactive Agents: Principles, Technical Layers, and Proactivity-Gym
**Authors:** Jio Oh, Seunghyun Do, Steven Euijong Whang (KAIST); Young-Jun Lee, Dongyeop Kang (University of Minnesota)
**Publication date:** 2026-09-29 (arXiv v1)
**Venue:** arXiv preprint; formal conference/journal acceptance not confirmed
**Paper link:** https://arxiv.org/abs/2609.37267
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-11-19

---

# When Your AI Assistant Decides to Help Without Asking, Does It Earn Your Trust — or Burn It?

## The problem the paper addresses

A growing number of AI agents don't wait to be asked. They notice you're about to miss a deadline and draft the email for you; they see an error in your code and quietly fix it; they decide, on their own, that now is a good moment to step in. This is "proactive" behavior, and it's quickly becoming a selling point for AI assistants. But almost all existing research and evaluation of AI agents focuses on *reactive* agents — ones that wait for a request and then execute it well. The authors argue nobody has laid out a clear, tested foundation for what makes a *proactive* agent actually good at its job: knowing not just *what* to do, but *whether*, *when*, and *how* to step in without being asked.

## Why this problem matters

An agent that barges in with help at the wrong moment isn't just unhelpful — it can be actively harmful to the relationship between a person and their AI tool, even when the help itself is correct. Imagine a coworker who finishes your sentence in a meeting, every meeting: technically right, but the "help" erodes something even as it (occasionally) saves time. As agents gain the ability to act continuously in the background — monitoring inboxes, codebases, calendars — the risk of this kind of unwanted interruption scales with how much autonomy we give them. Getting proactive timing and judgment wrong at scale could quietly poison people's willingness to rely on AI tools at all, even ones that are otherwise highly capable.

## What makes the system agentic

The paper studies LLM-based agents that operate inside simulated multi-day environments, built on real agentic coding/assistant "harnesses" (including Claude Code, Codex, and OpenClaw). These agents don't just answer a single question: they monitor a stateful environment over time, decide on their own initiative whether an intervention is warranted right now, choose when to spend compute (immediately vs. deferring work to idle periods), and take multi-step actions to actually produce the help they've decided to offer. The paper evaluates them as agents — on their *decisions* about whether/when/how to act — not merely on single-turn answer quality.

## How humans and the AI agent collaborate

This is a mixed-initiative relationship in its purest form: the agent, not the human, decides when to initiate a help episode. The human's role is to receive, judge, and respond to that initiative — accepting the help, rejecting it, or reacting to its timing — rather than to issue the triggering request. The paper's central claim is that this kind of collaboration can't be judged by task success alone, because the *manner and timing* of the agent's initiative itself shapes whether the human wants to keep collaborating with it at all.

## What role the human plays

In the paper's human study, 30 participants (8 undergraduates, 16 graduate students, and 6 working professionals) played the role of the person being proactively helped. Across 14 different scenarios, they judged whether and how they wanted an agent's unsolicited assistance — for example, choosing whether to accept help that arrived while they were in the middle of other work, versus help that was deferred to "sleep time" (a quiet period, like overnight) and ready for them later. Participants also reported how specific kinds of interventions affected their trust in the agent going forward.

## What role the AI agent plays

The proactive agent is the one with the initiative: continuously or periodically assessing the state of a multi-day scenario, deciding for itself whether there's a need worth addressing, choosing when to allocate its own effort (now vs. later), and then carrying out the task well enough to be useful once it does decide to act.

## How control, initiative, and decisions are shared

Initiative sits almost entirely with the agent — it decides whether, when, and how to intervene without being asked. But the human retains the downstream power that matters most: whether to accept the offered help, and crucially, how much they trust the agent afterward. The paper frames this as a three-way balancing act it calls "3T": **Task Capability** (can the agent correctly anticipate a real need and do the work well), **Temporal Allocation** (does it spend its effort at a sensible time, relative to resources and urgency), and **Trust** (does it sustain the human's confidence and avoid being relied on inappropriately). An agent can succeed at the task and still fail the collaboration if it gets the timing or trust dimension wrong.

## The paper's main idea

The authors argue that evaluating proactive agents purely on "did it produce the right output" misses the point, because *when* and *how* an agent inserts itself matters as much as *what* it produces. They propose the 3T framework as the missing foundation for designing and evaluating proactive agents, and they build a testbed, Proactivity-Gym, specifically to probe this timing-and-trust dimension that conventional benchmarks ignore.

## How the approach works

Proactivity-Gym is a simulation environment with multi-day, stateful scenarios and persona-conditioned simulated users, letting the authors run large-scale automated evaluations of many model/harness combinations (the paper reports 23 configurations spanning 9 models across 3 agent harnesses — Claude Code, Codex, and OpenClaw). Within this environment, agents must decide on their own whether a situation warrants proactive action, and if so, when to act and how to allocate compute between immediate and deferred ("sleep-time") effort. Separately, and central to the paper's human-centered claims, the authors ran a study with real human participants to see how people actually respond to and are affected by these intervention choices — the simulated-user benchmark measures the agents' behavior at scale, while the human study measures the human side of the relationship.

## Human study or evaluation design

Thirty real participants rated their reactions across 14 proactive-intervention scenarios. Scenarios varied along at least two axes highlighted in the results: whether the agent's help arrived while competing with the person's ongoing work, versus being deferred to a quiet "sleep-time" slot; and whether the help delivered was correct outright or needed the person's correction afterward. Participants reported acceptance decisions for each type of intervention and, separately, how a misaligned intervention affected their trust in the agent going forward.

## Participants and study setting

The 30 participants were a mix of 8 undergraduate students, 16 graduate students, and 6 working professionals. The study appears to have been a structured scenario-rating exercise (participants responding to a fixed set of 14 intervention scenarios) rather than a live, extended deployment; specific recruitment details, compensation, and demographic breakdown beyond the group counts were not confirmed from the sources available for this summary.

## Experiments or benchmarks

Two evaluation tracks: (1) the Proactivity-Gym benchmark, where 23 model-harness configurations were tested on multi-day simulated scenarios with simulated (not real) users, to measure agents' automated decisions about whether/when to intervene; and (2) the 30-person human study described above, which measured real people's acceptance and trust reactions to specific intervention patterns. No public, pre-existing benchmark dataset is reused — both the simulation environment and the human-study scenarios appear to be purpose-built for this paper.

## Main results

On the human side: participants accepted help that was correct but arrived while competing with their ongoing work only about 26.7% of the time. By contrast, they accepted deferred "sleep-time" help that still needed their correction the next morning about 97.8% of the time — and even when that overnight help needed revision, 64.4% of cases still favored having received it that way over immediate, in-the-moment interruption. The authors also report that a single misaligned intervention sharply reduced participants' subsequent trust in the agent, even when the task outcome itself was correct. On the benchmark side, the authors report that even the strongest tested model-harness configurations left substantial gaps in temporal allocation and intervention alignment, and that automated LLM-judge evaluations tended to conflate "did it do the task well" with "did it handle the human relationship well" — two things the paper argues must be measured separately.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's headline human-centered finding is about trust, not raw task performance: getting the *timing* of an intervention wrong — interrupting someone mid-task rather than deferring to a quiet period — cost the agent trust even when its output was correct, and that trust damage did not require the agent to be wrong, only badly timed. Conversely, participants were strikingly tolerant of imperfect help when it was offered at a low-cost moment (deferred, "sleep-time" delivery), accepting it the large majority of the time even knowing it might need fixing. This suggests that, at least in this study population and these scenarios, *when* help arrives shapes acceptance and trust more than *whether* it's perfect.

## What is genuinely new

*Authors' claims:* The authors present the 3T framework (Task Capability, Temporal Allocation, Trust) as a new, unifying way to think about what makes proactive agents good, and Proactivity-Gym as the first testbed purpose-built to probe this timing/trust dimension rather than just task correctness. They also claim that existing LLM-judge-based evaluation approaches systematically conflate task quality with relationship/trust quality.

*Demonstrated results:* The paper does show, with a real (if modest) human sample, a measurable gap between acceptance rates for immediate versus deferred help (26.7% vs. 97.8%), and a qualitative but clearly reported finding that a single poorly timed intervention can sharply dent trust regardless of correctness.

*Our interpretation:* This is best read as an early, foundational framing paper rather than a definitive, large-scale field study — it's proposing vocabulary and a testbed for a problem (proactive timing and trust) that the field hasn't had good tools to study, and backing it with a modestly sized but real human study plus a much larger simulated-user benchmark.

## Limitations and open questions

The human study is relatively small (N=30) and scenario-based rather than a longitudinal, real-world deployment, so it's unclear how these acceptance and trust patterns would hold up over weeks or months of actual use, across more diverse populations, or in higher-stakes domains. The large-scale model benchmark relies on persona-conditioned simulated users rather than real people, so its "gaps in temporal allocation and intervention alignment" findings are about model behavior, not confirmed human reactions, at that scale. The paper itself does not appear to report a peer-reviewed venue, and exact statistical significance testing for the human-study numbers was not confirmed from the sources used for this summary.

## Practical implications

For anyone designing a proactive AI assistant — a coding agent that offers unsolicited fixes, a calendar agent that reschedules things, a meeting agent that surfaces information unprompted — this paper's practical lesson is that *when* an agent interrupts may matter more to user trust than getting every intervention perfectly correct. A design pattern worth taking seriously: default to deferring non-urgent help to low-cost moments (overnight, between tasks) rather than interrupting active work, since people in this study tolerated imperfect deferred help far more readily than they tolerated correct-but-interrupting help.

## Why you should care

If you build, deploy, or just use AI tools that act on their own initiative, this paper is a useful reminder that proactivity is a double-edged design choice: it can save real time and effort, but it introduces a brand-new failure mode — damaged trust — that has nothing to do with whether the AI got the task right. As more agents gain the autonomy to act without being asked, understanding (and testing for) this timing/trust tradeoff, rather than just task accuracy, may be essential to whether people actually keep using them.
