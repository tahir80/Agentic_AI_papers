# AgentPanel: Toward a New Paradigm for Human–AI Collaboration in Exploring Scientific Questions

**Authors:** Zhiyao Cui, Qianyi Wang, Haoyang Yan, Yiqun Zhang, Siyue Ren, Hangfan Zhang, Zelin Tan, Hao Li, Chunjiang Mu, Dexian Cai, Shao Zhang, Chen Zhang, Meng Li, Jianan Chai, Yuting Fan, Zichao Ye, Xiaolei Yang, Xinyao Lu, Yuyang Yu, Wenjie Lou, Xiaosong Wang, Fenghua Ling, Shiyang Feng, Mao Su, Qiaosheng Zhang, Bo Zhang, Yang Chen, Lei Bai, Shuyue Hu (Shanghai Artificial Intelligence Laboratory)
**Publication date:** 2026-08-04 (arXiv id 2608.03283)
**Venue:** arXiv preprint (cs.AI); peer-review/acceptance status not confirmed from available sources
**Paper link:** https://arxiv.org/abs/2608.03283 (PDF: https://arxiv.org/pdf/2608.03283)
**Code link:** https://github.com/InternScience/AgentPanel
**Project page:** Not available separately (the GitHub repository doubles as the live platform's home)
**Date added:** 2026-09-11

> **A note on sourcing:** arXiv and its common mirrors were not directly reachable from this research session's network (outbound access to arxiv.org, huggingface.co, and similar hosts was blocked by the environment's egress policy), so this summary is built from the paper's publicly indexed abstract and HTML text, and the project's GitHub README, retrieved via web search rather than a direct, complete read of the typeset PDF. Facts that appear consistently across these sources (authors, system design, the human study's participant count and questionnaire results) are reported as such; anything we could not independently verify — exact offline-benchmark numbers, full ablation results, venue/acceptance status, and some implementation details — is marked "not available" or "not confirmed" rather than invented.

---

## The problem the paper addresses

When a researcher wants to sanity-check an idea or explore an open scientific question, they usually do one of two things: grab a colleague for a quick hallway conversation, or open a chat window with a single AI model. The paper argues both options are narrow. A hallway chat gives you one or two perspectives, shaped by whoever happens to be free. A single-model chatbot gives you one "voice" — even if you ask it to argue with itself, it tends to converge quickly rather than genuinely explore disagreement. Either way, researchers exploring genuinely open, cross-disciplinary questions get a narrower set of angles than they need before committing time to a direction.

## Why this problem matters

Early-stage idea exploration is where a lot of research value (and a lot of wasted effort) gets decided. A question examined from only one or two angles can miss a fatal methodological flaw, an adjacent field that already solved a similar problem, or a more promising reframing entirely. As LLMs get folded into research workflows, the authors' bet is that the real opportunity isn't replacing the researcher's judgment with an AI's answer, but giving the researcher access to a wider, more structured field of perspectives — human and AI — before they decide where to dig in.

## What makes the system agentic

AgentPanel is not a single chatbot; it is a standing, multi-agent platform. According to the paper and the project's own documentation, the system connects a large roster (the GitHub README describes 250+ agent instances built on 10+ underlying models, including Claude, Gemini, Grok, GLM, and DeepSeek variants) that operate autonomously inside a shared forum. Each agent is assigned a distinct role via a structured prompt scaffold — e.g., attending to conceptual boundaries, reproducibility, or deployability — and decides for itself when to jump into a thread (immediately, after reading others' answers, or late to synthesize), what form its answer takes, when to upvote or reply to other agents, and whether to revise its own earlier position as the discussion evolves. A scheduling layer manages agent status, retrieves context, and applies rule-based recommendations and policy filtering, while the agents themselves reach the platform's shared state only through a common structured tool interface rather than direct access — the hallmarks of an autonomous, multi-step, tool-mediated system rather than a single text-in/text-out model. The paper evaluates this system as an agentic platform (comparing it against a centralized multi-agent debate baseline), not simply as a language model.

## How humans and the AI agent collaborate

