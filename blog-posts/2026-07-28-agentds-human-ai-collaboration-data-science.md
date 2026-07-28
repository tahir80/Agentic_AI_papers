# Can AI Agents Replace Data Scientists? A Real Competition Says: Not Alone

**Authors:** An Luo, Jin Du, Xun Xian, Robert Specht, Fangqiao Tian, Ganghua Wang, Xuan Bi, Charles Fleming, Ashish Kundu, Jayanth Srinivasa, Mingyi Hong, Rui Zhang, Tianxi Li, Galin Jones, Jie Ding (University of Minnesota; Cisco Research)
**Publication date:** 2026-03 (exact day not available — arXiv id 2603.19005, competition ran 2025-10-18 to 2025-10-27)
**Venue:** arXiv technical report (peer-review status not confirmed)
**Paper link:** https://arxiv.org/abs/2603.19005
**Code / data link:** Challenge datasets on Hugging Face, e.g. https://huggingface.co/datasets/lainmn/AgentDS and https://huggingface.co/datasets/lainmn/AgentDS-Manufacturing (no single unified code repository confirmed)
**Project page:** https://agentds.org/
**Date added:** 2026-07-28

> **A note on sourcing:** arXiv (and the mirror hosts tried as fallbacks) returned network-policy blocks from this research session's proxy, so this summary is built from cross-checked search-engine excerpts of the paper's abstract, methodology, and results — plus a third-party analysis blog (Pebblous) that independently summarized the competition's leaderboard — rather than a direct read of the full PDF. Facts corroborated across multiple independent searches are presented as such; anything that couldn't be verified this way is marked "not available." The paper itself is an openly licensed arXiv preprint, so it is publicly readable even though this session could not fetch it directly.

---

## The problem the paper addresses

Every few months a new AI coding agent claims it can "do data science" end to end: load the data, engineer features, train a model, write up the results. But most of the benchmarks used to back up that claim let the agent work completely alone, on tasks with clean, well-specified answers. AgentDS asks a blunter, more practical question: on real, messy, domain-specific business problems — the kind with multimodal data, industry jargon, and validation metrics that don't always track real-world performance — how does an AI agent working *alone* actually compare to a team of humans who are *allowed to use AI however they want*? And in that second case, what does the "however they want" actually look like in practice?

## Why this problem matters

Organizations aren't deciding whether to use AI in data science — they're already doing it. The real decision is *how much* control to hand over: do you let an agent run the whole pipeline unsupervised, or do you keep a human steering while the agent executes? Getting this wrong has real costs — a fully autonomous pipeline that quietly optimizes the wrong metric, or a human team that's too cautious to capture any of the speed benefits AI offers. AgentDS is one of the first benchmarks to measure this trade-off directly, with real people making real delegation decisions under time pressure, rather than assuming an answer.

## What makes the system agentic

The AI side of AgentDS isn't a single-shot chatbot — participants and baseline systems both used LLM-based agents capable of multi-turn tool calling, autonomous code execution, and (in some team approaches) multi-agent orchestration, working through real data-loading, feature-engineering, modeling, and evaluation pipelines on genuine multimodal business datasets (images, text, PDFs). The AI-only baselines evaluated included general-purpose coding agents (e.g., GPT-4o– and Claude Code–based pipelines) running the full challenge autonomously — planning, writing, executing, and iterating on code without a human in the loop.

## How humans and the AI agent collaborate

There wasn't one fixed collaboration protocol — that's actually the point. Teams of up to four people were free to use any AI tools and agents they wanted, however they wanted, across a 10-day, 17-challenge, 6-industry competition. The paper's central contribution is documenting what teams actually chose to do with that freedom, and how that choice related to how well they scored.

## What role the human plays

Humans supplied the parts that AI agents in this competition struggled with most: framing the problem before writing any code, sanity-checking whether a result made domain sense, and deciding when to abandon an approach that wasn't working. Several teams reported starting with a fully autonomous agent pipeline, getting disappointing or expensive results (heavy prompt engineering, high API costs, off-target outputs), and then deliberately pulling back to a human-guided workflow where they set the direction and the agent executed it.

## What role the AI agent plays

Once humans had framed the problem, agents did the heavy execution: writing and running code, exploring feature combinations, generating boilerplate, and iterating quickly through variations that would be slow for a person to type out by hand. In the AI-only baseline condition, agents were also asked to do all of this — including the framing and pivoting — entirely on their own.

## How control, initiative, and decisions are shared

**Authors' claim / demonstrated pattern:** control shifted dynamically and adaptively rather than being fixed in advance. Teams that tried ceding full initiative to an autonomous multi-agent pipeline reported the approach becoming hard to sustain (cost, drift, opaque failures) and several switched to a model where the human held strategic initiative — choosing what to try next, what to compare, how to interpret a result — while the agent held execution initiative, actually writing and running the code to test that decision. This is adaptive delegation observed in the wild, not designed into a fixed interface.

## The paper's main idea

**Claim by the authors:** the strongest data-science results in this competition came not from AI alone or from humans working without AI, but from human-AI collaboration where humans retained strategic control (problem framing, domain judgment, deciding when to pivot) and AI agents supplied computational throughput (rapid coding, exploration, boilerplate) — and that current fully autonomous agents still fall short of top human-AI teams on realistic, domain-specific tasks.

## How the approach works

