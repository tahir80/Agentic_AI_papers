# When Code Authors Are Agents: A Large-Scale Study of Human–Agent Collaboration in Pull Requests

**Authors:** Anthonia Oluchukwu Njoku, Zohreh Sharafi, Foutse Khomh (Polytechnique Montréal — SENSE Lab and SWAT Lab)
**Publication date:** 2026-07-05 (proceedings publication date at AIware '26; exact preprint posting date not independently confirmed)
**Venue:** 3rd ACM International Conference on AI-Powered Software (AIware '26), co-located with FSE 2026, Montréal, Canada
**Paper link:** https://openreview.net/pdf?id=ArurxAmCtR (open-access submission draft); publisher version at https://doi.org/10.1145/3805760.3814909 (paywalled)
**Code link:** Not available (paper builds on the public "AIDev" dataset, https://huggingface.co/datasets/hao-li/AIDev — not the authors' own repository)
**Date added:** 2026-09-02

> **A note on sourcing:** This session's network access blocks direct fetches to arxiv.org, openreview.net, huggingface.co, and several other research-hosting domains (an organization-level egress policy). Full-text reading of the paper's PDF was therefore not possible. This summary is built from web-search-grounded excerpts of the paper's abstract and reported findings, cross-checked across multiple independent search results for consistency, plus publicly available conference/venue metadata. Anything not corroborated this way is marked "not available," and interpretive statements are labeled as such. Readers who want to verify exact figures should consult the OpenReview PDF directly.

---

## The problem the paper addresses

Autonomous coding agents (tools like Claude Code, GitHub Copilot's agent mode, OpenAI Codex, Devin, and Cursor) no longer just autocomplete lines of code — they now open entire pull requests (PRs) on real GitHub repositories, acting as a "code author" alongside human contributors. But a PR isn't just a patch; it's a request for a human team to review, discuss, and decide whether to accept it. This paper asks whether — and how — that human side of the process changes when the author on the other end is an AI agent instead of a person.

## Why this problem matters

Software teams are adopting coding agents fast, but most existing research focuses on whether the *code* the agent writes is correct. Far less is known about what happens in the human-facing part of the workflow: do maintainers review agent PRs differently, argue with them differently, merge them at different rates, or take longer or shorter to decide? If agent-authored contributions quietly reshape reviewing norms and reviewer effort at scale, teams need to know that before they scale up agent usage — otherwise they risk misjudging both the productivity gains and the hidden review costs.

## What makes the system agentic

The subjects of the study are five real, deployed autonomous coding agents — Claude Code, OpenAI Codex, Devin, GitHub Copilot's agent mode, and Cursor — observed "in the wild" on GitHub. Each of these tools is given a coding task, plans and executes a multi-step sequence of file edits and commits with real repository access, and packages the result as a pull request without a human writing the code line-by-line. That combination — a goal, multi-step planning and execution, and real tool/repository access, evaluated on its real-world output rather than on a single-turn benchmark — is what makes this agentic AI rather than a code-completion feature.

## How humans and the AI agent collaborate

The collaboration happens through GitHub's standard pull-request review workflow: the agent opens a PR, human reviewers (maintainers or teammates) read the diff, leave comments, request changes, and ultimately merge or close it. The paper studies this naturally occurring interaction at scale — comparing how it unfolds for agent-authored PRs versus human-authored PRs on the same repositories — rather than designing a new collaboration interface of its own.

## What role the human plays

**Reported by the authors, per available summaries:** human maintainers and reviewers are the ones who read agent-submitted diffs, comment on them, request changes, and decide whether to integrate (merge) or reject the contribution. Their engagement — how much and what kind of feedback they give — is treated as the key human input the paper measures, and reviewer comments on agent PRs reportedly differ systematically in tone (more analytic, less socially oriented) from comments on human PRs (longer, more explanatory, more socially oriented).

## What role the AI agent plays

The agent acts as an autonomous PR author: it independently proposes a change, produces the commits and code diff, and — per the paper's framing of "collaboration signals" — responds to review feedback within the PR thread. The paper's structural analysis reportedly finds agent PRs tend to have fewer commits but more change concentrated per commit (a large effect, Cliff's δ = 0.54) and more localized edits (medium effect sizes on files touched and lines deleted, a smaller effect on lines added) compared with human-authored PRs.

## How control, initiative, and decisions are shared

Initiative to propose a change sits with the agent; the decision to accept it sits entirely with human reviewers, who retain merge/reject authority throughout. This is not a jointly negotiated workflow — it is standard GitHub code review applied to a non-human contributor — but the paper's contribution is showing how that asymmetric structure (agent proposes, human disposes) plays out differently depending on task type and how agents are integrated day to day.

## The paper's main idea

**Claim by the authors, per available summaries:** the effect of coding agents on repositories is not purely technical — it is socio-technical. Agents don't just introduce code; they measurably reshape how human reviewers engage, communicate, and decide, and that reshaping varies by the kind of task being done (agents reportedly do comparatively better on documentation-type contributions and worse on contributions that change program behavior).

## How the approach works

The authors compared 40,214 pull requests across 2,807 GitHub repositories (repositories with over 100 GitHub stars, drawn from the public "AIDev" dataset), split into 33,596 agent-authored PRs from the five agents named above and 6,618 human-authored PRs from the same repositories, as a baseline. They analyzed these along three dimensions reported in the paper: integration outcomes (merge rate, time-to-integration), structural characteristics of the PRs (commit count, change concentration, files touched), and collaboration/communication signals during review (comment tone, social orientation, volume of bot-generated commentary).

## Human study or evaluation design

**Not a controlled, recruited human-subjects experiment.** This is a large-scale observational (mining-software-repositories style) study of naturally occurring GitHub activity: real maintainers and reviewers responding to real PRs, agent- and human-authored alike, with no researcher-assigned condition or intervention.

## Participants and study setting

**Real-world GitHub practitioners, not a recruited sample.** The "participants" are the maintainers and contributors of 2,807 real, popular (100+ star) open-source repositories who reviewed the 40,214 PRs in the dataset during the study period. No individual demographic or experience-level breakdown of these reviewers was available in the sources used for this summary; the setting is naturalistic field data rather than a lab or survey.

## Experiments or benchmarks

There is no held-out benchmark in the usual agent-evaluation sense. The "experiment" is a large-scale comparative and statistical analysis of the AIDev-derived PR dataset, contrasting agent-authored and human-authored PRs across integration, structural, and communication measures. The underlying public dataset (AIDev, https://huggingface.co/datasets/hao-li/AIDev) is separately documented by other researchers (Hao Li et al., arXiv:2602.09185) and is reused here as the data source rather than something the authors built themselves.

## Main results

**Claims reported by the authors, per available summaries (not independently re-verified against the primary source in this session):**
- Agent-authored PRs are integrated (merged) **significantly faster** than human-authored PRs on average.
- Agent-authored PRs nonetheless show a **lower overall merge rate** than human-authored PRs.
- **Task type moderates this pattern:** agents reportedly outperform humans on documentation-style contributions but underperform on contributions that change program behavior.
- **Structural differences:** agent PRs have fewer commits but more change concentrated per commit (Cliff's δ = 0.54, a large effect) and somewhat more localized changes (medium effect for files touched and lines deleted, smaller effect for lines added).
- **Communication differences:** review comments on agent PRs are reportedly more analytic in tone and less socially oriented, and attract proportionally more bot-generated commentary, while comments on human PRs are longer, more explanatory, and more socially oriented.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper, per available summaries:** the study documents a behavioral/communication-outcome effect — how reviewer commenting style and merge decisions differ for agent- versus human-authored work — as its measure of collaboration quality. **Not demonstrated (based on available excerpts):** no self-reported trust, workload (e.g., NASA-TLX-style), or safety-incident measures are reported; there is no evidence of a controlled comparison isolating *why* comment tone or merge rate differs (e.g., reviewer expectations, agent PR quality, or the visibility of AI authorship could each plausibly contribute). **Our interpretation:** the findings are best read as documenting that human reviewing behavior measurably adapts to agent authorship — a first-order signal of a collaboration effect — rather than as evidence about reviewers' subjective trust or workload, which the paper does not appear to measure directly.

## What is genuinely new

- A **comparative, large-scale (40k+ PR) analysis** contrasting agent-authored and human-authored contributions on the *same* repositories, rather than studying agent PRs in isolation.
- Evidence that the effect of coding agents is **socio-technical**: differences show up not just in code characteristics but in how humans communicate during review.
- A **task-type moderation finding** (agents relatively stronger on documentation, weaker on behavior-changing code) that offers a concrete, testable pattern for where agent contributions are currently best suited.

## Limitations and open questions

- **Observational, not experimental:** no manipulated condition, so reported associations (e.g., between authorship type and comment tone or merge outcome) describe correlational patterns, not proven causal effects.
- The sample is restricted to **higher-visibility repositories (100+ GitHub stars)** and five specific commercial agents; how well the patterns generalize to smaller projects, private repositories, or other agents is unclear.
- No individual-level reviewer demographics, expertise, or workload data are available, limiting insight into *who* is doing this review work and at what cost to them.
- **This session's own limitation:** because direct access to the paper's full text was blocked, the specific figures and framing above are drawn from consistent third-party search-result summaries rather than a direct read of the PDF — readers should treat exact numbers as approximate pending direct verification against the paper itself.

## Practical implications

For engineering teams already using or considering coding agents, the findings (as reported) suggest agent contributions may currently be best matched to lower-risk, more mechanical tasks like documentation, where they reportedly do comparatively well, while behavior-changing code likely still needs closer human scrutiny. The reported shift toward more analytic, less socially-oriented review commentary on agent PRs may also be worth watching as a signal of how review culture itself is adapting — not just the code being reviewed.

## Why you should care

This paper is a reminder that adopting coding agents isn't just a question of whether the generated code is good — it changes the human workflow wrapped around that code: how fast things get merged, how often they get merged at all, and how people talk to each other (or to a bot) during review. As agent-authored contributions become a larger share of real-world software development, understanding this socio-technical shift, at the scale of tens of thousands of real pull requests rather than a handful of lab tasks, is directly relevant to how teams should structure human oversight of agentic coding tools going forward.
