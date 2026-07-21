# Choose Your Agent: Tradeoffs in Adopting AI Advisors, Coaches, and Delegates in Multi-Party Negotiation

**Authors:** Kehang Zhu, Nithum Thain, Vivian Tsai, James Wexler, Crystal Qian (affiliations not independently confirmed from available sources)
**Publication date:** arXiv v1 submitted 2026-02-12; latest revision (v3) 2026-06-27 (arXiv id 2602.12089)
**Venue:** arXiv preprint. A closely related paper title, "Strategic Tradeoffs Between Humans and AI in Multi-Agent Bargaining," appears in the Proceedings of the 31st ACM Conference on Intelligent User Interfaces (IUI '26) (DOI 10.1145/3742413.3789078); whether this is the same work under a different title, or a separate but related paper by an overlapping author group, could not be independently confirmed from the sources reachable in this session.
**Paper link:** https://arxiv.org/abs/2602.12089
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-07-21

> **A note on sourcing:** arXiv could not be reached directly from this research session's network (all direct fetches returned HTTP 403, consistent with prior entries in this log). This summary is therefore built from cross-confirmed web-search snippets of the paper's abstract and reported results, checked against multiple independent search queries that returned consistent figures and quotes. Anything that could not be cross-confirmed this way — exact author affiliations, full methodological detail, the paper's relationship to the similarly-titled IUI '26 paper, and its precise peer-review status — is marked "not available" or "not confirmed" rather than invented.

---

## The problem the paper addresses

When you let an AI system help you negotiate — split a bill, close a deal, resolve a dispute — how much control should it actually have? It could just whisper suggestions in your ear (an **Advisor**), critique your moves after you make them (a **Coach**), or take the wheel entirely and negotiate on your behalf (a **Delegate**). This paper asks a deceptively simple question: which of these arrangements actually produces the best outcomes for people, and does that match what people say they want?

## Why this problem matters

AI negotiation and deal-making tools are increasingly being built into everyday software — split-the-bill apps, marketplace platforms, dispute-resolution tools. Most of these default to a low-autonomy "advisor" design, on the assumption that keeping a human firmly in the driver's seat is the safe, trustworthy choice. If it turns out that people's instinct to stay in control actually produces worse outcomes than handing over the wheel, that has direct implications for how such products should be designed — and for how much we should trust our own intuitions about when to rely on an AI agent.

## What makes the system agentic

The paper studies an LLM that operates in three distinct modes across multi-turn, multi-party bargaining games. In the **Delegate** mode specifically, the LLM is a genuine autonomous negotiating agent: it observes the state of an ongoing three-party bargaining game and independently makes and responds to multiple rounds of offers on the participant's behalf, pursuing the participant's payoff without turn-by-turn human instruction. According to the authors, the underlying LLM achieves super-human performance within this negotiation setting. The Advisor and Coach modes use the same underlying model but in more constrained roles (proactively recommending a move, or reactively critiquing one), and the paper's evaluation directly compares how the model performs and is used when it acts as a full agent versus a more passive assistant — placing this squarely within our working definition of agentic AI as a system that plans and acts across multiple steps, not just one that answers a single question.

## How humans and the AI agent collaborate

243 participants played three multi-turn bargaining games in groups of three real people. In each game, participants had access to exactly one of the three AI modalities, with the assignment randomized across games. This design lets the same real people experience — and be compared across — genuinely different divisions of labor between human and AI: getting advice they can take or leave, getting feedback on moves they've already made, or handing the negotiation itself to the AI.

## What role the human plays

In the Advisor and Coach conditions, the human remains the one actually making moves in the negotiation — they can accept, ignore, or modify what the AI recommends (Advisor), or use the AI's critique of their own proposals to revise their strategy (Coach). In the Delegate condition, the human's role shifts to that of a principal who has handed over execution: they set the AI loose to negotiate on their behalf and no longer make moves directly themselves.

## What role the AI agent plays

The same underlying LLM plays three different functional roles depending on the assigned condition: a proactive **Advisor** that recommends what to do next, a reactive **Coach** that gives feedback on a move the human has already proposed, and an autonomous **Delegate** that plans and executes the negotiation itself across multiple rounds.

## How control, initiative, and decisions are shared

This is a direct, controlled comparison of different levels of adaptive delegation: from advisory (AI suggests, human decides and acts), through coaching (AI reacts to human choices), to full delegation (AI decides and acts, human is not in the loop turn-by-turn). The paper's central contribution is showing that these different divisions of control produce different outcomes, and that people's stated preferences among these arrangements do not match which arrangement objectively performs best.

## The paper's main idea

**Claim by the authors:** there is a **preference-performance misalignment** in human-AI collaborative negotiation. According to the reported results, participants strongly preferred the higher-control Advisor mode (44% of preference share) over the Delegate mode (19%), yet it was only under Delegate access that groups significantly increased their collective surplus (the total value created in the negotiation). The authors attribute this gap to a "human filter" effect: the AI's proposals reliably create more joint value than manually-generated ones across all three conditions, but in the Advisor and Coach modes, humans modify, override, or ignore the AI's good suggestions — reverting outcomes back toward what humans alone would have achieved. The Delegate mode's advantage, per the authors, comes not from the AI behaving differently, but from removing that human-filtering step entirely.

## How the approach works

Participants were randomly assigned to experience the three AI modalities across three separate multi-turn bargaining games in fixed three-person groups, with treatment order randomized. The authors report adjusting for voluntary non-compliance (participants not doing what their assigned condition nominally allowed) to estimate individual welfare effects, finding that compliance-adjusted individual welfare gains under Delegate access were roughly 1.5 times the raw intent-to-treat estimate. A follow-up mechanism analysis compared the value created by AI-generated versus human-generated proposals across all conditions to isolate why the Delegate condition outperformed, framing the autonomous Delegate as acting like a "market maker" that injects rational, Pareto-improving proposals and restructures the trading environment.

## Human study or evaluation design

**Demonstrated in the paper (per available sources):** an online behavioral economics experiment with 243 real participants, organized into groups of three, each group playing three distinct multi-turn bargaining games with randomized assignment of AI modality (Advisor, Coach, or Delegate) per game.

## Participants and study setting

243 real online participants negotiating in real time with two other real participants per game — not simulated counterparts or personas. Exact recruitment platform, demographics, and compensation are **not available** from the sources reachable in this session.

## Experiments or benchmarks

There is no public benchmark or dataset here; the "experiment" is the bargaining-game platform itself, custom-built for this study. The underlying LLM's negotiation strength is reported as super-human within this specific game setting, but exact quantitative benchmark scores for the model in isolation were **not confirmed** from available sources.

## Main results

**Demonstrated in the paper (per available sources):**
- Preference: Advisor was the most preferred modality (44% of participant preference), versus Delegate at 19%.
- Performance: only the Delegate condition produced a statistically significant increase in group collective surplus.
- Mechanism: AI-generated proposals created more joint surplus than human-generated ones in every condition, but human override/modification in the Advisor and Coach conditions eroded most of that advantage; only Delegate access preserved it, by removing the human-filtering step.
- Compliance-adjusted individual welfare gains under Delegate access were reported at roughly 1.5× the raw intent-to-treat estimate.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper (per available sources):** the study directly measures a **decision-quality/preference gap** — the arrangement people say they want (Advisor) is not the one that objectively performs best for the group (Delegate), and the paper's own reported mechanism is that human oversight itself (modifying or overriding the AI) is what erodes performance in the lower-autonomy conditions. **Our interpretation:** this is one of the more concrete pieces of causal evidence in this line of work that "keeping a human in control" is not automatically the safer or better-performing choice — it can actively undermine an AI system's objectively better proposals, at least in this bargaining-game setting.

## What is genuinely new

- A direct, randomized, three-way comparison of Advisor / Coach / Delegate arrangements with the same underlying LLM and the same real participants, rather than comparing an AI-assisted condition only against a no-AI baseline.
- Quantitative evidence of a **preference-performance misalignment**: what people prefer (more control) is not what produces the best collective outcome (full delegation), directly relevant to how "calibrated trust and reliance" should be understood.
- A mechanism analysis pinpointing *why* lower-autonomy modes underperform: not because the AI reasons worse in those modes, but because humans dilute good AI proposals when given the chance to override them.

## Limitations and open questions

- This is a one-shot, online behavioral experiment on custom bargaining games — not a study of real-world, higher-stakes negotiation deployments (e.g., real commercial contracts or legal disputes), so how far these findings generalize is an open question.
- The paper's precise author affiliations, full recruitment/compensation details, and exact peer-review/venue status could not be independently confirmed from the sources reachable in this session.
- The relationship between this arXiv preprint and the similarly-described ACM IUI '26 paper "Strategic Tradeoffs Between Humans and AI in Multi-Agent Bargaining" is **not confirmed** — they may be the same work under a different title, related papers from an overlapping author group, or something else entirely; readers should verify directly.
- The study measures preference share and collective/individual surplus; it does not appear (from available sources) to report standardized trust or workload instruments (e.g., a trust scale or NASA-TLX), so claims about "trust" here are inferred from stated modality preference rather than a validated trust measure.

## Practical implications

For anyone building AI-assisted negotiation, deal-making, or dispute-resolution tools, this paper is a caution against defaulting to low-autonomy "advisory" designs purely because they feel safer or more controllable. If the goal is the best collective outcome, the findings suggest that the mechanism by which humans can override good AI proposals may itself be the thing standing between users and better results — and that interface and delegation design, not just raw model capability, determines whether an agent's strengths actually reach the people it's meant to help.

## Why you should care

This is a clean, quantified example of exactly the kind of gap this log tracks: people are not necessarily good judges of how much autonomy to give an AI agent, even when the AI is demonstrably better at the task in front of them. It adds real, randomized-experiment evidence to the "calibrated trust and appropriate reliance" and "adaptive delegation" themes that recur across this collection, and it's a useful counterweight to the more common assumption that more human oversight is always the safer design choice.
