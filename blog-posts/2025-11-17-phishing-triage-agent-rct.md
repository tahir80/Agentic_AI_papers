# Should You Trust the AI That Sorts Your Inbox for Threats? A Real-World Test Says Yes — Mostly

**Authors:** James Bono (Microsoft)
**Publication date:** 2025-11-17 (arXiv v1)
**Venue:** arXiv preprint — econ.GN / cs.AI (peer-reviewed venue not confirmed from sources used)
**Paper link:** https://arxiv.org/abs/2511.13860
**Code link:** Not available (the studied system, Microsoft Security Copilot's Phishing Triage Agent, is a proprietary commercial product; product documentation: https://learn.microsoft.com/en-us/defender-xdr/phishing-triage-agent)
**Project page:** https://learn.microsoft.com/en-us/defender-xdr/phishing-triage-agent
**Date added:** 2026-09-19

> **A note on sourcing:** this session's outbound network access to arxiv.org and its usual mirrors (Hugging Face, Semantic Scholar, alphaXiv, direct PDF hosts) was blocked at the network egress layer of the environment used to research this post (an infrastructure restriction, not a paywall — the paper is a public, open arXiv preprint). This summary was built from cross-checked search-engine excerpts of the paper's abstract, reported methodology, and reported quantitative results — corroborated across the arXiv listing itself, Microsoft's own technical write-up of the same study, and independent third-party summaries — rather than from a direct read of the full PDF. Facts that appeared consistently across multiple independent sources are presented as such; anything that couldn't be corroborated this way is marked as such below. Readers who need exact statistical tables, full model details, or the complete limitations section should consult the arXiv preprint directly.

---

## The problem the paper addresses

Security teams that protect companies from cyberattacks — Security Operations Centers, or SOCs — are drowning in phishing reports. Employees forward every suspicious-looking email to the security team, and someone has to look at each one and decide: is this a real attack, or just spam and false alarms? Doing that well takes time, and SOCs never have enough analyst-hours to keep up with the volume. Microsoft built an AI agent — the Security Copilot Phishing Triage Agent — to help, but building an agent that *can* triage phishing emails isn't the same as knowing whether it actually makes human analysts faster and more accurate once it's handed to them in a real workflow. This paper is a rigorous, real-world test of exactly that question.

## Why this problem matters

AI vendors make bold claims about productivity gains constantly, but genuinely controlled, real-world evidence for those claims — as opposed to marketing demos or lab benchmarks — is rare. Phishing triage is also a high-stakes setting to get this wrong: false alarms waste analyst time and cause "alert fatigue," while a missed real attack can lead to a breach. And there's a well-known risk with any AI decision aid: humans might start "rubber-stamping" — just clicking along with whatever the AI suggests without really checking it — which would erase any real safety benefit even if the numbers look good on paper. This study set out to measure not just whether the agent helped, but specifically *how* it helped, and whether analysts kept exercising real judgment while using it.

## What makes the system agentic

The Phishing Triage Agent is not a simple spam filter with fixed rules. Based on the paper's own description and Microsoft's technical documentation, it is an LLM-based system that autonomously reviews each reported email, examines its content, links, and attachments, correlates signals across multiple internal security data sources, and reaches an independent verdict (malicious or benign) — producing a plain-language explanation and a visual map of its own reasoning steps for each case. It also reorders the analyst's entire work queue by predicted priority, and it adapts over time: an analyst can tell it in natural language, "this email is harmless," and the agent adjusts its future behavior to that organization's patterns. That combination — autonomous multi-step investigation across real data sources, a produced decision with justification, and learning from human feedback — is what makes this a genuine agentic AI system rather than a static classifier, and the paper evaluates it exactly that way: not by asking "how accurate is the model on a benchmark," but by asking "what happens when real analysts use it to do real work."

## How humans and the AI agent collaborate

The agent doesn't make the final call — it prioritizes the analyst's queue and hands each analyst its verdict and reasoning as an input to *their* decision. The analyst still has to review the evidence and record their own classification. This is a supervised-triage arrangement: the agent does the investigative legwork and proposes a verdict, and the human remains the actual decision-maker, with the added ability to give the agent ongoing feedback that reshapes its future behavior.

## What role the human plays

Analysts remain the ones who make the final classification decision on every email. In the study, they were shown the same evidence a human would normally use — screenshots of the email and any URLs it contained, screenshots from sandboxed ("detonated") link visits, sanitized attachments, and the raw email/HTML/URL data — and, in the treatment conditions, the agent's queue ordering and/or its verdict and explanation. The analyst's job was to review that evidence (and, where present, the agent's input) and record a verdict through an instrumented survey platform.

## What role the AI agent plays

The agent does the front-loaded investigative work: reading and correlating the raw evidence, forming its own verdict, explaining that verdict in plain language, and — critically — deciding which emails in the queue are most likely to matter and pushing those to the top. According to the paper, this queue-reordering function turns out to be the dominant source of the measured benefit.

## How control, initiative, and decisions are shared

The study's three-arm design is specifically built to separate two distinct channels of agent influence. In the **Aware** condition, analysts saw the agent's queue ordering *and* its verdicts and explanations. In the **Blind** condition, the queue was reordered by the agent behind the scenes, but analysts weren't told this or shown the agent's verdicts — isolating the effect of priority-ordering alone. The **Control** condition had neither. This lets the authors decompose "how much did the agent help, and through which mechanism" rather than just reporting one combined number — and, per the paper, the answer is that most of the benefit (reported as roughly 83%) comes from the agent simply putting the right emails in front of analysts sooner, with the remaining benefit coming from analysts actually using the agent's stated verdicts and explanations once they get there.

## The paper's main idea

**Claim by the author:** a real, deployed LLM-based triage agent, integrated into analysts' actual workflow rather than a lab demo, meaningfully improves both the speed and the accuracy of human phishing triage — and it does this primarily by improving *where analysts look first*, not by replacing their judgment. Critically, the author's own behavioral analysis argues analysts did not simply defer to the agent's verdicts wholesale (no widespread "rubber-stamping"), and instead shifted their attention productively toward the emails that actually mattered.

## How the approach works

This is a randomized controlled trial (RCT), not an observational study. The author recruited 167 professional security analysts and had them triage a curated, privacy-vetted set of real, previously user-submitted phishing emails, presented through a standardized set of artifacts (annotated screenshots, sandboxed-link screenshots, sanitized attachments, and raw email/HTML/URL text) via an instrumented survey platform that recorded each classification decision and how long it took. Analysts were randomly assigned to the Control, Aware, or Blind condition described above, allowing a clean, causal comparison rather than just a before/after or self-selected comparison.

## Human study or evaluation design

This is a genuine, controlled, between-subjects randomized experiment with real working security professionals as participants — not a simulated user, not an internal retrospective log analysis, and not a small qualitative pilot. That randomization is what lets the paper make causal claims ("the agent caused this improvement") rather than merely correlational ones.

## Participants and study setting

167 professional security analysts took part, working through a curated corpus of real, privacy-vetted, user-reported phishing emails via an instrumented online survey/testbed platform rather than in a live production SOC queue. Beyond that, further demographic or recruitment detail (e.g., analysts' employer, seniority, or geography) could not be independently confirmed from the sources available in this research session.

## Experiments or benchmarks

There is no public benchmark dataset here; the "benchmark" is the curated, privacy-vetted corpus of real-world phishing/non-phishing emails assembled for the trial, evaluated through the three-arm RCT design described above (Control vs. Blind-queue-reorder vs. full Aware access to the agent's verdicts and explanations).

## Main results

**Reported by the author, per available search excerpts:**
- Agent-augmented analysts achieved **up to 6.5×** as many true positives found per analyst-minute compared with the control group.
- Verdict accuracy improved by **77%** compared with the control group.
- Roughly **83%** of the productivity gain is attributed to the agent's queue prioritization, versus roughly **17%** attributed to analysts using the agent's stated verdicts and explanations.
- Agent-augmented analysts reallocated their attention, spending **53% more time** specifically on malicious emails.
- The author reports analysts were **not** simply "rubber-stamping" the agent's malicious verdicts — i.e., they continued to exercise independent judgment rather than mechanically agreeing with the AI.

Exact confidence intervals, full regression tables, and the paper's formal statistical tests could not be independently verified from the sources available in this session; readers who need those specifics should consult the arXiv PDF directly.

## Effects on human performance, trust, workload, safety, or decision quality

This is the heart of the paper's contribution. On **performance**: both speed (true positives per analyst-minute) and accuracy (verdict correctness) improved substantially and simultaneously — a combination that's notable because speed/accuracy tradeoffs are common in triage work, and this result suggests the agent helped on both fronts at once rather than trading one for the other. On **appropriate reliance/calibrated trust**: the specific finding that analysts were not prone to rubber-stamping the agent's malicious verdicts is the paper's direct evidence against the classic failure mode of human-AI collaboration, where humans stop checking the AI's work and just approve it — a distinction the study explicitly investigates rather than assumes. On **attention allocation**: the 53% increase in time spent on genuinely malicious emails suggests the agent is helping analysts spend their limited attention where it has the most safety value, rather than uniformly across everything in the queue. The paper does not appear (per available sources) to report standard subjective workload or trust-survey instruments (e.g., NASA-TLX or a validated trust scale) — its human-related outcomes are primarily behavioral/performance measures rather than self-reported attitudes.

## What is genuinely new

- **A true randomized controlled trial**, not a case study, lab demo, or observational log analysis, evaluating a real deployed agentic AI product with real professional users doing their actual job.
- **A mechanism decomposition**: the three-arm design isolates how much of the benefit comes from the agent simply reordering the work queue versus from analysts acting on its stated verdicts and explanations — a distinction most human-AI collaboration studies don't attempt to separate.
- **Direct behavioral evidence against rubber-stamping**, addressing one of the most common concerns raised about human-AI decision aids, using actual analyst behavior rather than self-report.
- **A demonstrated case where speed and accuracy both improved together**, rather than the more commonly reported tradeoff between faster-but-less-careful and slower-but-more-careful human-AI workflows.

## Limitations and open questions

- **Single vendor, single agent, single domain.** This tests one specific commercial product (Microsoft's Phishing Triage Agent) in one task domain (phishing triage); how well the findings generalize to other agentic decision-support tools, other security tasks, or other organizations' analyst populations is an open question the paper itself doesn't resolve.
- **Curated test corpus rather than a live production queue.** Analysts triaged a privacy-vetted, assembled set of real emails through a survey platform, rather than the agent operating inside a live, moment-to-moment SOC ticket queue with all its real-world noise and time pressure — a reasonable and common trial design choice, but one that may leave a gap with fully live deployment conditions.
- **Author affiliation.** The sole author is affiliated with Microsoft, the company that builds and sells the product being evaluated — a conflict-of-interest consideration readers should weigh, even though the RCT design itself is a methodologically strong choice specifically intended to produce credible causal evidence.
- **No confirmed subjective outcome measures.** Available sources did not surface standard trust or workload survey instruments in this paper's results; it's unclear from what could be verified whether the full paper includes them.
- **Sourcing caveat (this summary).** Because direct full-text access was blocked in the research session that produced this post, exact statistical detail, full participant demographics, and the paper's own stated limitations section could not be independently verified beyond what surfaced in corroborated search excerpts.

## Practical implications

For any organization considering deploying an agentic AI triage or decision-support tool into a high-volume, judgment-heavy workflow, this paper offers a concrete, causally-grounded template: measure not just aggregate speed or accuracy, but *which mechanism* is driving the benefit (here, mostly queue prioritization) and whether humans are still exercising real judgment rather than deferring wholesale. The finding that queue reordering alone — even without showing analysts the agent's reasoning — drove most of the measured gain suggests that, at least for triage-style work, simply getting the right cases in front of the right person sooner may be a bigger lever than trying to make the AI maximally persuasive or explainable.

## Why you should care

Most human-AI collaboration papers either use small samples, simulated participants, or non-randomized before/after comparisons — good for generating hypotheses, but weak for establishing that an AI agent actually *causes* better outcomes once real people use it in real conditions. This paper is a rare example of a genuine randomized controlled trial, with real professionals doing their actual job, evaluating a real deployed AI agent, and specifically designed to separate "the AI made a good suggestion" from "the human still checked its work." Whether or not the exact numbers replicate elsewhere, the study design here — decompose the mechanism, check for rubber-stamping, measure real task performance — is a template other human-AI collaboration research in high-stakes domains should be borrowing from.
