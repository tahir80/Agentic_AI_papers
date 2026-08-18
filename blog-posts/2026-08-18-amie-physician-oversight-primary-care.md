# When an AI Agent Takes a Patient's History: A Real Clinic Test of AMIE, With Doctors Watching

**Authors:** Google Research / Google DeepMind, Beth Israel Deaconess Medical Center, and Harvard Medical School (large multi-institution author list; confirmed names include Anil Palepu, Khaled Saab, Peter Brodeur, Jacob M. Koshy, Ryutaro Tanno, David Stutz, Roma Ruparel, Joseph Xu, Amy Wang, Jihyeon Lee, Ellery Wulczyn, Charles Wu, Ava Homiar, Wei-Hung Weng, and additional co-authors; a complete author list could not be independently verified in this session — see the paper link for the authoritative list)
**Publication date:** 2026-03-09 (arXiv v1; revised through v3)
**Venue:** arXiv preprint (peer-reviewed venue not confirmed at time of writing)
**Paper link:** https://arxiv.org/abs/2603.08448
**Code link:** Not available (no public repository found for this paper at the time of writing; the study involves real patient data)
**Project page:** Not available (see related Google Research blog post, "Enabling physician-centered oversight for AMIE," which describes the underlying oversight architecture)
**Date added:** 2026-08-18

> **A note on sourcing:** this session's outbound network access to arxiv.org (and to several other paper-hosting mirrors) returned a blocked connection for direct fetches (organization egress policy, not a paywall — the paper is a public arXiv preprint). This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

Most AI systems that can "talk to patients" have only ever been tested in simulations — actors playing patients, or researchers grading transcripts after the fact. This paper asks a blunter question: what happens when you let a conversational AI agent take a real patient's medical history, before a real doctor's appointment, in a real clinic — with real safety staff watching in case something goes wrong? It is a feasibility study of moving a diagnostic AI agent out of the lab and into an actual primary-care workflow.

## Why this problem matters

A chatbot that performs well on a benchmark of scripted cases can still fail badly on an anxious real patient describing symptoms in their own words, at 11pm, before a visit they're worried about. The gap between "works on paper" and "works safely with real people" is exactly where AI healthcare tools tend to stall — either they never leave the pilot stage, or they get deployed without anyone having checked how real patients and real clinicians actually respond to them, and how much oversight they need. This study is a rare attempt to close that gap directly, in a live clinic, with the safety net (human supervisors) explicit and instrumented rather than assumed.

## What makes the system agentic

The system under study, AMIE (Articulate Medical Intelligence Explorer), is not a single-turn question-answering chatbot. Over the course of a multi-turn text conversation with a patient, it maintains and updates several pieces of internal state at once: a running patient summary, a working differential diagnosis, a list of information gaps it still needs to fill, and a draft management plan — deciding at each turn what to ask next based on what it still doesn't know. Google's own description of this line of work explicitly frames AMIE as "a research AI agent for multimodal diagnostic dialogue" rather than a static text generator. That combination — a goal (produce a usable differential diagnosis and plan), multi-step decision-making about what information to gather next, and persistent memory of the case as it evolves — is what puts this in agentic territory, even though the deployed system in this particular study does not call external tools or APIs during the conversation itself.

## How humans and the AI agent collaborate

The collaboration has two distinct layers. First, the patient collaborates directly with AMIE: the patient describes their symptoms and answers AMIE's follow-up questions in a text chat, and AMIE steers the conversation toward a complete history. Second, and more central to this paper's human-AI-collaboration angle, a layer of **human oversight sits over the entire interaction**: human safety supervisors watch every patient-AMIE conversation in real time against predefined safety criteria, empowered to intervene and stop a consultation if needed, while separately the patient's own clinician later reviews AMIE's output (differential diagnosis and summary) before or during the actual appointment.

## What role the human plays

Three distinct human roles are studied: (1) the **patient**, who converses with the agent and supplies the actual clinical information the agent reasons over; (2) the **human safety supervisor**, who monitors interactions live and holds veto/intervention authority over the AI's autonomy in the moment; and (3) the **primary care provider (PCP)**, who reviews AMIE's output for usefulness and compares, in the study's blinded evaluation, AMIE's differential diagnosis and management plan against their own.

