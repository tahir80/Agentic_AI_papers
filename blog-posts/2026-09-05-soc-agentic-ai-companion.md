# "Not Yet Another Tool": Teaching a Security AI Agent to Earn Analysts' Trust

**Authors:** Kritan Banstola, Faayed Al Faisal, Duy Dao, Ryan Irving, Daniel Lende, Xinming Ou (University of South Florida)
**Publication date:** 2026-09-05 (arXiv v1)
**Venue:** arXiv preprint, cs.CR (primary) / cs.AI (secondary); peer-reviewed venue not confirmed at time of writing. A related, shorter earlier-stage paper by an overlapping subset of authors ("Experiences of Using Agentic AI to Fill Tooling Gaps in a Security Operations Center") appeared at the NDSS Workshop on SOC Operations and Construction (WOSoC) 2026 — that is a companion piece, not this paper.
**Paper link:** https://arxiv.org/abs/2609.06250
**Code link:** Not available (no public repository found; the companion is tied to the host SOC's internal tooling)
**Project page:** Not available
**Date added:** 2026-09-20

> **A note on sourcing:** this session's direct network access to arxiv.org and every mirror tried (Hugging Face, alphaXiv, Semantic Scholar, the NDSS site, university news pages) was blocked at the network egress layer of this environment — not a paywall; the paper is a public, open-access arXiv preprint. This summary is built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported quantitative results, rather than a direct read of the full PDF. Facts that were corroborated across multiple independent search queries are presented as such; anything that couldn't be verified this way is marked "not available" or "not confirmed." Readers who want exact statistics, full qualitative quotes, or the complete related-work discussion should consult the arXiv preprint directly.

---

## The problem the paper addresses

Security Operations Centers (SOCs) — the teams that watch over an organization's networks for signs of intrusion — are flooded with tickets. The vast majority of these alerts turn out to be nothing (a routine software update phoning home, a laptop connecting to a slightly unusual server), but someone still has to check every single one, because the rare real threat looks identical to the noise until it's investigated. That triage work is repetitive, tool-heavy, and exhausting — a textbook case for AI automation. But plenty of "AI for the SOC" products have been tried and quietly abandoned because analysts didn't trust them, didn't understand how they reached their conclusions, or simply couldn't fit them into their existing workflow. This paper asks a more specific question than "can an LLM do SOC triage?" — it asks: *what does it actually take, in practice, for a real team of human security analysts to adopt an AI agent into their daily work and keep using it?*

## Why this problem matters

Cybersecurity teams are chronically understaffed and prone to burnout precisely because so much of the job is repetitive log-chasing punctuated by rare moments that really matter. If AI agents could reliably absorb the repetitive share of that work, it would free analysts to focus on the alerts that need human judgment. But a security tool that analysts don't trust, or that hallucinates a verdict they then have to double-check line by line, can be worse than no tool at all — it adds work instead of removing it, and in the worst case it could let a real threat slip through under a false sense of automation. Getting the human-AI handoff right in a high-stakes, adversarial environment like a SOC is a genuinely hard and consequential design problem, and one that most academic "agentic AI" papers don't test against real practitioners doing real work.

## What makes the system agentic

The system at the center of this paper — which the authors call "the Companion" — is a **ReAct-style LLM agent** (built with LangChain) that runs a genuine investigation loop: given a ticket, it reasons about what information it still needs, calls a tool to go get that information, incorporates the result, and repeats until it has enough evidence to write up a verdict. It pulls from four different kinds of real infrastructure: OSINT and threat-intelligence services (to check whether an external IP or domain looks malicious), the organization's SIEM (to find which internal host was involved), an internal DHCP lookup tool (to resolve that host to a physical device), and a device-identification portal (to attribute the device to a specific person). It also drives a headless browser (via Playwright) to visit each source itself and capture a screenshot, so its evidence is independently checkable rather than just asserted. That's multi-step planning, real tool use across heterogeneous live systems, and an end product (a drafted closing report) that goes well beyond a single text response — squarely fitting this survey's definition of agentic AI.

## How humans and the AI agent collaborate

This is the heart of the paper. Rather than designing the Companion in a lab and then handing it to analysts to test, the research team spent **14 months embedded inside a real university SOC** — first working as SOC analysts themselves, to genuinely understand the job, and only then building the AI system around what they'd learned. In the final four months of that fieldwork, **six experienced analysts** were invited to use the Companion on **108 live, real tickets** as part of their actual jobs — not a simulated exercise, not a lab task with paid crowdworkers, but real operational security work with real stakes.

## What role the human plays

Analysts remain the decision-makers throughout. They receive the Companion's investigation and draft write-up for a ticket, then **verify it against the evidence it gathered** (including those screenshots) before deciding whether to use it. Crucially, the authors report that analysts also **actively reshaped the Companion's behavior** over time — for instance, by customizing its system prompts to better match how they personally wanted investigations conducted or reports phrased — rather than passively accepting a fixed tool.

## What role the AI agent plays

The Companion does the tedious, tool-hopping legwork: pulling threat-intel data, cross-referencing the SIEM, resolving device identities, capturing verifiable screenshots of each lookup, and drafting a first-pass closing report and verdict for the ticket. It operates with meaningful autonomy inside its investigation loop (deciding for itself which tool to call next and when it has enough evidence) but its output is explicitly framed as a draft for human review, not a final action.

## How control, initiative, and decisions are shared

The arrangement is a form of human oversight with an unusually explicit verification mechanism: the Companion takes the initiative on gathering and synthesizing evidence, but analysts hold the final call, and the authors designed the system specifically so that call can be made cheaply — by making every claim traceable to a screenshot of the original source. According to the authors, analysts reused the Companion's output in their closing reports in **more than 90% of cases where that output was easy to verify — even in cases where they disagreed with its verdict**, suggesting that what analysts valued was the evidence-gathering and drafting labor the Companion did, which they could accept or overrule after their own quick check, rather than blind deference to its conclusions. The authors describe the overall dynamic as the tool and its human users **"co-evolving"**: the Companion adapts (via analyst-driven prompt customization) as analysts, in turn, adapt how much and how they rely on it.

## The paper's main idea

**Claim by the authors:** a SOC AI companion earns real, sustained adoption — becoming something other than "yet another tool" nobody actually uses — when it is (1) designed through deep, sustained immersion in analysts' actual daily work rather than built from the outside, (2) built to present its findings in an immediately, cheaply verifiable form (their screenshot-backed evidence trail), and (3) left open for analysts themselves to adapt and customize, rather than shipped as a fixed black box.

## How the approach works

The research proceeded in two phases embedded in the same SOC: an initial ethnographic phase, where the researchers (including an anthropologist co-author) worked as analysts themselves to map out the real workflow, tool-hopping patterns, and pain points; and a build-and-deploy phase, where they implemented the ReAct/LangChain-based Companion against the specific tools that phase revealed were the biggest bottlenecks, then handed it to six analysts to use on live tickets for four months while logging how its output was actually used (reused verbatim, edited, or ignored) in each ticket's closing report.

## Human study or evaluation design

This is a **real-world, longitudinal field deployment study**, not a lab experiment or a study built on simulated users. It combines ethnographic/participant-observation methods (the researchers' own 14 months as embedded analysts) with a quantitative log analysis of how six analysts actually used the deployed system on 108 real tickets over four months. The authors themselves flag a specific methodological limitation: reported time savings rely on analysts' **self-reported** time estimates rather than objective, automatically logged timestamps, and they propose a controlled, crossover-design replication with objective time tracking as future work.

## Participants and study setting

**Six experienced SOC analysts** at a real, operational university Security Operations Center, using the Companion on **108 actual security tickets** during the final four months of a 14-month embedded fieldwork engagement. This is a single-site case study — one SOC, one team — rather than a multi-organization trial.

## Experiments or benchmarks

There is no public benchmark here; the "test set" is the SOC's own live ticket stream. The authors report analyzing how the Companion's output was used across the 108 tickets handled during the deployment window, plus the qualitative/ethnographic record from the full 14-month engagement.

## Main results

**Reported by the authors, per available search excerpts:**
- In **more than 90%** of tickets, analysts reused the Companion's output in their closing report.
- Where the Companion's output was **easy to verify** (i.e., its screenshot evidence trail made checking cheap), analysts reused its content in over 90% of cases — **even when they disagreed with its verdict** — suggesting they valued the drafting/evidence-gathering labor independently of whether they trusted its final conclusion.
- The most frequent users saw reported **time savings of roughly 30–50%** on the tickets where they used the Companion.
- Analysts who **customized the Companion's system prompts** to their own preferences showed **even higher adoption** than those who used it unmodified.

Exact statistical tests, confidence intervals, and the full breakdown of "reused / edited / ignored" outcomes could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's outcome measures center on **adoption, reuse, and self-reported time savings** rather than a formal trust-scale instrument (e.g., no NASA-TLX or standardized trust questionnaire was confirmed from available sources). The finding that analysts kept reusing verifiable output even when they disagreed with the Companion's verdict is arguably the paper's most interesting trust-related result: it suggests analysts were calibrating their reliance not on whether the AI was "right," but on whether they could cheaply confirm what it had found — a distinct and arguably healthier form of trust than simply believing the AI's conclusions. Reported time savings (30–50% for heavy users) is a real-world productivity signal, though the authors themselves caution it rests on self-report rather than objective logging.

## What is genuinely new

- **A rare longitudinal, embedded field deployment** of an agentic AI system in a real, operational, high-stakes environment — 14 months of ethnographic immersion followed by 4 months of live use by real analysts on real tickets, rather than a lab study, a survey, or a short-term pilot.
- **A concrete design mechanism for cheap human verification**: pairing every automated lookup with a screenshot of the original evidence, so analysts can check the AI's work without redoing it from scratch.
- **Evidence that analyst-driven customization of the agent (not just researcher-driven tuning) increased adoption** — a data point for "the agent should be shaped by its users, not just its builders."
- **A trust finding that decouples "reuse" from "agreement"**: analysts kept using the AI's output even while overruling its verdict, once verification was cheap enough.

## Limitations and open questions

- **Single site, small team.** Six analysts at one university SOC is a modest sample from one organizational context; whether the findings transfer to a corporate SOC, a managed security provider, or a much larger team is untested.
- **Self-reported time savings.** The headline 30–50% productivity figure rests on analysts' own estimates, not automatic timestamp logging — a limitation the authors themselves acknowledge and propose to address with a future controlled, crossover-design replication.
- **No standard psychometric trust/workload instrument confirmed.** The paper's trust-related finding (reuse despite disagreement) is compelling but observational; it isn't paired with a validated survey instrument as far as could be verified from available sources.
- **Peer-review status.** As of this writing, this appears to be a recent arXiv preprint (with a related, distinct workshop paper by an overlapping author subset at NDSS WOSoC 2026); full peer-reviewed publication status for this specific paper is not confirmed.
- **Sourcing caveat (this summary).** Because full-text access was blocked in this research session, exact statistical detail, the complete qualitative/interview record, and the full limitations/future-work discussion could not be verified beyond what surfaced in search excerpts.

## Practical implications

For any organization considering deploying an LLM agent into a high-stakes operational workflow, this paper offers a fairly concrete playbook: spend real time understanding the existing human workflow before building anything (not just interviewing users but actually doing the job); design the agent's output to be cheaply, independently verifiable rather than trusted on faith; and build in room for the people who use it daily to reshape its behavior, rather than shipping a fixed black box. The finding that verifiability — not accuracy per se — seems to drive sustained reuse is a useful, transferable lesson well beyond cybersecurity, for any domain where an AI agent's conclusions need to be double-checked by a domain expert before they're acted on.

## Why you should care

Most "agentic AI meets human oversight" research either happens in a controlled lab with paid participants doing a synthetic task, or is a position paper arguing about what *should* happen. This paper is neither: it's a rare, sustained, real-world case study of an AI agent being built with and deployed alongside the actual professionals who have to live with it, in a domain (cybersecurity operations) where getting the human-AI handoff wrong has genuine consequences. Whether or not its specific numbers generalize beyond one university SOC, the underlying design principle it surfaces — verifiability earns trust faster than accuracy does, and letting users reshape the agent increases adoption — is a concrete, actionable finding for anyone trying to get a human-AI team to actually work together in practice rather than just in theory.
