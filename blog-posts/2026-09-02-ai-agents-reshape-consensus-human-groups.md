# AI Agents Reshape Consensus Formation in Human Groups

**Authors:** Lin Chen, Ziyi Liu, Xia Hu, Yong Li (author affiliations not independently confirmed from sources used)
**Publication date:** 2026-09-02 (arXiv id 2609.02122, v1; categories cs.CL / cs.CY / cs.SI)
**Venue:** arXiv preprint (not yet confirmed as peer-reviewed)
**Paper link:** https://arxiv.org/abs/2609.02122
**Code link:** Not available (no code repository could be found or verified)
**Project page:** Not available (no project page could be found or verified)
**Date added:** 2026-09-06

> **A note on sourcing:** arXiv (and every other candidate domain, including alphaXiv, Hugging Face Papers, and news sites reporting on this work) was unreachable from this research session's network — the fetch tool is blocked network-wide in this environment. This summary is therefore built entirely from web-search-grounded excerpts of the paper's abstract and reported findings, cross-checked across multiple independent search results, rather than a direct PDF read. Facts below reflect what those excerpts report; anything not confirmed is marked "Not available," and interpretive statements are labeled as such. Readers should verify details against the arXiv page directly before citing this paper.
>
> **A note on a similarly-named paper:** a separate, unrelated paper — "AI agents can coordinate via majority-following beyond human scale" by Giordano De Marzo and colleagues (Science Advances) — covers AI-only agent coordination with no human participants. It is a different study from the one summarized here and is not the subject of this post.

---

## The problem the paper addresses

Online communities, collaborative platforms, and shared workspaces increasingly mix real people with LLM-based agents that post, comment, label, or describe things alongside humans. When a group needs to agree on a shared label, term, or way of describing something — a "consensus" — nobody has had a clear picture of what happens when some fraction of the group's "participants" are actually AI. Do groups still converge on a shared understanding? Does it matter whether people know who's an AI? And whose way of describing things wins — the humans' or the agents'? This paper sets out to answer those questions directly.

## Why this problem matters

Consensus — a shared vocabulary, a shared understanding of a norm, a shared label for something ambiguous — is the glue that lets groups coordinate at all, from Wikipedia edit wars to product-review tag systems to community moderation guidelines. As AI agents move from being tools people consult to being active participants that talk, label, and negotiate meaning alongside humans, the ordinary process by which human groups hash out shared understanding could be quietly reshaped — not because anyone decided it should be, but as a side effect of who else is in the room. Understanding whether AI presence helps, disrupts, or takes over that process has real stakes for how platforms design and disclose AI participation in group settings.

## What makes the system agentic

The LLM agents in this study are not passive text generators answering isolated prompts. They are repeatedly paired with different partners (sometimes human, sometimes AI) across many rounds of a shared task, and in each round they must produce a description, observe how a partner responds, and adjust their subsequent choices based on the accumulated history of the group's evolving conventions. That is: they pursue a persistent goal (arrive at mutually understood descriptions), make repeated, path-dependent decisions across an extended interaction, and are evaluated on their behavior as participants in an ongoing social process — coordinating with other agents (both human and artificial) — rather than being scored as a one-shot language model on a single response.

## How humans and the AI agent collaborate

Humans and AI agents are placed into the same population and repeatedly and randomly paired off, each pairing playing a round of a "description game": one member describes a target, the other tries to identify or label it from that description, and over many repeated rounds across the group, a shared convention for how to describe things emerges — or fails to. Both humans and agents are simultaneously and interchangeably senders and receivers, and the group's convention is a genuinely joint outcome, built from a mix of human and agent contributions, rather than something the agent alone produces or the human alone directs.

## What role the human plays

Human participants take part directly in the description game exactly as the AI agents do — describing targets to a partner and interpreting partners' descriptions — across repeated rounds, without knowing in advance whether any given partner is human or AI. Their accumulated behavior (which expressions they adopt, resist, or gradually accept from partners) is the primary object of study.

## What role the AI agent plays

The AI agents play the same game as the humans: producing and receiving descriptions, and — the paper reports — settling into relatively stable expression choices across rounds, more so than the human participants. Because agents share a common "linguistic prior" (drawn from similar training), agent-produced expressions tend to cluster near one another, which the paper identifies as a mechanism by which agents interoperate with one another even before directly coordinating with humans.

## How control, initiative, and decisions are shared

No single side dictates the outcome. Consensus is an emergent, bottom-up property of many repeated pairwise exchanges rather than a decision handed down by either humans or agents; both sides can adopt, resist, or ignore the other's proposed expressions round to round. The paper's central manipulation is the *proportion* of agents in the population — a structural lever on how much collective initiative agents versus humans end up exercising over the emergent outcome, rather than either side being explicitly "in charge."

## The paper's main idea

**Claim by the authors:** as LLM agents shift from being tools that humans consult to being participants embedded within human groups, their mere presence — and in particular, what fraction of the group they make up — measurably reshapes how (and whether, and toward what) the group reaches consensus, and does so in ways that go beyond just adding "more voices" to the room.

