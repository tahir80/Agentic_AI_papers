# Assistant or Actor? Student Trust, Control, and Delegation Regret When Using a General-Purpose AI Agent

**Authors:** Shiva Pochampally, Shengwei An, Yan Chen (Department of Computer Science, Virginia Tech)
**Publication date:** July 2026 (arXiv id 2607.18257) — the arXiv identifier confirms the submission month/year; the exact day of the month could not be independently verified (see sourcing note below)
**Venue:** arXiv preprint (categories: cs.HC, cs.AI); no peer-reviewed conference or journal venue could be confirmed from the sources available
**Paper link:** https://arxiv.org/abs/2607.18257 (HTML: https://arxiv.org/html/2607.18257)
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-08-15

> **A note on sourcing:** This session's direct network access to arxiv.org (and mirrors such as ar5iv, Hugging Face, and Semantic Scholar) was blocked by organizational egress policy, so this summary could not be built from a first-hand read of the full PDF. It was assembled instead by cross-checking many independent web-search queries against snippets of the paper's abstract and HTML rendering. Facts that were consistent and specific across multiple independent searches — the authors, institution, study design, measured constructs, and the paper's three headline findings — are reported as such. Details that could not be confirmed this way (the exact submission day, the full descriptions of all five tasks, the paper's own stated limitations section, and any peer-review venue) are marked "Not available" or flagged as this summary's own inference, rather than invented. Readers who need exact figures should check the primary PDF directly.

---

## The problem the paper addresses

Until recently, most people's experience of an AI assistant was a chat window: you asked something, it answered, and nothing happened in the world unless you did it yourself. General-purpose AI agents — the paper studies one called OpenClaw — change that. You can now ask an agent to actually *do* things: search your files, draft and send an email, book something, browse on your behalf. The paper's core question is what happens to trust and comfort once an AI stops just talking and starts acting: how much should users let it do on its own, and when do they regret having let it act?

## Why this problem matters

An assistant that only talks is easy to trust or ignore — a bad answer costs you a moment. An assistant that *acts* can send the wrong email, book the wrong thing, or share the wrong file before you get a chance to catch it. As general-purpose agents move from labs into everyday student and worker life, the design choice of "how much should this agent be allowed to do without asking me first" has real consequences, and it isn't yet well understood how ordinary users actually want that boundary drawn.

## What makes the system agentic

The subject of the study, OpenClaw, is a general-purpose AI agent: it is given tasks in natural language and then plans and carries out multi-step actions in the world on the user's behalf — searching and reading files, composing and sending emails, and other everyday digital chores — rather than producing a single one-shot text reply. It is evaluated here specifically as an agent that *takes actions*, which is exactly the property the paper is interested in: the shift from an assistant that only advises to one that can also act as a delegated "actor."

## How humans and the AI agent collaborate

Each of the 20 student participants worked through five different daily tasks with OpenClaw, deliberately chosen to vary along three axes that matter for delegation: how much personal privacy was exposed, how severe the consequences of a mistake would be, and how reversible the agent's action was (e.g., a low-stakes, fully reversible file search vs. an irreversible action with social consequences, such as sending an email). For each task, participants experienced the agent operating with a given degree of autonomy, then reported how much trust, control, and transparency they felt, how much supervision effort it took, and whether they would have preferred to approve the action first.

## What role the human plays

Humans in this study are real end users delegating real daily tasks to the agent and directly experiencing the consequences of doing so — not simulated personas and not just annotators rating transcripts after the fact. Participants decided (or reported wanting to decide) how much autonomy to grant per task, rated the interaction on validated constructs (trust, perceived control, transparency, supervision burden, approval preference) on 5-point Likert scales after each task, and gave free-text reflections that the authors analyzed through thematic coding.

## What role the AI agent plays

OpenClaw is the delegate: it receives a task and a level of granted autonomy, and then executes the necessary steps itself — in some conditions previewing its intended action for approval, and in others simply acting. The paper's findings turn on exactly this variable: whether the agent asks first or just acts, and how visible and reversible the resulting action is.

## How control, initiative, and decisions are shared

Rather than a single fixed autonomy setting, the study varies how much initiative the agent is given per task, letting the researchers observe where users want the human to retain the final say versus where they're comfortable letting the agent proceed unsupervised. The paper's central empirical claim is that this isn't a fixed, agent-level setting in users' minds — it's negotiated task by task.

## The paper's main idea

