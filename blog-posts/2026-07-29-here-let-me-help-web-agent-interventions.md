# "Here, Let Me Help": What Happens When You Interrupt a Web Agent Mid-Task?

**Authors:** Joohee Kim, Sungbeom Cho, Duc M. Nguyen, Jaehyeong Jeon, Minjeong Shin, Sungahn Ko (South Korea; the senior author's lab works on human-AI visual analytics — exact institutional affiliations for all six authors not independently confirmed from available sources)
**Publication date:** 2026-04 (presented at ACM CHI 2026, April 23–28, 2026, Hamburg, Germany; exact submission/acceptance date not confirmed)
**Venue:** ACM CHI Conference on Human Factors in Computing Systems (CHI '26) — received an Honorable Mention Award (top 5% of accepted papers)
**Paper link:** https://dl.acm.org/doi/10.1145/3772318.3791536
**Code link:** Not available (no public repository found for this paper at the time of writing)
**Project page:** Not available
**Date added:** 2026-07-29

> **A note on sourcing:** direct network access to academic hosts (arxiv.org, huggingface.co, dl.acm.org, and even general web pages) was blocked or unreachable from this research session's network for every fetch attempted, so this summary is built entirely from cross-checked search-engine excerpts of the paper's abstract, methods, and results rather than a direct read of the full PDF or HTML. ACM's Digital Library moved to full Open Access starting January 1, 2026, so this CHI 2026 paper should be freely readable there — but we could not independently verify that access worked in this session. Facts below that were corroborated across multiple independent search queries are presented as such; anything that could not be verified is marked "not available" or "not confirmed."

---

## The problem the paper addresses

"Web agents" — AI systems that can browse real websites, click buttons, fill out forms, and complete tasks like booking a trip or buying a product — are moving from research demos into everyday tools. Most research on these agents asks one question: did it finish the task successfully? This paper argues that's the wrong lens for understanding how people actually work *with* these agents. In practice, users don't just wait passively for a web agent to succeed or fail — they watch it work, and often step in mid-task: pausing it, correcting it, nudging it in a different direction, or quietly preparing something in the background so the agent does the right thing next. The paper studies that in-the-moment intervention behavior directly, rather than only the end result.

## Why this problem matters

If a web agent is going to book your flight or place an order with your money, most people won't want to just fire off a request and walk away — they'll want the ability to catch a mistake before it becomes a $400 plane ticket to the wrong city. But agent interfaces today are largely built around a "set it and check the result" model, with little support for the many different ways a person might actually want to step in while the agent is still working. Understanding the real shape of that intervention behavior — not just "did they hit stop," but *why*, *when*, and *how* — is a prerequisite for designing agent interfaces that actually support safe, comfortable collaboration rather than forcing an all-or-nothing choice between full autonomy and full manual control.

## What makes the system agentic

The system studied is a **web agent**: given a goal in natural language, it autonomously plans and executes a sequence of actions on real, live websites — navigating pages, clicking elements, filling in forms, and carrying a task through to completion (e.g., completing a purchase or a booking) without being told each individual step. That multi-step, tool-using, environment-interacting behavior — evaluated by whether the agent actually completes real tasks on real websites, not just by the quality of a single text reply — is what makes this an agentic AI system rather than a conversational assistant.

## How humans and the AI agent collaborate

Collaboration here is defined by **real-time intervention during live execution**: the agent runs autonomously by default, and the human's role is to decide, moment to moment, whether to let it continue, stop it, redirect it, or quietly adjust the environment around it (for instance, changing a setting on the page) so the agent's next actions go the way the user wants. This is a live, in-the-loop form of collaboration — not a one-shot prompt followed by a final review, but an ongoing relationship between what the agent is doing and what the human notices and chooses to do about it.

## What role the human plays

The human is a supervising collaborator with the standing ability to interrupt. Across 12 structured tasks, participants watched the agent work on real websites and, whenever something concerned them or an opportunity to help arose, could either explicitly halt and override the agent's ongoing action, or implicitly guide or prepare the environment without fully stopping it. After each task, participants rated their satisfaction, trust, and the agent's effectiveness, and later took part in semi-structured interviews explaining why they intervened when they did — and, implicitly, why they sometimes didn't.

## What role the AI agent plays

The agent is the task executor: it interprets the user's goal, plans a sequence of actions, and carries them out autonomously on live websites across shopping, travel, and information-seeking domains, continuing to act unless and until the user intervenes. The paper describes participants as being at an "early-stage" of web-agent adoption — experienced with general-purpose AI chat tools like ChatGPT and Gemini, but largely unfamiliar with agents that act on their behalf in a live browser — which shapes how cautiously or trustingly they treated the agent's autonomy.

## How control, initiative, and decisions are shared

The paper's central contribution is a **taxonomy of intervention**, built from what participants actually did rather than a predefined checklist:

- **Explicit interventions** — the user deliberately halts or overrides the agent's ongoing action. These are further split by *target*: interventions directed at the agent itself (e.g., telling it to stop or change course) versus interventions directed at the web interface it's operating in.
- **Implicit interventions** — the user guides or prepares the environment (for example, adjusting something on the page) without fully interrupting the agent's current action, letting it continue while steering its next steps.

Rather than a single "human approves / agent proceeds" gate, this frames human-agent control-sharing as a spectrum of intervention styles that differ in how forcefully and how directly the human interrupts the agent's flow.

## The paper's main idea

**Claim by the authors:** understanding human-web-agent collaboration requires looking beyond outcome-based success metrics to the intervention behaviors that unfold *during* task execution — and these behaviors are diverse enough (explicit vs. implicit, agent-directed vs. interface-directed) that a fuller taxonomy is needed to design agent interfaces that support the way people actually want to stay involved.

## How the approach works

The researchers built a controlled study environment where a web agent operated on real, live websites to complete concrete tasks (e.g., shopping for a product, planning part of a trip, looking up information), while participants could intervene at any point. They recorded interaction logs, exactly when and why participants chose to stop or redirect the agent, and screen recordings of each session, then combined this behavioral data with post-task Likert-scale ratings (satisfaction, trust, effectiveness, ease of completion) and semi-structured interviews to build an inductive taxonomy of intervention reasons and forms.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, in-lab study in which each of 30 participants completed 12 tasks — drawn from 6 task designs spanning 3 domains and implemented on 6 different live websites — while the researchers logged the agent's actions, the participant's intervention behavior, and their subjective ratings after each task, followed by a semi-structured interview.

## Participants and study setting

**Demonstrated in the paper:** 30 university-affiliated participants, ages 18–35, who reported experience with general AI chat tools (ChatGPT, Gemini) but were largely unfamiliar with autonomous web agents — i.e., real, hands-on participants encountering this kind of agent for close to the first time, not a simulated or synthetic evaluation. Exact recruitment method, compensation, and gender/demographic breakdown are not confirmed from available sources.

## Experiments or benchmarks

There is no public, named benchmark. The study used 12 structured tasks (6 task designs × domain variants) across shopping, travel, and information-seeking, run against 6 real, live websites rather than sandboxed or simulated pages — meaning participants were interacting with the actual sites, not a mock-up.

## Main results

**Demonstrated in the paper (per available descriptions):**
- Participants used a genuinely varied set of intervention styles rather than a simple stop/don't-stop decision, motivating the explicit/implicit, agent-directed/interface-directed taxonomy described above.
- Satisfaction, perceived effectiveness, and trust in the agent were all **strongly and positively correlated with one another (r = .73–.87, p < .001)** — participants who trusted the agent more also tended to rate it more effective and reported higher satisfaction, and vice versa.
- The paper's qualitative interview data (exact themes not independently confirmed from available sources) reportedly explains *why* participants chose particular intervention styles at particular moments, connecting intervention behavior back to trust and perceived risk.
- Exact per-category intervention frequencies (e.g., what share of interventions were explicit vs. implicit) were not independently confirmed from available sources.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated in the paper:** the tight correlation between trust, satisfaction, and perceived effectiveness (r = .73–.87) is the paper's clearest quantitative human-outcome finding — it suggests that how much people trust a web agent and how they feel about the collaboration are not separable from each other in this setting. **Authors' framing / our interpretation:** because these measures move together so strongly, the paper's broader argument is that supporting the right kind of intervention (not just "any" stop button) is likely to be a lever for improving trust and satisfaction simultaneously, though the study is correlational and does not establish that a specific interface change causes trust to rise.

## What is genuinely new

- A **behaviorally derived taxonomy of intervention** in human-web-agent collaboration (explicit vs. implicit; agent-directed vs. interface-directed), built from what real users actually did during live agent execution rather than assumed a priori.
- A live, real-website (not sandboxed) evaluation environment across three practically important domains — shopping, travel, and information-seeking — capturing intervention behavior with agents genuinely acting on production websites.
- Direct quantitative linkage between trust, effectiveness, and satisfaction (r = .73–.87) in a live human-web-agent-interaction setting, rather than in a hypothetical or survey-only context.

## Limitations and open questions

- **Small, single-population sample** (n=30, university-affiliated, ages 18–35) — generalization to broader populations (older users, non-students, professional contexts) is untested.
- **One class of web agent tested**, described by the authors as reflecting "early-stage" web-agent adoption; how the taxonomy holds up for more capable or differently designed agents is an open question.
- **Self-reported trust/satisfaction/effectiveness measures** — strong correlations don't establish which factor drives which, or whether a specific interface change would improve trust causally.
- We were unable to independently verify additional details (full statistical reporting, exact task instructions, demographic breakdown, or supplementary/interview materials) since the full text could not be fetched in this session due to network restrictions — readers who need precise details should consult the paper directly via the ACM Digital Library link above.

## Practical implications

If the taxonomy generalizes, it gives builders of agentic browsers, shopping assistants, and travel-planning agents a concrete design vocabulary: interfaces should support not just a single "stop" button, but distinguishable ways to intervene — directly overriding the agent, redirecting the interface it's operating in, or quietly adjusting the environment without fully halting execution. The tight link between trust, satisfaction, and perceived effectiveness also suggests that investing in intervention affordances isn't just a safety feature — it may be directly tied to how much people end up trusting and liking the product.

## Why you should care

As web agents move from research prototypes toward everyday consumer tools that click, buy, and book things on real websites, the question of how a person stays meaningfully in control — without micromanaging every step — becomes a practical design problem, not just an academic one. This paper is one of the first to study that question with real participants intervening on a real, live web agent rather than a simulated one, and it offers early empirical evidence that the *style* of intervention people reach for is genuinely varied — a useful corrective for anyone designing agent interfaces around a single, blunt "pause/resume" control.
