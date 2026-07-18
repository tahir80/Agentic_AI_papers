# When the AI Talks to the Patient First: Putting a Human Safety Net Under a Medical Conversation Agent

**Paper title:** A prospective clinical feasibility study of a conversational diagnostic AI in an ambulatory primary care clinic
**Authors:** Peter Brodeur, Jacob M. Koshy, Anil Palepu, Khaled Saab, Ava Homiar, Roma Ruparel, Charles Wu, Ryutaro Tanno, Joseph Xu, Amy Wang, David Stutz, Wei-Hung Weng, Hannah M. Ferrera, David Barrett, Lindsey Crowley, Jihyeon Lee, Spencer E. Rittner, Ellery Wulczyn, Selena K. Zhang, Elahe Vedadi, Christine G. Kohn, Kavita Kulkarni, Vinay Kadiyala, Sara Mahdavi, Wendy Du, Jessica M. Williams, David Feinbloom, Renee Wong, Tao Tu, Petar Sirkovic, Alessio Orlandi, Christopher Semturs, Yun Liu, Juraj Gottweis, Dale R. Webster, Joëlle Barral, Katherine Chou, Pushmeet Kohli, Avinatan Hassidim, Yossi Matias, James Manyika, Rob Fields, Jonathan X. Li, Marc L. Cohen, Vivek Natarajan, Mike Schaekermann, Alan Karthikesalingam, Adam Rodman — Google Research / Google DeepMind, in partnership with Beth Israel Deaconess Medical Center (BIDMC) and Harvard Medical School
**Publication date:** 2026-03-09 (arXiv v1); latest revision 2026-03-15 (v3)
**Venue:** arXiv preprint; associated with the registered clinical trial [NCT06911398](https://clinicaltrials.gov/study/NCT06911398) ("AMIE's Clinical Conversational Abilities in an Urgent Care Setting") on ClinicalTrials.gov. No confirmed peer-reviewed journal publication was found as of this writing — treat "peer-reviewed" claims as unconfirmed.
**Paper link:** https://arxiv.org/abs/2603.08448
**Code link:** Not available (AMIE is an internal Google research system; no code release found)
**Project page:** https://research.google/blog/exploring-the-feasibility-of-conversational-diagnostic-ai-in-a-real-world-clinical-study/
**Date added:** 2026-07-18

*A note on sourcing: the tools available in this session could not directly fetch the arXiv PDF or HTML (an environment-level fetch restriction affected essentially all external domains except GitHub during this run). This summary is instead built from the paper's abstract and multiple independent secondary write-ups of its content (including Google's own research blog and third-party paper-review sites), cross-checked against each other for consistency. Specific figures below are flagged as authors'-stated results; anything that could not be independently corroborated is marked "not confirmed."*

---

## The problem the paper addresses

Large language models have gotten good at simulated medical conversations — answering test questions, role-playing with actor-patients, passing benchmarks. But a simulation is not a clinic. This paper asks a much blunter question: what happens when you let a conversational diagnostic AI talk to **real patients**, before a **real doctor's appointment**, in a **real primary care practice** — and is it safe enough to try?

## Why this problem matters

Every prior success for medical LLMs had an asterisk: simulated patients, scripted vignettes, retrospective chart review. None of that tells you whether the system behaves safely and usefully when an actual anxious patient, with an actual undiagnosed problem, is typing into it from home. Skipping straight to "let it run unsupervised in a real clinic" would be reckless; never testing it in the real world at all means it never leaves the lab. The paper's contribution is a middle path: real deployment, but with a human safety net built into the design from day one.

## What makes the system agentic

The system, AMIE (Articulate Medical Intelligence Explorer), is described by the authors as an **agentic system** built on Gemini, running in a "Thinking Mode" that maintains an internal state across the conversation rather than answering turn-by-turn in isolation. It doesn't just chat — it pursues a goal (complete a structured history, reason toward a differential diagnosis) across a multi-phase interaction, tracking what it has already learned about the patient and deciding what to ask next based on that evolving state. That combination — a goal, multi-step reasoning across turns, and an internal memory of the interaction so far — is what puts it in agent territory rather than single-shot chatbot territory, even though its "actions" are conversational rather than tool calls or API invocations. Reasonable readers could still debate how far along the "chatbot vs. agent" spectrum this sits; we flag that ambiguity rather than paper over it.

