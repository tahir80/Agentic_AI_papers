# HAI-Eval: Measuring Human-AI Synergy in Collaborative Coding

**Authors:** Hanjun Luo, Chiming Ni, Jiaheng Wen, Zhimu Huang, Yiran Wang, Bingduo Liao, Sylvia Chung, Yingbin Jin, Xinfeng Li, Wenyuan Xu, XiaoFeng Wang, Hanan Salam (author list and order per the arXiv listing; institutional affiliations not confirmed from available sources)
**Publication date:** 2025-12-04 (arXiv id 2512.04111, first posted under the title "CentaurEval: Benchmarking Human-in-the-Loop Value in Agentic Coding"; latest revision — retitled "HAI-Eval: Measuring Human-AI Synergy in Collaborative Coding" — posted 2026-05-21)
**Venue:** arXiv preprint; under peer review (an OpenReview listing exists under the title "HAI-Eval: Measuring Human-AI Synergy in Collaborative Coding", forum id `pKqt8psClA`; final venue decision not confirmed from available sources)
**Paper link:** https://arxiv.org/abs/2512.04111 (PDF: https://arxiv.org/pdf/2512.04111)
**Code link:** Not available (no public repository confirmed from available sources)
**Project page:** Not available
**Date added:** 2026-08-28

> **A note on sourcing:** arxiv.org was not directly reachable from this research session's network (the fetch tool reported the domain blocked at the network egress level), so this summary is built from the paper's abstract, an OpenReview mirror, and multiple independent secondary descriptions of the full text rather than a direct read of the original PDF. Facts that were confirmed consistently across independent sources (the benchmark design, participant count, study conditions, and headline pass-rate numbers) are reported as such. Anything that could not be cross-confirmed — author affiliations, exact demographic breakdown, compensation amount, final venue decision — is marked "not available" or flagged as uncertain rather than invented.

---

## The problem the paper addresses

There are now two separate ways people measure how good AI coding tools are. One is the old-fashioned way: give a human programmer a task and see how they do. The other is the new way: give an LLM coding agent the same kind of task, let it work alone in a sandbox, and score its output. Both of these measure solo performance — either the human alone, or the AI alone.

But that's not actually how most real coding with AI assistants happens today. A developer sits with Copilot (or a similar tool) open, going back and forth: the AI drafts something, the human steers it, the AI retries, the human catches a mistake it would have missed alone. Neither existing kind of benchmark measures *that* — the value that shows up specifically when a human and an AI work on the same problem together, each catching what the other misses.

## Why this problem matters

If your only measuring sticks are "how good is the human" and "how good is the AI," you have no way to answer a much more practical question: is a given AI assistant actually making the *pairing* better, or is it just adding noise a competent developer has to filter out? That question matters for anyone deciding whether to trust an AI coding assistant with real work, and for anyone trying to design the assistant itself — you can't optimize for good collaboration if you're only ever scoring solo performance.

## What makes the system agentic

The AI side of this study is not a single code-completion suggestion — it's an agentic coding assistant (the paper uses GitHub Copilot's agent capabilities) operating inside a full, standardized cloud development environment (GitHub Codespaces): reading a task specification, writing and editing files, running tests, and retrying autonomously (the paper reports it is allowed up to 25 autonomous attempts in the fully-autonomous condition) until it produces a solution or gives up. That is multi-step, tool-using, environment-acting behavior toward a goal — not a one-shot text reply — which is what qualifies it as agentic AI under our working definition.

## How humans and the AI agent collaborate

The paper's central design trick is what it calls **"Collaboration-Necessary" problems**: coding tasks deliberately built so that neither an unaided human nor a standalone AI agent can reliably solve them, but a human and an AI working together can. That forces the benchmark to actually measure collaboration, rather than measuring two solo performances side by side and calling the better one "the answer." Humans work inside a real, standardized IDE (a cloud-hosted VS Code environment with Copilot available), and can call on the AI, correct it, redirect it, or work independently, depending on the condition being tested.

