# (Im)Paired Programming: Coding Agents Improve Productivity but Harm Understanding

**Authors:** Nishant Balepur, Connor Baumler, Valerie Chen, Eunsol Choi, Rachel Rudinger, Jordan Lee Boyd-Graber
**Publication date:** 2026-07-29 (arXiv v1, id 2607.26375)
**Venue:** arXiv preprint (not yet confirmed as peer-reviewed at time of writing)
**Paper link:** https://arxiv.org/abs/2607.26375 (PDF: https://arxiv.org/pdf/2607.26375)
**Code link:** Not available (no dedicated public repository found for this study at the time of writing)
**Project page:** Not available
**Date added:** 2026-07-31

> **A note on sourcing:** arXiv was not directly reachable from this research session's network (the outbound proxy denies requests to arxiv.org under this session's egress policy), so this summary is built from the paper's abstract and cross-checked secondary descriptions gathered via web search, rather than a direct read of the full PDF. Facts that were consistently corroborated across multiple independent searches (authors, study design, sample size, and headline findings) are reported as such. Fine-grained statistics that would normally come from the paper's results tables (exact percentages, effect sizes, significance tests) were not accessible this way and are therefore *not* reported as specific numbers below — readers who need that level of detail should consult the paper directly.

---

## The problem the paper addresses

Modern "coding agents" (the kind built into tools like Cursor) don't just autocomplete a line of code — they can read a whole codebase, plan a multi-file change, and edit your files directly. That's a big shift from typing code yourself, or even from chatting with a bot and copy-pasting its answer. The paper asks a pointed question: when a coding agent does the editing *for* you, do you still learn and understand the code you end up with — well enough to keep working on it later without the agent's help?

## Why this problem matters

If developers (or students) increasingly "drive" an agent instead of writing code, and that agent quietly erodes their ability to read, debug, and extend their own codebase, that's a hidden cost that doesn't show up in a simple "did the task get done" metric. It matters for oversight (can you catch the agent's mistakes if you don't understand what it wrote?), for learning (are students who use agents actually building programming skill?), and for long-term productivity (can you maintain code you never really understood in the first place?).

## What makes the system agentic

The central object of study is a coding agent, in the mold of tools like Cursor, that operates inside a code editor: it reads the user's existing code and prompts, plans changes, and directly edits files across a multi-step session — rather than just returning a single chat response for the human to manually apply. That combination — multi-step planning and direct action inside a real coding environment, compared against a plain chatbot baseline — is what makes this an agentic AI system rather than a one-shot text generator.

## How humans and the AI agent collaborate

Each participant works with their assigned AI system across a coding task, choosing what to ask for, how much detail to give, and whether to review, edit, or simply accept the AI's output. With the coding agent, this can mean directly delegating edits to the agent; with the chatbot, it means writing code from scratch or manually adapting AI-suggested snippets. The paper specifically distinguishes different "interaction types" within the agent condition — for example, low-effort patterns like copy-pasting a prompt and auto-accepting whatever the agent produces, versus more effortful, engaged interaction — and studies how those interaction styles relate to what participants actually learn.

## What role the human plays

The 54 student participants are the ones building the actual product (a website), across two possible modes: using an agent that edits their code directly, or using a chatbot they must consult and then translate into code themselves (either writing it themselves or adapting generic snippets the chatbot provides). After building the site, participants are tested on their understanding of the resulting code and asked to extend it — this time without the AI's help — so the study can measure what they actually retained.

## What role the AI agent plays

In the agent condition, the AI is an active editor of the user's codebase: it takes the user's instructions and directly modifies the project files, aiming to get the website built with as little friction as possible. In the chatbot condition, the AI is more of an advisor: it can suggest code, but a human has to take that suggestion and put it into the project themselves, which the paper treats as a meaningfully different (and more manual) mode of collaboration.

## How control, initiative, and decisions are shared

Initiative shifts noticeably depending on condition and interaction style. With the coding agent, especially under "low-effort" usage (copy-paste prompting, accepting edits without review), most of the moment-to-moment coding initiative sits with the AI, and the human's role narrows to prompting and approving. With the chatbot, or with more effortful/engaged agent use, the human retains more hands-on control over what actually lands in the code. The paper's core contribution is showing that *where* this initiative sits has direct consequences for what the human ends up understanding.

## The paper's main idea

**Claim by the authors:** coding agents boost short-term productivity — helping users finish the immediate task faster — but this comes at a cost to the user's own understanding of the resulting code, especially when users interact with the agent in low-effort ways (e.g., copy-pasted prompts, auto-accepted edits). As a result, agent use does not prepare users to extend or maintain their own code without the agent's continued help.

## How the approach works

