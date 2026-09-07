# Delegating or Doing? Understanding User Behavior in Hybrid Human-Agent Interfaces

**Authors:** Gavin Raine Dizon, Tyrone Justin Sta. Maria, Jordan Aiko Deja, Yasuyuki Sumi (Future University Hakodate, Japan; De La Salle University, Manila, Philippines)
**Publication date:** 2026-08-20 (arXiv v1, id 2608.19551); revised 2026-08-25 (v2)
**Venue:** Accepted to HAI 2026 — the 14th International Conference on Human-Agent Interaction, Osaka, Japan (November 16–19, 2026)
**Paper link:** https://arxiv.org/abs/2608.19551 (PDF: https://arxiv.org/pdf/2608.19551)
**Code link:** Not available (no public repository found)
**Project page:** Not available
**Date added:** 2026-09-07

> **A note on sourcing:** this research session's network could not directly fetch arxiv.org, its mirrors, or other external paper-hosting sites (the outbound proxy blocked all of them by policy). This summary is therefore built entirely from the paper's abstract and cross-checked secondary descriptions gathered across many independent web searches, not a direct read of the full PDF. Facts corroborated across multiple independent searches (authors, dates, study design, participant count, and headline findings) are reported as such; anything that could not be cross-confirmed this way is marked "Not available" or flagged as uncertain rather than invented.

---

## The problem the paper addresses

Modern software increasingly gives you two ways to get something done: click through the interface yourself, or type a request to an embedded AI assistant that does it for you. But almost no research has looked at what happens when *both* options sit side by side in the same app, at the same time. Do people delegate everything they can? Do they stick with clicking because it feels safer? Or do they mix and match, task by task? This paper builds a real hybrid interface — half graphical, half conversational-agent — to find out.

## Why this problem matters

As LLM agents get wired directly into everyday business software (content management systems, CRMs, spreadsheets, admin dashboards) via protocols like MCP, designers face a concrete question: should the AI assistant be the default way to act, an optional shortcut, or something users have to be nudged toward? Getting this wrong wastes engineering effort on a delegation channel nobody uses, or worse, pushes people toward an AI path that doesn't actually save them time or effort. Since this trade-off will repeat across countless internal tools as agentic features get bolted onto existing software, real evidence about how people actually split their effort between "doing" and "delegating" is directly useful to product teams right now, not just in the abstract.

## What makes the system agentic

The authors built a web-based content management system augmented with an LLM agent connected through the Model Context Protocol (MCP). The agent doesn't just answer questions — it performs real CRUD (create, read, update, delete) operations against the application's backend on the user's behalf, executing the multi-step actions needed to complete a task (finding the right record, changing the right field, confirming the change) rather than producing a single text reply. Users could complete the same 16 task scenarios either by clicking through the standard graphical interface, by delegating the task to the conversational agent, or by freely mixing both within a single session — meeting the bar for an agent that acts on a goal via tool use in an external system rather than only chatting.

## How humans and the AI agent collaborate

The interface is genuinely hybrid: at every point, the user chooses whether to act directly (click, navigate, type into a form) or delegate the step to the LLM agent, which then executes the necessary backend operations and reports back. Nothing forces a single mode — a person can start a task manually and finish it by asking the agent, or the reverse, within the same scenario.

## What role the human plays

The human is the one deciding, moment to moment, how much control to hand over. Across 16 CRUD-based task scenarios, participants chose — freely, in the Hybrid condition — whether to complete each step themselves via the GUI or delegate it to the embedded agent, and the researchers logged that choice alongside clicks, page navigations, scrolling, and completion time.

## What role the AI agent plays

The agent is an on-demand executor: when delegated to, it interprets the request and carries out the corresponding create/read/update/delete operation against the CMS, standing in for the sequence of manual clicks and navigation the user would otherwise perform.

## How control, initiative, and decisions are shared

Control is split cleanly along a spectrum the study designed on purpose: a **Traditional-Only** condition (GUI only, no agent), an **AI-First** condition (agent-forward, delegation encouraged/default), and a **Hybrid** condition where both channels are always available and the user picks per task. This is a direct, controlled test of mixed-initiative, adaptive task allocation between a human and an agent, rather than a system where one side is fixed as "in charge."

## The paper's main idea

**Claim by the authors:** when both direct manipulation and AI delegation are available side by side, people's choice of which to use is driven less by which is objectively faster for a given task, and more by who the person is — their individual disposition and, notably, their trust in the agent — meaning delegation behavior is a personal/attitudinal pattern more than a rational task-by-task optimization.

