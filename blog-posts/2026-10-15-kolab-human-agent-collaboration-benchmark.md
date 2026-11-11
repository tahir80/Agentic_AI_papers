# Kolab: Can AI Models Even Tell If a Human Liked Working With Them?

**Paper title:** Kolab: Benchmarking Human-Agent Collaboration in Long-Horizon Workflows
**Authors:** Shirley Anugrah Hayati, Patricia Anugrah Setiani, Ruizi Wang, Zhouyi Li, Khanh Chi Le, Young-Jun Lee, Dongyeop Kang (University of Minnesota)
**Publication date:** 2026-10-15 (arXiv v1)
**Venue:** arXiv preprint, cs.AI / cs.CL / cs.HC / cs.LG; peer-reviewed venue not confirmed
**Paper link:** https://arxiv.org/abs/2610.21109
**Code link:** Not independently verified — the paper's own HTML page is reported (by secondary sources) to point to a project page at minnesotanlp.github.io/kolab, but this session could not open that page directly to confirm it is live
**Project page:** minnesotanlp.github.io/kolab (reported, not independently confirmed)
**Date added:** 2026-11-11

> **A note on sourcing:** arXiv and its mirrors were blocked at the network layer in the environment this summary was written in, so the full PDF/HTML could not be opened directly. This write-up is built from the paper's abstract and from several independent secondary summaries (aggregator pages, a third-party blog, and search-engine excerpts of the arXiv HTML) that were cross-checked against one another. The core framing, dataset description, and headline finding were consistent across all sources. Specific fine-grained numbers (e.g., exact model names and scores) came from only one secondary blog and are flagged below as **not independently verified against the primary paper** — check the arXiv preprint directly before citing them.

---

## The problem the paper addresses

Most tests of AI agents measure one thing: did the agent finish the task? Kolab's authors argue that this misses something that matters just as much in real work — whether the person on the other end actually found the collaboration *good*. An agent can finish a task and still frustrate, mislead, or go against the grain of the person it's supposedly helping. The paper asks a sharper question: when AI models are shown how a real professional and an AI agent worked together, can the models even tell whether that collaboration went well?

## Why this problem matters

Think of a contractor who technically finishes building your deck on time but ignores your instructions, redoes sections you'd already approved, and leaves you annoyed throughout. By narrow "task completion" metrics, that's a success. By any human measure, it's a bad collaboration. As AI agents get embedded into real jobs — writing code, drafting documents, managing spreadsheets — the gap between "got the task done" and "collaborated well with the human" becomes the gap between a tool people actually want to keep using and one they quietly abandon. If the AI models we use to *evaluate* agents can't perceive that gap either, we have no reliable way to measure or improve it.

## What makes the system agentic

Kolab isn't a single agent product — it's a dataset and benchmark built around real episodes of professionals working with AI agents across long, multi-step workflows (not one-shot Q&A). The underlying agents in these recorded sessions took actions across more than 90 software applications to help with realistic, multi-step professional tasks, and the benchmark separately tests frontier AI models' ability to reason about those completed collaborations. Both halves of the picture — the acting agents and the evaluating models — are large language/multimodal models doing more than producing a single text reply.

## How humans and the AI agent collaborate

During data collection, 50 real professionals worked through realistic, long-horizon problems from their own fields while using AI agents as part of their normal workflow, with their screens recorded throughout (115+ hours of recordings). Afterward, those same professionals gave their own first-hand judgments of how satisfying the collaboration was and how good the resulting output was. That combination — real work plus the real worker's own verdict on the collaboration — is the heart of the dataset.

## What role the human plays

The human is the domain expert actually doing the job: a professional from one of 40 different occupations tackling a real task, deciding moment to moment whether to accept, revise, or throw out what the agent offered, and ultimately judging — in their own words — whether the collaboration felt good and whether the output was good.

## What role the AI agent plays

The AI agent is the active collaborator embedded in the professional's workflow: it proposes contributions — drafts, edits, suggestions, actions within software — across a long multi-step task, which the human then keeps, modifies, or discards.

## How control, initiative, and decisions are shared

Control stays firmly with the human professional throughout: the agent contributes, but the person decides what to keep, what to change, and what to reject, and their own satisfaction judgment is the yardstick the benchmark ultimately cares about. The paper then flips the frame for its second contribution: it hands the *record* of that human-agent collaboration to a separate set of frontier AI models and asks them to play the role of an outside observer predicting how the human adoption and judgment will go.

## The paper's main idea