The paper's main contribution is the concept of **delegation regret**: a specific kind of dissatisfaction distinct from the agent simply making a mistake. Delegation regret shows up when the agent acts *successfully* but beyond the scope the user would have actually authorized in the moment — the user's complaint isn't "it got it wrong," it's "it shouldn't have just gone ahead."

## How the approach works

The authors ran a controlled, within-subject study: 20 AI-literate university students, most of them new to agentic delegation, each completed the same five tasks using OpenClaw. The tasks were engineered to systematically differ in privacy exposure, consequence severity, and reversibility (for example, a low-risk file-retrieval task to find a tuition deadline in a folder of mixed documents, versus an irreversible email-drafting-and-sending task with social consequences). After each task, participants rated trust, perceived control, transparency, supervision burden, and approval preference on 5-point Likert scales, and wrote free-text reflections that were later thematically coded.

## Human study or evaluation design

This is a real human-subjects, within-subject controlled study — not an LLM-judged benchmark and not a study built on simulated user personas. Every participant used the live agent to complete real tasks and reported their own reactions immediately afterward, combining quantitative Likert ratings with qualitative thematic analysis of open-ended reflections.

## Participants and study setting

Twenty university students took part, described as AI-literate but largely new to agentic delegation specifically (as opposed to chatbot use). The exact institution beyond Virginia Tech's involvement, recruitment method, and demographic breakdown could not be confirmed from the sources available for this summary and should be checked against the primary paper.

## Experiments or benchmarks

There is no public benchmark or dataset involved — this is a custom five-task protocol designed specifically for this study, not an evaluation against a shared leaderboard.

## Main results

Three findings recur consistently across the sources checked for this summary:

1. **Trust is calibrated per task, not per agent.** Participants were comfortable granting wide autonomy for advisory and low-stakes tasks, but demanded confirmation before irreversible, externally visible actions — the same person could trust the agent fully on one task and want a checkpoint on the next.
2. **Irreversibility plus external visibility — not stakes alone — drove trust withdrawal.** A moderate-stakes email task produced the sharpest drop in reported trust, while a task that was high-stakes but easily verifiable did not produce the same reaction.
3. **Delegation regret appeared when the agent acted without previewing its action first — even when the outcome was rated successful.** Getting the right result didn't prevent regret if the user never got a chance to see and approve the action beforehand.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central human-related outcomes are about trust and perceived control rather than raw task performance: participants' self-reported trust, sense of control, and willingness to grant autonomy shifted noticeably from task to task depending on reversibility and visibility, and "supervision burden" was explicitly measured as part of this trade-off. The clearest safety/control-relevant result is behavioral, not just attitudinal: regret was tied to the *design choice* of acting without preview, independent of whether the action actually succeeded — suggesting that outcome quality alone does not guarantee a satisfied, appropriately-trusting user.

## What is genuinely new

The paper's most distinctive contribution — as far as could be confirmed — is naming and empirically demonstrating **delegation regret** as a phenomenon separate from ordinary agent error: a specifically *process*-based dissatisfaction (the agent overstepped what would have been authorized) rather than an *outcome*-based one (the agent got it wrong). Tying this to concrete task properties — reversibility and external visibility rather than stakes alone — gives agent designers a more actionable lens than a single "risk level" slider.

## Limitations and open questions

*This summary's own interpretation, not verified verbatim from the paper's limitations section:* the study's sample is small (20 participants) and drawn from a single, AI-literate student population using one specific agent product (OpenClaw), which likely limits how far the findings generalize to other user groups, agents, or higher-stakes professional settings. The paper's own stated limitations, generalizability discussion, and any explicit future-work section could not be independently confirmed from the sources available for this summary and should be checked against the primary PDF.

## Practical implications

The sources checked describe the authors drawing out concrete design implications for agent builders: expose the agent's action boundaries to users up front, support per-task (rather than per-agent, one-size-fits-all) autonomy policies, and keep advisory output separate from agentic execution so users can tell "the agent is suggesting" apart from "the agent is about to act."

## Why you should care

If you build, deploy, or simply use a general-purpose AI agent that can take real actions on your behalf, this paper offers a concrete, human-tested reminder that "did it work?" is not the same question as "should it have just gone ahead?" — and that the second question is what actually drives regret and eroded trust, even when the agent performs flawlessly.

---

*Author's interpretation note: statements above describing what participants reported, felt, or preferred reflect the paper's own findings as far as they could be verified through independent secondary sources; the framing in "Why this problem matters," "Practical implications" (beyond the directly attributed design recommendations), and "Why you should care" reflect this summary's own interpretation and are not verbatim claims from the paper.*
