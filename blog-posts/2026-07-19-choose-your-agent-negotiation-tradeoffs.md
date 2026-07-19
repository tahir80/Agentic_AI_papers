# Choose Your Agent: Tradeoffs in Adopting AI Advisors, Coaches, and Delegates in Multi-Party Negotiation

**Authors:** Kehang Zhu (Harvard University), Nithum Thain, Vivian Tsai, James Wexler, Crystal Qian (Google DeepMind / PAIR)
**Publication date:** 2026-02-12 (arXiv v1); latest revision (v2) 2026-06-27
**Venue:** ACM International Conference on Intelligent User Interfaces (IUI '26), Paphos, Cyprus, March 23–26, 2026
**Paper link:** https://arxiv.org/abs/2602.12089
**Code link:** Not available (no public repository found at time of writing)
**Project page:** Not available
**Date added:** 2026-07-19

> **A note on sourcing:** the arXiv host was not directly reachable from this research session's network, so this summary is built from the paper's abstract, cross-confirmed secondary descriptions, and the authors' public research pages rather than a line-by-line read of the full PDF. Facts that could be independently cross-checked across multiple sources (authors, venue, participant count, study design, headline results) are reported as such; anything that could not be verified is marked "not available" rather than invented.

---

## The problem the paper addresses

If you hand an AI assistant a real negotiation — splitting money or resources with other people, where everyone wants a good deal for themselves — how much control should you actually give it? Should it just suggest what to do next and let you decide (an **Advisor**)? Should it wait and comment on the offer you've already made (a **Coach**)? Or should you hand it the keys and let it negotiate on your behalf (a **Delegate**)? This paper asks which of these arrangements people actually prefer, and — separately — which one actually gets better results.

## Why this problem matters

As LLM-based assistants move from "answer my question" into "act for me in situations with other people," this choice stops being academic. Negotiation is a good stress test because it's inherently social and adversarial: multiple parties, competing interests, and no single "correct" answer to check the AI's work against. Getting the human-AI division of labor wrong here isn't just inconvenient — it can mean leaving real value on the table, or handing over control to a system whose incentives you can't fully verify in the moment.

## What makes the system agentic

This isn't a single-turn chatbot giving negotiation tips. The paper builds three distinct LLM-based assistance modes that operate over a multi-turn bargaining game:

- The **Advisor** proactively recommends a move before the person acts.
- The **Coach** reactively critiques or comments on a move the person has already made.
- The **Delegate** autonomously plays multiple turns of the negotiation on the person's behalf, without a human approving each move.

All three are powered by the same underlying LLM, which the authors report performs at a superhuman level in this negotiation setting on its own. The Delegate condition in particular is a genuine multi-step agent: it observes the game state, plans a strategy, and executes a sequence of negotiation actions autonomously across turns — not a one-shot text reply.

## How humans and the AI agent collaborate

Each participant played through three separate multi-turn bargaining games in groups of three people, with each game randomly assigned one of the three AI assistance modes. This within-subject design lets the study compare, for the same people, how they behave and how well they do under Advisor-level guidance, Coach-level feedback, and full Delegate autonomy.

## What role the human plays

The human is the accountable party in the negotiation — the one whose payoff is actually at stake — who either acts directly on the AI's advice (Advisor), acts and then receives commentary on the move (Coach), or steps back and lets the AI act for them (Delegate). Across all three conditions, it's the human's outcome, and by extension how much surplus their group as a whole achieves, that the study measures.

## What role the AI agent plays

The AI's role shifts by condition: proactive recommender (Advisor), reactive critic (Coach), or autonomous executor (Delegate). Underlying all three is the same LLM playing the actual multi-turn bargaining game at what the authors describe as superhuman skill — the manipulation across conditions is purely about how much of that skill is filtered through human judgment before it becomes an action.

## How control, initiative, and decisions are shared

This is the paper's central axis: control is deliberately varied from mostly-human (Advisor: human retains every action, AI only suggests) through mixed (Coach: human still acts, AI comments after the fact) to mostly-AI (Delegate: AI acts autonomously across turns on the human's behalf). The paper's key move is separating what people *say they want* (which mode they prefer) from what actually *produces the best group outcome* (which mode they perform best under) — and showing these two things point in different directions.

## The paper's main idea

