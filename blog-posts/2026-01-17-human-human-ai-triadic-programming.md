# When Two Humans and an AI Code Together: What Happens to Learning and Trust?

**Paper title:** Human-Human-AI Triadic Programming: Uncovering the Role of AI Agent and the Value of Human Partner in Collaborative Learning
**Authors:** Taufiq Daryanto, Xiaohan Ding, Kaike Ping, Lance T. Wilhelm, Yan Chen, Chris Brown, Eugenia H. Rho (Virginia Tech, based on available sources)
**Publication date:** 2026-01-17 (arXiv v1); presented at CHI 2026 (April 13–17, 2026)
**Venue:** ACM CHI Conference on Human Factors in Computing Systems (CHI '26)
**Paper link:** https://arxiv.org/abs/2601.12134
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-07-27

---

## The problem the paper addresses

Most research on AI coding assistants studies one of two setups: two humans programming together, or one human programming with an AI helper. The paper argues that as AI assistants get folded into everyday programming, they are usually designed and studied as a *replacement* for a human partner — a single learner plus a chatbot — rather than as an *addition* to an existing human partnership. That framing, the authors say, overlooks the social and learning-oriented dynamics that happen specifically when people collaborate with each other, like explaining your reasoning out loud, noticing what your partner is doing, or feeling accountable to someone who's watching your work.

## Why this problem matters

Pair programming is taught and used precisely because working with another person changes how people learn — you talk through problems, catch each other's mistakes, and build shared understanding. If schools and companies simply swap in an AI assistant instead of a human partner, they may get faster code but lose those learning benefits. Understanding whether an AI can be added *alongside* a human partner — instead of replacing one — matters for how programming education and pair-programming practices are redesigned around AI tools.

## What makes the system agentic

The researchers built a custom collaborative programming environment in which an AI agent is a third participant, not just a query box. According to the authors, the agent supports multimodal interaction (voice, text, code typing, and interactive controls), observes the ongoing conversation and code, and is **proactive** — it can decide on its own when to jump in with a suggestion — while also remaining available on demand when a participant explicitly asks it something. That combination of self-initiated action and responsiveness to explicit requests is what puts this system in agentic territory rather than being a simple autocomplete or chatbot.

## How humans and the AI agent collaborate

Two human participants and the AI agent share a live programming workspace. The AI can watch the pair's conversation and code, choose to interject with help, or wait to be asked. The two humans can talk to each other, to the AI, or observe each other's interactions with the AI — all in the same session.

## What role the human plays

Participants write code, discuss the task with their human partner, decide whether to accept or question the AI's suggestions, and — critically — are aware that their partner can see how they're using the AI. This visibility is a key ingredient in the study's design.

## What role the AI agent plays

The AI agent acts as a third collaborator: it proposes code and suggestions, can proactively step in when it judges it's useful, and answers direct requests. It is designed to *augment* the human pair's collaboration rather than to replace either teammate.

## How control, initiative, and decisions are shared

Initiative is split three ways. The AI can take initiative (proactive suggestions) or wait for a human to request help (on-demand). Between the two humans, either partner can lead the coding, question the AI, or bring the group's attention back to the task. This is a mixed-initiative setup layered on top of a two-person collaboration, rather than a single human directing a single AI.

## The paper's main idea

The core idea is "triadic programming": add the AI as a genuine third participant in an existing human-human collaboration, and compare that to the more commonly studied setup of one human working alone with an AI (a "dyadic" human-AI pair). The authors also compare two ways of positioning the AI within the triad — reported in available sources as a shared versus a more personal/individual configuration — to see whether making the AI's use visible to a partner changes behavior.

## How the approach works

The team built the multimodal triadic environment described above and ran a controlled, within-subjects study where the same pairs of participants tried different collaboration setups (a dyadic human+AI baseline and triadic human-human-AI conditions) on programming tasks, so each pair's behavior could be compared across conditions.

## Human study or evaluation design

This is a **within-subjects study with real human participants** — not a simulation. Twenty people, organized into ten pairs, each went through multiple conditions: a dyadic human-AI baseline and the triadic human-human-AI setups, working on programming tasks in the researchers' custom environment.

## Participants and study setting

**20 participants (10 pairs)**, recruited for a hands-on lab-style study (consistent with a CHI human-subjects submission). Exact recruitment criteria, demographics, and compensation were not confirmed from the sources accessible in this session.

## Experiments or benchmarks

There is no public benchmark here — this is a custom, researcher-built study comparing conditions (dyadic HAI vs. triadic HHAI variants) on programming tasks designed for the study, not a standardized leaderboard.

## Main results

- Triadic (human-human-AI) collaboration produced **higher social presence and better collaborative learning** than the dyadic human-AI baseline, according to the authors.
- Participants in the triadic conditions **relied significantly less on AI-generated code** than in the dyadic baseline — they treated AI output more critically rather than accepting it outright.
- This effect on reliance was **strongest in the "shared" triadic condition**, where participants reported an increased sense of responsibility to understand the AI's suggestions before applying them, apparently because they knew their partner could see how they were using the AI.
- Participants described multiple new ways of learning that only emerged in the triadic setup: watching their partner interact with the AI, and learning by explaining ideas to their partner.

## Effects on human performance, trust, workload, safety, or decision quality

The clearest human-centered outcome is on **reliance and accountability**: having a visible human partner in the loop made people more careful and responsible about how they used AI-generated code, rather than accepting suggestions passively. The authors also report higher self-reported social presence (a sense of collaborating with another mind) in the triadic conditions. The paper does not report objective code-quality or task-completion-time differences in the sources available for this summary — the confirmed results are about reliance behavior and self-reported collaborative/social experience.

## What is genuinely new

The novel contribution is the **triadic framing itself**: instead of asking "does AI help a solo learner?", the paper asks "what changes when AI is added to an existing human pair, and does making that AI use visible to a partner change how people rely on it?" The finding that a *visible peer* — not the AI's own design — is what most changed participants' scrutiny of AI suggestions is, per the authors, a distinctive result.

## Limitations and open questions

- Small sample: 20 participants (10 pairs), typical for a controlled lab study but limiting generalizability.
- A custom research environment and researcher-designed programming tasks — not a mainstream production coding tool, so real-world transfer is untested.
- The study is set in a learning/educational programming context; whether the same accountability effect holds in professional, higher-stakes software engineering work is an open question.
- Exact statistical results (e.g., specific significance values, effect sizes) were not independently confirmed from the sources accessible in this session — the full PDF could not be fetched.

## Practical implications

The results suggest that programming-education tools and pair-programming setups shouldn't automatically hand each learner their own private AI assistant. Keeping a human partner visibly present — able to see how a teammate is using AI — appears to encourage more careful, accountable use of AI-generated code, and may preserve some of the learning benefits that come from working with another person.

## Why you should care

If you build, teach with, or study collaborative coding tools, this paper offers a concrete, human-tested reason to think about *who else is watching* when someone uses an AI coding assistant. It's a reminder that some of the safety and learning value of "having a human in the loop" may come specifically from social accountability to another person — not just from having a human somewhere near the system.

---

*Claims above distinguish, where possible, between what the authors state (e.g., their interpretation of why the "shared" condition had the strongest effect) and what was measured (reliance on AI-generated code, self-reported social presence, and qualitative participant reports). Precise statistical figures were not accessible in this session; readers wanting exact numbers should consult the full paper at the link above.*
