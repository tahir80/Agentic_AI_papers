# Human–AI Collaboration at Scale: Task Criticality, Agency, and Friction Across 250,000 Conversations

**Authors:** Yijia Shao, Humishka Zope, Yucheng Jiang, Jiaxin Pei, David Nguyen, Erik Brynjolfsson, Diyi Yang (Stanford Social and Language Technologies Lab / Digital Economy Lab), conducted through Anthropic's independent-research data-access program
**Publication date:** 2026-08-26 (Anthropic's public announcement of the independent-research findings); hosted as a preprint on alphaXiv
**Venue:** Independent research report / preprint — one of three studies released under Anthropic's "Enabling independent research on how people use Claude" program; not yet confirmed as peer-reviewed
**Paper link:** https://www.alphaxiv.org/abs/2608.human-ai-collaboration-at-scale (a stable, standard arXiv identifier could not be confirmed this session — see sourcing note below)
**Official announcement / project page:** https://www.anthropic.com/research/enabling-independent-research
**Code link:** Not available
**Date added:** 2026-08-30

> **A note on sourcing:** This session's network access blocks direct fetches to arxiv.org, alphaXiv, huggingface.co, semanticscholar.org, and even generic sites like Wikipedia (an organization-level egress policy, confirmed via repeated `EGRESS_BLOCKED` errors on the fetch tool and a blocked proxy tunnel on direct `curl` attempts). Full-text reading of *any* candidate paper was therefore not possible this session. This summary is built entirely from web-search-grounded excerpts — the paper's title, author list, and reported findings as quoted or paraphrased consistently across multiple independent search results, plus Anthropic's own official research-blog description of the same study — rather than a direct read of the paper's PDF or HTML body. Anything not corroborated this way is marked "not available," and interpretive statements are labeled as such. Readers who want to verify specific numbers should consult the paper directly.

---

## The problem the paper addresses

Millions of people now turn to conversational AI systems like Claude for real work, but almost everything we think we know about *how* that collaboration actually unfolds comes from small lab studies, surveys, or self-report — not from looking at what people actually do in real conversations. This paper asks a simple but under-answered question at scale: when a real person sits down with an AI agent to get something done, who is actually in charge, how much of the real stakes do they hand over, and what happens when the collaboration hits a snag?

## Why this problem matters

Design decisions about AI agents — how much autonomy to give them, when to insert human checkpoints, how to build in error recovery — are being made largely on assumption rather than evidence about real usage. If AI companies, regulators, and researchers are wrong about how much control people actually retain, or how often collaboration breaks down and how people cope when it does, oversight mechanisms and product designs can end up solving the wrong problem: over-engineering safeguards for scenarios that rarely happen, or leaving real high-stakes delegation with too little support.

## What makes the system agentic

The subject of the study is not a single custom-built agent but real-world use of Claude across two products: Claude.ai (general conversational assistant use, including tool-using capabilities like search and code execution) and Claude Code (an agentic coding assistant that plans, edits files, and executes commands across multi-step programming tasks). Both involve the LLM going beyond single-turn text generation — taking multi-step actions, using tools, and completing extended tasks — which is what makes the underlying systems "agentic" in the sense this research project cares about, even though the paper's own contribution is an analysis of usage patterns rather than a new agent architecture.

## How humans and the AI agent collaborate

Rather than observing collaboration in a lab, the researchers analyzed a large, privacy-preserving sample of real conversations — about 250,000 Claude.ai and Claude Code conversations from April–May 2026 — to characterize collaboration as it actually happens "in the wild." The analysis centers on three dimensions: **task criticality** (is the work consequential — does it affect other people or would it be hard to undo — or low-stakes?), **agency** (how much of the task does the human keep versus hand to the AI, using a human-agency framework the same research group has developed in prior work), and **friction** (points where the collaboration stumbles — misunderstanding, incorrect output, a need for correction — and what people do about it).

## What role the human plays

**Claim by the authors, per available summaries:** across the sampled conversations, people generally did not act as passive recipients of AI output. Roughly three-quarters of conversations had the human setting the direction of the task while Claude assisted, and people typically adapted or built on Claude's output rather than using it verbatim. When something went wrong, people actively worked to recover — asking Claude to clarify its reasoning ("disambiguation") or pointing out and fixing a specific error ("repair") rather than simply abandoning the task or blindly accepting a flawed result.

## What role the AI agent plays

Claude operates as the delegated-to collaborator: producing drafts, analysis, code, or other output in response to the task the human brings, and — per the paper's framing — often handling a substantial share of the actual task execution, including on conversations the researchers classified as "consequential" (affecting other people, or hard to undo). In Claude Code specifically, this extends to concrete multi-step agentic action: writing and modifying code, running commands, and iterating toward a working result.

## How control, initiative, and decisions are shared

The paper positions collaboration on a spectrum rather than a fixed split, using a five-level "Human Agency Scale" (from the AI handling a task essentially on its own, to the human's judgment being indispensable throughout) as a shared vocabulary for how much of a given task is retained by the human versus delegated to the AI. **A key reported finding is that this split is not simply correlated with how much is at stake:** contrary to a natural assumption that people would keep high-stakes work for themselves and only delegate trivial tasks, the study reports that **over half of the sampled conversations involved consequential work being delegated to Claude to some degree** — while the human, in most cases, still retained overall direction of the task.

## The paper's main idea

**Claim by the authors:** understanding human–AI collaboration requires looking at real, large-scale usage rather than lab proxies, and doing so reveals a more nuanced picture than "people trust AI with unimportant tasks and keep the important stuff to themselves." Task criticality, how much agency people retain, and how they handle friction are three separate, measurable dimensions of collaboration — and real users are, on the whole, actively engaged (setting direction, adapting output, recovering from errors) even on work that matters.

## How the approach works

The study used Anthropic's privacy-preserving analysis tooling (built for exactly this kind of aggregate, non-identifying analysis of conversation data) to classify a sample of roughly 250,000 real Claude.ai and Claude Code conversations along the three dimensions above — task criticality, agency level, and presence/type of friction and recovery. This is a large-scale observational analysis of naturally occurring behavior, not a lab experiment with randomly assigned conditions: the researchers designed their own classification scheme and research questions independently, with Anthropic's contractual review limited to privacy, policy-violation risk, and factual accuracy of the resulting findings (per Anthropic's own description of the program), not the substance of the conclusions.

## Human study or evaluation design

**Demonstrated in the paper (per available summaries):** this is not a recruited, controlled human-subjects experiment with an intervention and control group. It is a large-scale, privacy-preserving observational analysis of real, naturally occurring conversations between real users and Claude, sampled from actual product usage rather than a lab task assigned by researchers.

## Participants and study setting

**Real users, real setting, but not a traditional "study population":** the "participants" are the real people who used Claude.ai or Claude Code during the April–May 2026 sampling window, whose conversations were included (in privacy-preserving, aggregate form) in the analyzed sample of roughly 250,000 conversations. No demographic breakdown of these users (age, profession, expertise level, geography) was available in the sources used for this summary. This is naturalistic field data, not a lab or survey setting — its strength is realism at scale; its limitation is the corresponding lack of controlled comparison conditions and detailed participant-level detail.

## Experiments or benchmarks

There is no benchmark or leaderboard in the usual sense. The "experiment" is the classification and statistical analysis of the ~250,000-conversation sample along the criticality/agency/friction framework. Anthropic has also released an accompanying dataset resource ("Anthropic/enabling-independent-research," hosted on Hugging Face) connected to the broader independent-research program this study is part of, though this session could not verify what, specifically, that resource contains relative to this paper.

## Main results

**Claims reported by the authors, per available summaries (not independently re-verified against the primary source in this session):**
- Over half of the sampled conversations involved **consequential** tasks — work affecting other people or hard to undo — being delegated to Claude, contradicting an assumption that people mainly hand over low-stakes work.
- Roughly **three-quarters** of conversations had the human set the direction of the task while Claude assisted, rather than the human handing off both direction and execution.
- People typically **adapted** Claude's output rather than using it verbatim.
- **Friction** (a point where the collaboration didn't go smoothly) arose in roughly **half** of conversations, but was often "productive" — people frequently recovered from it using active strategies like asking Claude to clarify its reasoning ("disambiguation") or directly correcting a specific error ("repair").

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper, per available summaries:** the study documents behavioral patterns — how much direction people retain, how often they adapt versus accept output, how often and how they recover from friction — as a proxy for engaged, non-passive collaboration. **Not demonstrated (based on available excerpts):** the study does not appear to report standard psychometric outcomes such as self-reported trust ratings, cognitive workload measures, task-completion accuracy, or downstream safety incidents. **Our interpretation:** the reported patterns (majority retaining direction, high rates of adapting rather than copying output, active recovery from friction) are consistent with — but not direct proof of — healthy, calibrated reliance; a classification of behavior is not the same as a validated measurement of trust or workload, and the paper's framing as "productive" friction is the authors' interpretation of what the data shows, not an independently validated outcome measure.

## What is genuinely new

- **Scale and naturalism:** most human–AI collaboration research relies on lab studies with dozens of participants; this analyzes roughly a quarter-million real conversations, capturing collaboration as it actually occurs rather than as it's staged for a study.
- **A three-part framework (criticality, agency, friction)** for describing collaboration quality that goes beyond simple usage-frequency statistics.
- **A challenge to a common assumption** — that people delegate only low-stakes work to AI — with real-usage evidence that a majority of consequential-task conversations still involve substantial delegation, while direction-setting largely stays with the human.
- **A demonstration of what external, privacy-preserving access to real product usage data for independent researchers can produce**, as part of a broader access program Anthropic opened to outside labs (Stanford SALT Lab, Oxford's Human Information Processing Lab, and METR) with limited review rights over the findings.

## Limitations and open questions

- This is an **observational, not experimental** study: there is no manipulated condition or control group, so the findings describe correlational patterns in real usage, not causal effects of specific design choices.
- The classification of "consequential," "agency level," and "friction" relies on **automated/algorithmic analysis of conversation content**, which — like any large-scale text classification — is subject to some error rate; the precision of these classifications was not available in the sources used for this summary.
- The sample is restricted to **Claude.ai and Claude Code users specifically**, from a two-month window (April–May 2026); how well the patterns generalize to other AI assistants, other time periods, or non-English-speaking or non-Western user populations is unclear.
- No demographic or professional breakdown of the underlying users was available in the sources reviewed.
- **This session's own limitation:** because direct access to the paper's full text was blocked, the specific numbers and quotes above are drawn from consistent third-party and Anthropic-authored summaries rather than the primary source directly — readers should treat exact figures as approximate pending direct verification against the paper itself.

## Practical implications

For teams building or deploying agentic AI systems, the findings (as reported) suggest that people using AI for consequential work don't necessarily need to be nudged toward retaining control — many already do, by keeping direction-setting for themselves and adapting rather than passively accepting output. Instead, the more actionable design lever may be **friction recovery**: since friction is common but often resolved productively through clarification and correction, interfaces that make disambiguation and targeted correction easy (rather than assuming friction should be eliminated) may better match how people actually work with AI.

## Why you should care

This paper matters less for any single number and more for what it represents: a rare, real-world, privacy-preserving look at how millions of actual interactions between humans and an AI agent play out, rather than another lab study of a few dozen volunteers. If its headline claims hold up under further scrutiny, it pushes back on a tidy but possibly wrong story — that people only trust AI with the unimportant stuff — and points instead toward a more active, engaged picture of human–AI collaboration at scale, with implications for how both companies and researchers should think about where to invest in oversight and recovery tools.
