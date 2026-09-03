# Designing Proactive Thought Partners for Writing

**Authors:** Chao Zhang, Abe Davis, Chih-Wei Chen, Chin-Chia Hsu (Cornell University; Chih-Wei Chen and Chin-Chia Hsu affiliation as reported in web summaries: Google DeepMind — not independently confirmed from the paper itself)
**Publication date:** 2026-09-01 (arXiv id 2609.01588, v1, cs.HC / cs.AI / cs.CL)
**Venue:** arXiv preprint (not yet confirmed as peer-reviewed; a CHI submission is plausible given the authors' HCI focus and Cornell's regular CHI presence, but this could not be verified)
**Paper link:** https://arxiv.org/abs/2609.01588
**Code link:** Not available (no code repository could be found or verified)
**Project page:** Not available (no project page could be found or verified)
**Date added:** 2026-09-03

> **A note on sourcing:** arXiv itself was unreachable from this research session's network (the fetch tool is blocked for that domain), so this summary is built from web-search-grounded excerpts of the paper's abstract and reported findings rather than a direct PDF read. Facts below reflect what those excerpts report; anything not confirmed is marked "not available," and interpretive statements are labeled as such.

---

## The problem the paper addresses

When you're writing something — an essay, a report, a story — the kind of help you need keeps changing. Sometimes you're stuck for an idea. Sometimes you've gone down a tangent and need someone to point it out. Sometimes you just want quiet. Most AI writing tools, the paper argues, don't track any of that: they mainly offer the same kind of help all the time, usually autocomplete-style text suggestions, regardless of what's actually happening in your head as you write. The paper's target problem is designing AI "partners" that instead offer **higher-level cognitive support** — help with thinking, not just typing — and that decide **for themselves, proactively**, when and how to step in.

## Why this problem matters

A tool that only helps when explicitly asked is limited by how well a writer can articulate what they need in the moment — often the hardest thing to do while you're stuck. But a tool that interrupts too often, or at the wrong moments, becomes an annoyance rather than a help. Getting proactive AI assistance right in writing is a specific, well-studied case of a much broader problem in human-AI collaboration: how does an AI system judge when it should take initiative rather than wait to be asked, without either nagging the human or staying silent when it should speak up?

## What makes the system agentic

The "thought partners" in this paper are not passive suggestion boxes. Each partner is configured with a **role** (what kind of support it offers, e.g., generating ideas or flagging when the writer has drifted off-topic) and a **proactivity setting** (how and when it should intervene). As the person writes, the system continuously monitors the evolving document, decides — on its own, without being asked each time — when a configured partner's moment has come, and then surfaces a suggestion tailored to that moment. This is decision-making sustained over an extended writing session (participants used it for a full week), not a single request-and-response exchange, which is what makes it agent-like rather than a simple assistive feature.

## How humans and the AI agent collaborate

Collaboration here is explicitly **mixed-initiative**: the human sets up the collaboration in advance by creating and configuring partners (deciding what kind of help they want available and how eagerly it should appear), and from then on the AI agent decides, moment to moment, when to actually act on that standing permission. The human can also read, use, ignore, or dismiss any given suggestion. Control isn't handed entirely to either side — the person defines the boundaries of what kind of help is welcome, and the agent exercises judgment inside those boundaries about timing.

## What role the human plays

Participants configured their own thought partners — choosing roles and proactivity levels — before and during their writing, then wrote real documents over the course of a week while partners intervened. Reported findings indicate that participants used partners' suggestions for two different purposes: generating new ideas, and self-monitoring (checking their own writing against their goals or plan).

## What role the AI agent plays

The AI agent (each configured "thought partner") watches the writing as it develops and proactively initiates contact — offering suggestions at moments it judges appropriate, based on the role and proactivity settings the writer gave it — rather than waiting for the writer to ask.

## How control, initiative, and decisions are shared

Initiative is explicitly split and configurable: the writer decides, upfront, how much initiative to hand to each partner (the proactivity setting), and the agent then exercises that granted initiative autonomously during the actual writing. This is a direct, deployed instance of "mixed-initiative interaction" as a design variable rather than a fixed property of the tool — the paper studies how people actually tune that dial in practice.

## The paper's main idea

**Claim by the authors:** generic, one-size-fits-all proactive assistance (like autocomplete) misses the fact that writers' cognitive needs vary by person and by moment, and that a better design lets writers configure multiple different "thought partners," each with its own role and its own proactivity level, so the mix of support available can match the messiness of the writing process itself.

## How the approach works

