# Is Agentic Code Review Actually Helpful? What 31,000 Real GitHub Reviews Say About Trusting an AI Reviewer

**Authors:** Hong Yi Lin, Mingzhao Liang (The University of Melbourne), Kla Tantithamthavorn (Monash University), Patanamon Thongtanunam (The University of Melbourne)
**Publication date:** 2026-07 (exact day not available — arXiv id 2607.03316, cs.SE / cs.AI)
**Venue:** arXiv preprint (venue/peer-review status not confirmed)
**Paper link:** https://arxiv.org/abs/2607.03316
**Code / data link:** Replication package (datasets, labelling results, model training/inference/evaluation scripts): https://doi.org/10.5281/zenodo.21095394
**Project page:** Not available
**Date added:** 2026-07-25

> **A note on sourcing:** the arXiv host (and several mirror/API hosts tried as fallbacks) returned network-policy blocks from this research session's proxy, so this summary is built from cross-checked search-engine excerpts of the paper's abstract, methodology, and results rather than a direct read of the full PDF. Facts below that were corroborated across multiple independent search queries (authors, affiliations, dataset scale, headline percentages, rejection-reason breakdown, and the replication-package link) are presented as such; anything that could not be verified this way is marked "not available." The paper itself is an openly licensed arXiv preprint, so it is publicly readable even though this session could not fetch it directly.

---

## The problem the paper addresses

A growing number of software teams now let an AI agent — in this case a commercial tool called CodeRabbit — automatically read every new pull request (PR) and leave code review comments, the same way a human reviewer would: "this could be null," "this duplicates logic in file X," "consider extracting this into a helper." These are marketed as "agentic" reviewers because they don't just answer a question once — they gather context across a whole PR, reason about it, and post multi-part suggestions on their own initiative. But nobody had rigorously measured, at scale, what real developers actually *do* with those AI-generated comments once they land in a real pull request: do people accept them, ignore them, argue with them? This paper mines that exact behavior from real open-source projects.

## Why this problem matters

A code review comment is only useful if it changes what gets shipped. If an AI reviewer's comments get silently ignored, or worse, get accepted when they shouldn't be, the "agentic" label is doing more marketing work than engineering work. Understanding *why* developers reject an AI reviewer's suggestions — false positive, redundant, out of scope, or just a mismatch with team conventions — is exactly the kind of evidence needed before organizations decide how much to lean on these tools, and it's the raw material for building better, more trustworthy review agents.

## What makes the system agentic

CodeRabbit, the system under study, is described by the authors as an autonomous agent that reads pull request diffs, gathers surrounding code context, and posts review comments on its own initiative as part of the normal GitHub review flow — without a human first asking it a specific question. That combination — multi-step reasoning over a codebase, autonomous initiative to comment, and operating inside a real software tool/environment (GitHub) rather than a single chat turn — is what makes this an agentic system rather than a simple code-explanation chatbot. The paper studies it exactly as deployed in production, not in a research sandbox.

## How humans and the AI agent collaborate

The collaboration mechanism here is **review and approval**: CodeRabbit posts comments and suggested changes on a pull request, and the human developer who owns that PR decides, for each comment, whether to accept it (often by merging a suggested diff), start a discussion thread about it, or simply reject/ignore it. This is a real, everyday form of human oversight of an autonomous agent's output — the same accept/discuss/reject loop that any code reviewer's comment goes through, just with an AI on one side of it.

## What role the human plays

The developer is the decision-maker and gatekeeper: they read each AI-generated comment on their real pull request, judge whether it's correct and worth acting on, and then accept it, engage with it in a discussion, or dismiss it. Their choices — captured as ordinary GitHub activity, not a lab task — are the paper's primary data source.

## What role the AI agent plays

CodeRabbit plays the reviewer: it autonomously analyzes each of the 10,191 pull requests in the dataset and posts review comments and suggestions, covering both functional issues (bugs, correctness) and, less often, evolvability concerns (maintainability, design). It does this without being asked turn-by-turn — it acts on its own initiative as part of the PR workflow.

## How control, initiative, and decisions are shared