## How humans and the AI agent collaborate

This is the heart of why the paper matters for human–AI collaboration: AMIE never operates alone. Every single patient conversation was **watched live, in real time, by a human clinician acting as a safety supervisor**, who held explicit authority to interrupt the session.

## What role the human plays

Three distinct human roles show up in the study:
- **The patient** — has a text-chat conversation with AMIE for up to several days before their scheduled urgent care visit, describing their symptoms and answering AMIE's follow-up questions.
- **The safety supervisor** — a human clinician monitoring the live AI–patient chat with the authority to intervene or end the session at any time.
- **The primary care provider (PCP)** — reviews the AMIE-generated transcript and summary before or during the actual appointment, forms their own independent differential diagnosis, and later completes a survey on how useful they found it.

## What role the AI agent plays

AMIE conducts the conversational history-taking itself: asking questions, following up on the patient's answers, and producing both a transcript and a candidate differential diagnosis for the human clinician to review and build on — not to act on unilaterally.

## How control, initiative, and decisions are shared

Initiative is mostly AMIE's during the conversation itself (it drives the questioning), but authority is never fully handed over: the safety supervisor has standing override power throughout, and the PCP has final clinical authority afterward. The paper operationalizes the supervisor's oversight with **four predefined stop criteria** for when to intervene: (1) immediate concern for harm to self or others, (2) significant emotional distress linked to the AI interaction, (3) any potential for clinical harm the supervisor identifies from the conversation, or (4) an explicit patient request to end the session. This is a rare case of "human oversight of an autonomous agent" being turned into a concrete, pre-registered protocol rather than a vague promise.

## The paper's main idea

You can responsibly test a patient-facing conversational diagnostic agent in a live clinical setting, without exposing patients to unsupervised risk, by wrapping the agent in a real-time human safety-supervision layer with clearly defined trigger conditions — and then measure, empirically, how often that safety net actually gets used and how the AI's clinical reasoning compares to a human PCP's.

## How the approach works

AMIE conducted a structured, multi-phase text-chat interaction with each patient in the days before their scheduled urgent care visit, gathering a history and generating a candidate differential diagnosis and management plan. A human safety supervisor monitored every conversation live against the four stop criteria above. After the visit, the assigned PCP separately reviewed the AMIE transcript/summary and completed a survey (via REDCap) covering whether they read it, and their views on preparedness, potential harm, trust, and behavior change. Independent clinicians then performed a blinded comparison of AMIE's differential diagnosis and management plan against the PCP's own, without knowing which was which.

## Human study or evaluation design

