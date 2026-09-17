# When the Supervisor's Notes Get Lost in Translation: An AI That Watches the Watchers

**Authors:** Shih-Yu Lai (National Taiwan University; MoonShine Animation Studio), Wen-Fan Wang (Cornell Tech), Sai Ling (MoonShine Animation Studio), Shaune Jan (MoonShine Animation Studio), Bing-Yu Chen (National Taiwan University), Xiang "Anthony" Chen (UCLA)
**Publication date:** 2026-09-09 (arXiv v1)
**Venue:** Accepted to SIGGRAPH Asia 2026 (Conference Papers track); arXiv preprint at time of writing
**Paper link:** https://arxiv.org/abs/2609.10385
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-09-17

> **A note on sourcing:** this session's outbound network access to arxiv.org and its usual mirrors (alphaXiv, Hugging Face, Semantic Scholar, ar5iv, Pith) was blocked at the network egress layer, so this summary could not be built from a direct read of the full PDF. It is instead built from cross-checked excerpts surfaced by multiple independent web searches, including the paper's own abstract text, its reported system architecture, and its reported study design and results. Facts that appeared consistently across independent searches are presented as such; anything that could not be corroborated this way is marked "Not available" or "not confirmed." Readers who need exact statistics, full result tables, or direct quotations should consult the arXiv preprint directly.

---

## The problem the paper addresses

In animation and visual-effects (VFX) studios, a supervisor looks at a junior artist's work-in-progress shot, compares it against a brief, some reference images, and a pile of earlier verbal notes, and then tells the junior what to fix. That sounds simple, but the paper argues it quietly breaks down in practice: the criteria for "good" drift from review to review, a supervisor's judgment call ("this doesn't match the reference") loses the evidence that justified it by the time it reaches the junior artist, and the reasoning behind a request often doesn't survive the handoff at all. The junior ends up guessing, produces another round of a "not quite right" fix, and the whole review cycle repeats.

## Why this problem matters

This isn't a minor annoyance — repeated, unclear revision cycles are a well-known source of wasted time and frustration in creative production pipelines, and they scale badly as more junior artists and more shots move through a supervisor's queue. Beyond animation and VFX specifically, it's a sharp, concrete instance of a much more general problem for any human-AI or human-human delegation relationship: how do you preserve *why* a decision was made — the evidence behind it — as that decision gets handed down and re-interpreted by someone else, especially when the person handing it down (here, a supervisor) doesn't have time to write an exhaustive spec for every note?

## What makes the system agentic

MOONWALK is not a single-turn chatbot bolted onto a review tool. According to reported details of its prototype implementation, it runs an **eleven-dimension automated analysis pipeline** over a junior artist's work-in-progress — covering visual-quality dimensions like lighting, composition, color, style, perceptual quality, sketch/line quality, and specification faithfulness, plus implementation-diagnostic dimensions like controllability, consistency, efficiency, and stability. That analysis is carried out by a **three-model chain**: one multimodal model handles visual observation of the work-in-progress, a second compares it against the specification and reference materials, and a third synthesizes the findings into candidate discrepancies, citing the specific reference pixels/regions that justify each one. Those candidate discrepancies are then routed to a human supervisor for inspection and authorization before becoming action items. That's multiple models chained into a multi-step pipeline that perceives, compares against a specification, and proposes actions grounded in cited evidence — squarely within what this survey treats as "agentic": it goes well beyond producing a single text reply.

## How humans and the AI agent collaborate

The system is built around a three-stage loop the authors call **Intent → Evidence → Action**, instantiated as one shared project record with three linked operations. First, intent is "articulated" into a shared **Spec/Brief** and an annotated **Reference Hub** — the supervisor and team's collected briefs, evolving specs, and reference images, all in one place instead of scattered across chats and calls. Second, the AI pipeline "grounds evidence" by analyzing a submitted work-in-progress against that intent record and surfacing candidate discrepancies, each anchored to a specific piece of evidence rather than a vague comment. Third, the supervisor reviews those AI-surfaced candidates on a **Review Canvas** with region-level annotation, and "authorizes" the ones that matter into a prioritized, evidence-linked checklist that the junior artist actually executes.

