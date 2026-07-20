# OrchestrXR: A Multi-Agent System for Idea-to-Prototype XR Study Authoring

**Authors:** Shuqi Liao, Chenfei Zhu, Karthik Ramani, Voicu Popescu (Purdue University) — author order taken from secondary sources, not independently verified against the original PDF
**Publication date:** 2026-07-02 (arXiv id 2607.01588)
**Venue:** arXiv preprint (cs.HC); formal peer-review venue/acceptance not confirmed from available sources
**Paper link:** https://arxiv.org/abs/2607.01588 (PDF: https://arxiv.org/pdf/2607.01588)
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-07-20

> **A note on sourcing:** the arXiv host was not directly reachable from this research session's network (a network policy blocked arxiv.org, export.arxiv.org, and several mirror/reader services), so this summary is built entirely from the paper's publicly circulated abstract and secondary descriptions surfaced through web search, not a direct read of the typeset PDF. Facts that could be cross-confirmed across multiple independent search snippets (the abstract text, the three-agent architecture, the participant count and demographics, and the headline evaluation claims) are reported as such. Anything that could not be confirmed this way — exact quantitative scores, a confirmed peer-review venue, a code repository, and the authors' own stated limitations in full — is marked "not available" or "not confirmed" rather than invented.

---

## The problem the paper addresses

Researchers who study how people perceive and interact with immersive technology — Extended Reality (XR), covering VR/AR/MR — need to build "XR studies": mini interactive experiences with a defined task, a 3D scene, and interaction logic, that let them measure things like presence, performance, or behavior. Turning a study idea into a working prototype is currently a slog spread across three separate skill sets: designing the experiment itself (what should participants do, and why), building the 3D scene, and implementing the interaction logic in an engine like Unity. The paper argues this pipeline is "fragmented" — a researcher's initial intent can get lost or distorted as it passes from a design idea to a 3D scene to working interaction code, especially if they're not equally skilled at all three stages.

## Why this problem matters

Building even a simple XR study prototype today typically requires either a multidisciplinary team or a single researcher wearing three hats (experimental designer, 3D artist, and software engineer). That's a real barrier to iterating quickly on study ideas, and it can bias which studies get built toward whichever ones are technically easy rather than scientifically interesting. A tool that helps preserve a researcher's actual intent from idea to runnable prototype — without requiring them to master Unity or 3D modeling — could let more researchers test more ideas, faster.

## What makes the system agentic

OrchestrXR isn't a single prompt-to-code generator. It's built as a multi-agent workflow: three specialized LLM-driven agents — a Study Design agent, a Scene Generation agent, and an Interaction Generation agent — each own one stage of the pipeline, communicate through structured intermediate schemas (not just free-form text), and hand off progressively more concrete artifacts to one another, ultimately producing a runnable Unity prototype. The system performs multi-step planning and decision-making (translating a fuzzy research idea into a formal study specification, then a 3D scene layout, then interaction code), acts on an external environment (it actually generates and assembles a working Unity project, not just a text description), and is evaluated as a working system with real users rather than just as a text generator. That combination of orchestrated sub-agents, structured hand-offs, and concrete environment-level output is what puts it inside the agentic AI category rather than being a single-shot code generator.

## How humans and the AI agent collaborate

The researcher doesn't just type one prompt and wait for a finished prototype. OrchestrXR is explicitly described as a "controllable workflow," and the three stages are connected through an interactive human-agent interface — described in secondary sources as a shared chat interface — that lets the person see and respond to what each agent proposes before it becomes the input to the next stage. In other words, the human stays in the loop across all three hand-offs (idea → study design → scene → interaction), rather than only reviewing the finished product at the very end.

## What role the human plays

The researcher supplies the initial idea and the research intent behind it, then reviews and steers the structured specifications each agent produces at every stage — study design, scene, and interaction — so that their original intent carries through rather than drifting as it's transformed into increasingly concrete artifacts. This is a more active role than "type a prompt, get an output": it's closer to ongoing oversight and course-correction of a multi-stage authoring pipeline.

## What role the AI agent plays

Each of the three agents does the heavy lifting of translating researcher intent into a specific kind of artifact: the Study Design agent turns a rough idea into a structured experimental specification (tasks, conditions, logging needs); the Scene Generation agent turns that into a 3D scene layout; and the Interaction Generation agent turns the scene and design specification into working Unity interaction code. The system maintains "structured schemas" as explicit, inspectable intermediate representations at each stage, rather than passing loosely-structured prompts and outputs between agents — a design choice meant to keep the pipeline coherent and auditable rather than a black box.

## How control, initiative, and decisions are shared

Authors' framing (as surfaced in secondary sources): the workflow is designed to be "controllable" rather than "one-shot generation" — the system does not simply generate a finished prototype from a single instruction and hand it over. Instead, control is distributed across stages, with the human able to inspect and adjust the agents' structured intermediate output at each of the three hand-off points before the pipeline moves further downstream. This is best read as human oversight of a multi-agent pipeline with per-stage checkpoints, rather than a fully autonomous, hands-off generation process or a strictly turn-by-turn co-editing session — the exact turn-taking mechanics (e.g., whether the human can freely interrupt mid-generation, or only reviews between fixed stages) were not confirmed from the sources available to this summary.

## The paper's main idea

Treat XR study authoring as a structured, multi-stage, human-supervised pipeline — not a single generative leap from idea to prototype. By giving each stage its own specialized agent and an explicit, inspectable schema to hand off, the system aims to preserve the researcher's original scientific intent as it moves from an abstract idea down to concrete, runnable code.

