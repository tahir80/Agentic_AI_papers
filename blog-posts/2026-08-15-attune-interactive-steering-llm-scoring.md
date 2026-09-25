# Who's Really Keeping Score? Letting People Steer an AI Grader Instead of Just Trusting It

**Authors:** Bhavya Chopra, Meng Chen, Rebecca Dang, Chanbin Park, Shreya Shankar, Sepanta Zeighami, Bjoern Hartmann, Aditya Parameswaran (UC Berkeley, EPIC Data Lab)
**Publication date:** 2026-08-15 (arXiv v1)
**Venue:** To appear at ACM UIST 2026 (39th ACM Symposium on User Interface Software and Technology), November 2–5, 2026, Detroit, MI (peer-reviewed acceptance as reported in search results; final camera-ready status not independently confirmed)
**Paper link:** https://arxiv.org/abs/2608.14948
**Code link:** https://github.com/ucbepic/attune (reported live deployment and source repository; not independently browsed in this session)
**Project page:** Not available (beyond the GitHub repository above)
**Date added:** 2026-09-25

> **A note on sourcing:** this session's outbound network access to arxiv.org and every mirror/aggregator tried (direct PDF, HTML mirror, Pith, Semantic Scholar, Hugging Face) was blocked at the network egress layer (an organization policy on this session, not a paywall — the paper is a public arXiv preprint with an open GitHub repository). This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported system design, and reported study details and results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "Not available," and readers who need exact tables, full statistical detail, or verbatim participant quotes should consult the arXiv preprint or GitHub repository directly.

---

## The problem the paper addresses

Large language models are increasingly used to *score* things at scale — rating resumes, grading essays, triaging patients, judging whether a product listing is relevant to a search query. But a single scoring pass from an LLM is a black box: it produces numbers without showing its reasoning, and if a domain expert disagrees with a score, there's usually no way to say *why* other than rewriting the prompt and hoping. This paper asks: what if the people who actually understand the domain — a nurse, a lawyer, a teacher — could see the AI's reasoning as a set of inspectable, editable rules, and directly correct that reasoning rather than just the prompt?

## Why this problem matters

Scoring decisions are often high-stakes and inherently subjective — there's rarely a single "correct" rubric for judging a patient's triage urgency or an essay's quality. When organizations quietly hand this work to an LLM, any hidden bias or blind spot in the model's implicit rubric propagates across every record it touches, and the people with the domain expertise to catch that have no real lever to pull. The authors frame this as a trust and control problem, not just an accuracy problem: even a reasonably accurate LLM scorer isn't useful if the expert who has to sign off on it can't understand or adjust *how* it's scoring.

## What makes the system agentic

Attune doesn't just ask an LLM to output a number per record. According to the authors, given a task description and a scoring range, it runs a multi-step process on its own: it performs a series of pairwise LLM comparisons across the dataset to build up a "global" comparison graph, extracts the rationales the model gives during those comparisons, and bottom-up derives a set of explicit scoring criteria and rules from those rationales — before finally resolving everything into consistent numeric scores for every record. That's a pipeline of LLM-driven sub-tasks (compare, extract, generalize, assign, and later re-score after edits) chained toward a goal, rather than one prompt-and-response call — which is what puts it, even if narrowly, on the "agentic" side of the line for this newsletter's purposes rather than plain single-shot LLM scoring.

## How humans and the AI agent collaborate

Attune is explicitly built as a **mixed-initiative system**: the AI proposes a full first draft of the scoring logic (criteria, rules, and resulting scores) on its own initiative, and the human then inspects, edits, or overrides any part of that logic through direct manipulation and chat-based interactions. According to the authors, every edit a person makes compiles into a structured constraint that deterministically re-runs the scoring — so the human isn't just leaving feedback that might get incorporated; their edits become binding rules the system must follow going forward.

## What role the human plays

