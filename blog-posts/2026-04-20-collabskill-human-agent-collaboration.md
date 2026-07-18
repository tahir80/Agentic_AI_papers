# CollabSkill: Why the Best Solo AI Agent May Not Be the Best Teammate

**Paper title:** CollabSkill: Evaluating Human-Agent Collaboration On Real-World Tasks

**Authors:** Yijia Shao, Zora Zhiruo Wang, Neel Ahuja, Yicheng Wang, Bowen Liu, Diyi Yang

**Publication date:** 2026-04-20 (arXiv v1)

**Venue:** arXiv preprint; under review

**Paper link:** https://arxiv.org/abs/2606.09833

**Code link:** https://github.com/SALT-NLP/collaborative-gym (Collaborative Gym platform; a separate CollabSkill-specific implementation was not identified)

**Project page:** https://cogym.saltlab.stanford.edu/

**Benchmarks / datasets:** [GDPVal](https://huggingface.co/datasets/openai/gdpval), [APEX](https://arxiv.org/abs/2509.25721), and [APEX-Agents](https://arxiv.org/abs/2601.14242)
**Date added:** 2026-07-18

---

## The problem the paper addresses

AI agents are usually tested like solo contestants: give each one a task, let it work alone, and rank the final answers. CollabSkill asks a more human question: which agent produces the best work **when paired with a real person**?

That is harder to measure than it sounds. A team result mixes together the agent's ability, the worker's domain expertise, the worker's skill at using AI, and the interaction design. Simply averaging team scores can make an agent look strong because it happened to be paired with unusually capable people. The paper introduces an evaluation framework intended to separate those contributions.

## Why this problem matters

Workplace agents are increasingly used as collaborators, not just autonomous replacements. Yet a strong solo benchmark score does not guarantee that an agent will communicate well, expose the right controls, invite useful correction, or fit a person's workflow.

The practical risk is choosing workplace agents from the wrong scoreboard. It is like hiring a doubles tennis player using only singles results: raw ability matters, but so do coordination and the way the partnership changes both players' performance.

## What makes the system agentic

The five evaluated systems—Codex, Gemini CLI, Claude Code, Claude Cowork, and Manus—use large language models as their central reasoning component. They do more than return one response: they plan and perform multi-step work, use bash or browser tools, read reference files, operate specialized software, and create concrete deliverables such as spreadsheets, slide decks, PDFs, ZIP archives, and audio files.

Three terminal agents share a ReAct-style loop: reason about the next step, take a tool action, observe the result, and continue. Claude Cowork provides a desktop interface, while Manus is browser-based. The paper evaluates them as agents completing extended occupational tasks, not as chat models answering isolated questions.

## How humans and the AI agent collaborate

Each participant receives a task matched to their occupational background and is randomly paired with one of the five agents. The person supplies instructions and context, watches the work, asks for changes, checks claims, and refines the output as needed. The agent handles much of the procedural work: interpreting files, using tools, generating and revising the deliverable, and reporting progress.

The paper collected more than 1,500 human prompts. Its trajectory analysis records several substantive collaboration behaviors, including clarifying goals, defining the audience, specifying format and tone, showing examples of good work, discussing an approach before execution, supplying missing context, iterating, checking facts, and challenging weak reasoning.

## What role the human plays

The human is a working partner and domain-informed supervisor, not merely the source of an initial prompt. Participants:

- guide the task and communicate unstated requirements;
- decide how much work to delegate;
- add context the agent lacks;
- inspect, question, and refine intermediate or final work;
- verify important claims; and
- submit the team's finished deliverable.

Participants' professional backgrounds are part of the experimental design: tasks are matched to occupation so the human contribution resembles real work rather than generic crowd annotation.

## What role the AI agent plays

The agent is the execution partner. It plans multi-step work, reads task materials, invokes software or command-line tools, and produces the requested artifact. Depending on the human's chosen interaction style, it may work with relatively little interruption or go through several rounds of instruction, correction, and revision.

## How control, initiative, and decisions are shared

The study does not force every team into one fixed division of labor. Instead, people decide how actively to steer their assigned agent. That makes the sessions ecologically useful, but it also means the experiment measures several collaboration styles at once.

The human retains final control over instructions, corrections, verification, and submission. The agent takes operational initiative inside the task by selecting and executing sequences of actions. The study's Human Agency Scale then asks participants where they believe and prefer the boundary to sit, from full agent autonomy to continuous human involvement.

**Demonstrated result:** after hands-on collaboration, participants believed agents could operate more autonomously, but their *preferred* allocation of autonomy did not significantly change. Capability beliefs and desired control were therefore not the same thing.

## The paper's main idea

CollabSkill treats a team score as the sum of three parts: a latent human collaboration skill, a latent agent collaboration skill, and noise. It then updates estimates of both skills across the network of pairings.

The approachable analogy is a multiplayer game rating. If the same person performs well with several agents, the method assigns some credit to the person rather than whichever agent they happened to use. If many people do better with one agent than with others, more credit moves toward that agent. The paper reports a conservative score—roughly the estimated skill minus three standard deviations—so uncertain agents are not rewarded merely for having fewer observations.

## How the approach works

1. The researchers combine realistic tasks from GDPVal, APEX, and APEX-Agents and tag them with O*NET occupational categories.
2. A U.S.-based worker is matched to a task relevant to their background and randomly paired with one of five agents.
3. The person and agent produce a concrete deliverable and submit their interaction log.
4. An automated pipeline generates a task-specific rubric, then two independent agent judges score the deliverable. Their scores are averaged on a 0–100 scale.
5. A Bayesian rating model estimates separate human and agent contributions from the connected set of team outcomes.
6. Pre/post surveys measure trust, delegation comfort, perceived capability, desired autonomy, concern about role meaningfulness, and general sentiment toward agents.

The grading system received its own validation. Against official GDPVal rubrics, automatically generated criteria achieved 82.1% recall and 92.2% precision. Across 135 sampled task–deliverable pairs, automated and official-rubric scores correlated at (r=0.72).

## Human study or evaluation design

This was an IRB-approved study with real workers. Participants were randomly assigned agents for each session, completed up to five tasks, uploaded final deliverables and collaboration logs, and received $20 per completed task. The top three workers by CollabSkill score were offered additional bonuses.

The main outcome is the quality of the joint deliverable. The researchers also compare each human–agent outcome with the same agent running alone under a researcher-engineered system prompt. Bootstrap resampling and leave-one-human-out and leave-one-task-out tests examine ranking stability.

The design is not a controlled test of one specific collaboration interface against another: agents differ in model, interface, and sometimes harness. Two comparisons narrow that problem—three terminal agents use similar ReAct scaffolding, while Claude Cowork and Claude Code share an underlying model—but the study is primarily a broad evaluation framework.

## Participants and study setting

The study involved **93 U.S.-based workers recruited through Upwork**, contributing **386 sessions** on **165 distinct tasks** across 10 of 20 O*NET sectors. Participants averaged 9.6 years of experience in their chosen occupation. Seventy-six completed both the pre- and post-study surveys.

The tasks included realistic knowledge-work deliverables in areas such as investment banking, management consulting, law, primary care, and other professional services. This is a compensated study setting rather than a longitudinal deployment inside participants' own employers.

## Experiments or benchmarks

The evaluation draws tasks from:

- **GDPVal:** economically valuable work across many occupations;
- **APEX:** professional tasks in investment banking, consulting, law, and primary care; and
- **APEX-Agents:** cross-application tasks with extensive reference files.

The authors also compare the three terminal agents with solo-agent results on the collected tasks and with public results from SWE-bench Verified, GDPVal, and SciCode. These comparisons test the paper's central claim that autonomous and collaborative rankings need not agree.

## Main results

**Results demonstrated in the study:**

- Claude Cowork ranked first with a CollabSkill score of **76.738**, followed by Claude Code at **74.778**, Codex at **71.267**, Manus at **71.204**, and Gemini CLI at **69.555**.
- Claude Cowork retained first place in **71.3% of 10,000 bootstrap samples**. The ordering was moderately stable overall (mean Kendall's (	au=0.64)).
- Among comparable terminal agents, Claude Code ranked above Codex in collaboration even though Codex scored higher in the paper's solo evaluation and the cited autonomous benchmarks.
- Human skill changed whether the team helped: top-quartile workers beat the matched autonomous-agent baseline in **74%** of comparisons; bottom-quartile workers did so in only **27%**.
- The number of useful collaboration behaviors correlated with session quality ((r=0.262, p<0.0001)); raw turn count did not ((r=0.046, p=0.371)). More conversation was not automatically better conversation.
- Defining the audience showed the largest reported behavioral association: sessions displaying it scored **16.5 points higher on average** (84.7 versus 68.1). This is correlational, not proof that adding one audience sentence causes a 16.5-point gain.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated human-related outcomes:**

- Higher-skilled collaborators were much more likely to outperform the agent working alone: 74% for the top quartile versus 27% for the bottom quartile.
- Self-reported LLM familiarity correlated with estimated collaboration skill ((ho=0.297, p=0.010)). Comfort with delegation also correlated with skill ((ho=0.238, p=0.041)).
- After the tasks, trust increased by **0.58 points** ((p=0.004)) and delegation comfort by **0.45 points** ((p=0.039)) on seven-point scales.
- Participants shifted their estimate of agent capability by **0.50 levels toward greater autonomy** ((p<0.001)), but their preferred autonomy did not significantly change ((Delta=-0.16, p=0.105)).

The paper did **not** directly measure workload, safety incidents, long-term job performance, or calibrated trust against an objective reliability target. An increase in trust is therefore a measured attitude change, not evidence that reliance became appropriately calibrated.

## What is genuinely new

**The authors' novelty claim:** CollabSkill is the first systematic framework to rank agents on realistic occupational collaboration while explicitly modeling differences between human partners rather than treating those differences as noise.

The important practical contribution is the separation of “good at the task alone” from “good in a human team.” The interface comparison is also suggestive: Claude Cowork ranked above Claude Code despite sharing the same underlying model, indicating that how people access an agent can matter alongside model capability.

**My interpretation:** the most valuable new idea is not the exact 2026 leaderboard. Models will change quickly. It is the proposal that collaboration itself needs a benchmark whose unit of analysis is the team—and whose statistics acknowledge that people are not interchangeable test fixtures.

## Limitations and open questions

**Limitations identified by the authors:**

- Participants came only from U.S.-based Upwork workers, creating selection bias.
- The 386 sessions cover only half of the O*NET sectors and are too sparse for fine-grained subgroup analysis.
- A single scalar score cannot capture creativity, pressure response, interpersonal communication, or every quality of real work.
- Cost-effectiveness is excluded even though human and agent labor costs differ greatly.
- The rankings are a snapshot of rapidly changing early-2026 agents.

**Additional interpretation:** the additive rating model assumes human and agent contributions can be separated cleanly, yet collaboration may contain pair-specific chemistry—a particular worker may be especially effective with a particular interface. The paper also estimates human skill from team outcomes and then groups workers by that estimate when comparing against solo agents, so the striking 74%-versus-27% contrast should not be read as a randomized causal effect of training people to become “top quartile.” Finally, pre/post attitude changes lack a no-agent control group and do not establish long-term trust calibration.

Open questions include whether the framework generalizes inside real organizations, how to model specific human–agent pair effects, how collaboration quality changes over months, and whether better interfaces can help less-experienced workers without encouraging over-reliance.

## Practical implications

Organizations should not select agents solely from autonomous leaderboards. Pilot tests should include representative employees, realistic artifacts, and measures of correction, verification, trust, and desired control. Agent builders should evaluate whether their interfaces elicit high-value behaviors—clear goals, useful context, iterative refinement, and fact checking—rather than optimizing only for fewer human turns.

The finding that trust increased while preferred autonomy did not is especially important. Workers can update their beliefs about what an agent *can* do without wanting to surrender the same decisions. Deployment policy should respect that distinction.

## Why you should care

CollabSkill offers unusually direct evidence that an AI agent's value depends on the person and interface around it. The best solo performer was not the best terminal-based collaborator, strong human partners made teams substantially more competitive with autonomy, and hands-on use changed trust without erasing people's preference for meaningful control.

The broader lesson is simple: if agents are going to work with people, we should test the partnership—not just the machine.

---

*Attributions such as “the authors report” describe claims made in the paper. Numeric findings labeled as demonstrated results come from the reported experiments. Statements explicitly labeled “my interpretation” or “additional interpretation” are the summary writer's analysis.*