## How the approach works

**Demonstrated in the paper:** the authors ran a controlled "description game" experiment in which humans and LLM agents were mixed into a shared population at varying agent proportions and repeatedly, randomly paired off to play rounds of the game. By systematically varying the proportion of agents in the group, the authors could trace how the group's collective convergence behavior and the content of the resulting shared convention changed as a function of that one variable.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled experiment directly comparing group consensus dynamics across different human-to-agent ratios in the same description-game task, allowing a like-for-like comparison of low-, medium-, and high-agent-proportion conditions.

## Participants and study setting

**Demonstrated in the paper:** real human participants were mixed with LLM agents in repeated, randomized pairwise interactions within a collaborative description game. **Not available:** the exact number of human participants, their recruitment method or platform, and their demographics were not confirmed from the sources used for this summary.

## Experiments or benchmarks

There is no public benchmark or dataset involved; the "experiment" is the description game itself, run under multiple experimentally varied agent-proportion conditions, with the resulting group conventions analyzed for convergence strength and content.

## Main results

**Demonstrated in the paper (as reported in available excerpts):**
- Three distinct regimes emerged as the agent proportion increased: **low** agent proportions still allowed **human-led consensus** to form largely as it would among humans alone; **intermediate** agent proportions actively **disrupted convergence**, making it harder for the group to settle on a shared convention at all; and **high** agent proportions **restored strong consensus**, but shifted its content toward **agent-led conventions**.
- The content of the resulting consensus differed by who led it: human-led consensus tended to be **concrete, information-dense, and grounded in real-world analogies**, while agent-led consensus was **more abstract and sparser**.
- Mechanistically, agents' shared linguistic prior placed their expressions near one another in "expression space," and agents' choices were more stable round-to-round than humans', giving agents an outsized, disproportionate pull on where the group's convention eventually settled.
- Humans showed a trust-related dynamic: they **initially resisted** adopting expressions from partners they perceived as AI, but **gradually yielded** to conformity pressure as rounds progressed.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper (as reported in available excerpts):** human participants' willingness to adopt an AI partner's proposed way of describing something was not fixed — it began as resistance and shifted toward conformity over repeated exposure, indicating that perceived AI identity measurably affected human uptake behavior (a trust/reliance-adjacent outcome), and that the composition of the group (agent proportion) changed both whether the group reached agreement and the character of what was agreed upon. **Not available:** the paper's excerpts used here did not report standardized trust-scale scores, workload measures, or task-completion-time comparisons. **Our interpretation:** this is best read as evidence about collective decision-quality and human conformity dynamics in mixed human-AI groups, not as a study of individual task performance, safety, or workload in the way those terms are used in HCI usability studies.

## What is genuinely new

- A **direct, controlled manipulation of agent proportion** within human groups performing a shared consensus task — most prior human-AI collaboration work studies one human paired with one (or a fixed team of) agents, rather than agents as a variable fraction of an emergent social process.
- Identification of **three distinct qualitative regimes** (human-led, disrupted, agent-led) as a function of a single structural variable, rather than a simple "more AI is better/worse" finding.
- A concrete mechanistic account — shared linguistic priors plus higher expression stability — for *why* agents exert disproportionate pull on group outcomes once their share of the population is high enough.
- Empirical evidence of an initial-resistance-then-conformity trust dynamic toward perceived-AI partners, observed within a live, repeated collaborative task rather than a one-off survey question.

## Limitations and open questions

- Exact participant counts, recruitment details, and demographics were not available from the sources used for this summary — readers should check the paper directly.
- The task (a description/labeling game) is a simplified, abstracted proxy for real-world consensus processes (e.g., moderation norms, community guidelines, terminology standards); how well the three-regime finding generalizes to richer, higher-stakes group decisions is an open question the paper itself likely flags but that could not be confirmed here.
- It is not clear from available excerpts whether participants were told the true proportion of agents in their group in advance, which would materially affect the resistance-then-conformity finding.
- No code or data repository could be found or verified, limiting independent reproducibility checks at this time.

## Practical implications

For platforms and tools that mix human and AI contributors in shared spaces — comment threads, collaborative tagging, community wikis, multi-agent customer-support queues — this paper's regime structure is a concrete design signal: the proportion of AI participants in a group is not a neutral scaling knob. A little AI presence may leave human-led norms largely intact; a moderate amount may actively make it harder for the group to agree on anything; and a lot may produce strong agreement, but on the AI's terms rather than the humans'. That argues for treating agent proportion and its disclosure to participants as first-class design variables in any system where AI agents and humans jointly shape shared outcomes.

## Why you should care

This is a rare empirical, controlled study of what actually happens to a *group's* collective decision-making — not just one human's experience of one AI assistant — when AI agents are embedded as full participants rather than as tools on the side. If you build, moderate, or study any space where AI-generated contributions sit alongside human ones and the group is expected to converge on something, this paper's regime findings and its trust-resistance-then-conformity result are directly relevant to how you should think about disclosure, composition, and the risk of AI agents quietly steering group outcomes in ways participants may not notice or intend.