The human is the domain expert in the loop: someone who understands what "good" actually means for the task at hand (a clinician judging triage urgency, a hiring manager judging resume fit) but who is not expected to write prompts or understand how the underlying LLM works. Per the reported study design, participants reviewed the AI-derived criteria and pairwise rationales, agreed or disagreed with specific rules, and used Attune's steering interactions to correct or refine the scoring logic directly, rather than blindly accepting or rejecting the AI's numbers.

## What role the AI agent plays

The AI does the heavy lifting of the actual scoring workflow: running comparisons across potentially large sets of records, articulating *why* it prefers one record over another in each comparison, generalizing those rationales into a shared, human-readable set of criteria and rules, and applying (or re-applying, after human edits) those rules consistently across the full dataset.

## How control, initiative, and decisions are shared

Initiative starts with the agent — it proposes the first complete scoring logic without being told what the criteria should be. Control then shifts to the human, who holds veto and edit power over every criterion, rule, and resulting score, and whose edits are enforced deterministically rather than treated as soft hints. This is a fairly clean example of what the paper's design intends as *shared decision-making*: the AI's job is to draft a defensible, inspectable starting point at scale; the human's job is to correct it where their domain judgment says it's wrong.

## The paper's main idea

**Claim by the authors:** LLM-powered scoring becomes more trustworthy and more useful in practice when it produces its scoring logic bottom-up, in an inspectable and editable form, and gives users concrete, deterministic ways to steer that logic — rather than treating LLM scoring as an opaque function that can only be adjusted by rewriting prompts. The authors are explicit that they do not intend for this to let LLM scoring fully replace human judgment and oversight; the goal is to make the human oversight that already needs to happen more tractable.

## How the approach works

Reported technical design: Attune first gathers a "holistic" understanding of the dataset through pairwise LLM comparisons of records (rather than scoring each record in isolation), building a comparison graph from the outcomes. It then mines the rationales the LLM gave for each pairwise judgment and generalizes them bottom-up into a shared set of scoring criteria and rules, which serve as an explicit, shared representation of the scoring logic. Finally, it resolves the comparison graph and the derived rules into consistent numeric scores per record. The system is reported to be implemented as a web application (Next.js frontend, Python FastAPI backend) that streams progress to the user via server-sent events and routes LLM calls (via LiteLLM) to a model such as GPT-4.1.

## Human study or evaluation design

The paper reports two rounds of studies with real people, plus a separate technical evaluation:

- A **formative study (n = 12)** with people experienced in using LLM evaluators in enterprise pipelines, to shape the interface design.
- A **main user study (n = 8)**, referred to as P1–P8, with **domain experts in healthcare, law, education, and AI evaluation**, recruited via snowball sampling, to evaluate whether people could steer the scoring logic effectively and whether they came to trust the resulting scores.
- A separate **technical evaluation across three scoring workloads**, measuring inter-model agreement on the pairwise comparisons and on the final score assignments, independent of the human study.

## Participants and study setting

- Formative study: 12 participants (F1–F12) experienced with LLM evaluators in enterprise settings; each did a 45-minute remote session, including a walkthrough followed by roughly 25 minutes of think-aloud interaction on one of four scoring tasks (patient triaging, essay scoring, monitor-stand product relevance, and candidate resume screening), chosen to vary in required expertise and in whether the judgment was accuracy-based or subjective.
- Main study: 8 domain experts (P1–P8) in healthcare, law, education, and AI evaluation, recruited via snowball sampling; each did a 60-minute remote session with a feature walkthrough followed by 35–40 minutes completing a scoring task aligned with their own domain of expertise. All 8 participants used the same condition (Attune) on a single task each — the study did not report a randomized comparison against a non-steerable baseline condition within this sample.
- Both studies were remote, moderated sessions rather than a large-scale field deployment or randomized controlled trial.

## Experiments or benchmarks

- **Technical evaluation:** three scoring workloads, evaluated for inter-model agreement on pairwise comparisons and on final score assignments, rather than against a single public agentic benchmark.
- **User studies:** the formative (n=12) and main (n=8) studies described above, using real scoring tasks drawn from the participants' own domains rather than a synthetic benchmark.

