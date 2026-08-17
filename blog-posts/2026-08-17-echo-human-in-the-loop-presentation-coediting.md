# ECHO: Explainable Co-editing with Human-in-the-Loop Operations for Presentation Refinement

**Authors:** Yu Fu, Yongqi Kang, Yujia Zhou, Yong Zhao (Sichuan University)
**Publication date:** 2026-06 (arXiv id 2606.09851; exact day of first posting not confirmed from available sources)
**Venue:** arXiv preprint (peer-review status / target venue not confirmed from available sources)
**Paper link:** https://arxiv.org/abs/2606.09851 (PDF: https://arxiv.org/pdf/2606.09851)
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-08-17

> **A note on sourcing:** the arXiv host was not directly reachable from this research session's network, so this summary is built from the paper's publicly circulated abstract and secondary descriptions rather than a direct read of the full PDF. Facts that could be cross-confirmed across multiple independent search results (system design, study structure, participant counts, and headline numbers) are reported as such; anything that could not be verified is marked "not available" or flagged as an interpretation rather than invented.

---

## The problem the paper addresses

Generative AI tools have made it easy to get a first draft of a slide deck. But refining that draft — nudging one chart two centimeters left, making every section header the same size, fixing a table that overflows its box — is a different kind of work. Today's AI slide tools mostly work in one direction: you type an instruction, the model regenerates something, and you inspect the result. The paper calls this a "blackbox, one-way generation" paradigm. If the AI misreads what you meant, you can't reach in and correct just that one piece — you either accept the miss or start over.

## Why this problem matters

Presentation refinement is exactly the kind of task where small, precise edits matter: consistent fonts across dozens of slides, correctly aligned diagrams, a title that fits its box. A tool that only accepts vague instructions and generates a whole new version each time is both inefficient and anxiety-inducing — the authors' formative study found users develop what they call "trial-and-error anxiety" because they can't predict or control what a single instruction will change. This is a small but concrete example of a much bigger question this research log tracks: when an AI can take real actions on your behalf, how do you keep enough control to trust it without having to double-check everything it does?

## What makes the system agentic

ECHO is not a single prompt-in, slide-out generator. It runs a "Plan-Confirm-Execute" loop: given a user's instruction (natural language plus a visual selection on the slide), the system first interprets the intent and grounds it spatially using a vision-language model, then proposes a structured, schema-constrained operation plan (expressed as JSON edit operations) rather than just producing new content directly. That plan is shown to the user for confirmation before anything is executed, and the system maintains a dynamic memory of prior edits and confirmed operations across the session. Multi-step planning, tool-like structured actions on a real document, and persistent memory across turns — rather than a single text reply — are what make this an agentic system under our working definition, not just a chat-based generator.

## How humans and the AI agent collaborate

ECHO is explicitly built as a mixed-initiative, human-in-the-loop co-creation process. The user points at something on the slide and describes what they want in natural language; the AI proposes a concrete, inspectable plan for how it would carry that out; the user can confirm, adjust, or reject the plan before it is executed; and every executed operation is designed to be reversibly undoable. This turns each edit into a small negotiated transaction rather than a one-shot generation the user has to accept or discard wholesale.

## What role the human plays

The human supplies intent (via natural language and a visual selection on the canvas), reviews the AI's proposed operation plan before it runs, and decides whether to confirm it, refine the instruction, or step in and make the edit directly. According to the paper's qualitative analysis, participants also adapted how much control they exercised depending on the task: for logically strict academic slides (e.g., ones needing exact heading hierarchies or ordering), participants wrote longer, more explicit instructions up front (reported at an average of 41.2 words) — taking a more hands-on, directive stance — compared with shorter, more conversational micro-edits elsewhere.

## What role the AI agent plays

The AI grounds ambiguous multimodal instructions (what does "make this bigger" or "align these" refer to, exactly?) into a specific target on the slide, proposes a transparent, structured plan of the operations it intends to perform, executes that plan only after confirmation, and keeps track of prior edits so later instructions can build on earlier context. It is designed to make its own intent legible before acting, rather than acting first and letting the user inspect the result afterward.

## How control, initiative, and decisions are shared

Initiative is shared at the level of individual edit operations, not just the overall session: the human can initiate an edit request at any time, but the AI must propose and expose its plan before executing, and the human retains a checkpoint to accept or intervene at that point. The paper reports a plan confirmation rate of 81.3% — meaning participants accepted the AI's proposed plan roughly four times out of five without needing to intervene further, which the authors take as evidence of good alignment between the system's intent-parsing and what users actually meant, while still leaving room for correction in the remaining cases.

## The paper's main idea

**Claim by the authors:** the "semantic gap" and "control bottleneck" in AI-assisted document editing can be addressed by making the AI's intended actions explicit and confirmable before execution, rather than by trying to make single-shot generation more accurate. Grounding instructions precisely (using both language and a visual selection), representing the AI's intent as a structured, human-readable operation plan, and requiring confirmation before execution are presented as the key ingredients for turning presentation co-editing from "blackbox generation" into something closer to a negotiated, trustworthy collaboration.

## How the approach works

ECHO uses what the authors describe as a task-adaptive, neuro-symbolic architecture. A multimodal front end grounds a user's natural-language-plus-visual-selection input into a specific target element on the slide (using vision-language models to resolve spatial ambiguity). The system then generates a schema-constrained operation plan — a structured, inspectable representation of the intended edits, rather than free-form regenerated content — which is displayed to the user for confirmation (the "Confirm" step of Plan-Confirm-Execute). Once confirmed, operations are executed directly and deterministically against the document, and a dynamic memory mechanism retains context from prior turns so subsequent instructions can refer back to earlier edits. The design also guarantees that executed operations are reversible ("physical undo safety"), so a confirmed-but-unwanted edit can still be rolled back.

