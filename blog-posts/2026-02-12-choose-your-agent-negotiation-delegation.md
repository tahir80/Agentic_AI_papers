# Advisor, Coach, or Delegate? What a 243-Person Negotiation Experiment Reveals About Why People Choose AI Help That Isn't the Best Kind

**Paper title:** Choose Your Agent: Tradeoffs in Adopting AI Advisors, Coaches, and Delegates in Multi-Party Negotiation
**Authors:** Kehang Zhu (Harvard University), Nithum Thain, Vivian Tsai, James Wexler, Crystal Qian (Google DeepMind team affiliation reported; not independently re-verified per author)
**Publication date:** 2026-02-12 (arXiv v1); latest revision 2026-06-27 (v3)
**Venue:** Not independently confirmed. Secondary sources returned conflicting signals (one search result associated the work with ACM IUI 2026, another with a CSCW submission and an AAMAS 2026 ES workshop presentation) — treat all of these as unverified until checked against the arXiv listing directly. The paper is at minimum an arXiv preprint.
**Paper link:** https://arxiv.org/abs/2602.12089
**Code link:** Not available (no public code or data repository was found)
**Project page:** Not available
**Date added:** 2026-07-20

*A note on sourcing: the research environment that produced this summary could not directly fetch the arXiv PDF or HTML — outbound web requests to arxiv.org (and to most external sites other than raw GitHub content) returned HTTP 403 errors from the network policy in place for this session. The account below is built entirely from what could be recovered through web search snippets of the paper's abstract and indexed text, cross-checked across multiple queries for consistency. Specific figures (the 44%/19% preference split, the $10 base pay, the ~56.4-minute session length, the Prolific recruitment) appeared consistently across independent searches, which is why they are reported here as author-stated facts. Anything that could not be cross-confirmed — exact statistical tests, the full limitations section, the precise underlying LLM model, the final venue — is explicitly flagged below as unverified rather than presented as settled.*

---

## The problem the paper addresses

When you give someone access to an AI assistant for a high-stakes task, you usually have to decide (or let them decide) *how much control to hand over*. Should the AI just whisper suggestions while the person stays fully in charge? Should it comment on what the person is about to do? Or should it just go ahead and act on their behalf? Companies building AI copilots and AI agents face this design question constantly, but there's been little rigorous evidence about which mode people actually prefer, which mode actually produces the best outcomes, and — critically — whether those two things line up. This paper studies that question in a concrete, measurable setting: multi-party negotiation, where three people bargain with each other and each can optionally lean on an AI in one of three different roles.

## Why this problem matters

Negotiation is a good stand-in for a much broader class of real-world decisions — hiring, sales, resource allocation, contract terms — where multiple people with different interests have to reach an agreement, and where an AI assistant could plausibly help. If it turns out that people gravitate toward the AI mode that *feels* safest (keeping full control) rather than the one that actually works best, that's an important and slightly uncomfortable finding for anyone designing AI products: giving users the control they say they want could leave real value on the table. Conversely, if fully autonomous AI negotiation produces better group outcomes, that raises its own questions about trust, accountability, and whether "the AI decided" is an outcome people are willing to accept even when it's better for everyone.

## What makes the system agentic

The central object here is an LLM that is not just answering questions — it is embedded in an actual multi-turn bargaining game, where it can be asked to generate recommendations, critique a user's move, or, in the "Delegate" condition, take over the negotiation and autonomously act on a person's behalf across multiple turns, pursuing that person's interests toward a deal. That autonomous-execution role is what pushes this beyond a chatbot: the AI is given a goal (get the best outcome it can within the game's rules), it observes an evolving multi-party negotiation state, and it takes sequential actions (offers, counteroffers, acceptances) inside that environment without a human approving each individual move. The same underlying LLM is also evaluated in two less autonomous roles (advisor and coach), which lets the paper directly compare "AI acts for you" against "AI helps you act" using one consistent model.

## How humans and the AI agent collaborate

