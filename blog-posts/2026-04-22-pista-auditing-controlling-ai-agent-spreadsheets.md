# Pista: Letting People Watch — and Stop — an AI Agent While It Edits Their Spreadsheet

**Authors:** Sadra Sabouri, Zeinabsadat Saghi, Run Huang, Sujay Maladi, Esmeralda Eufracio, Sumit Gulwani, Souti Chattopadhyay (University of Southern California; Sumit Gulwani at Microsoft Research)
**Publication date:** 2026-04-22 (arXiv v1; date corroborated across multiple search-engine sources, not independently verified from the primary PDF)
**Venue:** arXiv preprint, categories cs.HC / cs.AI / cs.CE (peer-reviewed venue not confirmed at time of writing); also listed as a Microsoft Research publication
**Paper link:** https://arxiv.org/abs/2604.20070
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** https://www.microsoft.com/en-us/research/publication/auditing-and-controlling-ai-agent-actions-in-spreadsheets/
**Date added:** 2026-08-24

> **A note on sourcing:** this session's outbound network access to arxiv.org (and to several mirror sites, including Semantic Scholar and r.jina.ai) returned a blocked connection when fetched directly — an organizational egress policy on this session, not a paywall; the paper itself is a freely available preprint. This summary is built from the paper's official Microsoft Research publication page (fetched directly) and from cross-checked search-engine excerpts of the abstract, methodology, and results, rather than a direct read of the full PDF. Facts corroborated this way are presented as reported findings; anything that could not be verified is marked "not available" or "not confirmed."

---

## The problem the paper addresses

AI agents that can now open a spreadsheet, read your data, and start editing it on their own are getting good enough to be trusted with real, multi-step work — pulling numbers together, writing formulas, restructuring a table. But there is a catch the authors put bluntly: the agents' *capabilities* have outpaced people's *ability to actually oversee them*. In a normal chat interface, an agent thinks out loud in a wall of text that most users never read closely, and by the time something looks wrong, the mistake may already be baked into dozens of cells. This paper asks a very concrete question: how do you let someone watching an AI agent work through a spreadsheet actually see what it's doing, understand *why*, catch a mistake before it spreads, and step in without having to throw out the whole plan?

## Why this problem matters

Spreadsheets are a uniquely unforgiving place for this problem. As the authors note, "process and artifact are inseparable" in a spreadsheet — every decision the agent makes lands directly in a cell that belongs to, and reflects on, the user. A wrong assumption early in a multi-step task (a misread column, a wrong join, an off-by-one range) doesn't just sit in a chat log; it becomes a number someone might later present in a meeting or feed into a business decision. Because spreadsheets are also one of the most widely used tools in the world for exactly this kind of "knowledge work," getting oversight right here has outsized practical stakes — and it's a good test bed for a much broader question in agentic AI: as agents take on more autonomous, multi-step actions, how do we keep humans able to meaningfully supervise, correct, and stay accountable for the result?

## What makes the system agentic

Pista is built as an AI agent embedded in Microsoft Excel (both web and desktop) that plans and carries out multi-step spreadsheet work rather than answering a single question. Given a task, it decomposes the work into a sequence of discrete, auditable actions — inspecting data, writing or revising formulas, restructuring ranges — and executes them against the live spreadsheet, using the file itself as its working environment. That combination of a goal, a multi-step plan, and autonomous tool use inside a real software environment (rather than a single text reply) is what makes Pista agentic, not just a formula-suggestion feature.

## How humans and the AI agent collaborate

Pista's central design idea is to turn the agent's normally invisible, black-box execution into something a person can watch, question, and redirect step by step, rather than only inspecting the finished result. Instead of running to completion and handing back a spreadsheet, Pista narrates and exposes each action as it happens, gives the underlying formulas and data ranges it touched, lets the user ask follow-up questions about *why* it did something, and lets the user make localized corrections — editing or overriding a specific step — without having to restart or abandon the whole task.

## What role the human plays

The human is the **active auditor and co-author of the agent's work**: reviewing each step as Pista proposes or takes it, probing the agent's reasoning through follow-up questions when something looks off, catching errors before they propagate into later steps, and issuing targeted, localized corrections rather than relying only on the final output looking right.

## What role the AI agent plays

Pista is the **executor and explainer**: it plans and carries out the multi-step spreadsheet task itself (writing formulas, manipulating ranges, restructuring data), but it also does the extra work of making that execution legible — surfacing what it changed, which formulas and ranges were involved, and answering the user's questions about its reasoning, so the person overseeing it isn't stuck decoding raw output alone.

## How control, initiative, and decisions are shared

This is a step-by-step **shared-control / real-time-intervention** design rather than a simple "approve the final answer" gate. The agent retains the initiative to plan and act, but control is deliberately kept granular and interruptible: the user can intervene at essentially any individual action, not just at the end, and corrections are localized to the step in question rather than forcing a full restart. The paper frames this as trading some of the agent's unchecked autonomy for continuous, low-friction human oversight throughout execution.

## The paper's main idea

**Claim by the authors:** making an AI agent's spreadsheet actions auditable and locally correctable — rather than opaque and only reviewable after the fact — meaningfully changes how people experience working with the agent: they understand the task better, form a more accurate sense of the agent, and feel a stronger sense of ownership over what gets produced, not just when the output is correct but through the act of participating in producing it.

## How the approach works

