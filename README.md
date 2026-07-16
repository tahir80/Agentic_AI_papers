# Agentic_AI_papers

A running log of notable papers on agentic AI — agents, tool use, multi-agent systems, evaluation and benchmarks, planning and reasoning, memory, safety, reliability, and human–agent collaboration. Updated periodically with one new paper per run, newest first.

## Papers

| Date Added | Title | Authors | Published | Venue | Links |
|---|---|---|---|---|---|
| 2026-07-16 | [AgentTether: Graph-Guided Diagnosis and Runtime Intervention for Reliable LLM Agent Operation](https://arxiv.org/abs/2607.06273) | Chenyu Zhao, Shenglin Zhang, Wenwei Gu, Yongqian Sun, Dan Pei, Chetan Bansal, Saravan Rajmohan, Minghua Ma | 2026-07-07 (arXiv preprint) | Not available | [Paper](https://arxiv.org/abs/2607.06273) · [PDF](https://arxiv.org/pdf/2607.06273) · [Code (anonymous)](https://anonymous.4open.science/r/AgentTether-9416/) · Project page: Not available · Benchmark: [tau-bench family](https://github.com/sierra-research/tau2-bench) |

## Summaries

### AgentTether: Graph-Guided Diagnosis and Runtime Intervention for Reliable LLM Agent Operation

Production LLM agents fail in ways that are hard to fix: a bad decision early in a long, multi-step, tool-using task can silently poison everything that follows, and by the time the agent reports failure the root cause is buried in dozens of tool calls. Today's fixes are blunt instruments — blind retries add no diagnosis, outcome-only feedback tells you a run failed but not why, and self-reflection often lacks grounded evidence to stop the same mistake from recurring.

AgentTether, from researchers at Nankai University and Microsoft Research, proposes a run-time repair layer that sits outside the agent and its environment, so it works without retraining or redesigning either. It decomposes each agent run into "Transition Units" — observation–belief–action–feedback cycles — and links them into a dependency-aware "Critical Transition Graph." By combining an offline model of normal agent behavior with a run-local graph detector, it pinpoints the specific subtrajectory that caused a failure, then turns that diagnosis into targeted guidance stored in a cross-iteration "Repair Memory," optionally intervening live during re-execution to keep the correction in force.

Tested on 261 tasks drawn from the tau-bench family across three domains, AgentTether repaired 59% of Qwen3.7-max's initial failures and 65% of GPT-5.4's on the hardest Banking domain, while cutting the extra turns and tokens that repair normally costs. For anyone building production agents, it's a concrete step toward turning "the agent failed" into "the agent failed here, and here's why" — a diagnosis-first alternative to retry-and-hope reliability engineering.

*Note: the code repository above is an anonymized double-blind review link; venue/acceptance status was not independently verifiable at the time of writing.*