**Authors' claim:** there is a "preference-performance misalignment" in how people want to work with negotiation agents. People gravitate toward the mode that keeps them most in control (the Advisor), but the mode that actually produces the best collective results is the one that takes control away from them (the Delegate).

## How the approach works

Groups of three participants played multi-turn bargaining games online, with each game (presented in randomized order) granting access to exactly one assistance modality — Advisor, Coach, or Delegate — for the whole game. The authors then compared, across conditions, both participants' revealed preference for each mode and the collective surplus (total value captured by the group) each mode produced. As a mechanism check, the authors report that in the Advisor and Coach conditions, participants frequently modified, overrode, or simply ignored the AI's suggestions, pulling outcomes back toward ordinary human-level bargaining patterns — while the Delegate condition's advantage came specifically from bypassing that human filtering step entirely.

## Human study or evaluation design

**Demonstrated in the paper:** an online behavioral experiment with real participants playing real (if game-based) multi-party bargaining, with modality randomly assigned per game and preferences elicited directly from participants (e.g., which mode they'd choose again).

## Participants and study setting

**243 participants**, organized into three-person groups, in an online behavioral economics-style experiment. This is a real human-subjects study, not simulated users — the negotiation stakes and social dynamics (three real people bargaining with and against each other) are genuine, even though the setting is a controlled online game rather than a real-world deal.

## Experiments or benchmarks

There is no public benchmark here; the "task" is a custom multi-turn, multi-party bargaining game platform built for this study, with the three AI-assistance conditions as the experimental manipulation.

## Main results

**Demonstrated in the paper (per available descriptions):**
- Participants preferred the Advisor (44%) over the Delegate (19%) when asked which mode they wanted.
- Despite that preference, groups only achieved significantly higher collective surplus when using the Delegate.
- In Advisor and Coach conditions, people often modified, overrode, or ignored the AI's recommendations, reverting toward ordinary human bargaining outcomes.
- The Delegate's performance advantage is attributed specifically to removing that human "filtering" step, letting the AI's (reportedly superhuman) negotiation skill play out unmodified.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's headline human-related outcome is exactly the tension the title promises: **preference and performance point in opposite directions**. People feel more comfortable, and choose more often, to keep an AI in an advisory role where they retain the final say — but that comfort comes at a measurable cost in group surplus compared to letting the AI act autonomously. This is a directly evaluated collaboration finding, not a speculative claim: it's based on real participants' revealed choices and real, measured negotiation outcomes across the three conditions.

## What is genuinely new

- A controlled, within-subject comparison of three named, clearly differentiated levels of agent autonomy (Advisor / Coach / Delegate) in the *same* task and with the *same* underlying model, isolating the effect of autonomy level itself rather than model capability.
- Direct evidence of a **preference-performance gap**: the mode people want is not the mode that performs best for them — a concrete empirical case study relevant to trust, reliance, and delegation design.
- A mechanistic account of *why* the gap exists: human "filtering" of AI advice (modifying, overriding, or ignoring it) is identified as actively erasing the AI's performance edge in the Advisor/Coach conditions.

## Limitations and open questions

- The task is a controlled online bargaining game, not a real-world negotiation with real money, relationships, or long-term consequences — how much the preference-performance gap generalizes to higher-stakes settings is untested here.
- The underlying LLM is described as achieving superhuman performance in this specific setting; results might look different with a less dominant model, where ceding full control to the Delegate would be a riskier bet.
- We could not independently verify statistical test details, exact surplus numbers, or demographic breakdown of the 243 participants from the sources available in this session — readers who need precise figures should consult the paper directly.

## Practical implications

For anyone designing agents that act on a person's behalf in socially adversarial settings (negotiation, procurement, disputes), this paper is a caution against assuming user preference is a good proxy for what will actually serve the user's interests. If people systematically under-use an agent's most effective mode because it feels like a loss of control, product design may need mechanisms — track records, calibrated trust-building, staged autonomy — to close that gap rather than simply defaulting to whatever mode users say they prefer.

## Why you should care

Most human-AI collaboration research on agent autonomy asks "how do we get the AI to behave well when a human is watching." This paper flips the question around: it shows that the human's own choice of how much control to keep can itself be the bottleneck, even when a clearly better-performing option (full delegation) is sitting right there. That's a genuinely uncomfortable, useful finding for anyone building systems meant to negotiate, bargain, or otherwise act for people among other people.
