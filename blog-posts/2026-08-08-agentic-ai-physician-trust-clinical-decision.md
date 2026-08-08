# Agentic AI Enhances Physician Trust in Clinical Decision Making

**Authors:** Zhiling Yan, Zhe Fang, David J. King, Ann Pongsakul, Eashan Adhikarla, Hui Ren, Sunyang Fu, Quanzheng Li, Lifang He, Xiang Li, Hongfang Liu, Yonghui Wu, Lichao Sun
**Publication date:** 2026-06-16 (arXiv v1)
**Venue:** arXiv preprint (peer-reviewed venue not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2606.30658
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-08

> **A note on sourcing:** this session's outbound network access to arxiv.org returned a blocked connection for direct fetches (organization egress policy, not a paywall — the paper is a public arXiv preprint), so this summary is built from cross-checked search-engine excerpts of the paper's abstract and reported methodology/results rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

When a doctor is deciding whether to trust an AI's suggestion about a patient, "the AI said so" isn't enough — they want to know *why*. Older medical AI models can write out a chain of reasoning in words, but that reasoning is still just text the model generated; there's no way for a physician to check whether the model actually looked anything up or ran any calculation, versus just narrating a plausible-sounding story. This paper asks whether giving physicians AI that *visibly does things* — looks up a drug interaction, runs a clinical calculator, pulls up current literature — while reasoning through a case changes how much physicians actually trust it, compared to an AI that only writes out reasoning as text.

## Why this problem matters

Trust is the hinge on which AI's usefulness in medicine actually turns. An AI system can be accurate and still be useless if physicians don't trust it enough to act on its suggestions — and it can be dangerous if physicians trust it *too much* and stop scrutinizing its output. Getting this calibration right matters most in exactly the settings where AI is being pushed hardest: diagnosis and treatment planning, where a wrong call has real consequences for a patient. This paper's core question — does *how* an AI reasons (and whether that reasoning is verifiable) change physician trust, and does that trust track the AI's actual reliability — sits right at the center of that problem.

## What makes the system agentic

The paper's subject is what it calls "agentic AI" for clinical reasoning: rather than only generating a written chain of thought, the system can autonomously invoke external tools mid-reasoning — the paper's description mentions things like clinical calculators, image-analysis modules, and up-to-date literature search — and it renders both the intermediate reasoning steps and the tool outputs visible to the physician reviewing the case. That combination — a goal (reach a diagnostic or treatment recommendation for a specific case), multi-step reasoning that calls out to external tools rather than staying purely inside the model, and an evaluation that compares this "agentic" behavior against a "non-agentic" baseline doing the same task without tool use — is what puts this squarely in agentic AI territory rather than plain LLM text generation.

## How humans and the AI agent collaborate

The collaboration modeled here is a **trust-and-reliance** relationship rather than a back-and-forth conversation: for each of 315 real multimodal clinical cases, the agentic system works through its reasoning (calling tools as needed) and presents its conclusion and the visible trail behind it; physicians then judge how much they trust the reasoning itself and how much they'd actually act on (rely on) the recommendation. The paper studies this as two related but distinct human responses — trusting the *process* and relying on the *output* — and checks whether making the AI's tool use and intermediate steps visible changes both.

## What role the human plays

Three physicians serve as expert evaluators: for each clinical case they read the AI's presented reasoning (agentic or non-agentic version) and its output, and provide structured judgments of (a) how much they trust the reasoning process itself and (b) how much they would rely on the output in practice. The physicians are not steering or correcting the AI mid-task in this study — their role is post-hoc expert judgment of trust and reliance, applied consistently across a large case set.

## What role the AI agent plays

The AI does the clinical reasoning end-to-end for each case: in its agentic configuration it decides when to invoke external tools (e.g., a calculator, an image-analysis module, a literature search) as part of reaching a diagnostic or treatment recommendation, and it exposes both the intermediate steps and tool outputs to the physician rather than only a final answer. Its non-agentic counterpart reasons over the same cases without that tool-invocation and transparency layer, serving as the comparison condition.

## How control, initiative, and decisions are shared

Task initiative sits almost entirely with the AI within a case (it decides what to reason about and which tools to call), while evaluative authority sits entirely with the physician: the physician doesn't intervene in a given case's reasoning, but their trust and reliance judgments are the paper's entire measurement instrument, and the design explicitly treats "does the physician actually rely on this" as separate from "does the physician trust the process" — a shared-decision framing where the AI proposes and the human's calibrated (or miscalibrated) reliance is the outcome being measured.

## The paper's main idea

**Claim by the authors:** making an AI's reasoning agentic — i.e., letting it invoke external tools and exposing that tool use and the intermediate reasoning steps to the physician — measurably increases physician trust and reliance compared to a non-agentic AI reasoning over the same cases, and the increase holds specifically on tasks like treatment planning where verifiable tool use (rather than free-text reasoning) gives the physician something concrete to check.

## How the approach works

The system reasons over a clinical case and, in its agentic mode, calls out to external tools mid-reasoning (the paper's description cites clinical calculators, image-analysis modules, and literature search as examples) rather than generating only a self-contained written chain of thought. Both the calls to these tools and their outputs remain visible in the final presentation to the physician, alongside the AI's ultimate recommendation, so the physician can see not just a conclusion but a trail of externally-verifiable steps behind it. This agentic configuration is then run head-to-head against a non-agentic baseline — the same underlying reasoning task, without tool invocation or that transparency layer — across the same case set.

## Human study or evaluation design

**Demonstrated in the paper:** three physicians evaluated 315 real multimodal clinical cases, each scored under both the agentic and non-agentic AI conditions. For each case/condition, physicians provided quantified judgments capturing two distinct constructs: process-oriented **cognitive trust** (do I trust *how* this reasoning was produced) and outcome-oriented **behavioral reliance** (would I actually act on this output). The design lets the authors compare agentic vs. non-agentic AI on both measures, check how the two trust measures relate to each other, and break results out by task type (e.g., treatment planning).

## Participants and study setting

**Demonstrated in the paper (per available descriptions):** three physicians served as the expert raters, evaluating a shared set of 315 multimodal clinical cases. This is a small number of physician-raters (three), though the case volume they rated is substantial. Institutional affiliations were not confirmed from the sources available in this session; the author list spans multiple US institutions (including Lehigh University, Harvard-affiliated, and other medical/academic centers per the byline), which suggests — but does not confirm — a multi-institution clinical evaluation context.

## Experiments or benchmarks

There is no named public benchmark identified in the sources available; the evaluation uses a study-specific set of 315 real multimodal clinical cases assembled by the authors, compared across agentic vs. non-agentic AI conditions and broken down by clinical task type (diagnosis, treatment planning, etc., per the reporting).

## Main results

**Demonstrated in the paper (per available descriptions):**
- **Trust and reliance both increased with agentic reasoning:** physicians showed significantly higher cognitive trust and behavioral reliance for the agentic model compared to the non-agentic baseline (p < 0.001).
- **Trust and reliance are linked:** process-oriented cognitive trust was significantly associated with outcome-oriented behavioral reliance (p < 0.001) — physicians who trusted the visible reasoning process were also more likely to say they'd act on the output.
- **Task-specific effect:** on treatment-planning cases specifically, physicians preferred the agentic model's reasoning in 89.57% of cases — the strongest reported preference across task types.
- **A caution alongside the positive result:** the authors report that measurable **over-reliance on incorrect agentic outputs still occurred** — physicians didn't only trust the agentic system when it was right, which the authors use to argue that visible tool use and reasoning transparency alone do not substitute for continued clinician oversight.

## Effects on human performance, trust, workload, safety, or decision quality

The headline human-centered finding is that visible, tool-grounded reasoning changed physicians' trust and stated reliance in a statistically significant, consistent direction — physicians engaged differently with an AI they could partly verify than with one offering only free-text reasoning. **This is a demonstrated experimental result** (p < 0.001 for both trust and reliance comparisons, and for the trust–reliance association). The safety-relevant counterpoint is also a demonstrated result, not just a caveat: over-reliance on *incorrect* agentic outputs was still measurable, meaning higher trust in agentic AI did not fully track the AI's actual correctness — exactly the appropriate-reliance problem this research area cares about.

## What is genuinely new

- Directly comparing **agentic vs. non-agentic AI reasoning on the same clinical cases**, with physician trust and reliance as the outcome, rather than only comparing raw diagnostic accuracy between systems.
- Separating **cognitive trust in the process** from **behavioral reliance on the output** as two distinct, both-measured constructs, and quantifying how they relate to each other.
- A concrete, quantified demonstration that transparency/tool-verifiability changes trust **but does not eliminate over-reliance on wrong answers** — i.e., positive framing ("agentic AI is trusted more") and a genuine safety limitation ("and that trust isn't perfectly calibrated to correctness") reported side by side in the same study.

## Limitations and open questions

- **Small physician-rater pool:** only three physicians provided the trust/reliance judgments underlying every result in the paper; this is a real, expert evaluation, but it is a small panel, and the sources available did not confirm inter-rater reliability figures or how disagreements among the three were resolved.
- **Over-reliance persists:** the authors' own reported finding — that physicians still over-relied on incorrect agentic outputs — is an open safety question the paper surfaces rather than solves.
- **Specialty and case-mix scope not confirmed:** which clinical specialties, case complexity, or institutions the 315 cases were drawn from was not verified from the sources available in this session.
- **Peer-review status:** as of this writing this appears to be an arXiv preprint; a peer-reviewed publication venue was not confirmed.
- We were unable to independently verify additional details (full statistical tables, exact trust/reliance instrument wording, or supplementary materials) since the full paper could not be fetched in this session — readers who need precise details should consult the arXiv preprint directly.

## Practical implications

For teams building clinical AI tools, this paper's evidence points toward a concrete design lever distinct from raw model accuracy: making an AI's tool use and intermediate reasoning steps visible and checkable appears to shift how much physicians trust and rely on it. But the same study's over-reliance finding is a caution against treating that transparency as a safety mechanism on its own — visibility can build trust faster than it builds *justified* trust, so systems built this way likely still need explicit friction or checks to keep physician reliance calibrated to actual system correctness, not just to the presence of a visible tool trail.

## Why you should care

This is a rare case of a paper measuring the actual psychological effect that "agentic" behavior — tool use, visible intermediate steps — has on the domain experts meant to rely on it, in a real high-stakes setting, rather than assuming transparency is automatically good. The finding that trust rose *and* over-reliance on wrong answers persisted is the more useful (and more honest) result than either half alone: it says agentic transparency is a real lever on human trust, and a reminder that trust and correctness don't automatically travel together.