## Human study or evaluation design

The paper combines two kinds of evaluation. First, a **formative study with 10 participants** was used to identify the core pain points in existing AI-assisted slide editing — "trial-and-error anxiety" (not being able to predict what an instruction will change) and "inconsistent cross-page formatting" — which directly motivated ECHO's design. Second, **objective benchmark evaluations** tested intent-mapping and spatial-grounding accuracy across multiple underlying foundation models, comparing ECHO's architecture against baselines. Third, a **controlled study with 14 participants** measured real usage of the working ECHO system, including cognitive workload (NASA-TLX) and behavioral measures like instruction length and plan confirmation rate.

## Participants and study setting

Based on the available descriptions: 10 participants took part in the formative interview/observation study that shaped ECHO's design, and a separate 14 participants took part in the controlled evaluation of the built system. Demographic details, recruitment method, and institutional/IRB context were not confirmed from the sources available to this session.

## Experiments or benchmarks

There is no public, named benchmark here; evaluation combines (a) an objective, model-comparison benchmark for intent-mapping and spatial-grounding accuracy across multiple foundation models, and (b) the 14-participant controlled human study on the full interactive system. No public dataset or benchmark name was identified from available sources.

## Main results

**Demonstrated in the paper (per available descriptions):**
- Baseline (text-only, non-ECHO) approaches essentially failed at precise intent mapping and spatial grounding in the objective benchmark; ECHO's architecture raised Target Hit@1 accuracy to roughly 55%–85%, depending on the underlying foundation model.
- In the 14-participant controlled study, NASA-TLX cognitive workload scores dropped by 20.8% (reported as falling from 82.6 to 65.4) when using ECHO.
- Average instruction length dropped from 34.7 words (baseline) to 12.3 words with ECHO, which the authors interpret as a shift from "batch prompting" (long, upfront instructions trying to specify everything) to shorter, conversational "micro-editing" turns.
- The AI's proposed operation plans were accepted by users without further intervention 81.3% of the time.
- Qualitative analysis found that participants' collaboration style (how much upfront detail they gave, how much control they retained) shifted depending on the cognitive demands of the task — more directive and detailed for logically strict academic-slide tasks, more conversational elsewhere.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the controlled study reports a substantial reduction in self-reported cognitive workload (NASA-TLX, -20.8%) when using ECHO compared with the baseline condition, alongside behavioral evidence (shorter instructions, high plan-confirmation rate) consistent with reduced friction in expressing and controlling edits. **Authors' claim / our interpretation:** the shift toward shorter instructions and a high (but not total) plan-acceptance rate is presented by the authors as evidence that users could predict and calibrate their reliance on the system reasonably well — trusting it enough to give brief instructions, while still exercising the confirm/reject checkpoint on roughly one in five plans. We did not find a separately reported, validated trust-scale measurement (e.g., a standard trust questionnaire) in the sources available to us, so we treat "calibrated trust" here as our interpretation of the behavioral pattern rather than a directly measured construct.

## What is genuinely new

- A concrete architectural pattern — multimodal grounding → structured, schema-constrained plan → human confirmation → reversible execution — that operationalizes "mixed-initiative co-editing" for a real, high-friction document-editing task, rather than treating human oversight as an abstract design principle.
- Direct behavioral evidence (instruction length, plan confirmation rate) that giving users a legible, confirmable plan changes *how* they communicate with the AI, not just how they feel about the result.
- Evidence that users' desired level of control is not fixed but shifts with task type (structured/logical vs. more open-ended slide content), suggesting collaboration interfaces may need to adapt to task demands rather than assume one fixed interaction style.

## Limitations and open questions

- **Modest sample sizes.** A 10-person formative study and a 14-person controlled study are useful for early-stage HCI evaluation but are small; generalization to broader user populations, larger real-world decks, or non-academic presentation contexts is untested here.
- **Domain-specific.** The system and study are scoped to presentation slides; it's an open question how well the Plan-Confirm-Execute pattern transfers to other document types or to higher-stakes editing tasks.
- **No public code or dataset found.** We could not confirm code availability, so independent replication is not currently possible from the sources available to us.
- We were unable to independently verify statistical significance testing, full demographic details of participants, or the complete objective-benchmark methodology, since the full PDF could not be fetched in this session — readers who need those details should consult the paper directly.

## Practical implications

If the reported numbers hold up, the paper offers a fairly directly reusable design pattern for any AI tool that edits structured, visual documents (slides, but plausibly also diagrams, spreadsheets, or design files): don't just regenerate content from a vague instruction — ground the instruction precisely, show the user a legible plan of what you're about to do, and let them confirm or redirect before you act. That pattern is a concrete way to give people meaningful, low-effort oversight of an agent's actions without requiring them to supervise every pixel.

## Why you should care

This is a small-scale but well-instrumented example of a pattern this research log keeps circling back to: agents that act on real artifacts benefit from making their intended actions visible and confirmable, rather than opaque. ECHO's headline numbers (large workload reduction, shorter and more conversational instructions, a majority-but-not-total plan-acceptance rate) are a concrete data point for the argument that a "propose, then confirm" loop can meaningfully reduce the burden of supervising an AI agent — while the task-dependent shift in how much control participants wanted is a reminder that "the right amount of human oversight" isn't one fixed number, even within a single application.
