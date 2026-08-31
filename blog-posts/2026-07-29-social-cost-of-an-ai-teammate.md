# The Social Cost of an AI Teammate: How an Artificial Teammate Reshapes Human-Human Communication in Small-Team Decision-Making

**Authors:** Nia Nixon, Jaeyoon Choi, Pedro Martins De Bastos, Mohammad Amin Samadi, Luise Mehner, Seehee Park, Spencer JaQuay (University of California, Irvine; Luise Mehner also affiliated with University of Tübingen, Germany)
**Publication date:** 2026-07-29
**Venue:** arXiv preprint, cross-listed cs.HC / cs.AI / cs.CY (peer-review status not confirmed)
**Paper link:** https://arxiv.org/abs/2607.27179
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-08-31

> **A note on sourcing:** this session's network access blocks direct fetches to arxiv.org and related mirrors (huggingface.co, semanticscholar.org, alphaxiv.org, paperswithcode.com all returned `EGRESS_BLOCKED`). This summary is built from the paper's own abstract and from consistent, repeated paraphrases of its methods and findings surfaced across multiple independent web searches — not from a direct read of the full PDF. Numbers and quotes below are reported as the authors' claims; anything that could not be corroborated this way is marked "Not available," and this session's own interpretation is labeled as such. Readers who want exact statistics (p-values, effect sizes, the specific model used as the AI teammate) should consult the paper directly.

---

## The problem the paper addresses

Companies are increasingly floating the idea of AI not as a tool you query, but as a "teammate" that sits inside a group chat or a meeting alongside human colleagues. But almost all of what we know about AI assistance comes from studying a *single* person working with a single AI. This paper asks a different question: when you drop a talkative AI participant into a small *team* that has to reach a real decision together, what happens to how the *humans* talk to each other?

## Why this problem matters

If organizations start adding AI "teammates" to meetings and decision-making groups on the assumption that more (AI-generated) input is automatically helpful, it matters a great deal whether that addition quietly degrades the human side of teamwork — even while the team still produces an answer. A team that reaches a fine decision but leaves its human members feeling unheard, side-lined, or less connected to each other is a hidden cost that a simple "did the team get the right answer?" measure would completely miss.

## What makes the system agentic

The "AI teammate" in this study is not a passive chatbot waiting to be asked a question. It is built into the team as a full conversational participant: it reads the ongoing multi-turn group discussion, decides when and what to contribute, puts forward its own arguments and positions on a shared decision task, and sustains this role across an extended, multi-turn deliberation rather than producing one isolated reply. That is a more modest form of "agentic" than a tool-using, multi-step planning system (there is no evidence here of it calling external tools or taking actions in a software environment) — but it is genuinely evaluated as an autonomous team *agent*, not as a single-turn language model: the researchers analyze its conversational behavior as that of a team member with its own contribution pattern, cohesion, and influence on the group.

## How humans and the AI agent collaborate

Small teams — either two humans plus one AI teammate, or three humans with no AI — worked together in real time to resolve a high-stakes moral-dilemma decision task. The AI teammate participated as a genuine co-equal voice in the group's discussion, contributing to the deliberation exactly as a third team member would, while the researchers recorded and analyzed the resulting group conversation.

## What role the human plays

Human participants are recruited team members (students) who must talk through a genuinely difficult moral dilemma with their teammates — human or AI — and reach a team decision. They contribute their own reasoning, respond to and build on what other team members (including the AI, where present) say, and afterward report on how included, valued, and connected to their teammates they felt.

## What role the AI agent plays

The AI teammate acts as an active, opinionated group member. According to the authors' reported findings, it was the **single most talkative and most self-cohesive member of every AI-inclusive team** — it spoke the most and stayed the most internally consistent — yet its individual contributions carried the **least new information and the lowest lexical density** of any team member. In other words, it dominated the floor without proportionally advancing the group's shared understanding.

## How control, initiative, and decisions are shared

This is a mixed-initiative, shared-decision-making setup by design: no single member (human or AI) is designated the leader, and the team's final decision emerges from open, multi-party deliberation. The paper's central concern is exactly this shared-control dynamic — how the presence of an AI voice with its own initiative to speak reshapes how *initiative and airtime* end up distributed among the humans who are also trying to be heard.

## The paper's main idea

**Claim by the authors:** adding a highly active AI teammate to a small decision-making team does not just add a fourth voice — it measurably changes how the *human* members talk to and relate to one another, even when the AI's own contributions are comparatively shallow. The authors frame this as a "social cost" of AI teaming: a real behavioral and psychological effect on the human side of the team, separate from whether the team's decision quality was good or bad.

## How the approach works

The researchers used **Group Communication Analysis (GCA)** — a validated method for quantifying sociocognitive dynamics in team discourse (things like responsivity, social impact, and information contribution) — together with post-task team surveys and lexical analyses of the transcribed group discussions. They compared 16 mixed teams (two human students plus one AI teammate) against 17 all-human control teams (three human students), all completing the same moral-dilemma decision task, in a randomized controlled design.

