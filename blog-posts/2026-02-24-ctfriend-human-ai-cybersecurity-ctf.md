# Understanding Human-AI Collaboration in Cybersecurity Competitions

**Authors:** Tingxuan Tang, Nicolas Janis, Kalyn Asher Montague, Kevin Eykholt, Dhilung Kirat, Youngja Park, Jiyong Jang, Adwait Nadkarni, Yue Xiao (William & Mary and IBM Research, per cross-checked search-engine sources; not independently confirmed author-by-author)
**Publication date:** 2026-02-24 (arXiv v1)
**Venue:** USENIX Security 2026, under the title "From Assistance to Autonomy: An Empirical Study of AI Use in a Live Capture-the-Flag (CTF) Competition" (per the official USENIX program listing)
**Paper link:** https://arxiv.org/abs/2602.20446
**Code link:** Not available (the paper reportedly released CTFriend as a research tool, but no public repository URL could be independently confirmed)
**Project page:** Not available
**Date added:** 2026-08-29

> **A note on sourcing:** this session's outbound network access to arxiv.org (and to usenix.org, huggingface.co, and most other web domains) returned a blocked connection for direct fetches — an organization egress-policy restriction, not a paywall; the paper itself is a public arXiv preprint. This summary is therefore built entirely from cross-checked search-engine excerpts of the paper's abstract, methodology, and reported results, rather than a direct read of the full PDF. Facts corroborated across multiple independent search queries are presented as such; anything that could not be verified this way is marked "not available" or "not confirmed."

---

## The problem the paper addresses

When AI coding/hacking assistants show up at a cybersecurity competition, what actually happens when real competitors use them under time pressure? Most existing research either measures how well a fully autonomous AI agent can solve security challenges on its own, or studies AI assistance in artificial lab settings. This paper instead asks a more grounded question: in a live, onsite Capture-the-Flag (CTF) competition, how do human players actually perceive, use, and collaborate with an AI assistant — and how does that human-AI *team's* performance compare to AI agents working entirely alone on the same challenges?

## Why this problem matters

