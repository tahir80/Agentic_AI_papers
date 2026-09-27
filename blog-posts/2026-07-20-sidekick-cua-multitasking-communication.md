# Your AI Agent Is Working in the Background — Do You Know What It's Doing?

**Title:** Sidekick: Designing Communication for Effective Multitasking with Computer Use Agents
**Authors:** Ruei-Che Chang, Wenqian Xu, Anhong Guo (University of Michigan); Dingzeyu Li, Bryan Wang (Adobe Research)
**Publication date:** 2026-07-20 (arXiv v1)
**Venue:** Accepted to ACM UIST 2026 (39th ACM Symposium on User Interface Software and Technology), November 2–5, 2026, Detroit, MI; arXiv preprint (cs.HC)
**Paper link:** https://arxiv.org/abs/2607.17527
**Code link:** Not available
**Project page:** Not available (the lead author's personal site lists the paper with PDF/arXiv/video links, but a stable direct URL to a dedicated project page could not be confirmed)
**Date added:** 2026-09-27

> **A note on sourcing:** direct network access to arxiv.org and the usual mirrors was blocked at the network egress layer of the environment this summary was written in — this is an environment restriction, not a paywall; the paper itself is a public, open-access arXiv preprint. This write-up is built from cross-checked search-engine excerpts of the paper's abstract, stated methodology, and reported figures (including specific NASA-TLX numbers and study design details that appeared consistently across independent queries), rather than a direct read of the full PDF. Anything that could not be corroborated this way is marked "not available" or "not confirmed." Readers who want the complete method section, full statistics, and all design details should consult the arXiv preprint directly.

---

## The problem the paper addresses

"Computer Use Agents" (CUAs) — AI systems that can see a screen and click, type, and navigate through software just like a person — are increasingly able to run whole multi-step jobs on their own: filling in a spreadsheet, filing a form, moving files around. That autonomy is supposed to free people up to do something else while the agent works. But the paper points out an obvious snag: most CUAs currently tell you what they're doing (and what they've done) through a plain text chat log. If you're off doing other work while the agent runs in the background, catching up on a scrolling wall of text later is tedious, and it's genuinely hard to tell — at a glance — whether the agent is still working, has finished, or has quietly gone off the rails.

## Why this problem matters