Humans and agents share the same "forum objects" — questions, answers, upvotes, threads — but reach them through different interfaces: people use a web front end, agents use structured tools. A researcher posts a real scientific question, and the platform's roster of role-differentiated agents begins an asynchronous, forum-style discussion around it: they clarify the question's scope, stake out positions, challenge each other's reasoning, and — in some cases — revise their own answers based on the exchange. The human isn't limited to reading a finished report; they can browse the unfolding discussion, upvote or organize the answers they find promising, and jump in with follow-up questions or clarifications addressed to specific agents.

## What role the human plays

The human is the one who frames the question, decides which lines of discussion are worth pursuing, and steers the exploration by upvoting, replying, and asking follow-ups. They also decide when to stop: the platform can optionally generate a post-hoc summary report of the discussion once the researcher feels the exploration has run its course. In short, the human supplies the scientific judgment about what matters and where to dig deeper, while treating the agent panel as a source of breadth rather than a source of final answers.

## What role the AI agent plays

The agents supply breadth and structured disagreement. Rather than one model answering a question multiple times, AgentPanel's role taxonomy is designed to make different agents genuinely attend to different things — one might probe conceptual boundaries, another might stress-test reproducibility, another might focus on real-world deployability — and to interact with each other's answers (rebutting, grading evidence, conditionally revising) rather than just each producing an independent answer in isolation. The intended discussion arc the authors describe moves from concept clarification, to position-forming, to rebuttal and evaluation, to conditional revision, to a staged synthesis.

## How control, initiative, and decisions are shared

This is a mixed-initiative, asynchronous design. The human initiates by posting a question but does not need to drive every step — the agents autonomously carry the discussion forward on their own schedule and interaction rules. At the same time, the human retains ongoing initiative: they can intervene at any point with a follow-up question, redirect specific agents, or select which threads and answers to build on, and they make the final call on which ideas are worth pursuing. Neither side runs the whole process alone; the platform is explicitly built as shared infrastructure with humans and agents making different kinds of decisions on the same shared objects.

## The paper's main idea

**Claim by the authors:** single-model chat interactions and small human-only discussions under-explore the space of possible angles on a scientific question, and a *structured*, *role-differentiated*, multi-agent forum — rather than an unstructured multi-agent debate — produces both better ideas and a better experience for the human researcher steering the exploration. The paper's contribution is the concrete design of that structured forum (the role taxonomy, the answer-strategy/style/interaction-rule scaffold, and the shared tool-mediated environment) plus an evaluation of whether it delivers on that claim.

## How the approach works

Every agent's behavior is generated from a shared prompt scaffold with several configurable parameters: what the role primarily attends to, when it enters a discussion relative to other agents (first-response, watchful, or slow-burn), the format of its answer (e.g., TL;DR, line-by-line rebuttal, evidence grading, issue decomposition), rules for when to upvote/comment/reply, and how it updates its own prior conclusions (edit-with-changelog, probability updates, conditional rewrites). A scheduling/orchestration layer sits between the shared forum state and the agents, managing whose turn it is, retrieving relevant context, and filtering by platform policy, so that the discussion follows the intended clarify → position → rebut → revise → synthesize arc instead of many agents talking past each other. Humans interact with the same underlying forum through an ordinary web interface — posting questions, browsing and organizing answers, replying to specific agents, and requesting an optional summary report.

## Human study or evaluation design

**Demonstrated in the paper (per available sources):** the authors report two complementary evaluations. First, **offline experiments** compared AgentPanel's output against a centralized multi-agent debate baseline on dimensions including idea quality, exploration breadth, interaction effectiveness, and candidate-selection efficiency (the paper reports AgentPanel outperforming this baseline; specific numeric results were not confirmed from the sources available to us). Second, and most relevant to human–AI collaboration, the authors ran a **live human study with real researchers**: 20 valid participants submitted their own genuine research questions to the deployed platform, reviewed the agent-generated answers, optionally interacted further with agents, and completed a post-study questionnaire using 7-point rating scales.

## Participants and study setting

Participants were researchers who brought their own real scientific questions to the live, deployed AgentPanel platform — not a synthetic task set and not simulated personas. Detailed demographic information, recruitment method, and session length were not available from the sources reachable in this session.

## Experiments or benchmarks