AgentDS is a benchmark plus open competition: 17 challenges spanning six industries (commerce, food production, healthcare, insurance, manufacturing, retail banking), each built from real-world, often multimodal business data with the kind of distribution-shift and validation-metric quirks that make textbook benchmarks easier than real work. Competitors — 29 teams, 80 people total, drawn from 400+ registrations — tackled these challenges over 10 days using whatever AI tools they chose, while the authors separately ran AI-only agent baselines (including GPT-4o– and Claude Code–based pipelines) on the same challenges for direct comparison.

## Human study or evaluation design

**Demonstrated in the paper:** this is a real, open competition rather than a lab experiment with random assignment — participants self-selected into teams and challenges, and the "manipulation" (how much to delegate to AI) was each team's own choice rather than something the researchers controlled. The authors compare outcomes (leaderboard scores) across teams and against AI-only baselines, and separately report qualitative patterns in *how* higher-performing teams used their AI tools, drawn from participant reports and observed workflows.

## Participants and study setting

**Demonstrated in the paper:** 80 real participants organized into 29 teams (up to four people each), competing in a live, open, real-world online competition from October 18–27, 2025. This was not a simulated or persona-based population — these were genuine competition entrants working on real submitted solutions, evaluated on a public leaderboard.

## Experiments or benchmarks

The 17 challenges across 6 industries form the benchmark itself; AI-only baseline agents (including GPT-4o- and Claude Code-based pipelines) were run on identical challenges and ranked on the same leaderboard as the human teams, allowing direct, apples-to-apples comparison between AI-only and human-AI-team performance.

## Main results

**Demonstrated in the paper (cross-confirmed via a third-party leaderboard summary):**
- AI-only baselines performed at or below the median of human(-AI) team submissions on the overall leaderboard; the strongest solutions overall came from human-AI collaboration, not from AI or humans alone.
- On the reported leaderboard, a GPT-4o–based baseline placed 17th of 29 (below median), while a Claude Code–based baseline placed 10th (top third) — AI-only agents were competitive with mid-tier teams but did not lead the field.
- In a healthcare-domain challenge, human-guided iteration measurably improved on an initial agent-produced solution: cross-validated F1 rose from 0.846 to 0.896 after human-directed feature expansion and ensembling; MAE improved from $467 to $459 with human-guided feature enrichment; and a third healthcare challenge improved from F1 0.49 to 0.73 across four rounds of human-directed iteration.
- Teams that initially delegated fully to autonomous multi-agent pipelines often abandoned that approach mid-competition in favor of human-guided, agent-executed workflows, citing cost, unpredictability, and the need for heavy prompt engineering to keep fully autonomous agents on track.

## Effects on human performance, trust, workload, safety, or decision quality

**Authors' framing, based on observed competition behavior:** teams that treated AI as an execution partner — handling data loading, exploratory analysis, and boilerplate — while humans retained control over feature engineering, model selection, and result interpretation, achieved better outcomes than teams that either avoided AI or ceded full control to it. **My interpretation:** this is best read as evidence about effective task allocation and appropriate reliance under real competitive pressure, not a controlled trust/workload measurement — the paper does not report validated trust, workload, or satisfaction instruments (e.g., no NASA-TLX or Likert trust scales are confirmed from available sources), so claims about subjective experience should be treated as descriptive rather than psychometrically measured.

## What is genuinely new

- One of the first benchmarks to put real people, using real AI agents of their own choosing, head-to-head against AI-only agent baselines on identical, realistic, multimodal, domain-specific tasks — rather than comparing agents only to each other or to static human baselines from unrelated prior work.
- Direct leaderboard evidence that today's general-purpose coding/data-science agents, working alone, do not yet beat the best human-AI teams on this kind of task, while still being competitive with median performance.
- Documented, in-the-wild examples of teams *adaptively re-negotiating* how much to delegate to AI mid-competition, based on observed results rather than a fixed study design — a naturalistic window into calibrated reliance.
- Concrete before/after quantitative traces (e.g., the healthcare-challenge F1/MAE improvements) showing exactly where human-directed iteration added measurable value on top of agent-produced starting points.

## Limitations and open questions

- Participants freely chose their own AI tools and workflows rather than using one controlled, researcher-designed collaboration interface, so "the collaboration mechanism" varied considerably from team to team — this is realistic but makes it hard to isolate which specific interaction pattern drove better outcomes.
- It was a single, time-boxed (10-day) competition rather than a longitudinal study, so it can't speak to how collaboration patterns might evolve with sustained, everyday use.
- No validated psychometric measures of trust, workload, or user experience are confirmed from available sources — the collaboration benefits are inferred from leaderboard outcomes and participant reports, not measured directly.
- Some finer-grained statistical details (e.g., significance tests, full per-challenge breakdowns) could not be independently confirmed in this session because the full PDF was not fetchable; readers who need precise figures should consult the paper directly.

## Practical implications

For organizations weighing how much autonomy to give data-science agents, this paper offers real, competitive-pressure evidence rather than vendor claims: a "human sets strategy, agent executes" pattern currently outperforms both AI-only pipelines and unassisted human work on realistic, domain-specific tasks — and teams that tried handing over full control to autonomous agents frequently found it worth walking back. That's a concrete, actionable data point for how to design human-AI data-science workflows today, rather than waiting for fully autonomous agents to close the gap.

## Why you should care

If you've wondered whether AI agents are about to make human data scientists obsolete, this is one of the more grounded answers currently available: real people, real AI agents, real leaderboard, and the AI-only agents did not win. The paper's most useful contribution for anyone thinking about human-AI collaboration isn't just "humans still add value" — it's the specific, observed *shape* of that value (problem framing, sanity-checking, knowing when to pivot) and the fact that competitive teams discovered and adopted that division of labor themselves, under real pressure to win, rather than having it imposed by a study design.
