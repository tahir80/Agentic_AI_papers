# InsightToast: Proactive Information Retrieval & Glanceable Visualization in the Side Channel of Data-Rich Meetings

**Authors:** Mohammad Abolnejadian, Matthew Brehmer (School of Computer Science, University of Waterloo)
**Publication date:** 2026-08-31 (arXiv id 2608.31115, v1, cs.HC)
**Venue:** To appear at the 39th Annual ACM Symposium on User Interface Software and Technology (UIST '26), November 2026
**Paper link:** https://arxiv.org/abs/2608.31115
**Code link:** https://github.com/ubixgroup/InsightToast
**Project page / dataset:** https://zenodo.org/records/21502545 (Canadian Parliament Open Data and Embedded Vector Knowledge Base, UIST '26 supplemental dataset)
**Date added:** 2026-09-23

> **A note on sourcing:** arXiv.org, and most other academic-paper mirrors (alphaXiv, bytez, Semantic Scholar, Hugging Face Papers, AISeL, etc.), were unreachable from this research session's network (the fetch tool is blocked for those domains). This summary is therefore built from multiple rounds of web-search-grounded excerpts of the paper's abstract, introduction, methodology, and reported results — including its GitHub repository description — rather than a direct PDF read. Facts below reflect what those excerpts report; anything not confirmed is marked "not available," and interpretive statements are labeled as such.

---

## The problem the paper addresses

Picture a meeting where a group of people has to make a decision using a pile of background documents — reports, datasets, prior briefings. Every time someone says "wait, what did that report actually say?" or "do we have the numbers on that?", someone has to stop talking, open a laptop, search for the document, and read it — breaking the flow of the conversation. The paper calls this "costly task-switching": pulling up the right information from scattered sources takes people's attention away from each other and from the discussion itself, right when they most need to be thinking clearly together.

## Why this problem matters

This isn't a small inconvenience. The paper points out that this kind of disruption is worst exactly when it matters most: during cognitively demanding, high-stakes decision-making, where a team needs both the right facts and an uninterrupted train of thought. Existing tools force a choice between "keep talking without the facts" or "stop talking to go find them." Neither is good. The paper is chasing a genuinely open problem in human-AI collaboration: how can an AI system supply the right information at the right moment, without anyone having to ask for it, and without breaking the human conversation it's supporting?

## What makes the system agentic

InsightToast isn't a static search box that waits for a query. According to the paper and its accompanying GitHub repository, it runs a 15-agent, LangGraph-orchestrated pipeline (served by a FastAPI backend) that continuously: (1) listens to the live conversation and tracks its evolving topics, (2) autonomously decides when an information gap has emerged and searches across a knowledge base — in the evaluated scenario, a vector-embedded archive of Canadian Parliament legislative documents — using retrieval-augmented generation (RAG), and (3) synthesizes what it finds into a short, source-grounded insight (a text snippet or an interactive chart). This is real-time, multi-step, tool-using behavior — monitoring an environment (spoken conversation), deciding for itself when to act, retrieving from external data sources, and producing structured outputs — sustained continuously over a live meeting rather than a single request-response exchange, which is what makes it agentic rather than a simple lookup tool.

## How humans and the AI agent collaborate

The collaboration is explicitly mixed-initiative. The humans never ask InsightToast anything directly — they just talk to each other, as normal. The agent listens in the background and decides, on its own initiative, when to surface something useful. The humans, in turn, retain full control over what happens next: they can glance at a "toast" notification, ignore it, expand it into a chart, or fold it back into the conversation. Neither side waits for explicit turn-taking; the agent injects information proactively, and the humans decide moment-to-moment whether and how to use it.

## What role the human plays

Participants in the study played the role of meeting participants: they held real conversations aimed at reaching an informed group decision (in the evaluated scenario, on which legislative petitions to support), while InsightToast — or, in the comparison condition, a conventional on-demand search interface — ran alongside. Their job was simply to discuss and decide, using whichever information tool was active; researchers then measured how that tool shaped their conversation and their confidence in the resulting decision.

## What role the AI agent plays

The agent is the information-fetching, information-surfacing partner. It listens continuously, infers from the discourse when a factual or contextual gap has opened up, retrieves relevant material through its RAG pipeline, and delivers it unobtrusively — as a "glanceable" toast in a peripheral side channel — so participants can absorb it without derailing their conversation.

## How control, initiative, and decisions are shared

Initiative over *information retrieval* sits mostly with the agent (it decides when and what to fetch), while initiative over the actual conversation and decision stays entirely with the humans. This is a clean division of labor: the AI takes the proactive, background role of "keeping up with what the group might need," while people keep full ownership of the discussion and the final call. It's a concrete, deployed example of mixed-initiative interaction as a design choice, not just a conceptual ideal.

## The paper's main idea

**Claim by the authors:** if an AI system can track a live conversation well enough to know when relevant background information exists — and can retrieve and summarize it accurately and unobtrusively — it can let a group make better-informed decisions *without* forcing anyone to stop and search, by delivering that information as glanceable, source-grounded, peripheral notifications rather than as a full-attention interruption.

## How the approach works

**Demonstrated in the paper:** InsightToast's pipeline continuously transcribes and tracks the conversation to maintain topic context, then performs "multi-faceted proactive retrieval" across indexed sources (in the study, a knowledge base of legislative documents) whenever it detects an emerging informational need, and finally synthesizes the retrieved material into brief text or an interactive chart. Each surfaced insight is traceable back both to the moment in conversation that triggered it and to the specific source documents it came from, so participants can verify where the information came from rather than taking it on faith.

## Human study or evaluation design

**Demonstrated in the paper:** a within-subjects comparative study (N=16) in which each participant experienced both InsightToast and a baseline condition — a conventional, on-demand search interface — while working through a legislative-decision-making conversation task. After each condition, participants completed a questionnaire covering information-retrieval and decision-making effectiveness (drawing on established Satisfaction-with-Decision measures), workload, conversational engagement, and system usability, and the session ended with a semi-structured interview comparing the two conditions and reflecting on real-world adoption.

## Participants and study setting

**Demonstrated in the paper:** 16 participants (8 men, 8 women), predominantly graduate students (13 graduate, 3 undergraduate) from computer science and other fields, recruited via departmental mailing lists using purposive sampling stratified by familiarity with federal politics and by how often participants attended meetings involving data. Eleven participants attended in person and five joined remotely (on 13–14 inch screens). The study was approved by the University of Waterloo's research ethics board, and participants received a $25 CAD gift card. The task scenario used real, publicly available Canadian Parliament legislative documents as the shared knowledge base.

## Experiments or benchmarks

There is no public agent benchmark here; the "experiment" is the controlled, within-subjects human study itself, comparing InsightToast against a manual, on-demand search baseline on the same decision-making task. The paper also releases its Canadian Parliament document collection and embedded vector knowledge base as a supplemental dataset on Zenodo, which could support future comparative studies using the same materials.

## Main results

**Demonstrated in the paper (as reported in available excerpts):**
- InsightToast scored higher than the baseline search interface on five information-retrieval and decision-making measures (on 1–5 Likert scales).
- Participants reported reaching informed policy decisions while maintaining a more natural conversational flow under InsightToast than under the baseline.
- The system's proactive, multi-faceted retrieval was reported to preserve conversational flow better than having to actively pause and search.

**Not confirmed from available excerpts:** the exact numeric values, effect sizes, or statistical significance tests for each of the five measures; full breakdowns of the semi-structured interview themes.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper (based on available excerpts):** better self-reported information-retrieval and decision-making outcomes and improved conversational flow when using InsightToast, relative to manual search, on a task explicitly designed to be cognitively demanding and decision-oriented. Workload, engagement, and usability were all measured via questionnaire, though the specific comparative numbers on each of these individually could not be confirmed from the sources used. **Our interpretation:** the framing of the results — "scored higher on five measures" plus qualitative reports of smoother conversation — suggests a genuinely positive, if modestly scaled (N=16), effect on decision-making experience, rather than a large-scale, high-power quantitative trial; readers should treat this as an initial, promising design evaluation rather than definitive proof of real-world impact.

## What is genuinely new

- A working, real-time, 15-agent RAG pipeline that listens to live speech and proactively decides *when* to retrieve information, rather than answering only on explicit request — a nontrivial step beyond typical query-triggered RAG assistants.
- Delivering AI-agent output through a genuinely peripheral, "glanceable" side channel (ephemeral toast notifications with brief text or interactive charts) designed specifically to avoid breaking conversational flow, rather than through a chat window that demands full attention.
- A head-to-head, within-subjects comparison of proactive agentic delivery against a conventional on-demand search baseline, on a realistic group decision-making task grounded in real government documents, with a released dataset enabling replication.

## Limitations and open questions

- The study is modest in scale (16 participants, predominantly graduate students), which limits how confidently the findings generalize to other populations (e.g., working professionals, larger meetings, or non-English-speaking teams) or other meeting types.
- Full statistical detail (effect sizes, significance values per measure) could not be confirmed from the sources available to this summary, so the strength of the "scored higher on five measures" claim cannot be independently assessed here.
- The evaluated scenario is a specific kind of task (small-group legislative-petition decisions using a legislative document knowledge base); how well the proactive-retrieval approach generalizes to other domains, larger meetings, or messier real-world data sources than the curated Canadian Parliament dataset is an open question.
- As with any system that continuously listens to and analyzes conversation, there are unresolved practical questions around privacy, consent, and appropriate use in real organizational settings — these were not confirmed as being directly addressed in the excerpts available.

## Practical implications

For designers of meeting-support tools, virtual assistants, or any agent meant to operate alongside — rather than instead of — a live human conversation, InsightToast offers a concrete pattern: give the agent initiative over background information-gathering, but keep its delivery peripheral and glanceable so the humans retain control of the conversation itself. It's a template for "ambient" agentic assistance, distinct from chatbot-style AI that requires an explicit prompt to act.

## Why you should care

InsightToast is a rare case of an agentic AI system that is both genuinely autonomous (a real-time, multi-agent retrieval pipeline making its own decisions about when to act) and directly evaluated for its effect on a live human group's collaboration and decision-making — not just benchmarked on retrieval accuracy in isolation. If you care about how AI agents should share initiative with humans in real, high-stakes group settings, this is a concrete, recently published (August 2026), openly available data point, complete with code and a released dataset for others to build on.