Beyond the human study, the paper reports offline experiments against a centralized multi-agent debate baseline, evaluated along idea quality, exploration breadth, interaction effectiveness, candidate-selection efficiency, and practical utility. We could not confirm the exact quantitative benchmark results from the sources available to us in this session, so we do not restate specific numbers for that comparison here.

## Main results

**Demonstrated in the paper (per available sources):** in the 20-participant human study, participants rated the system positively across multiple 7-point-scale dimensions — usefulness (6.05), exploration breadth and upvote-based navigation (6.00 each), follow-up replies (6.60, the highest-rated item), the perceived necessity of diverse perspectives (6.30), and answer diversity (6.25) — with feasibility (5.65) and novelty (5.50) rated somewhat lower but still positive. In a comparative preference question, 65% of participants favored AgentPanel over the LLM tools they normally use, both for breadth of research directions surfaced and for overall suitability in early-stage exploration.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's human-facing evaluation centers on **self-reported perceived usefulness and preference**, not on independent measures like objective decision quality, task completion time, calibrated trust, or standardized workload instruments (e.g., NASA-TLX). **This is our interpretation, based on the available sources:** the consistently positive ratings — especially the high scores for follow-up interaction and perspective diversity, and the majority preference over participants' usual LLM tools — suggest the platform delivers on its core promise of perceived exploration breadth for real researchers with real questions. We could not confirm from available sources whether the study measured effects on downstream research decisions, actual idea quality as judged by independent experts, or any negative effects (e.g., information overload from many agents talking at once); readers who need that should consult the full paper directly.

## What is genuinely new

- A concrete, published role-taxonomy and prompt-scaffold design (role definition, answer strategy/timing, answer style, interaction rules, belief-update mechanism) intended to make a multi-agent discussion genuinely heterogeneous, rather than several copies of the same model restating similar points.
- A shared, persistent forum architecture in which humans and a large, heterogeneous roster of LLM agents (250+ agent instances across 10+ models, per the project's own description) operate on the same objects through different interfaces, with a scheduling/orchestration layer mediating turn-taking and context.
- A real-world deployment with a live human study (20 researchers bringing genuine research questions) rather than only an offline or simulated-user evaluation, directly measuring researchers' experience of collaborating with the agent panel.

## Limitations and open questions

- **Modest sample size.** The human study reports 20 valid participants — enough to establish a clear directional preference (65% favoring AgentPanel) but not a large-scale trial, and demographic/recruitment detail was not available to us.
- **Self-reported measures only, for the human study.** The reported outcomes are perceived usefulness, breadth, and preference on rating scales; we found no confirmed evidence of objective outcome measures (e.g., independent expert judgment of resulting idea quality, or measured research decisions downstream of using the platform).
- **Offline comparison scope.** The paper compares against a centralized multi-agent debate baseline; we could not confirm from available sources whether it was also compared against the single-model chatbot workflow that motivates the paper's opening problem statement.
- **Scale of the agent roster.** The GitHub project describes a very large number of connected agent instances (250+) and third-party models; how this scales in cost, latency, or moderation burden for the human is not something we could confirm from the sources available to us.
- Exact offline benchmark numbers, full participant demographics, session protocol, and venue/peer-review status could not be confirmed from the sources reachable in this session.

## Practical implications

If the paper's human-study findings hold up under further scrutiny, they suggest a workable template for teams building AI-assisted research tools: instead of one model trying to be many things in one chat, explicitly differentiate agent roles, timing, and interaction rules, and give the human a persistent, browsable, forum-like space to steer rather than a single request/response loop. The live, open-source deployment (per the project's GitHub repository) also means the design is something research teams or platform builders can inspect and adapt directly, rather than relying solely on a paper description.

## Why you should care

AgentPanel is a relatively rare example in this space: it's a genuinely multi-agent, autonomously operating system (not a single-model wrapper), evaluated with real researchers bringing real scientific questions rather than synthetic benchmarks or simulated users. It speaks directly to a core open question in human–AI collaboration — how much of the value of "talking it through" with multiple perspectives can be reproduced by a well-orchestrated panel of AI agents, and whether researchers actually find that useful in early-stage exploration. The 20-participant study is a modest first step, and the paper's own framing (self-reported usefulness and preference, not objective outcomes) should be kept in mind — but it's a concrete, deployed data point in a fast-moving conversation about what "collaborative AI for science" should actually look like.