Each of the three participants in a given negotiation session could, on their turn, choose to act completely manually, or to draw on whichever single AI modality that particular game had made available to them:

- **Advisor** — the AI proactively suggests what offer to make, before the person acts.
- **Coach** — the AI reacts to a move the person is about to make or has drafted, offering feedback rather than a from-scratch suggestion.
- **Delegate** — the AI is handed the turn outright and executes the negotiation move autonomously.

Participants played three separate multi-turn bargaining games, each one restricted to a single modality, so the comparison is within-subject: the same people experienced advisor-style help, coach-style help, and full delegation across different rounds.

## What role the human plays

Humans are the actual stakeholders in the negotiation — the outcome affects their own payout. On every turn, a human privately decides whether to act manually or to invoke whichever AI modality is available that round, and, in the advisor and coach conditions, whether to accept, edit, or ignore what the AI proposes. The paper's authors frame this editorial step — modifying or overriding an AI-generated offer — as central to the story: it's the mechanism through which human judgment either adds value or (as the results suggest) subtracts it.

## What role the AI agent plays

The AI plays three different roles depending on condition, but it is always the same underlying model, described by the authors as achieving "super-human performance" in this specific negotiation setting (the specific base model was not confirmed from the sources available). As Advisor it proposes; as Coach it critiques; as Delegate it acts. In the Delegate condition specifically, the AI's proposals reach the shared negotiation table unfiltered by human second-guessing.

## How control, initiative, and decisions are shared

This is the paper's real subject. Control is split along a graded axis — from full human control with an AI suggestion in the background, through human control with AI critique, to full AI initiative with human oversight reduced to whether to use the Delegate mode at all in a given game. Initiative shifts accordingly: in Advisor/Coach modes, the human retains the final say on every single move; in Delegate mode, initiative passes to the AI for as long as delegation is active. The paper's mechanism analysis (as reported in search-indexed text) argues that this difference in *who has final say* is exactly what separates a good outcome from a great one — because humans, even when shown a high-quality AI-generated offer, tend to water it down toward what the authors describe as "risk-averse social norms" when given the chance to edit it.

## The paper's main idea

The authors report what they call a **preference–performance misalignment**: participants strongly preferred the Advisor mode (44% of relevant choices, per the reported figures) over the Delegate mode (19%), yet it was only under Delegate access that a negotiating group's *collective* surplus (the total value created and split among the three parties) increased significantly. In other words: the mode people liked least was the one that objectively worked best for the group.

## How the approach works

According to the reported mechanism analysis, the reason Delegate mode outperforms is not that the underlying AI is smarter when it's "delegated" versus "advising" — it's the same model either way. The difference is that in Advisor and Coach modes, a human stands between the AI's proposal and the negotiation table, and that human tends to soften or override strong AI-generated offers to fit social norms around what feels like a "reasonable" ask — diluting the quality of what actually gets proposed. Delegate mode removes that filtering step entirely, so the AI's offers reach the table intact. The authors additionally report a positive externality: because Delegate-mode offers are higher-quality, they upgrade the shared pool of offers circulating in the negotiation — benefiting the whole group, including participants who didn't personally choose to delegate that round. Separately, the paper reports that across all three modalities, trades that originated from an AI-assisted proposal (of any kind) tended to generate higher joint surplus than fully manual proposals — suggesting the AI's input is valuable even when a human is standing in the way of it being fully realized.

## Human study or evaluation design

This is a genuine human-subjects study, not a simulation. It is an online, incentivized, within-subject behavioral experiment: each participant played three separate multi-turn, three-party bargaining games, one per AI modality (Advisor / Coach / Delegate), so every person experienced all three conditions. Recruitment, according to the reported details, went through Prolific under an IRB-approved protocol with no additional screening criteria beyond standard platform eligibility.

## Participants and study setting

