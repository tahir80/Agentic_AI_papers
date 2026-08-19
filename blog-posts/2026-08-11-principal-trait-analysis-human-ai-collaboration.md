# What Makes Someone Good at Working With an AI Agent? A New Method Tries to Measure It

**Authors:** Hunter McNichols, Kai Du, Andrew Lan (University of Massachusetts Amherst)
**Publication date:** 2026-08-11 (arXiv v1)
**Venue:** arXiv preprint, cs.CL (peer-reviewed venue not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2608.11460
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-19

> **A note on sourcing:** this session's outbound network access to arxiv.org and several mirror/aggregator sites (Hugging Face, Semantic Scholar, r.jina.ai) returned a blocked connection for direct fetches (organization egress policy, not a paywall — the paper is a public arXiv preprint). This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported findings, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

Two people can use the exact same AI coding assistant or AI tutor and get very different results — one gets fast, reliable help; another gets confused, generic, or wrong answers. Everyone has a hunch about why: some people are "better at prompting," or "more skilled at working with AI." But that intuition has mostly stayed a hunch. This paper asks a more precise question: can you actually *measure*, from the transcripts of real human-AI conversations, the specific behavioral patterns — the paper calls them "traits" — that separate collaborators who get good outcomes from those who don't?

## Why this problem matters

As LLM-powered agents move from novelty into everyday tools for coding, tutoring, and other knowledge work, the gap between people who use them well and people who don't is becoming a real, practical problem — for hiring, for training, and for designing the tools themselves. If we can't name what "good at collaborating with AI" actually consists of, we can't teach it, hire for it, or build agents that adapt to people who lack it. This paper is a step toward turning a vague soft skill into something measurable and, potentially, teachable.

## What makes the system agentic

The paper itself does not introduce a new AI agent — instead, it studies two *existing* real-world settings where an LLM-based agent is already doing agentic work with a human partner. In the professional setting (drawn from the SWE-chat dataset), the "collaborator" is an AI coding agent that plans and executes multi-step work inside real software repositories: reading code, writing and editing files, and calling tools, with reported findings that in about 40% of real sessions the agent writes essentially all of the code in the session, largely without pausing to check in with the human first. In the educational setting (drawn from the StudyChat dataset), the AI is a tutoring agent embedded in a university programming/AI course, sustaining multi-turn tutoring dialogues around student assignments rather than answering one question at a time. Both are agentic in the sense this digest cares about: goal-directed, multi-step, evaluated on real task outcomes — not just single text replies.

## How humans and the AI agent collaborate

In both underlying datasets, real people — professional developers in real repositories, and real university students in a real course — interact conversationally and iteratively with their respective AI agent to get a task done (ship a code change, understand and complete an assignment). The paper's own contribution sits one level up: it mines these real collaboration transcripts to extract recurring behavioral patterns ("traits") in how different humans steer, prompt, correct, and rely on their AI partner, and tests whether those patterns predict who ends up with better outcomes.

## What role the human plays

The human is the one being characterized. Their turns in the conversation — how they phrase requests, how much detail they provide, whether and how they push back on the agent's output, how much of the task they delegate outright versus stay hands-on for — are the raw material the method analyzes. Notably, in the professional coding dataset, prior reporting on SWE-chat found users push back on the agent's output in roughly 39% of sessions, one of many behavioral signals this kind of analysis can draw on.

## What role the AI agent plays

The AI agent is the task-performing partner: writing code, proposing tutoring explanations, executing multi-step work toward the shared goal. In this paper, the agent's own internal behavior is not the object of study — its outputs and the resulting task success are the yardstick against which human "traits" are scored.

## How control, initiative, and decisions are shared

Within the underlying sessions themselves, initiative appears to lean heavily toward the agent in the professional setting (agents in SWE-chat reportedly write essentially all of the code in a large share of sessions without proactively checking in), with the human's main lever being how much they delegate, how they prompt, and whether they intervene afterward. The paper's own analytical layer doesn't change that division of labor — it measures it, treating "how much a person steers vs. delegates vs. corrects" as exactly the kind of trait that might explain outcomes.

## The paper's main idea

**Claim by the authors:** effective human-AI collaboration is not one-size-fits-all — different people succeed by using systematically different behavioral strategies — and these strategies can be surfaced automatically, without predefined categories, directly from conversation transcripts using a method the authors call Principal Trait Analysis (PTA).

## How the approach works

PTA is described as a PCA-inspired (Principal Component Analysis-inspired) pipeline, but instead of decomposing numerical data, it operates on conversation transcripts through several unsupervised stages: it uses an LLM to extract observations about collaborator behavior from raw conversations, groups similar observations via text-embedding clustering into interpretable "trait" dimensions, scores every human collaborator along each derived trait, and then identifies which traits are most distinguishing across the population. The result is a small set of human-interpretable axes (e.g., patterns of specificity, delegation, or corrective behavior) along which any given collaborator's usage style can be scored — derived bottom-up from real data rather than defined in advance by the researchers.

## Human study or evaluation design

This is **not a controlled lab experiment** with recruited participants and randomized conditions. It is a **retrospective, data-driven analysis** of two existing real-world conversation corpora, applying the new PTA method to see whether the traits it derives are (a) statistically significant in explaining collaborator behavior and (b) predictive of task outcomes.

## Participants and study setting

**Demonstrated in the paper:** two real-world datasets, not simulated ones. (1) **StudyChat** — 1,540 real tutoring conversations from 171 real university students across two semesters of a programming-focused AI course, interacting with an LLM tutor. (2) **SWE-Chat** — real professional developers' interaction sessions with AI coding agents working on real software repositories (reported elsewhere as roughly 6,000 sessions, 63,000+ user prompts, and 355,000+ agent tool calls). Both are genuine human-generated interaction logs, not researcher-simulated dialogues.

## Experiments or benchmarks

There is no single public leaderboard benchmark here; the "experiment" is applying PTA independently to each of the two datasets and checking (1) whether the derived traits meaningfully separate collaborators' behavior and (2) whether trait scores correlate with, or help predict, task success in each setting, plus a comparison of whether traits found in one setting (e.g., coding) transfer to the other (e.g., tutoring).

## Main results

**Reported by the authors, per available sources:** PTA-derived traits were statistically significant in explaining collaborator behavior in both the professional coding and educational tutoring settings, and trait scores helped predict task outcomes in each. The analysis also reportedly surfaced both traits shared across the two very different settings and traits that were setting-specific — suggesting some behavioral patterns generalize across coding and tutoring, while others are unique to each domain. Exact statistical figures (e.g., effect sizes, correlation coefficients) could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

This paper does not run an intervention or measure how *changing* a collaborator's behavior would affect their outcomes — its contribution is diagnostic, not prescriptive. The demonstrated result is correlational: certain measurable behavioral traits are associated with, and can help predict, better human-AI collaboration outcomes in real settings. The authors themselves flag an important open question — **whether these traits are stable, teachable "skills" or just situational patterns remains unresolved**, since the paper's own reported results on generalizability across settings, and on how traits change over time for the same person, were inconclusive.

## What is genuinely new

- A **fully data-driven, bottom-up method** (PTA) for deriving human-collaboration "traits" directly from real conversation transcripts, rather than starting from a researcher-defined taxonomy of good/bad prompting behavior.
- **Cross-domain validation** on two genuinely different, real-world human-AI collaboration settings (professional software engineering and university-level tutoring) using real participant data in both.
- An explicit attempt to connect **measurable interaction behavior to task outcomes**, opening a path toward diagnosing (and potentially training) effective human-AI collaboration skills rather than treating them as an unmeasured soft skill.

## Limitations and open questions

- **Not a controlled study:** the paper analyzes existing conversation logs rather than running a designed experiment with randomization or intervention, so causal claims ("trait X causes better outcomes") are not established — only association/predictive power.
- **Unclear stability and teachability:** the authors themselves report inconclusive findings on whether derived traits generalize across settings and how they evolve over time for a given person — meaning it is not yet established whether these are stable "skills" at all.
- **Two datasets, two domains:** while cross-domain validation is a strength, both settings involve text-based coding/tutoring tasks; it's unconfirmed whether the method extends to very different agentic domains (e.g., physical/embodied agents, multi-agent oversight).
- **Peer-review status:** as of this writing, this appears to be an arXiv preprint with no confirmed peer-reviewed venue.
- Precise quantitative results (effect sizes, exact trait definitions, full statistical tests) could not be independently verified since the full paper could not be fetched directly in this session; readers who need precise details should consult the arXiv preprint directly.

## Practical implications

If traits like these do turn out to be stable and teachable, the practical payoff is significant: organizations could screen for or train "AI collaboration skill" much like any other workplace competency, and agent designers could use trait scores to adapt an agent's behavior — offering more scaffolding to a low-trait user, or more autonomy to a high-trait one — rather than treating every human partner identically. Educators could also use trait feedback to help students develop better AI-collaboration habits during coursework, which is directly relevant given one of the two datasets is itself drawn from a real classroom.

## Why you should care

Most human-AI collaboration research either builds a new agent or runs a one-off user study. This paper does something different and complementary: it turns already-happening, real-world human-agent collaboration into a measurement problem, asking not "does this agent work?" but "what do the *humans* who get good results out of it actually do differently?" That question — and a genuinely data-driven, non-simulated attempt to answer it across two very different real-world domains — is exactly the kind of foundational work that could eventually inform how agentic tools adapt to the humans using them, even though the authors are careful to say the "skills" framing is still an open question rather than a settled finding.
