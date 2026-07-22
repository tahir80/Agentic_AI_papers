# AI Writes Faster Than Humans Can Review: A Longitudinal Study of an Enterprise "2×" Mandate

**Authors:** Hao He, Shyam Agarwal, Yegor Denisov-Blanch, Pavel Azaletskiy, Sanmi Koyejo, Bogdan Vasilescu
**Publication date:** 2026-07-02 (arXiv id 2607.01904, v1, cs.SE)
**Venue:** arXiv preprint; peer-review status and target venue not confirmed in available sources.
**Paper link:** https://arxiv.org/abs/2607.01904
**Code link:** Not available (no public code/data repository found; the underlying dataset is proprietary company telemetry)
**Project page:** Not available
**Date added:** 2026-07-22

> **A note on sourcing:** arXiv could not be reached directly from this research session (network/proxy restrictions blocked both `arxiv.org` and general web fetches during this run), so this summary is built from the paper's title, abstract, and reported headline statistics as surfaced through multiple corroborating web searches, not a full read of the PDF. Figures below are the ones that appeared consistently across independent search results. Anything not confirmed this way is marked "Not available" rather than guessed.

---

## The problem the paper addresses

A lot of companies are now telling their engineers: use AI coding tools, and double your output. This paper asks a simple but under-studied question — what actually happens, over time, inside a real company that adopts a mandate like that? Specifically, it tracks what happens to **code review** — the human step where a colleague checks your code before it ships — once AI agents start writing a large share of that code.

## Why this problem matters

Writing code faster is only useful if the code is still safe to ship. Traditionally, a human reviewer is the checkpoint that catches bugs, security problems, and bad design before a change reaches production. If AI agents can generate pull requests much faster than people can review them, that checkpoint becomes a bottleneck — and companies have to decide how to respond: hire more reviewers, slow down, or lean more on automated review. Understanding which of these actually happens (and what it costs) matters for every organization currently rolling out similar "AI productivity mandates."

## What makes the system agentic

The "agents" here are the AI coding tools used across the company to autonomously draft and submit pull requests (PRs) — not a single research prototype, but the mix of LLM-based coding assistants and agents that generated an increasing share of real, merged code changes in the company's actual version-control and CI pipeline. These tools go beyond single text replies: they read a codebase, make multi-step edits, and submit changes directly into the company's real software-engineering workflow, where they are then evaluated the way any contributor's code would be — through review, merge, and (if something goes wrong) revert.

## How humans and the AI agent collaborate

This is not a lab prototype with a purpose-built collaboration interface — it's an observational study of collaboration as it already happens at scale inside a company's everyday engineering process: AI agents author code, and human engineers (and, increasingly, automated reviewers) check it before it merges. The paper's core contribution is documenting how that human-AI division of labor shifted over 28 months as the volume of AI-authored code grew.

## What role the human plays

Human engineers write some code themselves, use AI agents to draft the rest, and act as reviewers who read, question, and approve or reject pull requests — AI-authored or otherwise — before they merge. As the mandate pushed AI-authored PR volume up, the human reviewer's job increasingly became the rate-limiting step in the whole pipeline.

## What role the AI agent plays

AI coding agents autonomously draft an increasing share of pull requests — reportedly growing to roughly 90% of PR volume by the end of the study window — each one a multi-step, tool-using contribution (reading code, making edits, opening a PR) rather than a single generated snippet.

## How control, initiative, and decisions are shared

Initially, human review was the default gate nearly every PR passed through. As AI-authored volume grew far faster than the human reviewer pool, the organization visibly shifted the gate itself: automated review absorbed more and more of the checking work, and the share of PRs receiving *any* human review fell substantially. In other words, control over "who checks the AI's work" migrated, in practice, from mostly-human to increasingly automated — a real-world, unplanned instance of a system renegotiating the human's oversight role because the human couldn't keep pace.

## The paper's main idea

**Claim by the authors:** enterprises that mandate large AI-driven productivity gains without also scaling review capacity end up restructuring their review process around automation, not around adding human reviewers — and the paper presents this specific company's 28-month trajectory as documented, quantitative evidence of that dynamic, alongside evidence that easily observable quality proxies did not visibly worsen even as human review coverage dropped.

## How the approach works

