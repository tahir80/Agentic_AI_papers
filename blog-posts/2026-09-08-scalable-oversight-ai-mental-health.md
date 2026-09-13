# Scalable Oversight for AI in Mental Health: Lessons from 350,000 AI Coaching Conversations between Therapy Sessions

**Authors:** Matthew A. Scult (Grow Therapy), John L. Havlik (Stanford University School of Medicine), Kevin Ramotar (Grow Therapy), Ethan Goh (Stanford University School of Medicine), Manoj Kanagaraj (Grow Therapy)
**Publication date:** 2026-09-08 (arXiv id 2609.09533)
**Venue:** arXiv preprint — no peer-reviewed conference/journal venue confirmed as of this writing
**Paper link:** https://arxiv.org/abs/2609.09533 (PDF: https://arxiv.org/pdf/2609.09533)
**Code link:** Not available (no public repository found; this describes a deployed commercial system, not a released research artifact)
**Project page:** Not available (Grow Therapy's public product page, https://growtherapy.com/blog/ai-coach/, describes the same product but is company marketing content, not an academic project page)
**Date added:** 2026-09-13

> **A note on sourcing:** this session's network could not directly fetch arxiv.org, its mirrors, or Grow Therapy's own site (all blocked by the outbound proxy under organizational policy). This summary is built from the abstract text and framework description as it recurred consistently, near-verbatim, across many independent web searches, cross-checked against Grow Therapy's own public announcements about the same product. Facts corroborated this way are reported as such. Some figures — most notably a "99% detection accuracy" statistic — appear only in Grow Therapy's company blog/press materials, not confirmed as appearing in the arXiv paper itself, and are explicitly flagged as company-reported rather than paper-reported below. Anything that could not be cross-confirmed is marked "Not available."

---

## The problem the paper addresses

When a company deploys an AI system that talks to real people about real mental health struggles, "have a human check every single thing the AI says" sounds like the obviously safe answer. This paper argues that answer breaks down once the system is actually operating at scale. Reviewing every one of hundreds of thousands of AI-generated conversations one by one isn't just expensive — the authors argue, drawing on research into human vigilance, that it can backfire: people asked to watch a firehose of mostly-fine content for rare problems get worse at noticing the rare problem, not better. So the question the paper tackles is: if "review everything" doesn't actually work at scale, what should human oversight of a mental-health AI agent look like instead?

## Why this problem matters

AI chat tools are already being deployed to hundreds of thousands of real people between therapy sessions — not as a hypothetical future scenario, but as a live product decision companies are making right now. Get the oversight design wrong in this domain and the failure mode isn't a wrong recommendation in a shopping app — it's a missed or badly handled safety-relevant conversation with someone in psychological distress. This paper is a rare case of a company publishing what it actually learned from operating such a system at scale, rather than a lab study of what oversight could look like in theory.

## What makes the system agentic

Grow Therapy's "AI coach" is an LLM-based conversational tool that clients use between their scheduled therapy sessions, applying techniques drawn from established frameworks (CBT, DBT, ACT, behavioral activation) to help clients follow through on therapeutic goals and homework. It goes beyond producing isolated text replies in two ways described in the paper and the company's own materials: (1) an independent, parallel monitoring layer evaluates the coach's outputs and the conversation in real time, alongside the coach itself, and (2) when that layer detects a potential safety concern, the system can autonomously take action in the outside world — pausing the conversation, surfacing crisis or support resources to the client, and sending an alert into the clinician's workflow — rather than simply continuing to generate text. That combination of ongoing, multi-turn decision-making plus autonomous escalation actions is what pushes this past a plain chatbot and into agentic territory, and it is evaluated as such: the paper's central subject is the behavior and accuracy of this monitoring-and-escalation loop, not the quality of the coach's sentences.

## How humans and the AI agent collaborate

The paper's core methodological contribution is a **three-layer human-on-the-loop oversight framework**, built from the authors' experience running the coach across 350,000+ real conversations:

1. **Preventive design** — clinical expertise and guardrails are built into the system before any conversation happens, shaping what the coach can and can't do in the first place.
2. **Real-time monitoring** — a separate, parallel evaluator watches conversations as they happen and flags potential safety concerns, triggering automatic pauses and resource-sharing without waiting for a human to notice first.
3. **Continuous clinician evaluation** — licensed clinicians review flagged conversations and audited random samples on an ongoing basis, feeding what they find back into improving the system, rather than being asked to review every single conversation.

## What role the human plays

Real licensed clinicians sit at two points in the loop: they receive real-time alerts about specific conversations the automated layer has flagged, so they can use their own clinical judgment about what to do next for that client, and they conduct ongoing, targeted audits (flagged conversations plus random samples) that drive iterative improvements to the system. This is oversight aimed at the moments that matter, not blanket review of everything.

## What role the AI agent plays

The AI coach carries the conversation itself — applying evidence-based techniques over multi-turn dialogue — while a second, independent AI layer continuously evaluates that conversation for safety concerns in parallel. When that layer's confidence crosses a threshold, the system acts on its own: pausing the chat, presenting crisis or support resources to the client, and routing an alert to the human clinician, who then decides what happens next.

## How control, initiative, and decisions are shared

This is a graduated, risk-triggered handoff rather than either constant human supervision or full autonomy. Day-to-day coaching runs autonomously. The moment automated monitoring flags elevated risk, initiative shifts toward the human: the system constrains itself (pausing, sharing resources) and hands a specific, contextualized decision to a clinician, who exercises discretion the AI does not. Everything else — the bulk of low-risk conversations — is only sampled for human review after the fact, as a quality-improvement signal rather than a gate.

## The paper's main idea

**Claim made by the authors:** requiring a human to review every AI output does not scale as a safety mechanism for a system operating across hundreds of thousands of conversations, and — per the vigilance research they cite — can paradoxically make oversight *less* reliable by asking people to stay alert to rare events buried in overwhelmingly routine content. Their proposed alternative is to combine safety into the system's design up front, use an independent automated layer to do continuous, real-time triage, and reserve clinicians' limited attention for the flagged cases and audit samples where their judgment adds the most value.

## How the approach works

The three layers operate together as a pipeline: preventive design narrows what can go wrong before deployment; a real-time monitoring layer — described as operating independently and in parallel to the coaching agent itself, rather than being the same model grading its own homework — evaluates every conversation as it unfolds and can trigger an automatic pause plus resource-sharing; and a continuous clinician-evaluation layer combines automated scoring with targeted human review of flagged conversations and random samples, with findings from that review used to iteratively refine the system over time.

## Human study or evaluation design

**Demonstrated in the paper:** this is not a randomized controlled trial with an experimental manipulation; it is a large-scale, real-world deployment analysis — a report of lessons learned from operating the three-layer framework across a real product's full conversation volume, evaluating how well the automated monitoring layer performed and how the tiered human-review process functioned at scale.

## Participants and study setting

**Real users, real clinicians, real deployment.** The underlying data comes from actual clients of a real teletherapy platform (Grow Therapy) using the AI coach between real scheduled therapy sessions, with real licensed clinicians conducting the oversight described above. Exact participant/clinician counts, demographics, and IRB/ethics-review status were **not available** from the sources this session could access; what is confirmed is the scale — over 350,000 AI coaching conversations analyzed for the paper, with Grow Therapy's own public materials additionally citing more than 800,000 messages sent since the tool's December 2025 testing phase began.

## Experiments or benchmarks

Not a public benchmark. The "experiment" is the real deployment itself: the three-layer framework operating continuously over 350,000+ real conversations, with the automated real-time monitoring layer's flagging behavior and the clinician-review process as the objects of evaluation.

## Main results

**Demonstrated/reported by the authors:** the three-layer framework let the team catch and route safety-relevant conversations without requiring exhaustive human review of every interaction, and specific findings from clinician review of flagged and sampled conversations drove iterative improvements to the system over time. **Company-reported (not confirmed to appear in the paper itself):** Grow Therapy's own public announcement states that, in quality-assurance review to date, its safety system correctly identified 99% of potential safety concerns in relevant conversations — a figure worth citing with that caveat rather than treating as an independently verified paper result.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the central human-relevant outcome the paper addresses is clinician workload and reliability of safety oversight at scale — its explicit argument is that requiring clinicians to review every AI output would both overload them and, per vigilance research, likely *reduce* the reliability of that oversight, whereas targeting their attention at flagged/sampled conversations preserves meaningful human judgment where it matters most. **Our interpretation:** this is best read as a practitioner case study making an evidence-informed design argument, not a controlled experiment measuring trust or workload with validated instruments — readers wanting a randomized comparison between "review everything" and "review flagged/sampled" conditions will not find one here.

## What is genuinely new

- A rare, real-world account of what human oversight of an LLM-based agent actually looked like once deployed at hundreds-of-thousands-of-conversations scale, from a team that operated it, rather than a proposal or lab prototype.
- A concrete three-layer framework (preventive design, real-time independent monitoring, continuous targeted clinician evaluation) that decomposes "human oversight" into distinct mechanisms operating at different points in the pipeline, rather than treating oversight as a single review step.
- An explicit, literature-grounded argument that "review everything" is not just impractical but potentially counterproductive for safety at scale — a useful corrective for anyone assuming more human review is always safer.

## Limitations and open questions

- This is a single company's account of its own product; there is no independent replication, and the paper is not (yet) peer-reviewed.
- Key evaluation numbers describing how well the automated monitoring layer performs — including the widely cited "99%" detection figure — come from company communications and quality-assurance review, not from a controlled study design described in an academic methods section that this session could confirm.
- No demographic detail on clients or clinicians, no information on false-negative rates (missed safety concerns) beyond the headline figure, and no code or dataset release, limiting independent scrutiny.
- Because this is real production data from real clients in psychological distress, the ethical stakes of any oversight gap are unusually high; the paper does not, as far as this session could confirm, report a formal external ethics review process for the underlying deployment analysis.

## Practical implications

For any organization deploying LLM agents into safety-sensitive, high-volume settings — not just mental health — this paper is a direct argument against "just have a human check everything" as a scaling strategy, and a concrete alternative pattern: build safety into the system up front, use an independent (not self-grading) automated layer for continuous real-time triage, and spend scarce human expert attention on flagged cases and audit sampling rather than blanket review.

## Why you should care

This is one of the few available public accounts of how human oversight of an LLM-based agent actually behaves once it's running for hundreds of thousands of real conversations involving real people's mental health — not a hypothetical framework or a small lab study. If you're building, deploying, or regulating agentic AI in any high-stakes domain, its central, counterintuitive lesson is directly transferable: more human review is not automatically safer, and designing *where* and *when* people look matters more than trying to make them look at everything.
