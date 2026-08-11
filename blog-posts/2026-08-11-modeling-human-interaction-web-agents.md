# Modeling Distinct Human Interaction in Web Agents

**Authors:** Faria Huq, Zora Zhiruo Wang, Zhanqiu Guo, Venu Arvind Arangarajan, Tianyue Ou, Frank F. Xu, Shuyan Zhou, Graham Neubig, Jeffrey P. Bigham (Carnegie Mellon University and Duke University; exact per-author institutional mapping not independently confirmed)
**Publication date:** 2026-02-17 (arXiv v1, id 2602.17588); revised 2026-07-07 (latest version)
**Venue:** arXiv preprint (cs.CL/cs.HC); peer-reviewed venue/acceptance status not independently confirmed
**Paper link:** https://arxiv.org/abs/2602.17588 (PDF: https://arxiv.org/pdf/2602.17588)
**Code link:** Not independently confirmed (the paper builds on the open-source CowPilot framework, https://github.com/oaishi — exact repository holding this paper's own CowCorpus dataset/model code could not be verified from available sources)
**Project page:** Not available (a Hugging Face paper page exists at huggingface.co/papers/2602.17588, but this is a listing, not an authored project site)
**Date added:** 2026-08-11

> **A note on sourcing:** This session's outbound network access to arxiv.org, huggingface.co, and related mirror hosts was blocked by organizational egress policy, so this summary could not be built from a direct read of the full PDF. It is instead built by triangulating across multiple independent web searches (which draw on the arXiv abstract/HTML pages, a Hugging Face paper listing, and ResearchGate), cross-checking each factual claim across at least two independent search results before including it. Facts that were consistent across searches (authors, dates, dataset size, study design, headline numbers) are reported as such; anything that could not be cross-confirmed, or that appeared inconsistently across sources, is flagged below or marked "not available" rather than invented.

---

## The problem the paper addresses

When you hand a task over to an AI agent that browses the web for you — filling out a form, comparing prices, booking something — you rarely just walk away and come back when it's done. More often you hover: watching it work, occasionally correcting a wrong click, sometimes taking the mouse yourself for a step it keeps getting wrong, sometimes just letting it run. The paper argues that today's web agents have no real model of *that* behavior. They're built to either act fully on their own or wait for a person to type a new instruction — they can't tell, moment to moment, whether a given person is the hands-off type who'll rarely step in, or the hands-on type who wants to check every move. The paper's core problem is: **can we teach a system to recognize these different styles of human interaction, and use that to decide when a human is likely to want to step in?**

## Why this problem matters

As AI moves from single-turn chat answers into agents that take real, consequential actions on real websites (clicking, filling forms, submitting purchases), getting the human's role right stops being a nice-to-have UX detail and becomes central to whether people trust and actually use these tools. An agent that interrupts a hands-off user constantly is annoying; one that barrels past a hands-on user's objections is unsafe. If an agent could anticipate, based on how a specific person has been interacting so far, when that person is likely to want to intervene, it could proactively slow down, ask, or hand back control at the right moments — rather than applying one fixed policy to everyone.

## What makes the system agentic

The paper studies and builds on LLM-powered web-navigation agents — systems that read a live webpage, decide on a next action (click, type, scroll, submit), and execute it, repeating this loop across many steps to complete an open-ended task like booking a flight or filling out a form. This is squarely an agentic setting: multi-step planning and tool/environment interaction inside a real browser, not a single text response. The paper's own contribution — a model trained to predict, at each step, whether a human collaborator is about to intervene — is deployed inside a live, running web agent (built on the open-source **CowPilot** framework) rather than tested only offline, and the resulting intervention-aware agent is evaluated as a deployed agentic system in a live user study.

## How humans and the AI agent collaborate

Collaboration happens step-by-step inside a shared browser session. The agent proposes or takes the next action; at any point the human can let it continue, pause it, override its next move, or take over the browser entirely and act directly, before optionally handing control back. The paper's contribution sits on top of this existing collaborative loop: rather than treating every user identically, it models each person's distinctive interaction style and uses that model to anticipate the specific moments when *that* person is likely to want to intervene, so the agent can adjust — for example, by proactively slowing down or deferring — around those moments.

## What role the human plays

Humans are working co-pilots on real web tasks, not just prompt-writers. In the data-collection phase, 20 real users completed 20 real web-navigation tasks in collaboration with the CowPilot agent, producing the **CowCorpus** dataset: 400 trajectories containing over 4,200 interleaved human and agent actions, with each human intervention (a pause, an override, a takeover) logged at the step level. In the later evaluation phase, real users interacted live with the resulting intervention-aware agent and rated how useful they found it.

## What role the AI agent plays

The agent autonomously plans and executes multi-step web-navigation actions toward a goal, the way any LLM-based browsing agent does. What's new here is a second layer: a model trained specifically to predict, given the ongoing interaction, whether the human is about to intervene next — effectively giving the agent a running estimate of "is this person about to step in right now?" that it can use to adapt its own behavior in real time, rather than acting exactly the same way for every user and every step.

## How control, initiative, and decisions are shared

Control is explicitly shared and can shift step by step: the authors identify **four distinct interaction patterns** along a spectrum — hands-off supervision (mostly letting the agent run), hands-on oversight (closely watching, occasionally correcting), collaborative task-solving (working the task jointly, back and forth), and full user takeover (the human doing the step themselves). Rather than forcing every user into one fixed mode, the system is designed to recognize which pattern a given person is exhibiting and anticipate their specific intervention points, so initiative can move fluidly between agent and human depending on the individual and the moment.

## The paper's main idea

**Claim by the authors:** human intervention during agent execution is not a single uniform behavior — different people interact with web agents in qualitatively different, identifiable styles — and a model that learns to recognize these styles and predict *when* a given person is likely to intervene next can make an agent measurably more useful in live, deployed use, by letting it anticipate and adapt to intervention rather than treating every user identically.

## How the approach works

The authors first collected CowCorpus by having 20 real users perform 20 web tasks with the CowPilot human-agent collaborative browsing framework, logging every interleaved human and agent action (over 4,200 actions total) along with when and how humans intervened. They then analyzed this corpus to identify four recurring interaction patterns (hands-off, hands-on, collaborative, takeover) and used the labeled data to train language models to predict, at a given point in a task, whether the specific user is about to intervene next. These intervention-aware models were then deployed inside live web-navigation agents and tested with real users to see whether anticipating intervention actually improved the agent in practice.

## Human study or evaluation design

**Demonstrated in the paper:** the work involves two connected human studies. First, a data-collection study with real users producing the CowCorpus trajectories and intervention labels. Second, a live deployment study where users interacted with web agents that either did or did not use the intervention-prediction model, with usefulness rated by the users themselves after live use — not a simulated or offline-only evaluation.

## Participants and study setting

**Real, recruited users** — 20 people completed 20 web-navigation tasks in the data-collection phase that produced CowCorpus. Further demographic detail (recruitment method, background, compensation) was not confirmed from available sources. The live evaluation study used real users interacting with a deployed CowPilot-based web agent in real time; the exact participant count for this second evaluation phase was not independently confirmed from available sources (it may be the same 20-person pool or a separate group — this session could not verify which from the accessible material).

## Experiments or benchmarks

There is no public leaderboard-style benchmark here; the "experiment" is CowCorpus itself (400 trajectories, 4,200+ actions from 20 users across 20 tasks) plus two measured outcomes: how well trained language models can predict a specific user's next intervention compared to a base (non-personalized) model, and how much more useful users rated the resulting intervention-aware agent compared to one without this capability, in live use.

## Main results

**Demonstrated in the paper (per cross-checked secondary descriptions, not independently verified against the full PDF):**
- Models trained on CowCorpus to anticipate a given user's interventions improved intervention-prediction accuracy by **61.4–63.4%** over base language models.
- When these intervention-aware models were deployed in live web-navigation agents and evaluated with real users, the agent's user-rated usefulness increased by **26.5%** compared to the non-adaptive baseline. (Note: one secondary source reported this figure as 36.8%; the more consistently corroborated figure across independent searches was 26.5%, which we report here, but readers should verify the exact number against the primary PDF.)
- The four-pattern taxonomy (hands-off, hands-on, collaborative, takeover) was consistently described across sources as a core finding, distinguishing this from prior work that treats "user intervention" as a single undifferentiated behavior.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the paper's primary human-related outcome is *user-rated usefulness* of the agent, which rose substantially (reported as 26.5% higher) when the agent could anticipate a specific user's likely intervention points, compared to an agent without this capability. **Our interpretation:** this is evidence that adapting to an individual's collaboration style — rather than applying one fixed level of autonomy to everyone — has a measurable, positive effect on how useful people find a web agent in live use. The available sources did not report standardized trust, workload (e.g., NASA-TLX), task-success-rate, or safety metrics for this specific study, so those effects should be treated as **not established** from what could be confirmed here, even though the usefulness result is a meaningful indicator of a real, positive human-experience effect.

## What is genuinely new

- **CowCorpus**, a real-user dataset of 400 human-agent web-navigation trajectories with over 4,200 step-level interleaved actions, explicitly labeled for human intervention — a resource for future work on this problem, not just this paper's own model.
- A **four-pattern taxonomy of human interaction styles** with web agents (hands-off, hands-on, collaborative, takeover), moving beyond a single generic notion of "user intervention" toward recognizing that different people collaborate with agents in qualitatively different, identifiable ways.
- Demonstrating that a model built to **predict a specific user's next intervention** can be deployed inside a live agent and produce a measurable improvement in real users' rated experience — not just an offline accuracy number.

## Limitations and open questions

- The data-collection study is based on 20 users completing 20 tasks; this is a modest sample for establishing that four interaction styles generalize across the wide range of real-world web tasks and user populations.
- This session could not confirm the exact participant count, demographics, or statistical methodology of the live deployment study, nor whether formal significance testing was reported, since the full PDF could not be fetched (network-restricted); readers should verify these details directly.
- The one discrepancy found between independent secondary sources (26.5% vs. 36.8% usefulness improvement) could not be resolved without the primary text — a reminder that this summary rests on secondary triangulation rather than a first-hand read.
- No public code/dataset repository specific to this paper (as opposed to the earlier CowPilot framework it builds on) could be confirmed from available sources; readers wanting to reproduce or extend this work should check the arXiv page directly for release details.
- Peer-review/venue status is not confirmed; this is an arXiv preprint, most recently revised 2026-07-07.

## Practical implications

If the reported findings hold up under full-text verification, they suggest that builders of web/computer-use agents should not treat "how much should the agent ask/check/pause" as a single global setting. Instead, systems could benefit from learning a specific user's collaboration style over time and using that to anticipate the individual moments a *particular* person is likely to want to step in — potentially making agents feel more attuned and trustworthy without necessarily increasing how often they interrupt. The released CowCorpus dataset also gives other researchers real, step-level-labeled data to study human intervention in web agents rather than relying on synthetic or simulated interaction logs.

## Why you should care

Most discussion of "human-in-the-loop" AI agents treats the human as a single generic supervisor who checks in occasionally. This paper's real contribution is showing, with actual users and a live deployed system, that people collaborate with web agents in recognizably different styles — and that an agent which learns to anticipate *your* style, specifically, rather than applying one policy to everyone, measurably improves how useful people find it. That's a concrete, evaluated step toward agents that adapt to individual humans rather than asking every human to adapt to one fixed interaction pattern.