The authors treat this as a natural experiment: a mid-sized, AI-forward company that publicly committed, from mid-2025, to a "2×" mandate — doubling merged pull requests per engineer. The researchers analyzed a panel of the company's real engineering telemetry from January 2024 to April 2026 (i.e., well before and well after the mandate began), tracking PR volume, authorship (human vs. AI), reviewer counts, review type (human vs. automated), end-to-end PR cycle time, and coarse quality proxies (merge and revert rates) over that whole window.

## Human study or evaluation design

**Demonstrated in the paper:** this is not a recruited lab study or survey — it is a longitudinal, quantitative analysis of real, naturally occurring engineering activity (a "field" or "natural experiment" design) drawn from the company's own production data across the mandate period.

## Participants and study setting

The dataset covers **802 developers** and **196,212 pull requests** at one mid-sized, AI-forward company (not named in available sources), spanning January 2024 through April 2026. These are real engineers doing their actual jobs, not recruited study participants, crowdworkers, or simulated personas.

## Experiments or benchmarks

There is no public benchmark here — the "experiment" is the company's own mandate, and the "dataset" is its internal PR and review history. No public dataset or code release was found in available sources.

## Main results

- Per-capita merged-PR throughput reportedly reached **2.09×** the pre-mandate baseline by April 2026 — one of the largest such gains reported from a real field deployment of AI coding tools, per the authors.
- AI-authored PRs reportedly grew to roughly **90%** of total PR volume.
- The reviewer pool grew only about **1.5×** while AI-authored PR volume grew roughly **3.1×**, so per-reviewer load roughly doubled.
- The share of PRs receiving at least one **human** review reportedly fell from about **89% to 68%**, while the share receiving **automated** review reportedly rose from about **19% to 84%**, with automated review overtaking human review.
- 90th-percentile end-to-end PR cycle time reportedly climbed through 2025 (peaking near **66 hours**) before receding in early 2026, an overall reported increase of about **22%** over the window.
- Merge and revert rates reportedly stayed roughly flat across the period — the authors report no measurable penalty on these particular, coarse, short-horizon quality proxies despite the shift toward automated review.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper (as reported):** human reviewer workload rose sharply (per-reviewer load roughly doubling), and the share of code changes that a human ever laid eyes on dropped substantially as automated review filled the gap. **Authors' framing:** despite that drop in human review coverage, the flat merge/revert rates suggest no obvious quality collapse — but the authors' own quality proxies are described as coarse and short-horizon, so slower-emerging problems (e.g., long-term maintainability, security debt) would not necessarily show up in this data. **Our interpretation:** this reads less as evidence that "automated review is a safe substitute for human oversight" and more as a case study in how quickly production pressure can erode human oversight coverage before anyone formally decides to lower the bar.

## What is genuinely new

Most discussion of AI coding agents' effect on software engineering has relied on short-term productivity claims or small controlled studies. This paper's contribution is a rare, long (28-month), large-panel (802 developers, ~196K PRs), real-company natural experiment that tracks not just output volume but the downstream reallocation of human oversight capacity — arguably the clearest available evidence to date of AI-authored code volume outpacing human review capacity inside an actual organization, and of the organizational response (leaning on automated review) that followed.

## Limitations and open questions

This is a single-company, proprietary dataset — the company is not named in available sources, and no code or data release was found, so independent replication is not currently possible. It's an observational natural experiment, not a randomized controlled trial, so causal claims about the mandate specifically driving these outcomes should be treated cautiously. The quality proxies used (merge and revert rates) are, by the authors' own framing, coarse and short-horizon, so the paper cannot speak to slower-developing quality or security consequences of the shift away from human review. It's also unclear from available sources exactly which AI coding tools/agents were in use, or whether findings would generalize to companies of different size, domain, or review culture.

## Practical implications

For any organization currently mandating or considering large AI-driven productivity targets for engineers, this paper is a concrete warning: raising AI-assisted output without proportionally scaling review capacity does not stay a "someday" problem — in this case it visibly reshaped the review process within roughly a year, shifting oversight away from humans and toward automation by default, not by explicit policy choice. It's a strong argument for treating review-capacity planning as a first-class part of any AI-coding-agent rollout, not an afterthought.

## Why you should care

If your workplace is (or soon will be) under similar pressure to "do more with AI," this paper offers a rare, data-grounded look at what actually happens to the human side of the pipeline — not in theory, but at a real company, over real time. It's a useful reality check against the assumption that "a human will review it" scales for free as AI-authored code volume grows.