**Demonstrated in the paper:** the authors built a technology probe — a working prototype, not just a mockup — that lets a user create one or more thought partners, assign each a role and a proactivity setting, and then write with them active in the background. As the document evolves, the system evaluates when a partner should step in and surfaces its suggestion inline; participants also reportedly valued **lightweight visual representations** of the partners and suggestions framed in a **non-directive rhetorical style** (offered as a nudge rather than an instruction).

## Human study or evaluation design

**Demonstrated in the paper:** a field deployment using the technology probe, run with real participants over a full week of their own writing, rather than a short lab session on a fixed task. This is a qualitative-leaning, design-research style study aimed at understanding how people actually configure and use proactive support over realistic writing work, not a large-scale controlled experiment with a quantitative outcome metric.

## Participants and study setting

**Demonstrated in the paper:** 16 participants used the probe for one week each, writing their own real documents (rather than an artificial prompt-writing task) in their normal writing context. Beyond the participant count and duration, further demographic or professional detail about the participants was not available from the excerpts used for this summary — marked "Not available" rather than inferred.

## Experiments or benchmarks

There is no benchmark or automated evaluation component reported; the evaluation is the one-week, 16-participant field deployment itself, evidently analyzed through participants' configuration choices, usage patterns, and (typically for this kind of study) follow-up interviews — though the interview protocol itself was not confirmed from available excerpts.

## Main results

**Demonstrated in the paper (as reported in available excerpts):**
- Participants configured proactive support through **prospective planning** — that is, deciding in advance what kind of help they wanted and when, rather than only reacting to partners' behavior after the fact.
- Suggestions were used for two distinct purposes: **idea generation** (helping writers get unstuck or generate new material) and **self-monitoring** (helping writers check their own progress or focus against their intentions).
- Participants valued **lightweight visual representations** of active partners and suggestions, and preferred a **non-directive rhetorical framing** — phrasing that reads as an offer or a nudge rather than a command.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper (based on available excerpts):** the reported findings are about *how* participants used and experienced proactive support (configuration behavior, the two use-cases above, and design preferences for visuals and phrasing), rather than a quantitative measure of writing quality, output speed, trust scores, or workload. **Not demonstrated in the paper (based on available excerpts):** no controlled comparison against a non-proactive or autocomplete-only baseline, and no numeric trust, workload, or performance metrics were found in the sources used for this summary. **Our interpretation:** this reads as a design-research contribution (understanding how people want to configure and receive proactive help) rather than an effectiveness trial establishing that thought partners make people write better or faster — a distinction worth keeping in mind before treating the findings as evidence of a performance gain.

## What is genuinely new

- Treating **proactivity itself as a configurable, multi-dimensional design parameter** (role + proactivity level, potentially multiple partners at once) rather than a single fixed on/off behavior baked into the tool.
- A real, week-long field deployment of a working proactive multi-partner system with real writers doing their own writing, rather than a short lab task — a comparatively strong ecological-validity choice for this kind of HCI study.
- Empirical identification of two distinct ways writers actually use proactive suggestions in practice (idea generation vs. self-monitoring), plus concrete design preferences (lightweight visuals, non-directive phrasing) that could inform future proactive-AI writing tools.

## Limitations and open questions

- Sixteen participants over one week is a modest, design-research-scale sample; the paper does not appear to report a controlled quantitative comparison against a non-proactive baseline, so claims about benefit over existing tools should be treated as directional rather than statistically established.
- No quantitative human-outcome metrics (trust, workload, writing quality, time-on-task) were found in the sources used for this summary — it's not clear from available excerpts whether or how these were measured.
- Details on participant demographics, writing domains/genres, and the precise proactivity-configuration interface were not available from the excerpts used here.
- Code and project page availability could not be confirmed.

## Practical implications

For anyone building AI writing tools — or, more broadly, any proactive AI assistant — the paper suggests a concrete design move: let users configure *what kind* of help an agent should offer and *how eagerly*, rather than shipping one fixed proactivity behavior for everyone. The reported preference for non-directive phrasing and lightweight visual cues is a specific, actionable UI takeaway for anyone designing agents that interrupt human work.

## Why you should care

This paper is a timely, real-world-grounded (16 real writers, a full week each) look at mixed-initiative interaction in practice — an area many agentic-AI systems gesture at but few actually deploy and study over realistic timeframes. It's a useful counterpoint to benchmark-driven agent papers: the central question here isn't "how capable is the agent," but "how should an agent decide when to speak up," which is a core open problem for any AI system meant to work alongside a human rather than in place of one.
