# A Two-Week Trial: What Happens When Real Doctors Bring an AI Research Agent Into the Exam Room

**Authors:** Rogério Corga da Silva, Miguel Romano, Tiago Mendes, Marta Isidoro, Sandhanakrishnan Ravichandran, Shivesh Kumar, Michiel van der Heijden, Olivier Fail, Valentine Emmanuel Gnanapragasam (Synduct GmbH, Munich, with Portuguese healthcare institution collaborators)
**Publication date:** 2026-03-31 (medRxiv v1) / 2026-04-16 (arXiv v1); revised 2026-04-22 (arXiv v2); also published in the peer-reviewed journal *Cureus*
**Venue:** medRxiv preprint; arXiv preprint; *Cureus* (peer-reviewed medical journal)
**Paper link:** https://arxiv.org/abs/2604.16346
**Code link:** Not available (DR. INFO is a proprietary commercial product; no public code repository was found)
**Project page:** https://www.drinfo.ai/ (product site); https://www.medrxiv.org/content/10.64898/2026.03.31.26349817v2 (preprint); https://www.cureus.com/articles/477839-dr-info-at-the-point-of-care-a-prospective-pilot-study-of-physician-perceived-value-of-an-agentic-artificial-intelligence-clinical-assistant (journal version)
**Date added:** 2026-09-01

> **A note on sourcing:** this session's outbound network access to arxiv.org, medrxiv.org, and cureus.com returned blocked connections for direct fetches (an organization egress policy on this session, not a paywall — all three versions of the paper are openly readable). This summary was built from cross-checked search-engine excerpts of the paper's abstract, methodology, and results rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

Doctors spend an enormous share of their working day not examining patients, but hunting for information: looking up a drug interaction, double-checking a dosing guideline, or trying to remember the latest recommendation for a tricky differential diagnosis. The paper's authors cite this as consuming over half of physicians' working hours, feeding directly into the cognitive overload and burnout that plague modern medicine. This study asks a practical question: if you hand real, practicing clinicians an AI assistant that does this lookup-and-reasoning work for them — not in a lab demo, but during their actual five-day work weeks — do they find it genuinely useful, and do they trust it?

## Why this problem matters

Plenty of AI tools promise to save clinicians time, but most are validated only against static benchmark questions or in short, artificial lab sessions. That leaves a real gap: does a tool actually change how a busy physician works when it's just sitting in their pocket during a normal clinic day, competing with everything else pulling at their attention? A pilot that follows real clinicians through real working days — with all the noise, interruptions, and specialty-specific quirks that come with it — is a much sterner and more informative test than a benchmark score.

## What makes the system agentic

DR. INFO is not a single-shot question-answering chatbot. According to the paper, when a clinician asks it a question, the system executes a multi-step clinical information workflow: it **decomposes** the physician's query into its component parts, performs **clinical reasoning** over those parts, **retrieves and verifies sources** from curated medical knowledge bases and peer-reviewed literature (rather than the open web), and then **synthesizes a cited response** built from those verified sources. That decompose-reason-retrieve-verify-synthesize chain is a multi-step pipeline with intermediate decisions at each stage, not one forward pass through a language model — which is what puts it in agentic territory. The authors are explicit about the boundary of that agency, too: DR. INFO does not access electronic health records, write prescriptions, or take autonomous clinical actions — its "acting" is confined to the information-gathering and synthesis pipeline, with every clinical decision left to the human.

## How humans and the AI agent collaborate