Initiative is split cleanly along the review pipeline: the **agent has the initiative to comment** (it decides what to flag and when, autonomously, on every PR it's configured to review), while the **human retains the initiative to decide what happens next** (accept, discuss, or reject, and ultimately what gets merged into the codebase). There's no shared planning or joint editing here — it's a proposer/gatekeeper pattern, and the paper's core contribution is measuring how that gatekeeping actually plays out at scale.

## The paper's main idea

**Claim by the authors:** by mining tens of thousands of real developer responses to a widely used agentic code review tool "in the wild," you can build an empirically grounded picture of when and why agentic reviews succeed or fail to earn developer trust — going beyond vendor claims or small case studies — and that picture reveals learnable, predictable patterns in what gets rejected.

## How the approach works

The authors collected pull requests from real, active open-source GitHub repositories that use CodeRabbit, and paired each of CodeRabbit's review comments with the corresponding developer response (acceptance, discussion, or rejection), then manually and automatically labeled a large sample of rejected comments by *why* they were rejected (e.g., false positive, redundant, out of scope, intentional design trade-off, misaligned with team coding practices). On top of this labeled data, they trained and evaluated lightweight machine-learning models to see whether a comment's eventual acceptance or rejection could be predicted from its content and context.

## Human study or evaluation design

**Important distinction:** this is not a recruited, consent-based human-subjects study with surveys or interviews. It is a large-scale **naturalistic, observational mining study** of real developer behavior that already happened on public GitHub repositories. The "study design" is the choice of which repositories, pull requests, and comment-response pairs to collect and how to label rejection reasons — there was no experimental manipulation, and no participant was recruited or debriefed.

## Participants and study setting

**Demonstrated in the paper:** the dataset covers 31,073 paired code-review comments and developer feedback, drawn from 10,191 real pull requests across 239 real open-source GitHub repositories that use CodeRabbit for review. The "participants" are the real maintainers and contributors of those projects, acting in their normal workflow — not lab volunteers, but genuine practitioners whose decisions were observed rather than solicited.

## Experiments or benchmarks

There is no public leaderboard-style benchmark here; the "experiment" is the empirical mining study itself, organized into research questions covering (1) how developers respond to agentic review comments overall, (2) why comments get rejected, and (3) whether rejection can be predicted computationally. For the third question, the authors compared several lightweight learning-based prediction approaches against the labeled acceptance/rejection data.

## Main results

**Demonstrated in the paper:**
- Of the 31,073 review comments studied, **36.4% were accepted**, **7.3% triggered further discussion**, and **56.3% were rejected** — meaning more than half of this agent's review comments did not lead to a code change.
- The leading rejection reasons were **invalid suggestions**: false positives were the single most common reason (43.3% of rejections), followed by cases where the developer had made an **intentional design trade-off** the agent didn't recognize (23.7%), alongside comments that were redundant, out of scope, or misaligned with the team's actual coding practices.
- Over time, the proportion of invalid/false-positive suggestions reportedly decreased (roughly 7.5%), while rejections due to misalignment with team-specific coding practices correspondingly increased — suggesting the tool has gotten more technically accurate but still struggles to learn a given team's conventions.
- Agentic review comments skewed toward **functional concerns** (bugs, correctness) over **evolvability concerns** (maintainability, design) — but the functional comments were, on the whole, more likely to be judged invalid.
- Lightweight, non-LLM machine-learning models trained on the labeled data could predict whether a given comment would be rejected with **up to 76% F1 score**, indicating there are learnable, systematic patterns behind why developers reject certain AI review comments and not others.

## Effects on human performance, trust, workload, safety, or decision quality

**Authors' framing, based on the observed data:** the majority-rejection rate (56.3%) is the paper's central signal about developer trust and reliance — in real production use, developers are, more often than not, choosing *not* to act on this agent's suggestions, and the specific rejection reasons (false positives, misjudged trade-offs, mismatched conventions) point to concrete gaps between what the agent flags and what a human reviewer with project context would flag. **My interpretation:** this is indirect but meaningful evidence about calibrated reliance — developers appear to be exercising real judgment rather than rubber-stamping AI suggestions, which is a reassuring sign for oversight, but the high rejection rate also implies a real cost in reviewer time spent triaging comments that don't lead anywhere. The paper does not report direct measures of reviewer workload, satisfaction, or trust via survey instruments — those would need a separate, recruited study design.

## What is genuinely new

- One of the largest "in the wild" empirical looks at how real developers respond to a commercially deployed agentic code review tool, rather than a lab prototype or vendor-reported metric.
- A concrete, labeled taxonomy of *why* developers reject agentic review comments (false positive, redundant, out of scope, intentional trade-off, convention mismatch) — not just an acceptance rate.
- A demonstration that rejection is at least partly **predictable** from lightweight models, opening a path toward review agents that could learn to suppress low-value comments before posting them.
- A published replication package (datasets plus labelling, training, and evaluation scripts), supporting independent verification and reuse.

## Limitations and open questions

- This is an **observational, naturalistic study**, not a controlled experiment — it cannot establish causal claims about what would make developers trust the agent more, only describe patterns in what already happened.
- The study covers one commercial tool (CodeRabbit) as a case study; findings may not generalize to other agentic code review products with different underlying models or configurations.
- No direct measurement of developer-reported trust, workload, or satisfaction (e.g., via survey or interview) accompanies the behavioral acceptance/rejection data.
- We were unable to independently verify some finer-grained details (e.g., full statistical tests, exact repository list, or the complete rejection-reason taxonomy) because the full PDF could not be fetched in this session — readers who need precise details should consult the paper directly.

## Practical implications

For teams already using or considering an agentic code review tool, this paper is a concrete reminder that a majority of AI-generated review comments may currently go unacted-upon, and that false positives and mismatches with team-specific conventions are the leading reasons why. For tool builders, the finding that rejection is partly predictable suggests a practical near-term improvement: a lightweight filter that suppresses comments likely to be rejected before they're even posted, which could reduce reviewer fatigue and improve the tool's earned trust over time.

## Why you should care

This paper matters for anyone tracking human-AI collaboration in real workplaces because it swaps self-reported survey data or small lab studies for tens of thousands of *actual* decisions real developers made about a live AI teammate's output. It's a useful, humbling data point for the broader "can we trust agentic AI" conversation: even a widely deployed, commercially polished agentic reviewer is rejected more often than it's accepted in practice, and the specific reasons why are exactly the kind of evidence that should shape how — and how much — organizations lean on autonomous agents for tasks that used to require full human judgment.