## How the approach works

The team built a working CMS with standard GUI-based CRUD screens and layered an LLM agent on top via MCP, so the same backend actions were reachable either by clicking through the interface or by asking the agent in natural language. They then recruited participants into a between-subjects study, randomly assigning each person to one of the three interaction conditions (Traditional-Only, AI-First, Hybrid) and having them complete the same set of 16 scripted CRUD scenarios, while instrumenting the app to log every click, navigation, scroll event, delegation decision, and completion time.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, between-subjects human-participant experiment (not a simulation) comparing three interaction conditions on identical tasks, using both behavioral logging (clicks, navigations, scrolling, timing) and self-reported measures (trust and individual differences were analyzed in relation to delegation choices).

## Participants and study setting

**Real recruited participants:** N = 73 people, assigned between-subjects to the Traditional-Only, AI-First, or Hybrid condition. Exact demographic breakdown, recruitment method, and compensation were not available from the sources this session could access — consult the primary PDF for those details.

## Experiments or benchmarks

Not a public benchmark — a custom, purpose-built evaluation using 16 CRUD task scenarios inside the authors' own hybrid CMS prototype, compared across the three conditions.

## Main results

**Demonstrated in the paper (per available descriptions, not independently verified against the full PDF):**
- AI-assisted interaction significantly reduced low-level interaction effort — fewer clicks, page navigations, and scrolling actions — compared to the GUI-only condition.
- That reduced effort did **not** translate into faster task completion: total task duration did not differ significantly across the three conditions.
- Delegation behavior in the Hybrid condition correlated more strongly with individual differences and participants' trust in the agent than with objective task characteristics — i.e., who delegated and when tracked more closely with the person than with which task was objectively easier to hand off.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the study directly measured interaction effort (clicks/navigations/scrolling) and task completion time as behavioral outcomes, and examined trust and individual differences as correlates of delegation choice. **Our interpretation:** this is a meaningful, if modest, human-related finding — it suggests that the main benefit people got from having an AI agent available was not raw speed but a lower-effort way of working, and that who chooses to lean on the agent is shaped by disposition and trust as much as by the task itself. The paper does not appear to report standardized workload (e.g., NASA-TLX) or safety measures; its human-outcome evidence centers on effort/time logging and trust-related correlation analysis rather than a full battery of subjective scales.

## What is genuinely new

- A controlled, three-condition comparison (GUI-only vs. agent-first vs. freely hybrid) of the *same* underlying tasks in the *same* application, letting the authors isolate the effect of interface mode rather than comparing different tools or tasks.
- Direct behavioral evidence that lower interaction effort (fewer clicks/navigations) from delegating to an agent does not automatically mean faster completion — a useful corrective to the common assumption that "less clicking" equals "faster."
- Framing delegation choice as substantially a function of the person (individual differences, trust) rather than a rational, task-optimal decision, in a real hybrid interface rather than a hypothetical survey.

## Limitations and open questions

- This session could not fetch the full PDF, so exact statistics (effect sizes, p-values), the specific LLM/model used, full demographic details of the 73 participants, and the authors' own stated limitations could not be independently confirmed — readers who need precise methodology should consult the paper directly.
- The task domain is narrow (CRUD operations in a content management system); it is not established here how far the "delegation reflects the person, not the task" finding generalizes to higher-stakes or more open-ended agentic tasks.
- No code repository or public dataset was found, limiting independent replication at this time.

## Practical implications

For teams bolting LLM agents onto existing GUI-based software, this study is a caution against assuming that adding a delegation option automatically speeds people up: it may mainly reduce perceived effort rather than clock time, and adoption will likely hinge on individual users' trust and disposition rather than the interface simply presenting a faster path. That argues for designing hybrid interfaces that support both modes well and for measuring effort and trust separately from raw task-completion speed when evaluating an agentic feature's real value.

## Why you should care

A lot of agentic-AI product decisions are made on the assumption that "letting the AI do it" is a strict speed upgrade over doing it yourself. This paper's real, controlled, 73-participant test of a working hybrid interface pushes back on that assumption in a concrete way — and it does so by giving people an actual choice between doing and delegating on identical tasks, rather than asking them to imagine it. That combination of a genuinely agentic, tool-using system and a proper human-subjects comparison makes it a useful data point for anyone designing the next generation of human-agent hybrid tools.
