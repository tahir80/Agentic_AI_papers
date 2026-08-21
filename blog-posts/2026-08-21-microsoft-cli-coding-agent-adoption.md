# Who Actually Keeps Using an AI Coding Agent? Microsoft Tracked Tens of Thousands of Engineers to Find Out

**Authors:** Emerson Murphy-Hill, Jenna Butler, Alexandra Savelieva (Microsoft)
**Publication date:** 2026-07-01 (arXiv v1)
**Venue:** arXiv preprint (peer-reviewed venue not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2607.01418
**Code link:** Not available (no public repository found for this paper at the time of writing; the study relies on internal Microsoft telemetry that is not public)
**Project page:** Not available
**Date added:** 2026-08-21

> **A note on sourcing:** this session's outbound network access to arxiv.org (and to several other paper-hosting mirrors) returned a blocked connection for direct fetches (organization egress policy, not a paywall — the paper is a public arXiv preprint). This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

When a company rolls out a new AI coding agent to its engineers, two questions matter more than any benchmark score: will people actually try it, and will they keep using it once the novelty wears off? This paper studies exactly that, inside Microsoft's own early-2026 rollout of two command-line coding agents — Anthropic's Claude Code and GitHub's Copilot CLI — to tens of thousands of engineers. It asks who adopts these tools, who sticks with them, and whether the engineers who do use them actually ship more work as a result.

## Why this problem matters

Agentic coding tools are not free. At the scale of a large engineering organization, the token spend behind these agents can run into the millions of dollars a year, so a company that misjudges adoption, retention, or impact can end up with an expensive rollout that never moves the needle on engineering output. Most prior research in this space has either relied on surveys and interviews (which capture attitudes but not actual usage) or inferred AI use indirectly from public GitHub activity (which misses everything happening inside a company's private repositories). This paper's authors argue that enterprises considering or managing a large-scale agent rollout need direct, usage-level evidence, not proxies.

## What makes the system agentic

Claude Code and GitHub Copilot CLI are command-line tools that go well beyond autocomplete or single-turn chat: an engineer gives them a goal in natural language, and the agent plans a sequence of steps, reads and edits files, runs shell commands and tests, and iterates based on the results — all with a persistent view of the local codebase as its "environment." That combination of a goal, multi-step planning, and autonomous tool/command execution inside a real development environment is what makes these systems agentic, as opposed to a simple code-completion assistant that only ever proposes the next few lines of text.

## How humans and the AI agent collaborate

The collaboration here is the everyday one that plays out whenever a developer opens a terminal and decides to delegate part of their coding task to an agent instead of doing it by hand: the engineer decides when to invoke the tool, what to ask it to do, and — later — whether to keep using it at all. The paper does not study a single structured interaction protocol (like an approval gate or a clarification dialogue); instead it studies the aggregate pattern of thousands of individual delegation decisions made by real engineers over four months, and how those decisions spread through the organization and translated into measurable output.

## What role the human plays

The human is the **engineer deciding whether and how much to delegate**: choosing to try the agent in the first place (often after seeing a colleague use it), choosing whether to keep using it in the following weeks, and continuing to be the one who opens pull requests and gets them merged, with the agent as a tool woven into that ordinary engineering workflow.

## What role the AI agent plays

The agent is the **coding assistant Copilot CLI or Claude Code is invoked to run tasks on the engineer's behalf** inside the terminal — carrying out coding, editing, and command-execution work that the engineer would otherwise have done manually or not attempted at all.

## How control, initiative, and decisions are shared

This is a case of **human-initiated, on-demand delegation**: the engineer holds all the initiative about when to bring the agent into a task and when not to, and the agent has no autonomy over whether it gets used — it only acts once summoned. Where the paper's "shared control" angle really lies is at the organizational level: adoption and continued use are shaped less by top-down mandate and more by peer influence, meaning the effective spread of agent use through the company is a social, human-driven process, not something the tool or its vendor controls directly.

## The paper's main idea

**Claim by the authors:** command-line AI coding agents produce a measurable, sustained lift in engineering output for the people who adopt and keep using them, and — because that adoption spreads primarily through visible peer usage rather than demographics or top-down push — peer visibility should be a central lever in how organizations plan an enterprise rollout.

## How the approach works

The authors instrumented Microsoft's own environment to observe, at the level of individual engineers, who first tried Claude Code or Copilot CLI, when they tried it, whether they kept using it, and how their pull-request activity changed afterward — comparing this against engineers who had not (yet) adopted the tools. This is described as the first field study of its kind to use developer-level telemetry (rather than surveys or public-repository mining) to jointly analyze adoption and productivity impact of agentic command-line tools inside a real company.

## Human study or evaluation design

**Demonstrated in the paper:** an observational field study using organizational telemetry, not a lab experiment or a randomized controlled trial. The authors tracked real usage events (first use, subsequent activity) and merged pull-request counts for a large population of engineers, and modeled how adoption spread through engineers' social/reporting networks and what distinguished engineers who kept using the tools from those who tried it once and stopped.

## Participants and study setting

**Demonstrated in the paper:** tens of thousands of Microsoft software engineers, observed over a roughly four-month window (reported as spanning January–April 2026) during the company's early rollout of Claude Code and GitHub Copilot CLI. This is a single-organization, real-workplace field setting — not a lab, and not a subset of volunteers recruited for a study, but the population of engineers who had access to the tools during the rollout.

## Experiments or benchmarks

There is no public benchmark; the "experiment" is the natural rollout itself, analyzed retrospectively. The paper defines a specific operational measure of retention — an adopter counts as "retained" if they had recorded activity with the tool on at least 5 of the 14 days starting from their first use — and uses merged pull requests as its proxy for engineering output.

## Main results

**Demonstrated in the paper (per available descriptions):**
- **Adoption spreads socially:** the strongest predictor of whether an engineer tries Copilot CLI in a given week is whether their peers — especially their broader skip-level group — had already tried it, more so than any demographic factor examined.
- **Retention tracks coding activity, not demographics:** engineers who kept using the tools past the first two weeks were distinguished more by how actively they were already coding than by role, tenure, or other demographic variables.
- **A sustained output lift:** adopters merged roughly 24% more pull requests than the study estimates they would have without the tools, and this lift persisted across the full four-month observation window rather than fading out.

## Effects on human performance, trust, workload, safety, or decision quality

This is a **demonstrated result**, not a projection, on the specific dimension the paper measures: engineers who adopted and kept using the agentic CLI tools shipped more merged pull requests than comparable non-adopters, and that gap held up over four months rather than being a short-lived novelty effect. The paper is explicit that it does not measure deeper dimensions like code quality, review burden, trust, or workload directly — its productivity claim rests specifically on pull-request throughput, which the authors themselves flag as an imperfect proxy (a merged PR is not the same thing as the value it delivers).

## What is genuinely new

- **Enterprise-scale, developer-level telemetry** on real agentic-tool adoption and impact, as opposed to the survey- and interview-based methods, or public-GitHub-mining methods, that most prior developer-AI-adoption research has relied on.
- A **joint analysis of adoption *and* impact** in the same population — most existing studies look at one or the other, not both together with the same instrumentation.
- **Peer-network effects as the dominant adoption driver**, identified through actual usage-spread data rather than self-reported influence.

## Limitations and open questions

- **Output proxy is coarse:** the paper uses merged pull requests as its measure of impact, which does not capture code quality, review overhead created for reviewers, or whether the work was actually valuable — a limitation the authors acknowledge directly.
- **Single organization:** the findings come from one company's internal rollout (Microsoft) of two specific tools (Claude Code and Copilot CLI); how well the social-adoption and retention patterns generalize to other companies, engineering cultures, or tools is not established.
- **Observational, not causal by design:** without random assignment to "gets the tool" versus "doesn't," the reported 24% lift is an estimated association from an adoption/impact model rather than a randomized-experiment result — reported sources available in this session did not fully specify the paper's causal-identification strategy, so this should be treated as the authors' best estimate rather than a guaranteed causal effect.
- **No direct measurement of collaboration quality:** the paper studies whether and how much engineers use the agent, not how well individual human-agent sessions went, how engineers reviewed or corrected agent output, or how trust or reliance calibration evolved at the level of individual interactions.
- **Peer-review status:** as of this writing, this appears to be an arXiv preprint; a peer-reviewed publication venue was not confirmed from the sources available in this session.

## Practical implications

For any organization planning a large-scale rollout of agentic coding tools, this paper's most actionable finding is about *how* adoption actually spreads: not through mandates or demographics, but through engineers seeing their own peers using the tool. That suggests rollout strategies emphasizing visible internal champions and peer-to-peer sharing may matter more than top-down training pushes. It also offers a concrete, if imperfect, answer to the ROI question every organization asks before spending heavily on agent token budgets: in this one large deployment, sustained adopters shipped meaningfully more merged work, and that lift did not evaporate after the initial excitement wore off.

## Why you should care

Most of the human–AI collaboration literature on coding agents comes from controlled lab studies with a few dozen participants, or retrospective mining of public open-source repositories. This paper instead looks at what actually happens when tens of thousands of real engineers at a real company are given access to a real agentic tool and left to decide, on their own, whether to keep using it — which is a distinctly different and complementary kind of evidence about how humans actually choose to delegate work to AI agents, and what happens to their output when they do. It won't tell you whether any individual human-agent coding session went well, but it tells you something that matters just as much for anyone deploying these tools at scale: whether people keep coming back, and why.
