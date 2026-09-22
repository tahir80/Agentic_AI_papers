# Seven AI Editors, One Human Boss: Inside CHORUS's Take on Human-AI Translation

**Authors:** George X. Wang (New York University); Jiaqian Hu (Middlebury Institute of International Studies at Monterey); Jing Qian (New York University)
**Publication date:** 2026-02-22 (arXiv v1, titled "Who Has the Final Word? Designing Multi-Agent Collaborative Framework for Professional Translators"); major revision 2026-09-18 (arXiv v3, retitled "CHORUS: Designing Human–AI Multi-Agent Collaboration for Professional Translators")
**Venue:** Accepted, ACM ICMI 2026 (28th ACM International Conference on Multimodal Interaction), Napoli, Italy — long paper
**Paper link:** https://arxiv.org/abs/2602.19016
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-09-22

> **A note on sourcing:** this session's outbound network access to arxiv.org and its usual mirrors (Hugging Face, alphaXiv, Semantic Scholar, ar5iv, Jina Reader) was blocked at the network egress layer, so this summary could not be built from a direct read of the full PDF. It is instead built from cross-checked excerpts surfaced by multiple independent web searches, including the paper's own abstract text and reported study design and results, triangulated across several independent search queries that returned consistent figures. Facts that appeared consistently across independent searches are presented as such; anything that could not be corroborated this way is marked "Not available" or "not confirmed." Readers who need exact statistics, full result tables, participant demographics, or direct quotations should consult the arXiv preprint or the ICMI 2026 proceedings directly.

---

## The problem the paper addresses

Professional translators — the people who translate contracts, medical documents, literature, or marketing copy for a living — work in a world where mistakes are expensive and "close enough" often isn't good enough. When they use AI to help, today's options are limited: a single AI model either spits out one translation in one shot, or it "self-refines" its own draft in isolation. Neither approach gives the translator much structured control. The AI doesn't distinguish between "this is a factual accuracy problem" and "this is a terminology consistency problem" and "this is a tone/register problem" — it just gives one blob of text or one blob of suggested edits, leaving the translator to untangle which issue is which and decide what to do about each one, largely on their own.

## Why this problem matters

Translation is a genuinely multi-dimensional skill: a good translation has to be accurate, use the right specialized terms, read naturally in the target language and locale, and match the intended style and audience — all at once. Translation quality researchers have long used a framework called **MQM (Multidimensional Quality Metrics)** to formally separate these dimensions when scoring translation errors. But AI writing tools rarely mirror that structure back to the human using them. If AI assistance is going to genuinely help rather than just generate more text for a translator to re-check, it needs to respect how translators actually think about quality — dimension by dimension — and it needs to leave the translator, not the AI, holding final authority over a decision that carries real professional and legal consequences.

## What makes the system agentic

CHORUS isn't a single model producing one translation. It is a **multi-agent system**: a pool of specialized AI agents, each aligned to a different MQM quality dimension (the paper cites examples like Accuracy, Terminology, and Locale/style), plus a coordinating **Dimension Router** that reads the current sentence and the translator's apparent intent and decides which subset of agents should weigh in. The system also runs a **live effort algorithm** that watches the translator's editing history and interaction behavior over time and uses that to adjust which agents get emphasized as the session goes on. This is multi-step, tool/memory-grounded (agents draw on shared glossaries and style guides), adaptive behavior in service of a goal — not a single text response — which is what makes it agentic rather than just "a chatbot that translates."

## How humans and the AI agent collaborate

The collaboration is structured as an **iterative refinement loop that the translator controls**. As the translator works through a document, the relevant specialist agents surface targeted, dimension-labeled suggestions (e.g., an accuracy concern here, a terminology inconsistency there). The translator inspects these suggestions, decides which to accept, adapt, or ignore, and keeps editing. The system also builds a **Live Style Guide** — a visualization that summarizes the translator's own revision patterns over time, effectively reflecting their habits and idiosyncratic traits back to them as a form of personalized feedback.

## What role the human plays

The professional translator is the author and final decision-maker. They write and edit the translation, evaluate the multi-dimensional suggestions the agents raise, choose what to incorporate, and retain sign-off on the finished text. Their ongoing editing behavior also actively shapes how the system behaves next, via the live effort algorithm — so the human isn't just a downstream approver, they're continuously steering the collaboration.

## What role the AI agent plays

The AI side is organized as a **routed team of specialists** rather than one generalist. The Dimension Router triages each sentence and picks which quality-dimension agents are relevant; those agents independently generate revision suggestions grounded in shared reference material (glossaries, style guides, contextual metadata); and the live effort algorithm continuously re-weights the agents' focus based on how the translator is actually behaving, rather than applying a fixed, one-size-fits-all suggestion policy throughout the session.

## How control, initiative, and decisions are shared

This is a clear case of **mixed initiative with human final authority**: the AI agents proactively surface suggestions across multiple quality dimensions without being asked sentence-by-sentence, and the system adapts its own behavior based on the human's editing signals — but the translator is always the one deciding what actually goes into the final translation. The paper's design goal, in the authors' framing, is explicitly to preserve the translator's final authority while externalizing the multi-dimensional analysis work into structured, interpretable AI support, rather than handing decision-making to the AI.

## The paper's main idea

**Claim by the authors:** operationalizing the MQM quality framework as a set of specialized, coordinated AI agents — routed dynamically per sentence and adapted to the individual translator's editing behavior over time — gives professional translators more usable, better-structured AI support than either a single-shot AI translation or a single self-refining AI agent, because it maps onto how translators actually decompose and reason about quality.

## How the approach works

