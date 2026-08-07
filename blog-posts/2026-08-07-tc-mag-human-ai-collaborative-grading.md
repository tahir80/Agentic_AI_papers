# Smarter Together: Would You Let an AI Grading Team Mark Your Students' Homework?

**Authors:** Sanskriti Uma (Geniebook), Surjya Ghosh (BITS Pilani, K K Birla Goa Campus), Dio Dzaky Achmad Mustaqim (Geniebook)
**Publication date:** Presented at ACM IUI '26, March 23–26, 2026, Paphos, Cyprus (pages 106–133)
**Venue:** Proceedings of the 31st ACM International Conference on Intelligent User Interfaces (IUI '26)
**Paper link:** https://dl.acm.org/doi/10.1145/3742413.3789130 (DOI: 10.1145/3742413.3789130)
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-07

> **A note on sourcing:** this session's outbound network access to both arXiv and the ACM Digital Library returned "403 Forbidden" for direct fetches, so this summary is built entirely from cross-checked search-engine excerpts of the paper's abstract, methods, and reported results rather than a direct read of the full PDF. ACM moved to fully Open Access publishing for all its venues (including IUI) starting January 1, 2026, so the paper itself should not be paywalled — the fetch failures here reflect this session's network restrictions, not access rights. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

Grading short-answer, partial-credit questions — the kind of math or reasoning problem where a student can be "half right" — is slow, inconsistent even between human teachers, and gets harder the more students a school has relative to teachers. Fully automated AI graders exist, but they tend to be black boxes: they hand back a score with little insight into *why*, which makes it hard for a teacher to know when to trust the number and when to double-check it by hand. Smarter Together asks: can an AI grading system be built to mirror the actual, small decisions a human teacher makes while marking — and if it explains itself that way, does it change whether teachers are willing to let it do the grading?

## Why this problem matters

In resource-constrained schools with large classes and few teachers, more automation could free up time for actual teaching. But grading feeds directly into a student's record, so a wrong or miscalibrated automated score is a real harm, not a minor inconvenience. That makes this a sharper test case for human-AI collaboration than many "AI assistant" scenarios: the paper isn't just asking whether an AI can grade accurately, it's asking whether a busy, expert human — the teacher — can be given enough insight into *how* the AI reached a score to reasonably decide when to trust it and when to intervene.

## What makes the system agentic

The paper's system, TC-MAG (Teacher-Cognition Multi-Agent Grading), is built as a pipeline of six coordinating LLM agents, each standing in for one discrete step of how a teacher actually grades: drafting a rubric, checking it against grading guidelines, producing a "blind" first mark, producing a second independent mark, arbitrating any disagreement between the two, and cross-checking to calibrate a confidence score. Each agent commits to and logs its own bounded decision before handing off to the next — a multi-step, goal-directed pipeline evaluated on real deployment-style reliability metrics (inter-rater agreement scores against expert human graders), not on the quality of a single generated response. That combination — decomposed multi-step reasoning, coordination between specialized agents, and evaluation as a working system rather than a chatbot — is what makes TC-MAG agentic rather than a single prompted LLM call.

## How humans and the AI agent collaborate

The collaboration here is not moment-to-moment steering during execution — TC-MAG runs its six-step pipeline largely on its own for a given student response. Instead, the human role sits at the review and adoption stage: after TC-MAG produces a score, it also produces staged, teacher-legible explanations (anchored to its own micro-decisions) and a calibrated confidence bucket. Teachers use these outputs to decide, per response, whether to accept the AI's grade, dig into the underlying reasoning, or override it themselves. The paper studies this as a **calibrated-trust and delegation** problem: does giving teachers the right kind of explanation, at the right level of detail, change how much of the grading they're willing to hand over?

## What role the human plays

Teachers are domain experts sitting in a review-and-decide role: they inspect the AI's staged explanations and confidence signal for a given response, decide whether to accept the grade as-is, and — per the paper's design — get pointed toward the specific likely failure points the confidence score flags, rather than having to re-review every single answer from scratch.

## What role the AI agent plays

TC-MAG does the actual grading work end-to-end (rubric creation, guideline checking, two independent blind marks, arbitration, and confidence cross-checking), and it also produces the explanatory material — staged or summarized, depending on configuration — that a teacher uses to decide how much to trust a given score.

## How control, initiative, and decisions are shared

Grading execution is agent-led: TC-MAG runs its full pipeline autonomously per response. Oversight is human-led and selective: teachers don't approve every micro-step, but they retain the final call on whether to accept a grade, informed by the explanation format and confidence bucket the system surfaces. The paper's central manipulation is exactly this hand-off point — varying *how* TC-MAG communicates its reasoning and uncertainty to see how that shifts teachers' willingness to delegate rather than manually re-grade.

## The paper's main idea

**Claim by the authors:** decomposing automated grading into agents that mirror a teacher's own granular decision steps — and then surfacing staged, confidence-calibrated explanations built from those steps — produces both higher-reliability grading than existing baselines *and* a system teachers are more willing to actually delegate to, because the explanations target where a teacher would want to look first.

## How the approach works

TC-MAG chains six anchored LLM agents through the grading process (rubric creation → guideline check → first blind mark → second blind mark → arbitration → confidence cross-check), logging each step. On top of this pipeline, the system can present its reasoning to a teacher either as a short summary or as a "staged," progressively detailed explanation tied to the underlying micro-decisions, paired with a confidence bucket meant to flag where the AI itself is least sure.

## Human study or evaluation design

**Demonstrated in the paper:** the authors report two linked evaluations — (1) a large-scale accuracy validation of TC-MAG's grading against real student data and expert-adjudicated gold labels, and (2) a mixed-methods classroom study with practicing teachers that varied explanation format and exposure to the confidence score, measuring how these changes affected teachers' stated willingness to delegate grading to the system and where their attention concentrated when reviewing AI-produced grades.

## Participants and study setting

**Demonstrated in the paper (per available descriptions):** the accuracy validation used 2,000 real responses from Singapore primary school students on 1–4-mark mathematics questions, scored against teacher-adjudicated gold labels. The teacher-facing delegation study recruited 14 practicing teachers with an average of 12.1 years of teaching experience — real domain-expert participants, not simulated personas — in a mixed-methods (quantitative + qualitative) design.

## Experiments or benchmarks

There is no public, named benchmark; both the grading-accuracy validation and the teacher delegation study use study-specific datasets (the 2,000-response Singapore primary-math corpus, and researcher-constructed grading/explanation scenarios shown to the 14 teachers).

## Main results

**Demonstrated in the paper (per available descriptions):**
- **Grading reliability:** TC-MAG reached what the authors describe as deployment-level reliability — Cohen's κ = 0.968 on 1-mark questions and quadratic-weighted κ = 0.936 on 2–4-mark questions — outperforming individual human teachers (Δκ = +0.063, p < .001) and the strongest LLM baselines tested (minimum Δκ = +0.012, p < .001).
- **Teacher delegation study (N=14):** explanation format and the presence/format of TC-MAG's confidence score both measurably shifted teachers' stated willingness to delegate grading to the system, and shifted where teachers focused their review attention toward likely failure points rather than re-checking everything.
- **Diagnosticity of explanations:** staged (progressively detailed) explanations were substantially more diagnostic for teachers than summarized ones — reported positive likelihood ratio (LR+) of 11.5 for staged explanations versus 4.60 for summarized explanations — informing a "progressive disclosure" design where explanation detail scales with the system's own confidence.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's human-centered finding is that *how* an AI grader explains itself materially changes whether a domain expert is willing to rely on it: staged, micro-decision-anchored explanations paired with calibrated confidence buckets shifted teachers toward greater willingness to delegate grading and helped them concentrate limited review time on the cases most likely to be wrong, rather than uniformly re-checking every score. **This is the authors' framing of their own results**, based on the mixed-methods analysis of the 14-teacher study; exact effect sizes and statistical tests for the delegation-willingness outcome specifically (beyond the LR+ diagnosticity figures) were not independently confirmed from the sources available in this session.

## What is genuinely new

- A grading pipeline explicitly decomposed to **mirror a teacher's own cognitive micro-steps** (rubric → guideline check → double-mark → arbitrate → calibrate), rather than a single end-to-end "grade this" prompt.
- Directly tying **explanation staging and confidence-bucket design** to a measured behavioral outcome — teachers' willingness to delegate — instead of treating explainability as a feature added on faith.
- A **progressive-disclosure strategy** (explanation detail scaling with confidence) grounded in a measured diagnosticity difference (LR+ 11.5 vs. 4.60) between staged and summarized explanations, rather than a fixed one-size-fits-all explanation format.

## Limitations and open questions

- **Small delegation-study sample (N=14):** sufficient for a mixed-methods classroom study but limited for strong statistical generalization about delegation behavior across teacher populations.
- **Single domain and grade band:** validated on Singapore primary-school mathematics short-answer questions; it's unclear how the six-agent decomposition or the delegation findings transfer to other subjects, grade levels, or countries/curricula.
- **Self-reported delegation willingness:** the core human-outcome measure is teachers' stated willingness to delegate rather than a large-scale, longitudinal measure of actual grading behavior once such a system is deployed in real classrooms over time.
- We were unable to independently verify additional details (full statistical reporting, exact interview protocol, or supplementary materials) since the full paper could not be fetched in this session — readers who need precise details should consult the paper directly via the ACM Digital Library.

## Practical implications

For anyone building AI tools meant to assist (not replace) expert reviewers — in education or other high-stakes review settings — this paper is evidence that the *design of the explanation itself* is a lever for trust and adoption, separate from raw model accuracy. A system that already grades reliably can still fail to earn a domain expert's confidence if its explanations aren't structured to match how that expert actually checks work; conversely, matching explanation structure and confidence signaling to expert review habits appears to be something teachers respond to directly.

## Why you should care

This is a concrete, quantified example of a theme that recurs across human-AI collaboration research: raw AI accuracy and human trust are not the same thing, and closing the gap between them can require deliberately engineering *how* an AI communicates its own uncertainty and reasoning to the specific person who has to decide whether to rely on it. For a task as consequential as grading a child's schoolwork, that gap — and this paper's attempt to close it with real teachers, not simulated ones — is worth paying attention to.