## What role the human plays

Humans sit at both ends of the loop and hold the authority in the middle. Supervisors (and the broader team) supply the intent — the brief, the references, and the evolving creative direction — and then, critically, they are the ones who decide which AI-surfaced discrepancy actually becomes an action item; the AI's candidates are proposals, not verdicts. Junior artists are on the receiving end, executing the resulting checklist, but the design is meant to let them do that with the original evidence attached, rather than a decontextualized note. The authors are explicit that **aesthetic authority and final prioritization must remain with practitioners** — the system is designed to support, not replace, that judgment.

## What role the AI agent plays

The AI's job is described by the authors as **administrative coordination**: keeping the shared intent record consistent, running the multi-model comparison pipeline against a submitted work-in-progress, flagging candidate discrepancies with cited evidence, and helping consolidate the supervisor's authorized decisions into an organized, prioritized checklist. It does the labor-intensive, detail-tracking legwork of comparing a shot against a sprawling set of specs and references — work that's easy for a busy supervisor to do incompletely or inconsistently under time pressure — while deliberately not making the final creative call itself.

## How control, initiative, and decisions are shared

This is a clear case of **human oversight with agent-initiated proposals and mandatory human authorization**: the AI pipeline takes the initiative to scan for and surface potential problems (mixed-initiative, in that it doesn't wait to be asked about each shot), but nothing becomes an actionable revision until a human supervisor reviews and authorizes it on the Review Canvas. Control over the "what to change" question stays firmly with the human; the AI's role is to make sure the human doesn't miss things and that whatever the human does decide travels downstream with its justification intact.

## The paper's main idea

**Claim by the authors:** creative review breakdowns are fundamentally a *traceability* problem — intent, evidence, and action get disconnected from each other as work moves through a review pipeline — and that a system which explicitly keeps those three things linked in one shared record, while still routing every consequential decision through human authorization, can measurably improve how well an AI-assisted review cycle preserves reasoning and reduces the guesswork downstream.

## How the approach works

MOONWALK operationalizes the Intent-Evidence-Action framework as one shared project record viewed through three linked operations: **Articulate Intent** (the Spec/Brief plus annotated Reference Hub), **Ground Evidence** (the eleven-dimension, three-model-chain analysis of a work-in-progress against that intent, surfacing evidence-anchored candidate discrepancies), and **Authorize Action** (the supervisor's Review Canvas, where authorized decisions get consolidated into a prioritized, evidence-linked checklist for the junior artist). Reported model choices for the evaluated prototype were GPT-4o-mini for visual observation, Gemini 2.0 Flash for specification/reference comparison, and Claude 3.5 Sonnet for synthesizing the final, evidence-cited discrepancy candidates.

## Human study or evaluation design

The authors ran an **in-studio, within-subject comparative study** with real animation/VFX professionals, comparing MOONWALK against a **chat-only interface using the same underlying AI models** on matched production materials, with participants' own existing studio workflows serving as a retrospective, ecological point of comparison (i.e., not a third randomized condition, but a reference point from their normal practice). This is a real deployment-adjacent evaluation with practitioners doing review work resembling their actual jobs, not a simulated task with recruited crowdworkers.

## Participants and study setting

**19 professional animation/VFX practitioners** took part — 10 in senior/supervisor roles and 9 in junior-artist roles — drawn from **two studio contexts**. Further demographic detail (studio names, experience levels, project types) was not confirmed from the sources available in this session.

## Experiments or benchmarks

There is no public benchmark here — this is a custom, studio-embedded comparative evaluation using each participating studio's own matched production materials, comparing the full MOONWALK system against a chat-only baseline built on the same AI models, across 13 Likert-scale items and 9 head-to-head comparative questions.

## Main results

**Reported by the authors, per available search excerpts:**
- MOONWALK was rated above the neutral midpoint on **12 of 13** Likert-scale items.
- MOONWALK was preferred over the chat-only baseline on **8 of 9** head-to-head comparative questions.
- Specific reported comparative results include: junior-executable checklists preferred **74%** of the time, reduced senior–junior clarification need reported at **63%**, and blind-spot identification and evidence-linked feedback each favored MOONWALK at **79%**.
- Qualitatively, the study reportedly found stronger **intent alignment**, **decision traceability**, and **checklist executability** with MOONWALK, alongside a consistent finding that **aesthetic authority and final prioritization need to stay with the practitioners** rather than the system.

Exact statistical tests, full result tables, and participant quotations could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The study's outcome measures center on **collaboration quality and decision quality** rather than standardized instruments like NASA-TLX workload scores or a formal trust scale — specifically, how well the AI-assisted workflow preserved the traceability of a decision (why a note was given), how executable the resulting checklist was for junior artists without needing to go back and ask for clarification, and how effectively the system surfaced things a supervisor might otherwise have missed ("blind-spot identification"). These are meaningful proxies for reduced rework and reduced friction between senior and junior collaborators, though they are not the same as a validated workload or trust instrument, and this session could not confirm whether such standardized instruments were also used in the full paper.

## What is genuinely new

- A concrete **Intent-Evidence-Action** design framework aimed specifically at the traceability failure in creative review handoffs, rather than a generic "AI feedback" tool.
- A **multi-model analysis pipeline** (eleven dimensions, three chained models) that grounds every flagged issue in cited visual evidence rather than free-text criticism.
- A real **in-studio comparative study with working professionals** (19 practitioners across two studios) rather than a lab study with recruited non-experts or a purely technical benchmark — a relatively rare combination for a systems paper in this space.
- A clear, load-bearing design commitment to **human authorization as a gate**: the AI proposes and organizes, but every actionable item passes through a human supervisor before a junior artist ever sees it.

## Limitations and open questions

- **Small, domain-specific sample.** Nineteen practitioners across two studios is enough to see a consistent pattern but not enough to generalize confidently across the wider animation/VFX industry, let alone other creative-review domains.
- **Comparison baseline is a chat interface using the same models**, not a completely independent tool — this isolates the value of MOONWALK's structured Intent-Evidence-Action interface specifically, but doesn't tell us how it stacks up against other structured review tools already used in the industry.
- **No standardized trust/workload instrument confirmed.** It's unclear from available sources whether validated scales (e.g., NASA-TLX, a standard trust questionnaire) were used alongside the study-specific Likert items and comparative questions.
- **Sourcing caveat (this summary).** Because full-text access was blocked in this research session, the exact wording of the 13 Likert items and 9 comparative questions, the statistical analysis, and any qualitative practitioner quotations could not be verified beyond what surfaced in cross-checked search excerpts.

## Practical implications

For any studio-scale creative pipeline — not just animation and VFX — this is a fairly transferable pattern: instead of asking an AI to just "give feedback" in a chat window, tie its output to a persistent, shared record of intent and evidence, and route every actionable suggestion through a human authorization step before it becomes a task for someone downstream. That combination (grounded, evidence-cited AI suggestions + mandatory human sign-off + traceable handoff) is a concrete template for AI-assisted review workflows in other domains where a senior reviewer's judgment needs to travel intact to a junior executor — code review, editorial workflows, or clinical chart review are all structurally similar problems.

## Why you should care

Most "AI feedback" tools promise to replace part of a human reviewer's judgment. MOONWALK is a useful counter-example: it's explicitly designed *not* to make the creative call, and its authors report that practitioners still valued it — not because it decided things for them, but because it kept track of *why* decisions were made and made sure that reasoning survived the handoff to the person who had to act on it. As agentic AI tools get folded into more professional review and delegation workflows, this paper is a concrete, practitioner-tested data point on a design pattern — agent proposes with evidence, human authorizes, evidence travels downstream — that keeps humans in charge of judgment while still getting real, measured benefit from the AI doing the tedious cross-checking work.