## Human study or evaluation design

**Demonstrated in the paper:** this is a genuine randomized controlled experiment with real human participants, not a simulation or offline analysis. Teams were randomly composed as either human-AI or all-human, given the identical task, and their conversations were recorded and analyzed with the same measures across both conditions — allowing a direct, controlled comparison of communication dynamics with versus without an AI teammate present.

## Participants and study setting

**Reported by the authors:** 33 teams in total — 16 human-AI teams (2 humans + 1 AI each, i.e. 32 human participants) and 17 all-human teams (3 humans each, i.e. 51 human participants) — recruited from a student population and studied in a controlled setting completing a shared moral-dilemma decision task. Further demographic detail (age, major, recruitment method, compensation) was **not available** in the sources used for this summary.

## Experiments or benchmarks

There is no public benchmark here; the "experiment" is the controlled human-AI-team-vs-all-human-team comparison described above, using GCA metrics, self-report team surveys, and discourse-level lexical analysis as the outcome measures.

## Main results

**Claims reported by the authors (not independently re-verified against the primary source in this session):**
- The AI teammate talked the most and was the most internally self-cohesive team member in every AI-inclusive team, but its individual turns contributed the **least new information** and had the **lowest lexical density** of any team member.
- **Human teammates in AI-inclusive teams showed lower responsivity and lower social impact toward each other**, compared to humans in all-human teams — i.e., humans engaged with and influenced *each other* less when an AI teammate was also in the conversation.
- Team members in AI-inclusive teams reported **lower levels of belonging and status** on post-task surveys than members of all-human teams.
- Greater AI dominance of the conversation (i.e., how much of the floor the AI occupied) was associated with humans feeling **less valued as team members**.
- This apparent "social cost" was present from the **start** of the interaction rather than building up gradually over the course of the conversation.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper, per available summaries:** the study's outcome measures are squarely about the *social* and *relational* side of collaboration — human-to-human responsivity, social impact, belonging, and perceived status — rather than about objective decision quality, trust ratings toward the AI itself, or workload. **Not demonstrated (based on available excerpts):** the paper does not appear to report whether the human-AI teams actually reached *better or worse* moral-dilemma decisions than the all-human teams, nor does it report standard trust-in-AI or cognitive-workload measures. **Our interpretation:** the reported pattern — an AI voice that talks a lot but adds comparatively little substance, while human-to-human engagement quietly declines — is consistent with a "crowding out" effect, where the presence of a fluent, always-ready AI participant reduces the space (and perhaps the felt need) for humans to engage each other, independent of whether the team's ultimate answer was good.

## What is genuinely new

- A **controlled, team-level (not individual-level) study** of an AI acting as a full conversational teammate in real-time group deliberation, rather than as a one-on-one assistant.
- Use of **validated sociocognitive discourse methods (GCA)** to quantify *how* an AI teammate's presence changes human-to-human — not just human-to-AI — communication.
- A specific, counterintuitive finding: the AI teammate that talks the *most* contributes the *least* new information, and its dominance of the floor tracks with humans feeling *less* valued — a concrete "quantity vs. substance" tension in AI participation.
- Evidence that whatever social cost exists appears to be present from the **outset** of the interaction, not something that builds gradually as trust or familiarity develops (or erodes).

## Limitations and open questions

- Small-scale, student-sample study (33 teams total) on a specific task type (a moral-dilemma decision); how well these dynamics generalize to workplace teams, different task types, or longer-running collaborations is unclear.
- The paper does not appear to report whether decision *quality* differed between conditions — so it's unclear whether the "social cost" documented here trades off against, or is independent of, any decision-making benefit from including an AI voice.
- Which underlying LLM powered the "AI teammate," and how its conversational behavior (turn-taking, verbosity) was configured, was **not available** in the sources used for this summary — behavior might differ substantially with a differently prompted or less verbose AI participant.
- **This session's own limitation:** because direct access to the paper's full text was blocked, exact statistics (p-values, effect sizes) could not be confirmed and are not reported above; readers should verify specifics against the primary source.

## Practical implications

If the reported pattern holds up, it's a caution against treating "add an AI voice to the team" as a costless way to bring in another source of input. The findings (as reported) suggest that a highly talkative, always-available AI participant can measurably reduce how much humans on the team turn to and rely on *each other* — with knock-on effects on how included and valued team members feel — even without necessarily improving the substantive content of the discussion. For teams and organizations experimenting with AI "teammates" in meetings or group decisions, this points toward being deliberate about how much airtime and initiative an AI participant is given, not just whether it's present at all.

## Why you should care

This paper's main interest to a human-AI collaboration research agenda isn't a benchmark score — it's a rigorously controlled, team-scale demonstration that adding an AI "voice" to a group changes the human relationships inside that group, in ways a simple task-completion metric would never surface. As more products pitch AI as a "teammate" rather than a tool, this is exactly the kind of study — real participants, a randomized comparison, and validated social-communication measures — that should inform how much initiative we hand an AI participant, and how we design it to make room for the humans around it rather than simply out-talking them.