This was a **prospective, single-arm, real-world feasibility study** — not a simulation, and not a randomized controlled trial (the authors' own framing: a feasibility study, with the single-arm design as an acknowledged limitation, not a comparative trial). It was conducted at Healthcare Associates, an ambulatory primary care practice within Beth Israel Deaconess Medical Center, and is registered on ClinicalTrials.gov as NCT06911398.

## Participants and study setting

**100 adult patients** completed an AMIE text-chat interaction up to five days before an urgent care appointment at BIDMC's primary care practice, with their treating **PCPs** and a set of **human safety-supervisor clinicians** participating alongside them. This is real people using the system for real (upcoming) medical visits, not actors or crowdworkers.

## Experiments or benchmarks

There is no public benchmark here; the "experiment" is the live clinical deployment itself, evaluated against the pre-registered safety protocol, blinded diagnostic-quality comparison against PCPs, and post-visit clinician/patient surveys.

## Main results

**As reported by the authors (via the abstract and consistent secondary sources):**
- AMIE's differential diagnosis included the eventual final diagnosis (per chart review roughly two months later) in **90%** of cases, with **75%** top-3 accuracy.
- A blinded comparison of AMIE's and the PCP's diagnosis/management quality found no statistically significant difference (differential diagnosis quality, p = 0.6; appropriateness of the management plan, p = 0.1; safety of the management plan, p = 1.0).
- The human safety supervisors monitored all 100 conversations live and **never needed to stop a session** under the four predefined stop criteria.
- On **three occasions**, a supervisor chose to add an optional remark to the conversation even without a stop-worthy trigger: once to help clarify symptoms, once to clarify when the patient should seek emergency care, and once to correct a factual detail about a surgery date.
- Patients reported high satisfaction, and their self-reported attitudes toward AI **improved significantly** after the interaction (p < 0.001).
- PCPs generally found the AMIE output useful for visit preparedness, describing a shift in the visit's nature from "gathering the history" toward "verifying and building on a history already gathered," and noted that AMIE-prepared patients arrived more organized with clearer questions.

## Effects on human performance, trust, workload, safety, or decision quality

This is where the paper's evidence is genuinely about collaboration, not just model accuracy. Safety was measured directly and operationally (a live human overseer, a defined intervention protocol, and an empirical zero-required-interventions outcome — plus three instances of light-touch, non-mandatory human input). Decision quality was measured by comparing AI-generated and human-generated diagnoses head-to-head under blinding. Patient trust/attitude and PCP-perceived workload impact were measured through pre/post surveys rather than assumed. Together, that is a considerably more rigorous human-outcomes package than most agentic-AI papers offer — even though, as a single-arm feasibility study, it cannot tell us how AMIE would fare against a true control condition or at larger scale.

## What is genuinely new

Most agentic-AI safety discussion is theoretical: "a human should be able to intervene." This paper actually built that intervention capability into a live clinical deployment, pre-registered the exact conditions under which a human would exercise it, ran the AI with real patients and a real downstream medical decision at stake, and reported what the human overseer actually did (nothing mandatory, but occasional light-touch guidance) rather than merely what they were empowered to do. Pairing that with a blinded AI-vs-clinician diagnostic comparison, in the same study, is unusual.

## Limitations and open questions

**Stated or clearly implied by the design itself:**
- **Single-arm, no control group** — there is no parallel group of patients who skipped the AMIE interaction, so the study can show feasibility and safety-net behavior but cannot isolate AMIE's causal effect on downstream outcomes the way a randomized trial could.
- **Single site, single specialty context** — one academic medical center's urgent care/primary care setting; generalization to other health systems, patient populations, or acuity levels is untested here.
- **Small sample for population-level safety claims** — 100 conversations with zero required interventions is reassuring but far too small a sample to bound the true rate of rare, serious safety failures.
- **Feasibility, not efficacy** — the authors frame this explicitly as a feasibility study; it is not designed or powered to prove that AMIE improves clinical outcomes.

**Open question the paper raises:** if a real-time human safety net worked this smoothly here, how does that protocol need to change as these systems are deployed at larger scale, across more diverse patients and conditions, where rare failure modes are more likely to surface? The authors' own blog post notes this feasibility study and a separate, larger, ongoing multi-site study (with Included Health) are described as sequential steps toward that answer — not a finished answer in themselves.

## Practical implications

This is a template other health systems (and arguably other high-stakes agentic-AI deployments generally — legal, financial, safety-critical domains) can borrow: don't just claim an agent is "supervised" — write down the exact conditions under which a human must intervene, staff a live human monitor with real override authority, and measure how often that authority actually gets used. It also offers a concrete, evaluable pattern for "shared decision-making": AI drafts a differential diagnosis, a human clinician reviews and can build on or override it, and the two are compared afterward rather than one simply replacing the other.

## Why you should care

Most "human oversight of AI agents" writing is aspirational — a policy sentence, a diagram with a human icon in the loop. This paper is one of the few recent, openly available examples where that oversight was actually built as a working protocol, deployed with real patients making real medical decisions, and measured: how often the human backstop was used, whether patients trusted the process more afterward, and whether the AI's clinical judgment held up against a human doctor's under blinded comparison. Whatever you think of AI in healthcare specifically, it's a useful, concrete case study in what "meaningful human oversight of an autonomous agent" can look like when someone actually tries to build and measure it, rather than just promise it.

---

*Claims attributed to "the authors" reflect what is reported in arXiv:2603.08448 and its abstract, as corroborated across multiple independent secondary sources describing the paper. Passages marked as interpretation, or noted as "not confirmed," are the summary writer's own reading and are not necessarily asserted by the paper itself. Because this run could not directly fetch the primary PDF, readers who need exact wording or additional statistical detail (e.g., full survey breakdowns, exact participant demographics) should consult the arXiv page directly.*