The whole promise of a computer-use agent is that a person can hand it a task and go do something else — that's what "multitasking with an agent" means in practice. But if the only way to check on the agent is to stop what you're doing and read through its running commentary, the supposed time savings evaporate, and worse, people may either over-monitor (checking constantly, defeating the point of delegating) or under-monitor (missing a mistake the agent made, like a wrong number typed into a spreadsheet cell, until it's too late). Getting this feedback loop right is a precondition for computer-use agents to be genuinely useful collaborators rather than one more thing demanding constant attention — which is exactly why interface design for human oversight of these agents, not just the agents' raw capability, is the subject of active HCI research right now.

## What makes the system agentic

The CUA at the center of this paper fits the paper's own framing squarely: it "autonomously execute[s] complex, multi-step tasks within GUIs." In the study, the agent is given a data-entry-and-arithmetic task on a spreadsheet and carries it out step by step — reading cells, typing values, computing sums — without a human doing each click. It operates in two modes the paper explicitly designs around: running in the **background** while the human works on something else, and running in the **foreground** while the human watches. It is evaluated not as a one-shot question-answerer but as a semi-autonomous actor inside a live GUI environment, including being deliberately made to make mistakes so the researchers could study whether and how people catch them — which is what makes this a study of human oversight of an agent, not just a chatbot exchange.

## How humans and the AI agent collaborate

The human hands the agent a job (in the study: filling in and computing values across spreadsheet columns), then splits attention between that delegated task and other work. The system, called **Sidekick**, is the communication layer sitting between the two: it doesn't change what the agent can do, but it changes how the agent reports on itself, adapting the reporting style to what phase of interaction the human and agent are currently in.

## What role the human plays

The human is the delegator and supervisor: deciding to hand off a task, doing other work while the agent runs, periodically checking in on progress, and — critically — catching and correcting the agent when it makes a mistake. In the study, the researchers intentionally had the CUA introduce errors into the spreadsheet task, so the human's monitoring and intervention behavior could actually be measured rather than assumed.

## What role the AI agent plays

The CUA executes the delegated multi-step GUI task on its own, in the background or foreground as the situation calls for, and — via Sidekick — communicates its status back to the human in three different ways depending on what's happening: quiet ambient signaling while unattended, a catch-up summary when the human returns their attention to it, and live, spoken-and-visualized narration of its own reasoning when the human is actively watching it work.

## How control, initiative, and decisions are shared

This is a clean example of **mixed-initiative, phase-adaptive shared oversight**: the agent has the initiative to act autonomously (including out of the human's direct sight), but the human retains supervisory authority and the ability to intervene at any point, and the *system's job* is to make sure the human has just enough information, at just the right moments, to exercise that authority without being forced to babysit the agent constantly. Control isn't split by task — it's split by **interaction phase**: ambient awareness while away, a resumption briefing on return, and close, transparent supervision when directly watching.

## The paper's main idea

**Claim by the authors:** the reason current CUA feedback fails to support effective multitasking isn't that it's absent, but that it's the *wrong shape* for how human attention actually moves during multitasking — mostly plain text requiring sustained reading, regardless of whether the human is away, just returning, or actively watching. Their proposed fix is to match the feedback modality to the attentional phase: ambient/peripheral cues when unattended, multimodal (visual + spoken) summaries at the moment of return, and verbalized/visualized live reasoning during active foreground supervision.

## How the approach works

The authors first ran a **formative study** with CUA experts and everyday GenAI users to characterize what was missing from existing chat-style feedback (the authors report this identified that current feedback is largely text-based, demands sustained attention, and offers poor visibility into past actions once the user looks away). From those findings they built the **Sidekick** prototype with three linked feedback layers: (1) ambient cues (the authors describe color-coded signaling) that communicate the agent's execution state while it runs unattended in the background; (2) a multimodal summary — combining visual and spoken elements — delivered when the human resumes attention, to support quick reorientation without reading a full transcript; and (3) verbalized narration plus on-screen visual annotation of the agent's reasoning when it is operating in the foreground under direct observation.

## Human study or evaluation design

The authors ran a **within-subjects controlled lab study** comparing four conditions on the same underlying task: (1) **manual** — the human does the task alone with no CUA; (2) a **chat-style baseline**, where the CUA reports through a typical text chat; (3) a **peripheral-text** condition, where similar text feedback is shown in an ambient/peripheral display rather than a chat window; and (4) **Sidekick**, the paper's full multimodal, phase-adaptive design. Every participant experienced all four conditions, letting the researchers compare feedback designs head-to-head rather than just comparing "with agent" to "without agent."

## Participants and study setting

**30 participants** took part in the controlled comparison study (the formative study that shaped Sidekick's design drew on a separate, smaller group of CUA experts and GenAI users, whose exact count was not confirmed from the sources used for this summary). Demographic details of the 30 participants were not confirmed from the sources available. The task itself: a CUA was set to fill in spreadsheet columns with data-entry and arithmetic work — three columns of 16 entries each — and the researchers had it deliberately introduce two errors per column, so they could measure whether and how quickly participants, under each feedback condition, noticed and corrected those mistakes while also working on something else.

## Experiments or benchmarks

There is no public benchmark here — this is a custom, purpose-built lab task (spreadsheet data entry and arithmetic with injected errors), designed specifically to let the researchers measure multitasking performance, monitoring behavior, and error-catching under controlled, comparable conditions across the four feedback designs. Measures reported include overall and sub-task (spreadsheet/arithmetic) scores, spreadsheet error counts, how often participants switched between the delegated task and their other work, how much time they spent monitoring the agent, subjective workload (NASA-TLX), and post-task ratings of trust, confidence, and usability.

## Main results

**Demonstrated results:** All three CUA-assisted conditions (chat baseline, peripheral text, and Sidekick) produced significantly lower NASA-TLX perceived workload than doing the task manually (a significant main effect of Condition, reported as p < .001), with mean workload scores of roughly 63.83 (manual) versus about 52.97 (chat baseline), 56.46 (peripheral text), and 54.11 (Sidekick) — but the three CUA-feedback conditions did not differ significantly from one another on workload alone. Separately, the authors report that Sidekick specifically improved multitasking performance and error/action traceability compared with the chat and peripheral-text baselines, and that it supported this without adding extra monitoring effort — participants reportedly used Sidekick's ambient color cues to judge when it was worth stepping in. Post-task subjective ratings of trust, confidence, and usability were reported as broadly similar across the CUA-feedback conditions, which the reporting attributes to the CUA being deliberately built to be imperfect, so participants had reason to stay watchful no matter which feedback design they were using.

## Effects on human performance, trust, workload, safety, or decision quality

Delegating to a CUA at all — regardless of feedback design — measurably lowered workload relative to doing the task manually, which is itself informative: offloading execution to an agent frees cognitive capacity even before you optimize how that agent communicates. On top of that baseline effect, Sidekick's specific contribution (per the authors' reported results) was to make oversight more *effective* — better at catching injected errors and better at supporting task-switching — without costing extra workload or requiring more monitoring time than the plainer feedback styles. Trust and confidence didn't clearly shift in Sidekick's favor in this study, which is a meaningful and honestly-reported null result: better communication design here shows up as improved oversight performance, not automatically as higher trust.

## What is genuinely new

**My interpretation:** the paper's real contribution isn't the idea of giving feedback about an agent's status — plenty of systems do that — it's the specific insight that feedback needs differ by *attentional phase*, and the concrete design response of building three distinct, tailored communication layers (ambient / resumption-summary / live-narration) rather than one generic channel. Testing this directly against both a realistic chat-style baseline and a peripheral-display baseline, on a task with real injected errors, is what turns the idea into an evaluated claim rather than a design proposal.

## Limitations and open questions

The authors' own framing and the reported study design point to several open questions: this is a single controlled lab task (spreadsheet entry with arithmetic) with one CUA implementation and artificially injected errors, run with 30 participants — so how this generalizes to messier, more varied real-world CUA tasks (web browsing, multi-app workflows, longer-horizon jobs) is untested here. The study is also a single session per participant, so it can't speak to longer-term effects like habituation to ambient cues, complacency setting in over repeated use, or whether trust calibration changes with extended exposure — all open questions the paper does not claim to resolve.

## Practical implications

For anyone building products around computer-use agents (and this is a fast-moving space right now, with multiple major AI labs shipping computer-use agent features), the practical takeaway is concrete: don't rely on a single chat-style status feed as the entire oversight interface. Splitting communication into background-ambient, resumption-summary, and foreground-narration layers — matched to what the human is actually doing at that moment — is a design pattern this paper shows measurably helps people catch agent mistakes and multitask more effectively, without the added cost of constant monitoring.

## Why you should care

If you use, or plan to use, an AI agent that can act on your computer while you do something else, this paper is directly about the interface problem you'll actually run into: not "is the agent smart enough," but "will I know if it messed up, and can I tell without babysitting it." It's a concrete, tested answer to a design question that most computer-use-agent products currently punt on by defaulting to a plain chat log — and to my reading, it's a useful reminder that better outcomes from human-AI oversight often come from interface design, not just from a smarter or more capable agent.
