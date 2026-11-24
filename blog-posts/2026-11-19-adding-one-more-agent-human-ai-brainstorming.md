**Paper title:** Adding One More Agent: How AI Team Size and Formation Shape Productivity and Diversity in Human-AI Brainstorming Teams
**Authors:** Rong-Ching Chang, Hao-Chuan Wang (affiliation reported as UC Davis in secondary sources; not independently confirmed from the paper itself)
**Publication date:** 2026-11-19 (arXiv v1)
**Venue:** arXiv preprint (cs.AI, cross-listed cs.CL). Peer-review status not confirmed.
**Paper link:** https://arxiv.org/abs/2611.26663
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-11-24

> **A note on sourcing:** This network environment could not directly reach arxiv.org (or mirrors such as the HTML/PDF rendering, Hugging Face, or ar5iv) to download the full paper. This summary is built entirely from the paper's abstract and multiple verbatim excerpts (method and results passages) surfaced through web search, not from a full read of the PDF. Numbers and quotes are reproduced as found; anywhere a detail could not be confirmed, that is flagged explicitly rather than guessed.

---

# When You Add a Second AI to the Brainstorm, Who Actually Does the Thinking?

## The problem the paper addresses

Lots of research has shown that giving one person a generative-AI partner can boost how many ideas they produce in a brainstorm. But real teams are not always one human plus one AI — workplaces are increasingly experimenting with *several* AI "teammates" in the same room. The paper asks a question that sounds simple but had not been carefully tested: if one AI partner helps, does a *second* one help even more, or does it start to crowd out the humans instead?

## Why this problem matters

As AI note-takers, drafting bots, and "AI teammates" get added to meetings and workshops, teams are making real decisions about how many AI participants to invite and how those AI participants should behave. If two AI partners simply double the benefit of one, adding more AI to a session is an easy win. If instead a second AI partner changes the *group dynamic* — for example, by crowding out what humans actually contribute — then "more AI" is not automatically better, and team design (how many AI teammates, and how they're configured) becomes its own design problem, separate from the now-familiar one-human-one-AI case.

## What makes the system agentic

The AI "partners" in this study are not single-turn chatbots answering one prompt. Based on the available excerpts, they:
- take part in an ongoing, multi-turn, shared brainstorming session alongside human teammates, rather than producing one isolated response;
- autonomously decide, turn by turn, whether and what to contribute to a shared idea board (the study describes a turn policy in which each AI partner could contribute at most one message per human turn, implying the AI decides when to act within that budget);
- are configured ahead of time along a "behavioral formation" dimension — calibrated to average human brainstorming behavior, or customized to a specific participant — which shapes how they act over the course of the session, not just what they say once;
- are evaluated at the level of the team's collective, multi-turn output (board composition, authorship share, idea diversity) rather than being graded on a single response.

This is a lighter-weight form of agentic behavior than a tool-using coding or research agent: there is no external tool/API use described in the available excerpts, and the "action" is limited to deciding when and what to post into a shared digital environment. It still satisfies the task's working definition at a basic level — an LLM-centered system pursuing a goal (contributing ideas) through repeated, autonomous turns in a multi-party environment, evaluated as a team member rather than as a single-shot text generator. Readers who need classic multi-step tool use (API calls, code execution, external environments) should treat this as a borderline case on the lighter end of "agentic."

## How humans and the AI agent collaborate

Human participants and one or two AI partners share a live brainstorming session and a shared digital idea board. Everyone — human and AI — can post ideas to the board during the session; the paper's figures (more items reaching the board, AI's rising share of authorship) are all about how this shared posting activity splits between humans and AI as team composition changes.

## What role the human plays

Humans are full participants in the brainstorm: they converse, generate ideas, and choose whether to turn those ideas into posts on the shared board. The paper's central behavioral finding is about *this* choice — the study reports that humans "kept talking" (i.e., continued to participate in discussion) but converted fewer of their ideas into actual board posts as more AI partners were added, meaning the human's authorship behavior, not just their conversational presence, is the outcome of interest.

## What role the AI agent plays