1. **MQM-as-agents:** Each MQM quality dimension (accuracy, terminology, locale/style, and others) is implemented as its own specialized agent capable of generating targeted revision suggestions for that dimension.
2. **Dimension Router:** For each unit of text and inferred translator intent, a router selects a relevant subset of agents from the larger pool, rather than running all agents on everything.
3. **Shared grounding:** Agents draw on shared memory resources such as glossaries, style guides, and contextual metadata so their suggestions stay consistent with project-specific terminology and style.
4. **Live effort algorithm:** The system tracks the translator's editing/interaction history during the session and uses it to adapt which agents are emphasized, aiming to match support to the translator's actual, changing needs rather than a static policy.
5. **Live Style Guide:** A feedback visualization summarizes the translator's own revision patterns, surfacing potential idiosyncratic habits back to them.
6. **Translator-controlled loop:** All of this feeds into an iterative refinement loop where the translator inspects, accepts, rejects, or edits suggestions, and retains final authority over the output.

## Human study or evaluation design

A **within-subject study** compared CHORUS against baseline conditions described as zero-shot AI translation and single-agent AI self-refinement. Each translator worked under multiple conditions, allowing direct within-person comparison of time, effort, and quality outcomes. Final translation quality was scored using the standard automatic machine-translation metrics **BLEU** and **COMET**, alongside translators' own reports of cognitive effort.

## Participants and study setting

**30 licensed English–Chinese professional translators** took part in the within-subject study. This is a real, credentialed professional population directly relevant to the paper's claims — not crowdworkers, students, or simulated users. Further recruitment and demographic detail (e.g., years of experience, employment setting) was not independently confirmed from the sources available in this session.

## Experiments or benchmarks

There is no public shared benchmark here; this is a custom, controlled comparative study using real translation tasks completed by the 30 professional participants under CHORUS versus baseline conditions, scored with BLEU/COMET plus translator-reported effort and qualitative feedback.

## Main results

**Reported consistently across cross-checked search excerpts:** CHORUS reduced task **completion time by 33.8%** relative to baseline conditions, **lowered translators' self-reported cognitive effort**, and **improved final translation quality** as measured by BLEU and COMET. Qualitative feedback indicated that the dimension-labeled agent suggestions made translation issues easier to inspect and reduced the need for translators to repeatedly re-prompt the AI, compared to single-agent baselines. Exact statistical tests, confidence intervals, and full result tables could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central human-performance outcomes are **efficiency** (time-on-task) and **effort** (self-reported cognitive load), both of which reportedly improved under CHORUS relative to baselines, alongside improved output quality. The qualitative finding that dimension-routed suggestions reduced "repeated prompting" and made issues "easier to inspect" points to a workload and usability benefit specifically tied to how AI support is structured and presented, not just to the AI's raw translation capability. This session could not confirm whether standardized trust or workload instruments (e.g., NASA-TLX, trust scales) were formally administered.

## What is genuinely new

- **MQM operationalized as agent architecture:** rather than treating translation quality dimensions as a scoring rubric applied after the fact, CHORUS turns them into the organizing structure for how AI agents divide labor and surface suggestions during the work itself.
- **A router that adapts per sentence and per translator:** the Dimension Router plus live effort algorithm means the mix of active agents isn't fixed — it responds to both the immediate text and the individual translator's observed editing behavior over the session.
- **A reflective feedback layer (Live Style Guide):** turning a translator's own revision history into a personalized summary of their habits is a distinct design contribution beyond simply generating better suggestions.
- **A real professional-population, within-subject evaluation** against both zero-shot and single-agent baselines — a comparison design that isolates the value of the multi-agent, dimension-routed approach specifically, rather than just AI-assistance-versus-no-assistance.

## Limitations and open questions

- **Single language pair and population.** The evaluation covers English–Chinese translation with licensed translators; how well the approach generalizes to other language pairs, domains (e.g., legal vs. literary), or less experienced translators is untested.
- **Automatic quality metrics alongside human effort.** BLEU and COMET are standard but imperfect proxies for translation quality; the paper pairs them with translator-reported effort, but independent expert quality review was not confirmed from the sources used here.
- **Within-subject study, single session design.** Longer-term effects — such as whether the Live Style Guide's habit-reflection actually changes translator behavior over weeks or months, or whether efficiency gains persist as novelty wears off — are open questions.
- **Sourcing caveat (this summary).** Because full-text access was blocked in this research session, exact statistics, full demographic details, and direct participant quotations could not be verified beyond what surfaced in cross-checked search excerpts; the earlier arXiv version of this paper reported a smaller six-translator preliminary study, and it was not possible to fully confirm from this session's sources whether every reported figure in the current 30-participant study is drawn from the identical experimental protocol as that pilot.

## Practical implications

For anyone building AI writing or translation tools aimed at professionals, CHORUS offers a concrete, testable design pattern: instead of one AI voice giving one blob of feedback, decompose quality into the dimensions your domain experts already use, assign specialized agents to those dimensions, route them dynamically per unit of work, and keep the human as the final editor-in-chief rather than a downstream approver of AI output. The reported gains in speed and effort, in a real professional population, suggest this kind of structured, dimension-aware multi-agent support may be a more usable middle ground than either raw one-shot generation or an autonomous self-refining agent.

## Why you should care

CHORUS is a rare case in agentic-AI research: a multi-agent system evaluated not on an autonomous benchmark, but on whether it actually helps real, credentialed professionals do their job faster and with less strain, while explicitly preserving their final authority over high-stakes output. As agentic AI spreads into other high-stakes professional editing and review contexts — legal drafting, medical documentation, technical writing — this paper is a useful, concrete data point for how to structure human-AI collaboration around the quality dimensions professionals already use, rather than around what's easiest for a single AI model to generate.