The authors ran a controlled study in which 54 students built a website using one of two AI systems: a coding agent that edits the user's code directly, or a chatbot, where the user either writes the code themselves or adapts generic snippets the chatbot provides. After the build phase, the study measures understanding through comprehension questions about the resulting code and a follow-up task requiring participants to extend that code *without* AI assistance — directly testing whether the collaboration left them capable of working independently afterward. The authors also characterize distinct interaction styles within the agent condition (e.g., low-effort copy-paste-and-accept versus more engaged prompting and review) and relate those styles to comprehension outcomes.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled study with real human participants (54 students) building a website under one of the two AI-assistance conditions described above, followed by a comprehension assessment and an unassisted code-extension task. This is a real, in-person(-style) human-AI collaboration study, not a simulated-user or LLM-only evaluation.

## Participants and study setting

**54 students**, each building a website with either a code-editing agent or a chatbot-based workflow. The exact demographic breakdown, course/institutional context, and between- vs. within-subject assignment could not be confirmed from the sources available in this session — consult the paper directly for those details.

## Experiments or benchmarks

There is no pre-existing public benchmark here; the "benchmark" is the custom website-building task itself, paired with a comprehension quiz and an unassisted extension task designed specifically for this study to probe understanding rather than just completion.

## Main results

**Demonstrated in the paper (per available descriptions):**
- Coding agents helped users complete the initial website-building task, consistent with a productivity benefit from agent-based editing.
- Despite that, agent use harmed participants' comprehension of the resulting code and left them less prepared to extend it on their own afterward, compared to the chatbot condition.
- Within the agent condition, low-effort interaction patterns — copy-pasting prompts and auto-accepting the agent's edits without review — were specifically linked to lower comprehension, suggesting the *way* people used the agent mattered as much as whether they used it.
- Despite self-reporting weaker understanding, participants still preferred the coding agent overall, because it was faster and easier to use.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central human-related finding is a **productivity–comprehension trade-off**: agent-based collaboration sped up task completion but measurably reduced participants' own understanding of, and readiness to independently extend, the code they produced — with the size of that comprehension cost tied to how passively or actively the person engaged with the agent. On the experience side, participants preferred the agent condition regardless of this comprehension gap, indicating a mismatch between what users say they want (speed, ease) and what actually best supports their own learning and long-term independence from the tool. **Our interpretation:** this is a concrete empirical illustration of a broader oversight risk raised elsewhere in this repository (e.g., "Overseeing Agents Without Constant Oversight" and "AI Writes Faster Than Humans Can Review") — if agent-assisted developers understand their own code less well, their capacity to catch agent mistakes or safely extend the system later is correspondingly weaker, even though they feel satisfied in the moment.

## What is genuinely new

- Directly measuring the *comprehension cost* of agentic (direct-edit) coding assistance against a chatbot baseline, using a real, unassisted follow-up task rather than only self-reported understanding.
- Distinguishing interaction *style* within agent use (low-effort copy-paste-and-accept vs. more engaged interaction) as a factor that predicts how much comprehension is lost — not just whether an agent was used at all.
- Surfacing the gap between user preference (agents are liked because they're fast and easy) and user outcome (agents leave people less able to work independently on their own code) as a specific, demonstrated tension rather than a general worry.

## Limitations and open questions

- The study population is students building a website — a specific educational/early-career setting; it is not established from available sources how far these comprehension effects generalize to experienced professional developers working on production codebases.
- Fine-grained statistics (exact comprehension score differences, effect sizes, significance levels, precise breakdown of interaction-style categories) could not be confirmed in this session because the full PDF was not reachable; readers needing precise numbers should consult the paper directly.
- It is not clear from available sources whether the study measured longer-term retention (e.g., days or weeks later) beyond the immediate follow-up extension task, or whether effects differ by task complexity or prior programming experience.

## Practical implications

If these findings generalize, they suggest that teams and educators adopting agentic coding tools should not treat "the agent got the task done" as the only success metric — the *way* people interact with the agent (skimming and accepting vs. reviewing and engaging) appears to matter for whether they retain the ability to maintain that code without the agent later. This points toward concrete design and process ideas: interfaces or workflows that nudge users away from pure copy-paste-and-accept usage, and deliberate practice or review steps built into agent-assisted workflows specifically to protect comprehension, not just throughput.

## Why you should care

This paper puts a real, human-measured number on a worry that's easy to state abstractly but hard to demonstrate: that letting an AI agent do your coding for you can quietly leave you less able to understand, debug, or extend your own software — even as it makes you faster and even as you end up preferring it anyway. For anyone thinking about human oversight of coding agents, or about how to safely fold agentic tools into engineering teams or classrooms, this is a concrete data point that "faster" and "better for the human in the long run" are not the same thing, and that *how* people use an agent shapes which of those two they get.