## How the approach works

OrchestrXR is organized around three design strategies, per the paper's own framing: (1) structured schemas — explicit, stage-specific representations of the study, scene, and interaction specifications, rather than raw prompts and outputs; (2) multi-agent orchestration — three specialized agents, each responsible for one stage, that pass structured artifacts forward while propagating context (so downstream agents know about upstream research goals); and (3) interactive human-agent interfaces that let the researcher engage with the process rather than only the final result. The pipeline's end product is a Unity-based prototype the researcher can run.

## Human study or evaluation design

The paper reports a two-session user study. Session 1 focused on how well research intent survived as it propagated through the three authoring stages (study design → scene → interaction) — a form of "specification propagation" or intent-preservation assessment. Session 2 had participants use the system more like a coherent end-to-end workflow, from idea to a runnable prototype, and gathered their subjective experience of that process. Exact session structure (tasks assigned, order of conditions, whether there was a non-agentic baseline for comparison) was not confirmed from the sources available to this summary.

## Participants and study setting

12 participants took part: 11 Ph.D. students and 1 Master's student (9 male, 2 female, 1 preferred not to disclose), aged 23–36 (mean 27.83). They had substantial relevant research experience — an average of 4.17 years, having run or been substantially involved in an average of 6.58 prior user studies — and reported prior familiarity with common XR tools (Unity, Blender, OpenXR, Unreal) and AI tools (ChatGPT, Gemini, Codex, Claude Code), meaning this was a population of experienced XR researchers rather than novices or general crowdworkers. Each session lasted about 90 minutes, and participants were compensated with a $60 gift card.

## Experiments or benchmarks

This is a real-user study rather than an automated benchmark against a public leaderboard — there is, as far as could be confirmed, no standardized public benchmark for "XR study authoring" that the paper compares against. The paper does describe the system's applicability across multiple XR research paradigms (perceptual studies, interaction performance evaluation, spatial behavior analysis, and procedural skill training), suggesting the study tasks were designed to span this range, though the specific task set was not confirmed from available sources.

## Main results

According to secondary descriptions of the paper's findings: the system achieved strong "specification propagation" in Session 1, meaning core study intent — research goals, task mechanics, and overall workflow structure — was generally well preserved as an idea moved into a formal study design. However, preservation was reportedly harder to maintain at the more concrete, downstream stages: condition structure, state carriers, and logging semantics were described as more difficult to preserve correctly in the scene- and interaction-level outputs than the higher-level study design was. In Session 2, participants reportedly described the system positively, characterizing it as a coherent workflow from idea to a runnable prototype. Precise quantitative scores (e.g., an exact intent-preservation percentage, or standard usability-scale numbers) could not be confirmed from the sources available to this summary.

## Effects on human performance, trust, workload, safety, or decision quality

The available secondary sources describe participants' experience in qualitative, generally positive terms (a "coherent workflow," effective support for early-stage authoring) but do not report standardized quantitative measures of trust, workload (e.g., NASA-TLX), decision quality, or safety from this study. Readers should treat the positive characterization as the authors' summary of participant sentiment rather than as a validated, numeric usability or trust metric — this summary could not independently confirm the underlying scores.

## What is genuinely new

Based on what's confirmed: applying a multi-agent, schema-mediated pipeline — with per-stage human checkpoints — specifically to the problem of XR study authoring, an area that (per the paper's framing) has previously been fragmented across separate design, 3D-scene, and interaction-coding steps. The explicit design choice to keep structured, inspectable intermediate representations between agents (rather than passing free-form text) is presented as central to preserving researcher intent across the pipeline, and the accompanying real-user evaluation with experienced XR researchers is a genuine (if small-scale) human-subjects contribution, distinguishing it from purely technical, benchmark-only agent papers.

## Limitations and open questions

The clearest limitation reported in secondary sources: OrchestrXR is constrained by current LLMs' visual and spatial reasoning, which can produce implausible object relationships, incorrect relative scale, or unreasonable object placement during scene generation. The system currently targets early-stage prototyping with simulated input in a virtual development setting, and does not yet support real XR device input (i.e., testing on an actual headset). The study population was small (12 participants) and skewed toward experienced XR researchers already familiar with related AI and XR tools, so findings may not generalize to less experienced researchers or to more complex study designs. This summary could not confirm whether the paper includes a comparison against a non-agentic or single-agent baseline, which would be needed to isolate how much of the benefit comes specifically from the multi-agent, schema-based design versus simpler alternatives.

## Practical implications

If the reported intent-preservation results hold up under closer scrutiny, tools built this way could lower the technical barrier for XR researchers to go from a study idea to a testable prototype without needing to personally master 3D scene construction and Unity interaction scripting — potentially letting more, and more diverse, study ideas get built and tested. The paper's own framing suggests the harder open problem is not generating plausible-looking output, but faithfully preserving the researcher's precise experimental intent (conditions, logging, state semantics) as ideas become code — a caution against treating these systems as "generate and trust" tools without human review at each stage.

## Why you should care

This paper is a useful, concrete example of "agentic AI with a human in the loop" applied to a real, if niche, research-tooling problem: rather than a single LLM call that either succeeds or fails, it's a supervised pipeline where a domain expert (the XR researcher) checks and steers the system's output at each of several stages. It's a smaller-scale, more specialized cousin of the broader trend — coding agents, research agents, planning agents — toward LLM-based multi-agent systems that are designed for ongoing human oversight and correction rather than fire-and-forget autonomy, evaluated here with a real (if small) group of the domain experts who would actually use such a tool.
