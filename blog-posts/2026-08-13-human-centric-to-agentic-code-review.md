# From Human-Centric to Agentic Code Review

**Authors:** Suzhen Zhong, Shayan Noei, Bram Adams, Ying Zou (Queen's University, Kingston, Canada)
**Publication date:** 2026-07-14 (arXiv v1, id 2607.13196)
**Venue:** arXiv preprint (cs.SE); peer-reviewed venue/acceptance status not independently confirmed
**Paper link:** https://arxiv.org/abs/2607.13196 (PDF: https://arxiv.org/pdf/2607.13196)
**Code link:** Not available — the paper is described as releasing a longitudinal replication dataset/package, but no independently verifiable repository URL could be confirmed from available sources
**Project page:** Not available
**Date added:** 2026-08-13

> **A note on sourcing:** This session's outbound network access to arxiv.org and related mirror/host domains (Hugging Face, Semantic Scholar, alphaXiv, ar5iv, etc.) was blocked by organizational egress policy, so this summary could not be built from a direct read of the full PDF. It is instead built by triangulating across many independent web searches that draw on the arXiv abstract/HTML page and secondary discussions of it, cross-checking each factual claim across results before including it. Facts that were consistent across searches (authors, dates, dataset scale, the three-era framing, the smell-prevalence numbers) are reported as such; anything that could not be cross-confirmed is flagged below or marked "not available" rather than invented. Readers who want to rely on exact figures should verify against the primary PDF.

---

## The problem the paper addresses

Code review used to mean one thing: a human teammate reads your changes and leaves comments. In the last couple of years that has changed fast — first LLM-based bots started leaving natural-language review comments, and more recently, more autonomous "agentic" reviewers arrived that can go fetch extra project context, run tests and linters, and check their own claims before commenting. The paper asks a very concrete question: as real open-source projects moved through these three generations of review technology, did review quality actually get better, worse, or just different — and how did the *way humans and AI reviewers work together* change along the way?

## Why this problem matters

Code review is one of the main places where an organization's judgment about software quality gets exercised — and, increasingly, one of the main places where humans and AI agents now have to collaborate directly, since an "agentic" reviewer isn't just producing an answer, it's participating in a back-and-forth process alongside human reviewers, authors, and (sometimes) other bots. If adopting AI reviewers, especially fast, quietly erodes review quality — more rubber-stamping, more repeated blind spots — that's a governance problem hiding behind a productivity win. Understanding *how* teams are actually integrating AI into review, and what that does to real review outcomes, matters for anyone deciding whether and how to bring agentic reviewers into their own workflow.

## What makes the system agentic

The subject of the study is not a single system the authors built, but real-world "agentic code review" tools already operating inside GitHub pull requests at scale — reviewers that, per the paper's description, go beyond generating natural-language feedback from a diff (what the authors call the "LLM-assisted" era) by autonomously retrieving additional project context, running development tools, and verifying their own findings before posting a review comment. That is squarely agentic behavior: a goal (produce a sound review), multi-step tool use (context retrieval, tool execution, self-verification), and an action taken in a real external environment (commenting on and shaping a real pull request) — evaluated not in a lab but in its actual deployed setting.

## How humans and the AI agent collaborate

Collaboration happens inside the ordinary GitHub pull-request review loop, but with the reviewer pool now mixed: human reviewers, LLM reviewers, and agentic reviewers all participate — sometimes on the same PR. Humans author code, respond to review comments (from humans or AI), and decide whether to accept, dispute, or ignore AI-generated feedback; AI reviewers post comments, flag issues, and in the agentic era, actively verify claims using tools before commenting. The paper studies this as an evolving, mixed human-AI process rather than a single fixed interaction pattern, tracking how the balance and quality of that process shifted as projects adopted each new generation of AI reviewer.

## What role the human plays

Humans remain review participants throughout all three eras studied — authoring pull requests, reviewing others' code, and reacting to AI-generated comments. The paper reports that human reviewers keep contributing a qualitatively different kind of feedback than AI reviewers do: things like building shared understanding, discussing testing, and transferring knowledge, rather than only flagging defects. In other words, even as AI reviewers took on more of the review workload, humans didn't just supervise — they kept doing a distinct part of the review job that the AI reviewers, by the paper's account, did not replicate.

## What role the AI agent plays

Across the three eras the paper tracks, the AI reviewer's role expands substantially: in the human-centric era, AI is at most a supporting bot or older ML tool; in the LLM-assisted era, an LLM reads a diff and produces natural-language review feedback; in the agentic era, AI reviewers independently retrieve extra project context, run development tools, and verify findings before commenting — taking on a more autonomous, investigative role focused primarily on code improvement and defect detection.

## How control, initiative, and decisions are shared

The paper's own contribution here is a classification of *how* projects actually shared this transition: it identifies three distinct **AI reviewer adoption patterns** across the 207 projects studied — **Gradual AI Adoption** (LLM and then agent reviewers layered in incrementally alongside the existing human process), **Rapid LLM Adoption** (a fast shift to LLM-assisted review without much agent infrastructure), and **Rapid AI Agent Adoption** (projects that jump more directly to multi-agent review, largely skipping a distinct LLM-assisted phase). These patterns describe, in effect, different ways real teams handed initiative from purely human reviewers toward AI reviewers — and the paper's central finding is that *which* pattern a project followed mattered a lot for what happened to review quality.

## The paper's main idea

**Claim by the authors:** review quality and process are not simply "improved" by AI adoption in a uniform way — the effect depends heavily on *how* a project adopts AI reviewers (gradually vs. rapidly, LLM-first vs. agent-first), and specifically on the resulting human-AI collaboration patterns that adoption produces, which the authors argue are a strong explanatory factor for review-quality outcomes alongside more traditional review factors.

## How the approach works

The authors mined 1.02 million reviewed pull requests from 207 open-source GitHub projects whose review history spans all three eras (human-centric, LLM-assisted, agentic), using this longitudinal data to (1) classify each project into one of the three AI-adoption patterns based on how its reviewer composition changed over time, (2) measure the prevalence of established "code review smells" — recognized problematic review patterns such as **Review Buddies** (a narrow, repeatedly-reused set of reviewers) — before and after AI reviewers joined, and (3) measure review efficiency (time to a review decision) under each adoption pattern and reviewer configuration.

## Human study or evaluation design

**Demonstrated in the paper:** this is a large-scale, naturalistic mining study of real, in-the-wild human-AI code review activity — not a lab experiment with recruited participants and self-report instruments. Its "human study" is effectively the recorded behavior of real developers reviewing real code across 207 active GitHub projects, comparing what those same human reviewer communities did before and after AI reviewers entered their workflow.

## Participants and study setting

**Real developers, real projects, no recruitment.** The dataset covers 207 open-source GitHub projects and 1.02 million pull requests, capturing the actual review activity of the human developer communities maintaining those projects as they transitioned through the three review eras. No demographic details, surveys, or self-report measures are involved — the "participants" are the developers whose ordinary GitHub activity is being mined, not lab or crowdsourced study recruits.

## Experiments or benchmarks

There is no public leaderboard-style benchmark; the empirical apparatus is the longitudinal PR dataset itself, analyzed by (a) AI-adoption-pattern classification per project, (b) code review smell detection using an established review-smell taxonomy, and (c) review-turnaround/efficiency measurement, all compared across the human-centric, LLM-assisted, and agentic eras and across the three adoption patterns.

## Main results

**Demonstrated in the paper (per cross-checked secondary descriptions; verify exact figures against the primary PDF):**
- Across the dataset, the prevalence of code review smells rose sharply once AI reviewers entered the process: on average, from about **16% for human-only reviews** to about **60% for LLM-involved review patterns** and about **53% for agent-involved review patterns**.
- **Rapid LLM Adoption** (fast switch to LLM-assisted review without built-up agent infrastructure) was significantly associated with an *increase* in code review smell prevalence.
- Once LLM and agent reviewers were part of the process, the specific **human-AI collaboration pattern** (e.g., who initiates a review, how many AI reviewers are involved) became a strong explanatory factor for smells like **Review Buddies** — alongside more traditional review factors.
- For review efficiency, agent-involved patterns — particularly reviews initiated by an AI agent or involving multiple AI agents — were associated with **faster review decisions**, but specifically under the **Gradual AI Adoption** and **Rapid AI Agent Adoption** patterns, i.e., the speed benefit was not uniform across all adoption styles.
- Human reviewers continued to contribute feedback focused on understanding, testing, and knowledge transfer — a qualitatively different contribution than the code-improvement/defect-detection focus the paper attributes to AI reviewers.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the paper's human-relevant outcome is measured indirectly, through the *quality and structure of the review process itself* rather than through self-reported trust or workload — specifically, the rise in review-smell prevalence (more Review Buddies, narrower reviewer pools, and related problematic patterns) once AI reviewers joined, and the dependence of that outcome on which adoption pattern a project followed. **Our interpretation:** this is evidence that simply adding AI reviewers — especially quickly, via the "Rapid LLM Adoption" pattern — can come with a real, measurable cost to review-process health (e.g., narrower reviewer diversity), even as agent-involved reviews sped up decision time in some adoption patterns. The paper does not report standardized trust, workload (e.g., NASA-TLX), or safety-incident metrics, so those specific effects should be treated as **not established** by this study, distinct from the review-smell and turnaround-time effects that are.

## What is genuinely new

- A **longitudinal, three-era framing** (human-centric → LLM-assisted → agentic) applied to real project histories at scale (1.02M PRs, 207 projects), rather than a single-snapshot comparison of "with AI" vs. "without AI."
- A **typology of AI-reviewer adoption patterns** (Gradual AI Adoption, Rapid LLM Adoption, Rapid AI Agent Adoption) that lets the paper show adoption *style*, not just adoption itself, predicts review-quality outcomes.
- Evidence that **human-AI collaboration pattern** (who initiates review, how many AI reviewers participate) is itself a significant explanatory variable for review smells — treating the collaboration structure, not just the presence of AI, as the object of study.

## Limitations and open questions

- This is an observational, naturalistic mining study of GitHub history, not a controlled experiment — it can identify strong associations between adoption pattern and review-quality outcomes, but the paper's own causal claims (to the extent it makes any) should be read with the usual caveats of retrospective repository mining.
- No self-report data from the human developers involved (trust, perceived workload, satisfaction) appears to be part of this study, so it cannot speak to how reviewers *felt* about the transition, only to what the recorded review artifacts show.
- This session could not confirm peer-review/venue status, a public replication package or code/dataset link, or the exact statistical methodology (e.g., significance thresholds, controls) because full-text access was network-restricted; readers should verify these directly against the arXiv PDF.
- The 207 projects studied are all open-source GitHub projects; whether these adoption-pattern effects generalize to closed-source/enterprise codebases with different review norms is not established here.

## Practical implications

If the reported association holds up under full-text verification, it's a caution for engineering organizations rolling out AI code reviewers: *how* you adopt matters. A fast, LLM-first rollout that isn't paired with attention to reviewer diversity and review-process design appears more likely to accumulate review smells like an over-reliant, narrow reviewer pool — even if it also speeds up nominal review turnaround. Teams considering agentic reviewers might get more value from a more deliberate, gradual integration that keeps human reviewers doing the parts of review (context-building, testing discussion, knowledge transfer) that this study suggests AI reviewers are not yet replicating.

## Why you should care

This paper is a reminder that "add an AI reviewer" is not one intervention — it's a family of different human-AI collaboration arrangements, and the arrangement you pick appears to change what you get. Rather than asking only "do agentic reviewers help or hurt," the paper's real contribution is showing, with a very large real-world dataset, that the *pattern of collaboration* between human and AI reviewers is itself something worth designing deliberately — not a side effect to be discovered after the fact.
