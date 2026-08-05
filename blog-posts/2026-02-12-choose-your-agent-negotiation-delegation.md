# Choose Your Agent: Tradeoffs in Adopting AI Advisors, Coaches, and Delegates in Multi-Party Negotiation

**Authors:** Kehang Zhu (Harvard University), Nithum Thain (Google DeepMind), Vivian Tsai (Google DeepMind), James Wexler (Google DeepMind), Crystal Qian (Google DeepMind) (affiliations per author institutional pages; not independently confirmed as a full affiliation list from the paper itself)
**Publication date:** 2026-02-12 (arXiv v1, id 2602.12089); revised 2026-06-27 (v3)
**Venue:** Submitted to Proceedings of the ACM on Human-Computer Interaction (CSCW 2026); formal acceptance status not independently confirmed from available sources
**Paper link:** https://arxiv.org/abs/2602.12089 (PDF: https://arxiv.org/pdf/2602.12089)
**Code link:** Not available (no dedicated public repository found for this study at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-05

> **A note on sourcing:** arXiv and related hosts (Semantic Scholar, ar5iv, Hugging Face Papers) returned network/access errors when fetched directly in this research session, so this summary is built from the paper's publicly circulated abstract and cross-checked secondary descriptions of its methodology and results, rather than a direct read of the full PDF. Facts that could be cross-confirmed across multiple independent searches (authors, study design, participant counts, and headline quantitative findings) are reported as such; anything that could not be verified this way is marked "not available" or flagged as uncertain rather than invented.

---

## The problem the paper addresses

When people get access to an AI assistant for a task that involves other people — like negotiating a deal — they don't just get one generic "AI helper." They can get very different *kinds* of help: an assistant that suggests what to do but lets you act (an Advisor), one that critiques your move after you've made it (a Coach), or one that just acts on your behalf (a Delegate). This paper asks a simple but under-studied question: when people can choose between these different levels of AI control in a live, multi-party negotiation, which one do they pick — and does the one they pick actually make them (and their group) better off?

## Why this problem matters

Most human-AI collaboration research studies a single fixed way of using an AI assistant. But real products increasingly let users choose *how much control* to hand over — a suggestion box versus an autopilot toggle, in effect. If people systematically gravitate toward the AI modality that feels most comfortable rather than the one that actually produces the best outcomes, that's a real, costly design problem: users could be leaving value on the table simply because full autonomy feels riskier than it is, or because a hands-on advisor feels safer than it actually performs.

## What makes the system agentic

The AI in this study is not a single-turn chatbot. In its most autonomous form (the "Delegate"), it plays a live, multi-turn bargaining game on the participant's behalf: it observes the state of an ongoing three-way negotiation, decides what offer or counter-offer to make on each turn, and continues acting across the whole game without the person previewing or approving each move. The same underlying LLM also operates in less autonomous modes — proposing offers for a human to accept or reject (Advisor) and critiquing offers the human has already made (Coach) — but in every mode it is making sequential, goal-directed decisions inside a live multi-agent bargaining environment, and the paper evaluates it as a negotiating agent (by the deals and surplus it produces), not merely as a text generator.

## How humans and the AI agent collaborate

Participants played three-person bargaining games where, in each game, everyone had access to exactly one of the three AI assistance modes. On every turn, each participant privately decided whether to act manually or lean on the AI in whatever mode was available that round. This means the human retains a turn-by-turn choice over how much to involve the AI, even within a single fixed modality — they weren't forced to use the AI every time it was offered.

## What role the human plays

The human is the negotiator with something real at stake in the outcome (their share of a limited pool being divided in the game). They decide, turn by turn, whether to act for themselves or invoke the AI in whatever mode is on offer, and — across the three separate games — experience what it feels like to work with an advisor, a coach, and a delegate in turn.

## What role the AI agent plays

The AI plays three distinct roles depending on the game's assigned modality: it proactively recommends a move that the human can take or ignore (Advisor); it reacts to a move the human has already made, offering feedback rather than an alternative (Coach); or it autonomously executes the negotiation move itself (Delegate). The paper notes all three modes are powered by the same underlying LLM, described as performing at a super-human level within this specific negotiation setting.

## How control, initiative, and decisions are shared

Initiative shifts along a clear spectrum across the three conditions: Advisor keeps the human fully in control of the final action while the AI only proposes; Coach lets the human act first and the AI comment afterward; Delegate hands the actual move to the AI. Because each participant experienced all three modes (in randomized order) across separate games, the study can directly compare how much initiative people are comfortable ceding, and what that costs or gains them.

## The paper's main idea

**Claim by the authors:** people's preferences about how much control to hand an AI negotiating assistant do not line up with which level of control actually produces the best group outcomes — a "preference-performance misalignment" that has real consequences for how AI-assistance features should be designed and defaulted.

## How the approach works

The authors ran an online behavioral experiment in which 243 participants were grouped into triads and played three multi-turn bargaining games, one per AI-assistance modality (Advisor, Coach, Delegate), presented in randomized order to control for ordering effects. On every turn of every game, each participant privately chose whether to act manually or use the AI mode available that round, and the researchers logged both the choice and its downstream effect on the deal reached.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, real-participant online behavioral experiment — not a simulation or hypothetical account — in which every participant personally experienced all three AI-assistance modalities and made real, incentivized decisions about whether to rely on the AI each turn.

## Participants and study setting

**243 real participants**, organized into groups of three, playing three separate multi-turn bargaining games online (one game per AI modality, order randomized). Demographic details of the participant pool are not available from the sources consulted for this summary.

## Experiments or benchmarks

There is no public benchmark here; the "experiment" is the custom three-modality bargaining-game platform itself, built to let the same participants experience Advisor, Coach, and Delegate assistance under comparable conditions and to log every manual-vs-AI choice alongside the resulting negotiation outcomes.

## Main results

**Demonstrated in the paper (per available descriptions):**
- Participants showed a clear preference ranking among the AI modalities: the higher-control **Advisor was preferred by 44%** of participants, notably more than the **Delegate, preferred by only 19%**.
- Despite that preference, **groups only significantly increased their collective surplus (the total value extracted from the negotiation) when using Delegate access** — the mode people liked least was the one that measurably helped the group the most.
- This constitutes the paper's central "preference-performance misalignment": comfort with an AI modality and that modality's actual payoff are not the same thing, and can point in opposite directions.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's core human-related finding is about **decision quality under different control-sharing arrangements**: people's stated/revealed preference for retaining control (Advisor) did not track with the arrangement that best served their collective economic interest (Delegate). **Our interpretation:** this suggests that in multi-party, higher-stakes coordination settings, a felt sense of control can come at a real, measurable cost to group outcomes — an important nuance for anyone assuming that "give users more control" is a costless design default. We could not confirm from available sources whether the paper additionally reports separate subjective trust, workload, or satisfaction scale results beyond the modality-preference and surplus figures above.

## What is genuinely new

- Directly comparing three distinct levels of AI control (Advisor, Coach, Delegate) **within the same participants**, in the same competitive multi-party task, rather than studying one assistance style in isolation.
- Quantifying a specific **preference-performance misalignment** — showing not just that people have preferences among AI autonomy levels, but that those preferences run counter to which level actually produces better group outcomes.
- Framing AI-assistance-level choice as a genuine, live design axis in a **multi-party** (not just one human + one AI) setting, where a person's choice of AI modality also affects the other real people they're negotiating with.

## Limitations and open questions

- The task domain is a **bargaining/negotiation game**, a specific and somewhat abstracted social setting; how far the preference-performance misalignment generalizes to other collaborative work (e.g., coding, planning, creative tasks) is not established from available sources.
- Full participant demographics, the exact statistical tests behind the reported percentages, and any additional subjective measures (trust, workload) beyond modality preference and collective surplus could not be confirmed, since the full PDF was not directly fetchable in this research session.
- The paper notes the underlying LLM performs at a super-human level in this specific negotiation setting — it is not established from available sources how the findings would change with a less capable or more error-prone AI assistant.

## Practical implications

If these findings generalize, they suggest that AI product teams should be cautious about assuming user-preferred assistance modes are also the best-performing ones — a system that defaults to the most-liked interaction style (e.g., a suggestion-only advisor) may be leaving real value on the table compared to a less-loved but more autonomous mode. This is directly relevant to designing negotiation-support tools, and more broadly to any multi-party or multi-stakeholder setting (e.g., group scheduling, resource allocation, collaborative purchasing) where an AI's level of autonomy is a configurable, user-facing choice rather than a fixed system property.

## Why you should care

This paper puts a concrete number on a design tension that a lot of human-AI products quietly assume away: that giving people more visible control over an AI assistant is always the right (or at least harmless) default. Here, the mode people liked least — full delegation — was the one mode that measurably grew the group's total gains, while the mode people liked most just felt safer without actually paying off collectively. For anyone building AI assistants meant to support decisions involving other people, not just a single user, that's a reminder that comfort and performance can pull in opposite directions, and that measuring both is necessary before deciding what to make the default.
