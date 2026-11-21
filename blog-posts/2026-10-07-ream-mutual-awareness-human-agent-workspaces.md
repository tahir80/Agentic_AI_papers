# When Your AI Research Assistant Works Faster Than You Can Watch It

**Paper title:** Ream: Unfolding Mutual Awareness in Human-Agent Workspaces
**Authors:** Peiling Jiang, Sangho Suh, Varsha Kishore, Jonathan Bragg, Haijun Xia, Pao Siangliulue, Daniel S. Weld, Amy X. Zhang, Joseph Chee Chang (institutional affiliations not independently confirmed from the sources used; several authors — Jonathan Bragg, Daniel S. Weld, Pao Siangliulue, Joseph Chee Chang — are known from prior work to be associated with the Allen Institute for AI's Semantic Scholar research group, and Daniel S. Weld and Amy X. Zhang with the University of Washington, and Haijun Xia with UC San Diego, but this was not verified against the paper itself)
**Publication date:** 2026-10-07 (arXiv v1)
**Venue:** arXiv preprint, cs.AI and cs.HC (peer-reviewed venue not confirmed from sources used)
**Paper link:** https://arxiv.org/abs/2610.09497
**Code link:** Not available (the paper's appendix reportedly describes Ream as a web app built with React and an Elysia/Bun backend, but no public repository was found)
**Project page:** Not available
**Date added:** 2026-11-21

> **A note on sourcing:** this session's network access to arxiv.org and its usual mirrors (export.arxiv.org, alphaxiv.org, huggingface.co, semanticscholar.org, papers.cool) was blocked by this environment's network policy, so the full PDF could not be opened directly. This summary is built entirely from the paper's title, abstract fragments, section headings, and appendix excerpts as they surfaced across several web searches, cross-checked against each other for consistency. The paper itself appears to be a freely available, open-access arXiv preprint. Any number or claim below that could not be cross-confirmed is explicitly marked "not confirmed from sources used" — please check the arXiv preprint directly before citing specific figures.

---

## The problem the paper addresses

Imagine hiring a research assistant who reads, searches, and summarizes papers at superhuman speed — but who you can only talk to through a chat box. By the time you've typed a question about what they just did, they may already be three steps further along, and you have no easy way to see what they actually looked at, what they decided was important, or whether it still matches what you care about right now. Ream's authors call this a "mutual awareness" problem: in a shared workspace where a human and an AI agent are both working toward the same goal, each side needs an ongoing sense of what the other has done, is doing, and currently cares about — and today's chat-based agent interfaces don't really provide that.

## Why this problem matters

The authors pick literature review as the sharpest version of this problem: both the human researcher and the AI agent are simultaneously retrieving, reading, and synthesizing a growing, shared pile of papers. If the agent races ahead without the person noticing what it picked up or skipped, the person either has to constantly interrupt it to "catch up" (defeating the point of delegating) or just trust the output blindly (risking missed or misread papers). As LLM agents are increasingly used for exactly this kind of open-ended research work, the authors argue, the standard chat interface — where awareness is limited to whatever gets explicitly typed out — is a bottleneck for real collaboration, not just a minor UX inconvenience.

## What makes the system agentic

Ream's underlying system includes an agent that performs multi-step, autonomous retrieval and synthesis: it searches for and pulls in papers, reads/processes them, and produces structured outputs (not a single chat reply), feeding into a shared literature-review workspace. This goes well beyond a single-turn question-answering exchange — the agent is pursuing an open-ended research goal across many steps, using tools (retrieval) along the way, and its work is evaluated as an ongoing collaborative process rather than as a one-shot output.

## How humans and the AI agent collaborate

Instead of building more awareness features into the chat log, Ream makes the **shared work products themselves** — papers, notes, highlights, and other "structured artifacts" — the medium through which awareness flows. The system tracks, in both directions, what the human has engaged with (read, annotated, lingered on) and what the agent has engaged with (retrieved, cited, built upon), and surfaces this as localized visualizations attached to the artifacts, rather than as a separate status update or a wall of chat messages.

## What role the human plays

The human is a researcher conducting a real literature review. They read and annotate papers, and — crucially to the paper's argument — the system is designed so their evolving interests and areas of focus become visible to the agent even when they haven't explicitly typed them out in chat. They also use the awareness visualizations to inspect what the agent has been doing and to steer it toward (or away from) particular directions.

## What role the AI agent plays

The agent autonomously retrieves and works through literature relevant to the shared task, and its own activity — what it looked at, what it built on, what it hasn't gotten to yet — is made visible back to the human through the same artifact-centered visualizations, rather than requiring the human to ask "what have you done so far?" in chat.

## How control, initiative, and decisions are shared

This is a case of **mixed-initiative work with continuous bidirectional visibility**: both the human and the agent act independently and in parallel on a shared set of documents, and the system's main innovation is giving each party a steady, low-effort view into what the other is doing and caring about, so either side can adjust course — the human steering the agent, or the agent picking up on where the human's attention has shifted — without needing an explicit conversational turn to do so.

## The paper's main idea

**The authors' claim:** when humans and agents work concurrently on a shared, evolving body of material (rather than through back-and-forth chat), the key design lever is "artifact-centered mutual awareness" — tracking and visualizing each party's engagement with the shared artifacts themselves — rather than only logging the conversation between them. Ream operationalizes this through three mechanisms reported in the abstract: structured artifacts, bidirectional engagement tracking, and localized visualizations, combined with the agent's own retrieval capability.

## How the approach works

As the human reads and annotates papers in the workspace, and as the agent retrieves and works with papers, Ream logs this engagement on both sides and attaches lightweight, localized visual indicators directly onto the relevant artifacts (e.g., showing which papers the agent has drawn on, or which sections a person has focused on), rather than requiring either party to scroll through a chat transcript to reconstruct what happened. The exact visual design of these indicators was not confirmed from the sources used here.

## Human study or evaluation design

The paper reports (per available excerpts) two evaluation components: a monitored, in-lab study of a complete, continuous work session, and a separate longitudinal/field-deployment component testing whether the design holds up with repeated, less-controlled real-world use. One section heading found in the sources reads "Awareness visualizations help users inspect and steer agent work," suggesting this was one of the paper's explicit research questions, though the full set of research questions was not confirmed.

## Participants and study setting

The paper's abstract reportedly describes a user study involving **18 researchers** in total. Separately, appendix material referenced in search excerpts shows a monitored lab study with **12 participants** (labeled P1 through P12). It was not possible to confirm from the sources used whether the 12-participant lab study is a subset of the 18, or how the longitudinal field deployment's participant count relates to either figure — this should be checked against the primary paper.

## Experiments or benchmarks

No public agent benchmark is used; this is a system/design-research paper evaluated through real-user studies on real literature-review work, not an automated leaderboard task. There is no public dataset or benchmark release confirmed from the sources used.

## Main results

**As reported in available excerpts (not independently verified against the primary PDF):** across the lab and field studies, participants reportedly used the engagement-tracking visualizations to inspect evidence the agent had gathered, to steer the agent's ongoing work, to communicate through annotations, and to reflect on their own shifting research focus. In the monitored lab study, a notably large majority of participants — reported as **10 of 12** — asked, unprompted, to keep using Ream after the study ended without compensation, or to export the reports generated during their session. The field deployment is reported to have surfaced themes consistent with the lab study, suggesting the design held up outside a fully controlled setting, though specific field-study numbers were not confirmed.

## Effects on human performance, trust, workload, safety, or decision quality

*Based on available excerpts, not a full read of the paper:* the clearest human-related signal is the strong, spontaneous demand to keep using the tool (10/12 lab participants), which is suggestive of genuine perceived value rather than mere politeness, though it is a self-selected, uncompensated-continuation signal rather than a validated trust, workload, or decision-quality scale. The sources used did not surface standardized instruments (e.g., NASA-TLX workload scores, calibrated trust scales, or decision-accuracy metrics) — if the paper includes them, they were not found in the material available to this summary, and this should be treated as an open item to confirm directly against the paper.

## What is genuinely new

*Authors' framing, as surfaced in the sources used here:* rather than trying to make agents more awareness-friendly through richer chat (e.g., more detailed status messages or progress logs), Ream reframes awareness as something that should live on the **shared artifacts** both parties are actually working with — extending ideas from human-human collaborative-awareness research (e.g., from CSCW) into human-agent workspaces, and pairing this with an agent that has its own retrieval capability so its activity has something concrete to attach awareness signals to.

## Limitations and open questions

- *My interpretation:* the core lab study (reportedly 12 participants) is small, and it was not possible to confirm from available sources what the comparison condition was (e.g., a chat-only baseline) or what was quantitatively measured beyond qualitative themes and the "wanted to keep using it" signal.
- The relationship between the "18 researchers" figure and the "12 lab participants" figure is unclear from the sources used and should be checked against the paper directly.
- No confirmed quantitative results on accuracy, time, or trust/workload scales were found in the sources used — the summary here relies on qualitative, thematic reporting rather than statistics.
- Code, demo, and project-page availability could not be confirmed; the system's apparent scale (reported as roughly 66,000 lines of TypeScript) suggests it is a substantial custom build, which may limit easy reproducibility or reuse by other researchers.
- The domain tested is specifically literature review; how well "artifact-centered mutual awareness" generalizes to other shared human-agent work (e.g., coding, data analysis, writing) is an open question the paper does not appear to test directly.

## Practical implications

*My interpretation, following the authors' own stated motivation:* builders of research-assistant and other long-running agentic tools might get more effective, lower-friction human oversight by attaching lightweight awareness signals directly to the shared documents or artifacts an agent and a person both touch, rather than relying solely on a chat log to communicate what each side has done or currently cares about. This could be especially relevant for any tool where an agent is expected to work semi-independently over an extended session (not just answer single queries) while a person periodically checks in and redirects it.

## Why you should care

As AI agents are increasingly asked to do open-ended, multi-step work alongside a person — gathering sources, drafting, analyzing — rather than just answering one question at a time, simply watching a chat transcript stops being a workable way to stay in the loop. Ream's authors offer a concrete alternative: make the *things you're both working on* carry the signal of who did what and who cares about what, rather than leaving that entirely to conversation. The early evidence here — a design-research study with a modest number of real researchers, not a large randomized trial — points toward this being a promising direction rather than a settled answer, but the strength of the "people wanted to keep using it unprompted" signal is a meaningful, if informal, indicator that the approach resonated with the people who tried it.