**Claim by the authors:** existing agent benchmarks reward automation — finishing tasks — but strong scores there don't tell you whether an agent is a good *collaborator*. To actually measure that, you need real, long-horizon human-agent work paired with the human's own judgment of the collaboration, and then you can test whether AI models can recognize good collaboration from bad.

## How the approach works

The authors built Kolab, a dataset of 115+ hours of screen recordings from 50 professionals spanning 40 occupations and roughly 10 sectors, collaborating with AI agents on realistic problems from their own jobs (reported secondary detail: around 100 recorded workflow sessions, covering interaction with 90+ software applications). Each recording is paired with the professional's own ratings — their satisfaction with the collaboration and their judgment of the output quality, including which specific agent contributions they ultimately used, revised, or discarded. The benchmark then poses two evaluation tasks to frontier AI models that never saw the live collaboration happen: (1) forecast how the professional will use the agent's contributions, and (2) predict the professional's own satisfaction and quality judgments, including after being given extra workflow context.

## Human study or evaluation design

This is not a controlled lab experiment with random assignment; it's a large, naturalistic data-collection effort. Fifty real professionals did real, long-horizon work from their own occupations while collaborating with AI agents, and their screens were recorded throughout the process. Afterward they supplied their own first-person judgments of the collaboration and output quality, which became the ground-truth labels the benchmark tests models against.

## Participants and study setting

Real human participants: 50 professionals drawn from 40 distinct occupations across roughly 10 sectors (exact recruitment method and demographic breakdown: **not available** from the sources used). The setting was each professional's own realistic long-horizon work, captured via screen recording rather than a synthetic lab task — reported secondary detail puts the dataset at around 100 sessions totaling 115+ hours.

## Experiments or benchmarks

Kolab itself is the benchmark: no prior public benchmark is reused. The authors tested multiple frontier multimodal models (reported secondary detail, not independently verified: a handful of closed models alongside at least one open-weight model) on two tasks built from the human-labeled recordings — forecasting agent-contribution adoption and predicting the professionals' own satisfaction/quality ratings.

## Main results

**Reported by the authors (consistent across multiple independent secondary sources):** frontier AI models — including the most capable ones tested — tend to *overestimate* how well human-agent collaboration went, and they struggle to tell high-quality collaboration apart from low-quality collaboration. Giving a model more workflow context did not reliably fix this. One secondary source additionally reports specific numbers (e.g., a top adoption-forecasting F1 around 0.71 for the best-performing model, and correlation scores for satisfaction prediction in the range of roughly 0.08–0.38 depending on the model) — these specific figures come from a single third-party blog summary and are **not independently verified** against the primary paper.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's human-related contribution is less about *measuring an effect on* the professionals (it is not an intervention study) and more about *capturing their authentic judgment* as ground truth: real professionals' own ratings of collaboration satisfaction and output quality are the standard the AI models are tested against. The demonstrated result is that current frontier models' perception of collaboration quality does not reliably track that human judgment — AI systems overestimate how well collaboration is going relative to what the human professional actually felt.

## What is genuinely new

*Authors' framing:* prior agent benchmarks almost entirely reward task automation; Kolab is presented as a large-scale, real-professional, long-horizon dataset built specifically around collaboration quality rather than task completion, paired with a benchmark that tests whether AI models can even recognize good versus poor human-agent collaboration from the human's own perspective.

## Limitations and open questions

- *My interpretation:* this is an observational dataset, not a randomized experiment — it tells us models misjudge collaboration quality, but not yet how to design agents that collaborate better.
- Sample size (50 professionals) is sizable for this kind of qualitative/behavioral data collection but still modest for generalizing across 40 occupations and 10 sectors.
- Recruitment method, demographics, and full statistical detail were **not available** from the sources used in this session.
- Specific per-model scores reported by a single secondary blog could not be checked against the primary PDF in this session and should be verified before being cited.
- Code/data release location is reported by secondary sources but could not be independently opened and confirmed live in this session.

## Practical implications

*My interpretation:* if the AI models we might use to auto-evaluate or auto-improve agentic assistants can't accurately judge whether a human collaborator was satisfied, then relying on model-based judges (or on task-completion rates alone) to certify "this agent collaborates well" is premature. Teams building agentic tools for real professional work should treat human-reported collaboration satisfaction as a distinct, necessary measurement — not something safely inferable from an AI judge or from whether the task got done.

## Why you should care

This paper is a reality check for anyone impressed by agent benchmarks that only report task success. It shows, with real professionals doing real long-horizon work across 40 occupations, that even frontier AI models are currently bad at recognizing good collaboration from bad — including overestimating how well things are going. That's the gap that determines whether people actually want an AI agent as a work partner, not just whether it technically finished the job.