The collaboration here is a query-and-consult loop embedded in real clinical workflows. A physician or medical student, in the middle of seeing patients, poses a real clinical question to DR. INFO on their phone or in-workflow tool. The agent runs its retrieval-and-reasoning pipeline and returns a cited answer. The clinician reads that answer, decides how much to trust it, and folds it (or doesn't) into their own clinical judgment. There's no live human supervisor watching each query the way there is in some other agentic-healthcare studies — the "collaboration" being measured is subtler: whether, over repeated real-world use across a working week, physicians come to rely on the tool, and for which kinds of tasks.

## What role the human plays

Twenty-nine clinicians — 25 physicians and 4 medical students across multiple specialties, at Portuguese healthcare institutions — used DR. INFO voluntarily during their normal clinical duties. Their role in this study is threefold: they are the **end users** posing real clinical questions during actual patient care; they are **evaluators**, submitting diary entries after each use rating time savings and decision support; and they are **survey respondents**, completing a baseline questionnaire and a final Net Promoter Score (NPS) evaluation. Notably, the paper reports that junior physicians and students perceived greater benefit than senior clinicians, while senior clinicians tended to use the tool for narrower, more specific tasks — drug dosing verification and confirming a differential diagnosis — suggesting the human's role and reliance on the agent shifted with their own seniority and expertise.

## What role the AI agent plays

DR. INFO acts as an on-demand information and reasoning assistant: it takes a clinician's natural-language question, retrieves relevant evidence from curated medical sources, reasons over that evidence, and hands back a cited, synthesized answer — playing a supporting, consult-like role rather than an autonomous decision-maker. It never initiates a query itself; every interaction in this study starts with a human's question.

## How control, initiative, and decisions are shared

Initiative for starting each interaction rests entirely with the clinician — the agent responds to queries, it does not proactively surface information unprompted in this study. Once a query is posed, the agent has full control over its own multi-step retrieval-and-reasoning process, and the clinician cannot steer or interrupt it mid-computation; they only see the final synthesized answer. Final clinical decision-making authority, however, remains entirely with the human physician: DR. INFO does not write orders, touch the patient record, or take any autonomous action — it is a bounded consult tool whose output is only ever an input into the clinician's own judgment.

## The paper's main idea

**Claim by the authors:** an agentic, retrieval-grounded AI clinical assistant can be deployed into real clinicians' actual working weeks — not just a lab setting — and be perceived by those clinicians as genuinely saving time and supporting decisions, with that perceived value holding steady across a full working week of real use rather than fading after a novelty effect wears off.

## How the approach works

Eligible physicians and medical students at Portuguese healthcare institutions were recruited on a voluntary basis and given access to DR. INFO v1.0. Over a two-week window, each participant was asked to use the tool across five working days during their normal clinical duties, posing whatever real clinical questions arose naturally. After each use, participants logged a diary entry rating perceived time savings and decision support for that specific interaction. Participants also completed a baseline case report form before the study and, at the end, a final evaluation including a Net Promoter Score.

## Human study or evaluation design

**Demonstrated in the paper:** a prospective, single-arm, pilot feasibility study — there is no control group or comparison condition (such as clinicians working without the tool, or against another AI system). The design leans on repeated, in-context, real-world use (diary entries logged immediately after each real use) rather than a single retrospective survey, which the authors present as a strength for capturing perceptions close to the moment of use.

## Participants and study setting

**Demonstrated in the paper:** 29 clinicians (25 physicians, 4 medical students) across multiple specialties at Portuguese healthcare institutions, using DR. INFO during real clinical duties over a two-week period (five working days of use). Of the 29 enrolled, 26 completed the baseline questionnaire, 28 submitted at least one diary entry (90 diary entries in total), and 16 (55%) completed the final NPS evaluation — a meaningful drop-off the authors do not obscure.

## Experiments or benchmarks

There is no public benchmark or synthetic dataset here — the "experiment" is the real-world deployment itself, and the outcome measures are the 90 real diary entries and the final survey/NPS responses from real clinicians using the tool on their own real cases.

## Main results

**Demonstrated in the paper (per available descriptions):**
- **High perceived time savings:** mean rating of 4.27 out of 5 (95% CI: 3.97–4.57), with 87.8% of diary entries indicating agreement or strong agreement that the tool saved time.
- **High perceived decision support:** mean rating of 4.16 out of 5 (95% CI: 3.86–4.45).
- **Stability over time:** both time-saving and decision-support ratings stayed roughly stable across the five-day study window rather than declining — suggesting the perceived benefit wasn't just first-use novelty.
- **Strong Net Promoter Score:** an NPS of 81.2 among the 16 clinicians who completed the final evaluation, with no detractors reported.
- **Usage patterns varied by seniority:** junior physicians and medical students reported higher perceived benefit overall, while senior clinicians used the tool more narrowly, mainly for drug-dosing verification and confirming a differential diagnosis.

## Effects on human performance, trust, workload, safety, or decision quality

This is where the paper's contribution is concentrated, and it is worth being precise about what was — and wasn't — measured. The **demonstrated** results are physician-*perceived* time savings and decision support, self-reported via diary entries and surveys, plus a strong self-reported willingness to recommend the tool (NPS). These are real, repeated, in-the-moment perceptions from real clinicians using the tool on real cases — not a lab vignette. What the study does **not** demonstrate is any objective, externally verified measure of clinical outcome, diagnostic accuracy, or workload reduction (e.g., time-motion data, chart-confirmed diagnostic correctness, or patient outcomes) — the paper's own framing is explicitly about physician-*perceived* value, not measured clinical benefit. That distinction matters: strong self-reported satisfaction is meaningful evidence for adoption and usability, but it is a different (and generally weaker) form of evidence than an objective outcome measure would be.

## What is genuinely new

- A **real-world, longitudinal field pilot** of an agentic clinical-information assistant embedded in clinicians' actual working weeks, rather than a one-off lab session or retrospective benchmark — a meaningfully higher bar of ecological validity than most agentic-healthcare evaluations attempt.
- **Repeated, in-the-moment diary measurement** (90 diary entries logged immediately after real use) rather than a single retrospective survey, which reduces recall bias in the self-reported ratings.
- Evidence that perceived benefit **did not decay** across a full working week, addressing (though not eliminating) the concern that positive first impressions of a new AI tool are often just novelty.
- A finding that **role and seniority shape how clinicians use and value the tool** — juniors leaning on it more broadly, seniors using it for narrower, specific verification tasks — which is a useful signal for anyone designing task allocation between clinicians of different experience levels and an AI assistant.

## Limitations and open questions

- **Single-arm, no control group:** there is nothing to compare against — no "clinicians without the tool" arm, no alternative AI tool, and no randomization — so the study cannot isolate the tool's causal effect from other factors (e.g., a general Hawthorne effect from being observed).
- **All outcomes are self-reported perceptions**, not objectively measured clinical outcomes, diagnostic accuracy, or time-motion data — the paper deliberately measures *perceived* value, and that framing should not be read as evidence of measured clinical benefit.
- **Substantial attrition on the final evaluation:** only 16 of 29 enrolled clinicians (55%) completed the final NPS survey, and the strongly positive NPS is based on this smaller, self-selected subgroup — those who dropped out may have had different (or no) opinions.
- **Small, single-country sample:** 29 clinicians at Portuguese institutions is a modest pilot sample; generalizability to other health systems, specialties, and patient populations is not established.
- **Commercial, closed system:** DR. INFO is a proprietary product from the company running the study (Synduct GmbH), and no code or model details are publicly available — independent replication or scrutiny of the underlying agent pipeline is not possible from the paper alone.
- **Full statistical detail could not be independently verified** in this session since the full PDF could not be fetched directly; readers who need precise confidence intervals and methodology detail should consult the paper directly.

## Practical implications

For teams building or evaluating clinical information-retrieval agents, this pilot is a useful existence proof that a retrieval-grounded, multi-step agentic assistant can be dropped into clinicians' real working weeks and be experienced as valuable rather than as one more disruptive tool to fight with — at least by a self-selected, voluntary group of early adopters. It also flags a design-relevant pattern worth testing further: junior and senior clinicians may want different things from the same agent (broad support versus narrow, specific verification), which argues for evaluating — and potentially designing — agentic clinical tools with attention to the user's own expertise level, not a one-size-fits-all interaction.

## Why you should care

Most papers about AI agents in medicine either stay in the benchmark sandbox or study a single, tightly choreographed clinical encounter. This one instead tracks real doctors carrying a real AI tool through their actual working lives for two weeks, logging what they thought immediately after each real use — and finds that the perceived benefit held up, didn't fade, and varied sensibly by how experienced the clinician was. It is a modest, honestly-reported pilot rather than a definitive trial — no control group, self-reported outcomes only, and real drop-off in survey completion — but that same honesty about its limits is exactly what makes it a credible, useful data point for the still-thin evidence base on how real clinicians actually live with agentic AI day to day.