## Main results

**Reported by the authors, per available search excerpts:**
- Inter-model agreement on pairwise comparisons ranged from fair to almost-perfect across the three evaluated datasets, with Cohen's κ averaging **0.59** and raw agreement of **66.2%** across datasets.
- Agreement on the final score assignments (a harder, ordinal task) was fair-to-moderate, with quadratic-weighted κ averaging **0.57**.
- In the main study (n=8), domain experts are reported to have trusted the bottom-up derived criteria relatively quickly, composed steering interactions fluidly to adjust the scoring logic, and grounded their confidence in the resulting scores specifically in being able to inspect and understand the underlying logic — rather than trusting the numbers on faith.

Exact statistical tests, full result tables, and direct participant quotes could not be independently verified from the sources available in this session; readers should consult the arXiv PDF for the complete numbers.

## Effects on human performance, trust, workload, safety, or decision quality

The study's human-centered outcome is primarily about **trust and comprehension** rather than task speed or workload: participants are reported to have trusted the AI-derived scoring criteria relatively quickly once they could see and edit the underlying rationale, and to have been able to compose corrective "steering" actions fluidly rather than struggling to translate their domain judgment into a fix. No NASA-TLX–style workload measure, safety-incident data, or a controlled comparison against an unsteerable baseline within the same participant pool was surfaced in the sources checked for this summary — this should be read as a gap in what could be confirmed, not necessarily an absence in the full paper.

## What is genuinely new

- **Bottom-up, human-readable scoring logic**, derived from the LLM's own pairwise comparison rationales, rather than a rubric a person has to write in advance or a black-box numeric output.
- **Deterministic steering**: user edits compile into structured constraints that reliably change future scoring, rather than being folded back in as another soft prompt that the model might or might not follow.
- **A real study with genuine domain experts** (healthcare, law, education, AI evaluation professionals) scoring tasks from their own fields, rather than crowdworkers or simulated personas standing in for expertise.

## Limitations and open questions

- **Small, single-condition human sample.** Eight domain experts, each doing one task under one condition, is a reasonable sample for a formative/evaluative HCI systems paper but is not powered to detect subtle differences in trust, workload, or accuracy, and did not include a randomized comparison against a non-steerable baseline within the same cohort.
- **Snowball recruitment.** Both studies recruited participants through personal/professional networks, which can skew toward people already favorably disposed toward AI tools or already familiar with the research team.
- **Moderate, not high, model agreement.** The reported Cohen's κ (0.59) and quadratic-weighted κ (0.57) indicate fair-to-moderate agreement between models rather than near-perfect reliability, meaning the underlying scores themselves still carry real uncertainty that steering can reduce but not eliminate.
- **Authors' own caveat:** the team explicitly does not claim this should let LLM scoring replace human judgment and oversight — the paper is positioned as making that oversight more tractable, not as removing the need for it.
- **Sourcing caveat (this summary):** because full-text access was blocked in this research session, exact statistical tests, full participant quotes, and complete result tables could not be verified beyond what surfaced in cross-checked search excerpts.

## Practical implications

For any organization already using LLMs to score resumes, support tickets, essays, or similar records at scale, this paper offers a concrete alternative to "rewrite the prompt and hope": expose the model's own comparison rationale, generalize it into rules a domain expert can actually read, and let that expert edit the rules directly, with the system guaranteeing those edits are enforced. That's a meaningfully different (and, per the reported study, better-trusted) mode of human oversight than treating an LLM scorer as a fixed black box to be accepted or discarded wholesale.

## Why you should care

Most "AI in the loop" scoring setups quietly ask a person to either trust the machine's number or manually redo the work — there's rarely a real middle path. Attune's reported design and its small but genuine study with real clinicians, lawyers, educators, and evaluators is a concrete example of what shared decision-making over an automated pipeline can look like in practice: the AI still does the scaling; the human still has the final, enforceable word on the logic behind the numbers.