## What role the human plays

Across the study's conditions, the (45 recruited, real) human participants variously: solve tasks completely on their own (no AI), or work with Copilot available and use it however they judge best — asking it to draft code, correcting its output, deciding when to trust it and when to take over. In one condition, a human also acts purely as a fallback for the AI, stepping in only to unstick clearly mechanical/procedural failures (e.g., a broken environment step) without providing any logical or design help — a way of isolating "the AI's own reasoning" from "the AI plus a safety net."

## What role the AI agent plays

The AI (the Copilot-based coding agent) plays two different roles depending on condition: in one, it works completely autonomously end-to-end, relying only on its own retry logic; in another, it works as an active collaborator that a human developer directs, corrects, and builds on in real time inside the shared IDE.

## How control, initiative, and decisions are shared

The paper structures this explicitly as four distinct conditions, forming a spectrum of who is in control:

- **CH — human-only:** the person solves the task with no AI assistance at all.
- **C0 — fully autonomous AI:** the Copilot-based agent works completely alone, using only its own built-in retry behavior (up to 25 attempts) with zero human input.
- **C1 — minimally-intervened AI:** a researcher steps in only to fix strictly mechanical/procedural failures (broken setup, environment issues) — never to help with the actual logic or design of the solution — isolating how good the AI's own reasoning is once you remove pure friction.
- **C2 — human-AI collaboration:** a human developer works with Copilot freely available throughout the task, deciding for themselves how much to lean on it.

This design lets the study isolate exactly what "the human contributes," "the AI contributes," and "the collaboration itself contributes," rather than lumping them together.

## The paper's main idea

**Claim by the authors:** existing evaluations of coding ability — whether of humans or of AI — miss an important category of real-world problems: tasks that are specifically hard *because* they need both human judgment and AI execution, and that are more tractable when the two work together than when either works alone. The paper argues that measuring "human-in-the-loop value" (or "human-AI synergy") requires a benchmark purpose-built around such tasks, not a benchmark that just runs the same tasks past a human and an AI separately.

## How the approach works

The authors built 45 reusable problem templates, each capable of generating many concrete task instances (450 in total), so the same underlying "shape" of collaboration-necessary problem can be tested repeatedly without participants seeing identical tasks. Two of the four conditions (the fully autonomous AI and the minimally-intervened AI) are run against this large, static, reproducible 450-task dataset so AI-only performance can be measured at scale. The other two conditions (human-only, and human-AI collaboration) are run live, with real participants working inside a standardized cloud IDE (GitHub Codespaces, pre-configured per task with the right dependencies and Copilot enabled), so the human conditions are directly comparable to each other and, as much as possible, to the AI-only conditions.

## Human study or evaluation design

The human portion is a **within-subject study with 45 participants**, each of whom worked through multiple tasks under different conditions (the paper describes each participant completing several tasks split between unaided and AI-assisted conditions), so the same person's solo and collaborative performance could be compared directly rather than comparing different people to each other. Per secondary descriptions, participant credentials were verified and candidates completed a brief screening task using VS Code with Copilot before being included, and the protocol was reviewed and approved by an institutional review board (IRB).

## Participants and study setting

**45 real human participants**, recruited through personal contacts and advertisements on university forums. Per available secondary descriptions, participants were East Asian current students or recent graduates (undergraduate through PhD level) in computer science or related fields, all of whom reported regularly using AI coding agents already, and were sorted into professional skill tracks based on a background/skills questionnaire. The authors reportedly acknowledge this as a limitation: the sample is not demographically representative of the broader population of professional software engineers (see Limitations below). This is a real, hands-on lab-style study — participants worked live inside the cloud IDE — not a simulated or logged-only evaluation.

## Experiments or benchmarks

The core artifact is the **HAI-Eval / CentaurEval benchmark** itself: 45 "Collaboration-Necessary" problem templates generating a reproducible 450-task static dataset (used for the two AI-focused conditions), plus a live, dynamic version of the same task family used for the two human-involving conditions. Five different LLMs were benchmarked in the AI-only conditions; the human-involving conditions used Copilot as the collaborative assistant.