Pista breaks a spreadsheet task into a sequence of discrete actions instead of a single opaque multi-step run. For each action, it surfaces what it's about to do (or did) along with the specific formulas and data ranges involved, so the user has a concrete "handle" on the change rather than an abstract description. The interface supports two intervention paths: users can ask the agent follow-up questions to probe its reasoning about a step, and they can directly issue targeted, localized edits or corrections to a specific action without derailing the rest of the plan. The authors compared this design against a baseline agent of equivalent underlying capability that lacked this step-level transparency and control.

## Human study or evaluation design

**Demonstrated in the paper:** a two-stage, real-participant evaluation — a formative study to surface the problems people have overseeing a baseline (non-auditable) spreadsheet agent, followed by a within-subjects summative study directly comparing Pista against that baseline agent on equivalent tasks. This is a designed, controlled human-subjects study, not a simulation or a purely observational log analysis.

## Participants and study setting

**Demonstrated in the paper:** a formative study with 8 participants and a summative, within-subjects evaluation with 16 participants, who used Pista and a baseline spreadsheet agent to complete tasks and were then compared on outcomes and perceptions. The exact participant recruitment pool and task domain details were not independently verifiable from the sources available in this session beyond what is summarized here — treat specifics such as participants' professional background as "not available" unless confirmed from the full text.

## Experiments or benchmarks

There is no public standardized benchmark here; the "experiment" is the controlled, within-subjects comparison the authors ran themselves — the same 16 participants completing spreadsheet tasks with both Pista and the baseline agent, allowing a direct paired comparison of behavior and self-reported experience.

## Main results

**Demonstrated in the paper (per available descriptions):**
- **Stronger sense of ownership:** 12 of the 16 summative-study participants reported that Pista gave them a stronger sense of ownership over the resulting spreadsheet than the baseline agent did.
- **Better comprehension through interaction, not just output:** participants reported understanding the task and the result better because they could see and question the agent's steps as it worked, rather than only inspecting the finished spreadsheet — several described recognizing their own reasoning reflected back in the agent's steps.
- **Errors caught earlier:** the auditable, step-level design let users identify problems in the agent's assumptions or actions before those problems propagated further into the spreadsheet, compared to the opaque baseline.
- **Active participation changed more than the task outcome:** the authors report that participating in execution (rather than only reviewing a finished result) shifted users' comprehension of the task, their perception of the agent, and their sense of their own role in producing the work.

## Effects on human performance, trust, workload, safety, or decision quality

This is a **demonstrated result** on the specific dimensions the paper measured: participants' sense of ownership/co-authorship, their comprehension of both the task and the agent's actions, their ability to catch errors before they compounded, and their overall perception of the agent all improved with Pista's step-level auditability and local-correction design, compared with a capability-matched baseline agent that lacked it. The paper's evaluation is centered on comprehension, error-catching, and ownership/perception rather than on raw task-completion speed, workload questionnaires, or long-term trust calibration — those broader dimensions are not reported as directly measured outcomes in the sources available here.

## What is genuinely new

- A **step-decomposed, auditable execution model** for an agent operating directly inside a real, widely used productivity tool (Excel), rather than a chat transcript or a research-only sandbox.
- **Localized correction** as a first-class interaction: users can fix or redirect a single action mid-task instead of only accepting or rejecting the agent's work as a whole after the fact.
- Direct **empirical evidence, from real participants comparing the same system with and without this transparency layer**, that granular auditability changes not just error-catching but people's subjective sense of ownership and understanding — a human-centered outcome that's easy to assert and comparatively rare to actually measure with a controlled study.

## Limitations and open questions

- **Small participant pool:** 8 (formative) and 16 (summative) participants is a modest sample for a controlled HCI study; the sources available here do not report statistical significance testing or effect sizes for the ownership and comprehension findings, so the strength and generalizability of "12 of 16" as a robust effect is worth treating cautiously pending the full paper.
- **Single application domain:** the findings are specific to spreadsheet editing in Excel; whether the same auditable, step-correctable design generalizes to other agentic domains (documents, code, browsers) is not established by this paper.
- **No long-horizon or field deployment data:** this is a controlled study of discrete tasks, not a longitudinal or real-workplace deployment, so effects on sustained trust calibration, workload over time, or reliance patterns outside the lab are open questions.
- **Peer-review status unconfirmed:** as of this writing this appears to be an arXiv preprint (also hosted as a Microsoft Research publication); a peer-reviewed publication venue was not confirmed from the sources available in this session.

## Practical implications

For anyone building or deploying agentic tools inside productivity software, Pista's core lesson is concrete and actionable: exposing an agent's plan as discrete, inspectable, individually correctable steps — rather than a single opaque run with a final "accept/reject" — is a design pattern that measurably changes how much people understand, trust, and feel ownership over agent-produced work. That's a directly transferable idea for any tool where an AI agent takes multi-step actions on a person's behalf and the person is expected to remain accountable for the result.

## Why you should care

Most agentic AI coverage focuses on how *capable* agents are getting; this paper is a reminder that capability without legible, interruptible oversight can quietly erode the thing that makes delegation to an agent safe in the first place — a person's ability to actually understand and correct what happened. It's also a useful example of doing the harder, less flashy work of running a real controlled study with real participants comparing two versions of the same agent, rather than only asserting that a transparency feature "should" help. If you use, build, or manage AI agents that take actions on your behalf in everyday tools, this paper's central bet — that step-level auditability and local correction beat all-or-nothing acceptance — is worth paying attention to.