## What role the AI agent plays

AMIE conducts the entire history-taking conversation with the patient autonomously — choosing what to ask, tracking what it has learned, and converging on a differential diagnosis and a draft management plan — which is then handed off to the human clinician ahead of the actual appointment. The agent operates independently during the conversation; it is not being steered turn-by-turn by a human, though it is a bounded, watched autonomy rather than an unsupervised one.

## How control, initiative, and decisions are shared

Within a single conversation, initiative sits almost entirely with the AI: it drives the dialogue and decides what information to pursue next. Control, however, is layered above that: human safety supervisors hold real-time stop authority throughout every conversation (a live oversight/approval layer, even though in this study they never had to exercise it), and the treating clinician retains final decision-making authority over diagnosis and management — AMIE's output is explicitly framed as something for the patient to *discuss with their provider*, not a decision delivered directly to the patient. This is a "human oversight of an autonomous agent" pattern: the agent acts, the human supervises and can interrupt, and the human clinician remains the final decision-maker.

## The paper's main idea

**Claim by the authors:** an LLM-based conversational diagnostic agent can be deployed feasibly and safely inside a real ambulatory-care workflow — with live human safety oversight as the operational safeguard — and can produce history-taking and differential-diagnosis output that patients find satisfying to interact with and that clinicians find comparably useful (on several dimensions) to a primary care provider's own initial reasoning.

## How the approach works

Patients scheduled for a non-emergency urgent care appointment at an academic medical center's primary care practice were invited to complete a text-chat conversation with AMIE up to five days before their visit. AMIE gathered history conversationally, kept an internal working differential diagnosis and list of open information gaps, and produced a summary, differential diagnosis, and draft management plan for the clinician. Throughout, human safety supervisors watched every conversation in real time against predefined criteria that would trigger an intervention. Afterward, blinded evaluators compared AMIE's differential diagnosis and management plan against the treating PCP's own, and patients and clinicians were separately surveyed about their experience.

## Human study or evaluation design

**Demonstrated in the paper:** a prospective, single-arm (non-randomized) feasibility study. 100 adult patients scheduled for urgent care appointments completed a text-chat interaction with AMIE in advance of their visit. The study measured (a) conversational safety and quality, (b) patient and clinician experience, and (c) AMIE's clinical reasoning (differential diagnosis and management plan) compared against the actual treating PCP's reasoning on the same cases, via blinded assessment.

## Participants and study setting

**Demonstrated in the paper:** 100 real adult patients at Healthcare Associates, an ambulatory primary care practice within Beth Israel Deaconess Medical Center (a Harvard-affiliated academic medical center), interacting with AMIE ahead of real urgent care appointments. Human safety supervisors and the patients' own treating PCPs were also direct participants in the study's human-in-the-loop design. This is a single-institution, single-arm study — there is no control-group comparison arm reported.

## Experiments or benchmarks

There is no named public benchmark; this is a study-specific, real-world clinical deployment. The comparison condition is not a separate AI baseline but the treating PCPs' own differential diagnoses and management plans for the same 100 real cases, assessed via blinded review.

## Main results

**Demonstrated in the paper (per available descriptions):**
- **No safety interventions needed:** human safety supervisors monitored all 100 interactions in real time and did not need to intervene to stop any consultation under the study's predefined safety criteria.
- **Patient experience improved:** patients reported high satisfaction, and their self-reported attitudes toward AI improved after interacting with AMIE (p < 0.001).
- **Clinician-perceived usefulness:** PCPs found AMIE's output useful, reporting a positive impact on their preparedness for the visit.
- **Diagnostic quality roughly comparable, with a caveat:** blinded comparison found no significant difference between AMIE and PCPs on the quality of the differential diagnosis (p = 0.6) or on the appropriateness (p = 0.1) and safety (p = 1.0) of the proposed management plan — but PCPs significantly outperformed AMIE on the *practicality* (p = 0.003) and *cost-effectiveness* (p = 0.004) of their management plans.
- **Diagnostic accuracy against later chart review:** AMIE's differential diagnosis included the eventual final diagnosis (confirmed by chart review 8 weeks later) in 90% of cases, with 75% top-3 accuracy.