## Main results

**Demonstrated in the paper (per consistently cross-confirmed secondary descriptions):**
- Standalone AI agents performed very poorly on these deliberately collaboration-necessary problems: around **0.67%** pass rate for the fully autonomous condition (C0).
- Unaided humans did better but still struggled: around **18.89%** pass rate working completely alone (CH).
- Human-AI collaboration (C2) substantially outperformed both solo conditions, reaching around **31.11%** pass rate.
- The authors report qualitative evidence of what they describe as an "emerging co-reasoning partnership": the pattern of who contributes the key breakthrough on a given task is not fixed — sometimes the human supplies the critical insight and the AI executes it, and sometimes the AI's suggestion is what unlocks progress for the human — challenging a simple "human directs, AI just executes" hierarchy.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central measured outcome is task success (pass rate) under different levels of human-AI collaboration, which is itself a direct measure of collaborative decision quality: the same people solved roughly 1.6x more of these tasks when paired with the AI than when working alone (18.89% → 31.11%), a first-hand demonstration that, on tasks purpose-built to need both, the pairing measurably outperforms either party alone. **This is a result the authors report directly, not our interpretation.** We could not confirm from available sources whether the paper additionally reports separate self-reported trust, workload (e.g., NASA-TLX), or time-on-task measures — readers who need those should consult the paper directly.

## What is genuinely new

- A benchmark design built around problems that are *provably* (by construction) hard for either a human or an AI alone, rather than repurposing standard coding-benchmark problems and simply adding a "with AI help" condition.
- A four-condition design (human-only, fully autonomous AI, minimally-intervened AI, human-AI collaboration) that separates "how good is the AI's raw reasoning," "how good is the AI once you strip out pure procedural friction," and "how good is the actual collaboration" — rather than a single human-vs-AI comparison.
- A real, live, IRB-approved human study (45 participants working in a standardized cloud IDE) rather than only a static, log-mined, or simulated evaluation of "human-AI collaboration."

## Limitations and open questions

- **Narrow participant pool.** All 45 participants are reported to be East Asian students or recent graduates in computer science, already regular users of AI coding agents — this limits how confidently the results generalize to professional software engineers more broadly, to other demographics, or to less AI-experienced developers.
- **Small absolute pass rates.** Even the best (collaborative) condition solved under a third of tasks (31.11%), meaning these "Collaboration-Necessary" problems remain difficult even together — a useful stress test, but not evidence that human-AI pairing solves such problems reliably.
- **Domain scope.** The benchmark is specifically about coding tasks; the paper's synergy findings should not be assumed to transfer automatically to other kinds of agentic collaboration (writing, research, decision support, etc.).
- We could not independently verify exact statistical tests, full demographic tables, or the paper's own stated limitations section from the sources available in this session, since the full PDF could not be fetched directly — readers who need precise details should consult the paper.

## Practical implications

If the reported numbers hold up, they offer a concrete, quantified counter-argument to evaluating coding agents purely on solo autonomous benchmarks: on tasks designed to need both a human and an AI, autonomous-only agent performance can be extremely poor (under 1% here) even though the same AI, used collaboratively, contributes to a large jump in success rate. That's a practical argument for coding-agent builders to evaluate and tune for the *collaborative* mode specifically, rather than assuming that gains in autonomous benchmarks automatically translate into better human-AI pairing outcomes.

## Why you should care

This paper gives a rare, purpose-built way to actually measure something people say a lot but rarely quantify: that "the human-AI pair is better than either alone." Instead of asserting that, it built tasks specifically designed to make it testable, ran real people through a real study, and reported the resulting numbers. For a research log focused on human-AI collaboration in agentic systems, that combination — a synergy-measuring benchmark plus a genuine, IRB-approved human study — is exactly the kind of methodological contribution worth tracking, even though (per available sources) it does not yet report the trust/workload-style outcomes some other papers in this collection do.