CTF competitions are a controlled but realistic proxy for real offensive-security work: participants have to find and exploit vulnerabilities against the clock, with objective pass/fail outcomes (you either capture the flag or you don't). As AI assistants get folded into real security workflows, understanding whether they genuinely help human experts — or just look impressive in isolated benchmarks — matters for how organizations should actually deploy them, and for what "collaboration" should mean when the AI can plausibly out-hack the human it's supposed to be assisting.

## What makes the system agentic

The paper's centerpiece, **CTFriend**, is not a single-turn chatbot. According to cross-checked descriptions of its architecture, it's a tool-augmented conversational agent built on a LangChain-based orchestration core that manages multi-turn conversational context and invokes external tools through the Model Context Protocol (MCP), with a Streamlit front end for the chat interface. It supports multiple LLM backends (the study used Claude-family models — Sonnet 4.5, Opus 4.1, and Haiku 3.5). Separately, the study also benchmarked four independent autonomous CTF-solving agents — systems that self-direct their own prompting and tool use to attack challenges without a human in the loop — on the same fresh challenge set, giving a direct agentic-AI-vs-agentic-AI-plus-human comparison.

## How humans and the AI agent collaborate

Participants chatted with CTFriend during a live CTF, asking it to help analyze challenge files, reason about vulnerabilities, or suggest exploitation steps. Critically, CTFriend keeps flag submission under human control — it doesn't act as an automatic solver — so the human decides what to try, what to trust, and when to actually submit an answer. The AI, in turn, can use its own tools to gather information or draft solutions, but its output flows back through the human before anything counts.

## What role the human plays

The human is the decision-maker and gatekeeper: they steer the conversation, choose which of the AI's suggestions to test, and hold final authority over flag submission. Over the course of the competition, participants also increasingly decided how much of a given subtask to hand off to the AI outright versus doing it themselves — an evolving, self-directed delegation decision rather than a fixed division of labor.

## What role the AI agent plays

CTFriend acts as an on-demand collaborator: reasoning about challenges, using its own tools when useful, and producing candidate exploits, code, or analysis in response to the human's prompts. In the separate benchmark arm, other AI agents played a fully autonomous role, solving challenges with no human input at all.

## How control, initiative, and decisions are shared

Initiative shifted over the course of the event. Per the authors' reported finding, as the competition progressed, teams increasingly delegated larger subtasks to the AI, effectively giving it more agency and autonomy within the session — a naturally occurring, human-driven adjustment of the human-AI division of labor rather than a fixed protocol imposed by the system.

## The paper's main idea

The authors' central empirical claim, as reported in available summaries, is that **the practical bottleneck in human-AI CTF collaboration is often not the AI's reasoning ability but the human's prompting effectiveness** — and that autonomous agents, by self-directing their own prompting and tool use, sidestep that bottleneck. This is presented as an explanation for why the standalone autonomous agents in the study reportedly outperformed most (though evidently not all) of the human-AI teams.

## How the approach works

The team deployed CTFriend as an opt-in assistant during a live, onsite CTF competition, instrumenting every conversation so it could later analyze the full interaction history. In parallel, they ran four autonomous AI agents through the same freshly written challenge set, producing an agent-only scoreboard to compare directly against the human-AI teams' results.

## Human study or evaluation design

This is an observational field study layered onto a real competition, combined with qualitative analysis of the resulting interaction logs and (per the USENIX abstract) pre/post surveys of participants' perceptions, trust, and expectations of the AI — administered before and after they actually used CTFriend hands-on.

## Participants and study setting

Per the USENIX Security 2026 program listing, 41 of the competition's 95 total participants opted to use CTFriend. The team reportedly analyzed 2,299 messages across 168 chat sessions, drawn from a subset of 38 participants with usable logs. This was a real, live, in-person CTF competition — not a lab simulation and not crowdsourced online work.

## Experiments or benchmarks

There was no standardized public benchmark; the evaluation used a freshly authored, competition-specific challenge set (so it couldn't have leaked into any model's training data). Four autonomous AI agents were benchmarked on the same challenges to produce a directly comparable agent-only score.

## Main results

According to cross-checked reporting on the paper: the standalone autonomous AI agents placed second overall in the competition, outperforming most of the human-AI teams. The authors' proposed explanation is that human prompting quality — not the underlying model's reasoning — was often the limiting factor for the human-AI teams, a bottleneck the self-directed autonomous agents didn't face. The qualitative analysis of chat logs is reported to have produced five findings spanning emergent interaction patterns, strategies associated with more successful collaboration, and the risks and rewards of relying on the AI; only some of these five are confirmable in detail from the sources available to this summary (see Limitations below).

## Effects on human performance, trust, workload, safety, or decision quality

The clearest human-centered finding reported across multiple sources: participants' *expected* future effectiveness of AI and their *willingness to use AI again* in future competitions both **decreased** after they actually used CTFriend hands-on, compared to their pre-competition expectations. Participants reportedly attributed this drop to recurring model failures they personally encountered — flawed reasoning, hallucinated details, and non-working exploit code — which eroded their trust in the AI's output. This decline was reportedly more pronounced among participants with higher pre-existing CTF expertise, consistent with more skilled users being better positioned to catch the AI's mistakes.

## What is genuinely new

- **Authors' claim:** a live, onsite, real-competition study of human-AI collaboration in offensive security, rather than a lab study or a purely autonomous-agent benchmark.
- **Demonstrated:** a direct, same-challenge-set comparison between human-AI teams and fully autonomous agents, within the same competition.
- **Demonstrated:** a measured pre-vs-post shift in participant trust and expected reliance on the AI, tied to specific failure modes participants observed.
- **My interpretation:** this is one of relatively few studies to show trust in an AI assistant declining after real hands-on use in a high-skill technical domain, rather than the more commonly reported pattern of novices over-trusting AI — a useful counterpoint for anyone assuming exposure to an agentic assistant reliably builds confidence in it.

## Limitations and open questions

The paper is a single-event, single-competition study, which limits how far its specific numbers generalize to other CTFs, other security domains, or non-competitive/lower-pressure work settings. This summary itself has a limitation worth being explicit about: because this session could not fetch the arXiv PDF or the USENIX page directly (network egress restrictions blocked those domains), several details — the exact content of all five qualitative findings, the paper's own stated limitations section, precise participant-count reconciliation (38 vs. 41 in different reported figures), and full author affiliations — are based on cross-checked search-engine excerpts rather than a direct reading of the source text, and should be verified against the primary PDF before being cited further.

## Practical implications

For organizations deploying AI assistants in security work, the results (as reported) suggest two things worth planning around: first, that effective prompting/tasking skill may matter as much as raw model capability for getting value out of a human-AI security team; and second, that trust built through marketing or demos may not survive real hands-on friction with a still-imperfect assistant — teams should expect skepticism to rise, not just fall, as people gain first-hand experience with a system's actual failure modes.

## Why you should care

This paper is a useful reality check against the assumption that pairing a skilled human with an AI assistant is strictly better than either working alone. In this study's onsite competition, autonomous agents reportedly beat most human-AI teams, and the humans who used the assistant came away *less* confident in it than before — a genuinely uncomfortable finding for anyone designing human-AI collaboration tools for expert domains, and a reminder that calibrated trust has to be earned through reliability, not assumed from capability.