## Effects on human performance, trust, workload, safety, or decision quality

This is a **demonstrated experimental result**, not a projection: patient attitudes toward AI measurably improved after real use (p < 0.001), and clinicians reported the AI's output made them more prepared for the visit. On safety, the demonstrated result is that the human-supervisor safety net operated throughout every interaction without a single needed intervention — evidence that the oversight layer worked as designed in this sample, though the authors' own framing (a feasibility study) means this should be read as an initial safety signal, not proof the system is safe unsupervised at scale. On decision quality, the paper's own statistically significant finding that PCPs still bested AMIE on practicality and cost-effectiveness of management plans is a genuine limitation the authors report, not something this summary is inferring.

## What is genuinely new

- A **real-clinic, real-patient prospective deployment** of a conversational diagnostic AI agent, rather than a simulated-patient or retrospective-transcript evaluation — a step change in ecological validity for this line of work.
- **Live, instrumented human safety oversight** built into the study design itself, with a predefined intervention criterion and a reported outcome (zero interventions needed) rather than oversight as an unstudied afterthought.
- A **head-to-head, blinded comparison** between the agent's clinical reasoning and the actual treating clinician's reasoning on the same real cases, broken into separate dimensions (diagnosis quality, appropriateness, safety, practicality, cost-effectiveness) rather than one aggregate score.

## Limitations and open questions

- **Single-arm, single-institution design:** there is no randomized control group and no comparison across multiple clinical sites; generalizability to other patient populations, specialties, or health systems is not established by this study.
- **Feasibility, not efficacy, framing:** the authors themselves describe this as a feasibility study — it demonstrates the workflow can run safely with oversight, not that it improves outcomes at scale.
- **Practicality and cost-effectiveness gap:** the agent's management plans were rated significantly weaker than PCPs' on real-world practicality and cost, an open problem the paper does not claim to solve.
- **Oversight burden not fully characterized:** the paper reports that supervisors never needed to intervene, but the reported sources available in this session did not confirm details like supervisor caseload, time spent per review, or how supervisor decisions might scale beyond a 100-patient study.
- **Peer-review status:** as of this writing, this appears to be an arXiv preprint (with revisions through v3); a peer-reviewed publication venue was not confirmed from the sources available in this session.
- Full statistical detail, the complete author list and affiliations, and supplementary materials could not be independently verified since the full paper could not be fetched directly in this session — readers who need precise details should consult the arXiv preprint directly.

## Practical implications

For teams building clinical AI agents, this study is a concrete existence proof that a structured human-oversight layer — live monitoring with defined intervention criteria, plus clinician review of the agent's output before it reaches a decision — can let a conversational diagnostic agent operate in a real clinical workflow without an observed safety failure in a 100-patient pilot. It also draws a clear boundary: the agent's diagnostic reasoning held up reasonably well against a human clinician's, but its practical, resource-aware judgment (what's actually feasible and affordable for this patient) did not — a reminder that "as good as a doctor" is not one property but several, and some of them (like cost-effectiveness) may lag behind others even when core diagnostic reasoning is comparable.

## Why you should care

This is one of the few papers in this space that puts a real LLM-based agent in front of real patients in a real clinic, with a real human safety net switched on and measured — rather than measuring the agent in isolation or the human's oversight in isolation. The result is neither a triumphant "AI doctor" story nor a cautionary tale: patients responded well and became more comfortable with AI, clinicians found the output useful, the safety layer held without a single intervention being needed, and the agent's core diagnostic reasoning roughly matched a human clinician's — while still falling measurably short on the practical, cost-aware judgment that experienced clinicians bring. That mixed, specific picture is more useful than either extreme, and it is exactly the kind of evidence human-AI collaboration research needs more of.