Each AI partner's role is to generate and post ideas to the shared board within the one-message-per-human-turn budget, following whichever "behavioral formation" it was assigned (calibrated to average human behavior, or customized to the participant it's paired with). With two AI partners instead of one, the AI side of the room produces a larger fraction of all posted ideas — reportedly rising from roughly half of board authorship with one AI partner to roughly three-quarters with two.

## How control, initiative, and decisions are shared

No one is explicitly "in charge": both humans and AI partners can take initiative and post to the board at any point (subject to the AI's turn budget), making this a mixed-initiative setting rather than one where a human gates or approves AI contributions. What the paper manipulates is the *composition* of that mixed-initiative team — one AI partner vs. two, and how those AI partners are configured — and then observes how the balance of initiative between humans and AI shifts as a result, without any single party being handed formal control.

## The paper's main idea

The authors' central claim is that findings about single-AI-partner brainstorming do not simply scale up when a second AI partner is added. Specifically: a lone AI partner's contribution to the team's total output is comparable to a lone human's, so going from zero to one AI partner looks like a fairly linear productivity gain. But the *group-level* jump in total output comes specifically from adding a *second* AI partner — and that gain is not a clean "more of the same," because it coincides with a substantial drop in how much humans personally author, even though humans keep participating in conversation.

## How the approach works

The study uses a controlled experiment that crosses two design variables: (1) the number of AI partners in the team (one vs. two), and (2) how those AI partners are "formed" — calibrated to represent average human brainstorming behavior, versus customized based on the individual participant they are paired with. These AI-team conditions are compared against a human-human dyad baseline (no AI). All teams work through a live, shared brainstorming session using a common digital idea board, and the researchers measure both how many ideas land on the board and who (human or AI) is credited with authoring each one, as well as how varied/diverse the human-authored ideas are.

## Human study or evaluation design

This is a study with real human participants in real (if researcher-run) team sessions, not a simulated-user or LLM-as-judge evaluation. According to the available excerpts, 168 participants (N=168) took part, assigned across the human-human baseline and the one-AI-partner and two-AI-partner conditions (with the "calibrated" vs. "customized" formation varied within the AI conditions). Per-condition sample sizes, recruitment platform, and demographic details were not available in the sources used for this summary and should be checked directly in the paper.

## Participants and study setting

168 participants took part in a brainstorming-team experiment, with human-human pairs serving as the no-AI reference condition. The task context (what participants were asked to brainstorm about), session length, and exact recruitment method could not be confirmed from the excerpts available to this write-up.

## Experiments or benchmarks

This is a single original experiment rather than a reuse of an existing benchmark: a brainstorming task performed by teams under the human-human, one-AI-partner, and two-AI-partner conditions, each crossed with the AI's "calibrated" vs. "customized" behavioral formation.

## Main results

Based on the available excerpts:
- A single AI partner's contribution roughly matched a single human's total board output (reported effect size d = +0.37, p = .064 — a marginal, not clearly significant, difference).
- Two-AI-partner rooms produced more total board items than one-AI-partner rooms (reported as 55.8 vs. 41.8 items).
- The AI side's share of total board authorship rose from roughly half (one AI partner) to roughly three-quarters (two AI partners).
- Human-authored idea *volume* dropped substantially when a second AI partner was present, even though humans continued to participate in the session's conversation — i.e., talking did not translate into posting at the same rate.
- The "formation" manipulation (calibrated vs. customized AI behavior) shaped human authorship when there was one AI partner, but the authors report this effect "vanished" once a second AI partner was added.
- A supplementary regression reported in the paper's appendix found that the AI's own share of generated content was not a statistically significant predictor of how many ideas humans authored (R² = .315; coefficient p = .319) — suggesting the human authorship drop is not simply explained by "the AI posted more, so humans posted less" in a direct mechanical sense.
- AI presence appears associated with greater overall diversity of human-authored ideas, but the excerpts suggest that only the two-AI condition increased diversity *within* a given session (as opposed to diversity only showing up when pooling across sessions) — this nuance is reported secondhand and should be verified against the paper's own definitions.

## Effects on human performance, trust, workload, safety, or decision quality

- **Human contribution/performance:** The clearest, best-supported effect in the available excerpts is on human *authorship volume*: adding a second AI partner is associated with humans producing substantially fewer of their own ideas on the shared board, even as total conversational participation continues and total group output rises.
- **Diversity of human output:** The presence of AI partners is reported to relate to greater diversity in the ideas humans do author, with a possible added effect specific to having two AI partners rather than one — though the exact mechanism and statistical strength of this claim could not be confirmed from the excerpts available.
- **Trust, workload, safety:** No findings on trust, perceived workload, or safety were found in the excerpts available to this summary; if the paper reports these, they were not surfaced by the searches used here and should be checked directly in the source.
- These are the authors' own reported findings, as reconstructed from search excerpts; this write-up has not independently verified the statistics beyond what is quoted above.

## What is genuinely new

As the authors frame it, the contribution is showing that results from one-human-one-AI brainstorming research do not simply extrapolate to teams with multiple AI partners: the step from one to two AI partners is where the team-level productivity jump appears, but it is also where human authorship drops and where the "formation" (calibration vs. customization) manipulation stops mattering. That is a genuinely new empirical wrinkle — it separates "AI team size" from "AI configuration" as two independent levers and shows they interact in a non-obvious way.

## Limitations and open questions

- This is a fresh arXiv preprint (posted 19 Nov 2026 per the arXiv listing); peer-review status is not confirmed, and figures should be treated as provisional pending the full statistical appendix.
- Several headline comparisons reported in secondary excerpts, including the key one-AI-vs-human effect (d = +0.37, p = .064), are not clearly statistically significant at conventional thresholds — "roughly matched" is this write-up's paraphrase of a marginal result, not a confirmed equivalence.
- The task domain, session length, exact recruitment method, demographic breakdown, and per-condition sample sizes could not be confirmed from the sources used and should be checked in the paper directly.
- No model name (e.g., which specific LLM powers the "AI partners") was found in the available excerpts; this write-up cannot confirm which underlying model was used, only that the system is described as generative/AI-partner-based in a manner consistent with LLM-based agents in this research area.
- No trust, workload, or safety measures were found in available excerpts, so this paper's contribution should be read as being about productivity and authorship/diversity outcomes specifically, not the fuller set of human-centered outcomes (trust, cognitive load) that other papers in this collection measure directly.
- The full PDF could not be retrieved in this environment; numbers and interpretations above should be checked against the original paper before being cited elsewhere.

## Practical implications

For anyone designing tools or workshops that mix multiple AI "participants" with human teammates — AI co-ideation tools, multi-bot meeting assistants, group-creativity software — this paper's reported findings caution against assuming that adding more AI teammates is a simple multiplier on team output. The reported results suggest it's worth explicitly tracking *who authors what* (not just how much total content a session produces), since a rising group total can mask a shrinking human contribution. It also suggests that tuning an individual AI partner's behavior to the specific human it's paired with may matter less once there's more than one AI in the room — a design nuance worth testing before investing heavily in per-user AI personalization in multi-AI team settings.

## Why you should care

This paper sits right at the center of a question a lot of teams are about to face in practice: not "should I add an AI assistant," which is now a familiar decision, but "how many, and configured how." Its value for human-AI collaboration research is that it treats *team composition* itself as an experimental variable, and it reports a genuinely counter-intuitive result — that a second AI partner's extra output can come, in part, at the expense of how much humans contribute, even while everyone keeps talking. That is exactly the kind of finding that should give pause to anyone who assumes more AI participation is automatically a free win for a human team's own creative output.

---

*Disclaimer: This summary distinguishes, where possible, between the authors' own stated claims, the specific quantitative results found in available excerpts, and this write-up's own interpretation (clearly marked above, e.g. in "What makes the system agentic" and "Practical implications"). Because the full PDF could not be retrieved directly in this environment, readers who want to cite exact statistics, task details, or the full limitations section should consult the original paper at the link above.*