243 participants completed the study. Reported compensation was a $10.00 base payment plus a performance-based bonus that averaged $4.50, for sessions that averaged roughly 56.4 minutes — meaning outcomes had real (if modest) financial stakes for participants, which strengthens the behavioral validity of the preference and performance results relative to a hypothetical, unincentivized survey.

## Experiments or benchmarks

There is no public benchmark or dataset associated with this paper (none was found in available sources). The "benchmark" here is the custom three-party bargaining game itself, run as a controlled behavioral experiment rather than scored against a fixed test set.

## Main results

- Preference: Advisor chosen in 44% of relevant instances vs. 19% for Delegate (reported figures; the remainder presumably split between Coach and manual action, though the exact breakdown was not confirmed from available sources).
- Performance: only Delegate access produced a statistically significant increase in group collective surplus (the specific effect size and test statistics were not confirmed from available sources — the "significant increase" characterization comes from the reported abstract/summary text, not a directly verified numeric table).
- Mechanism: human editing of AI-generated offers in Advisor/Coach modes is reported to dilute offer quality relative to letting the AI's offer stand unedited.
- Spillover: Delegate-mode offers were reported to raise the quality of the overall shared offer pool, benefiting non-delegating participants too.
- AI-assisted proposals (across all three modes) were reported to produce higher joint surplus when accepted than fully manual proposals.

## Effects on human performance, trust, workload, safety, or decision quality

The clearest, best-supported human-related outcome in this paper is the **preference–performance gap itself**: people's stated/revealed preference for retaining control (Advisor) does not track with what actually maximizes group welfare (Delegate). This is a decision-quality finding about the *choice of AI mode*, not just about negotiation outcomes. Beyond that headline result, the available sources did not surface confirmed quantitative measures of trust, workload, or perceived safety (e.g., no Likert-scale trust ratings or NASA-TLX-style workload scores were found in the material accessible here) — if the paper collects those, they were not visible in the search-indexed text this summary relies on, and should be treated as **not available** rather than absent from the paper itself.

## What is genuinely new

Two things stand out as the paper's distinctive contribution, based on the available material: (1) directly pitting three *distinct levels of AI initiative* — advisory, coaching, and full delegation — against each other using the *same underlying model*, isolating the effect of control-sharing itself rather than confounding it with AI capability differences; and (2) identifying a concrete behavioral mechanism (human editing dilutes AI offer quality) for *why* more autonomous AI assistance can outperform more human-controlled assistance, rather than simply reporting that it does.

## Limitations and open questions

Reported here as author claims where explicit, and as this summary's own reasonable inferences elsewhere (marked accordingly): this is a single negotiation-game domain, so it is an open question (my own interpretation) whether the preference–performance misalignment generalizes to other high-stakes collaborative-decision domains such as hiring or medical triage, where autonomous "delegation" may carry very different accountability and trust consequences. The study is online and incentivized but still a lab-style behavioral experiment rather than a field deployment inside a real negotiation platform. The paper's own stated limitations and future-work discussion could not be retrieved in this session (network-restricted), so this section should not be read as a full or authoritative account of the authors' own caveats — only as what could reasonably be inferred without seeing the full text.

## Practical implications

If the core finding replicates, it has a direct and somewhat counterintuitive implication for anyone designing AI copilots or AI agents for collaborative, multi-stakeholder decisions: exposing users to the *most controllable* AI mode (recommendations they can freely edit or ignore) may feel safer and be preferred, while quietly leaving value on the table relative to letting the AI act with more autonomy. That's a real tension for product design — between what builds user comfort/adoption and what actually produces the best collective outcome — and it argues for measuring both preference *and* performance separately rather than assuming the two align.

## Why you should care

This paper offers a fairly rare thing: real people, real (if modest) money on the line, and a clean experimental separation between three specific ways an AI agent can share control with a human — versus the outcomes each one produces. Its central tension (the mode people want isn't the mode that works best) is exactly the sort of finding that should make anyone building or overseeing collaborative AI agents pause before assuming that "give users maximum control" is automatically the right design default.
