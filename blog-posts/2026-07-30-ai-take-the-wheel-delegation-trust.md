# AI, Take the Wheel: What Drives Delegation and Trust in Human-Computer Cooperative Question Answering?

**Authors:** Maharshi Gor, Yoo Yeon Sung, Yu Hou, Eve Fleisig, Zhu Irene Ying, Tianyi Zhou, Jordan Boyd-Graber (University of Maryland, based on author institutional pages; not independently confirmed as a full affiliation list from the paper itself)
**Publication date:** 2026-05-27 (arXiv v1, id 2605.28255)
**Venue:** Findings of the Association for Computational Linguistics (ACL 2026)
**Paper link:** https://arxiv.org/abs/2605.28255 (PDF: https://arxiv.org/pdf/2605.28255)
**Code link:** Not available (no dedicated public repository found for this study at the time of writing)
**Project page:** Not available
**Date added:** 2026-07-30

> **A note on sourcing:** arXiv, the ACL Anthology, and Semantic Scholar were not directly reachable from this research session's network (the outbound proxy returned policy-denial errors for these hosts), so this summary is built from the paper's publicly circulated abstract, the ACL Anthology listing, and cross-checked secondary descriptions rather than a direct read of the full PDF. Facts that could be cross-confirmed across multiple independent searches (authors, venue, study design, participant/decision counts, and headline quantitative findings) are reported as such; anything that could not be verified this way is marked "not available" or flagged as uncertain rather than invented.

---

## The problem the paper addresses

When a person works alongside an AI system on a task, they constantly face small trust decisions: should I let the AI just handle this on its own, or should I do it myself and only check the AI's answer afterward? The paper argues that these are actually two *different* decisions that prior research usually lumps together — **delegation** (letting the AI act autonomously, before you've seen what it will produce) and **adoption** (seeing the AI's suggestion and then deciding whether to go along with it). Nobody had studied both, together, with the same real people, in a realistic competitive setting.

## Why this problem matters

As AI assistants get woven into real work, people don't just get one shot at deciding whether to trust the AI — they make a stream of these calls, some before seeing any output ("should I hand this off?") and some after ("now that I see its answer, do I believe it?"). If we only study one type of decision, we get an incomplete, possibly misleading picture of how human-AI trust actually plays out moment to moment. Getting this wrong in real deployments means people either lean on unreliable AI when they shouldn't, or ignore good AI suggestions when they shouldn't — both costly mistakes.

## What makes the system agentic

The AI "teammates" in this study are not one-shot question-answering chatbots. They are quizbowl agents that must make a live, sequential judgment call as a question is read aloud, word by word: keep listening, or "buzz" now and commit to an answer, weighing an accuracy/reward trade-off (answering earlier scores more but risks being wrong). Alongside that action, the agents estimate their own confidence and generate explanations for their answers. That combination — a running, multi-step decision process that ends in a committed action, self-assessed confidence, and generated justification, evaluated as a competitive teammate rather than judged only on single-turn answer accuracy — is what makes this agentic AI rather than a plain QA model.

## How humans and the AI agent collaborate

Human trivia players and AI agents are paired as real-time teammates in a quizbowl match. At different points, the human can choose to delegate a question to their AI teammate — letting it buzz and answer without a preview — or can wait to see the AI's suggested answer (with its confidence score and explanation) and then decide whether to adopt it. Both kinds of reliance happen repeatedly across a single match, and both are logged and analyzed.

## What role the human plays

The human is the one who ultimately holds authority in the partnership: deciding, question by question, whether to hand control to the AI outright (delegation) or to review and judge a specific AI suggestion before acting on it (adoption). Humans bring their own domain knowledge and initial guesses into these judgment calls, which the paper shows shapes how they interpret and use the AI's input.

## What role the AI agent plays

The AI agent acts as an active teammate rather than a static tool: it decides in real time whether/when to buzz, estimates how confident it is, and produces an explanation for its answer that the human can use to judge whether to trust it. Sixteen different AI agents (varying likely in underlying model or configuration) played this teammate role across the study.

## How control, initiative, and decisions are shared

Initiative is explicitly split and studied as two separate control points rather than one blended "trust the AI or not" switch: (1) an upfront delegation decision, made before the AI's output is known, and (2) a downstream adoption decision, made after seeing the AI's suggestion, confidence, and explanation. This lets the paper isolate how much of human-AI reliance is really about "should I let it try" versus "do I believe what it produced."

## The paper's main idea

**Claim by the authors:** improving human-AI collaboration requires separately understanding *when* people delegate versus *when* they adopt, because these are different decisions with different failure patterns — and today's people are making both of them sub-optimally, in identifiable, systematic ways (such as confirmation bias), which better-designed confidence signals and explanations could help fix.

## How the approach works

The authors built a cooperative quizbowl platform where a human and an AI agent form a team competing against others. As each question is read, the system tracks the point at which a human could delegate to their AI teammate, and separately, the point at which the AI offers a suggested answer (with a confidence score and explanation) for the human to adopt or reject. Every one of these decisions, across many matches, is logged, letting the authors analyze reliance patterns statistically rather than anecdotally.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, real-participant study in which expert human trivia players were paired with AI teammates across 24 competitive matches, generating 387 delegation decisions and 1,440 adoption decisions — a substantial, decision-level dataset of real human reliance behavior, not a simulated or hypothetical account.

## Participants and study setting

**23 expert human players**, paired across 24 matches with a pool of **16 AI agents**, competing in a live quizbowl-style question-answering game. These are real human participants with genuine trivia expertise, not crowdworkers unfamiliar with the task or simulated personas standing in for people.

## Experiments or benchmarks

There is no single named public benchmark here; the "benchmark" is the custom cooperative quizbowl competition itself, instrumented to capture every delegation and adoption decision along with the AI agents' confidence scores and explanations, so the authors could statistically relate decision outcomes to features like AI confidence, explanation content, and whether the human's own initial guess agreed or disagreed with the AI.

## Main results

**Demonstrated in the paper (per available descriptions):**
- Human-AI teams outperformed either humans or AI agents working alone — collaboration had a real, positive payoff.
- Even so, humans made systematically sub-optimal reliance decisions in both directions: **under-relying** on the AI when it was actually correct (missing roughly 3.7–3.9% of such opportunities, depending on the source consulted) and **over-relying** on the AI when it was actually wrong and misleading (roughly 1.5–1.7% of such cases).
- **Confirmation bias** was a major driver of under-reliance: when the AI's suggestion agreed with a human's own initial (incorrect) answer, humans were far more likely to under-use the correct signal the AI could have added — reported at around 64.5% in this specific agreeing-but-wrong scenario.
- Reported AI confidence became close to uninformative (near chance) specifically in cases where the human and AI disagreed — exactly the situations where a reliable confidence signal would matter most.
- Explanation features that best *predicted* whether the AI was actually correct were not necessarily the same features that made humans *trust* the AI's answer — i.e., what makes an explanation persuasive and what makes it a genuinely good signal of correctness can diverge.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's central human-related contribution is about the **quality and calibration of human reliance decisions**, not a single trust/workload questionnaire score. Demonstrated findings: measurable rates of under-reliance and over-reliance, a clear confirmation-bias effect pulling humans away from correct AI help when it matched their own (wrong) instinct, and a breakdown between what predicts AI correctness versus what predicts human trust. **Our interpretation:** this points to real people not being well-calibrated in when to trust AI teammates by default, and suggests that today's typical AI confidence/explanation displays are not sufficient on their own to fix that — a conclusion consistent with, and adding sharper quantitative texture to, findings from other papers already in this repository (e.g., "Overseeing Agents Without Constant Oversight" and "Comparing Human Oversight Strategies for Computer-Use Agents") about the limits of trusting surface-level AI signals.

## What is genuinely new

- Studying **delegation and adoption as two distinct, separately measurable reliance decisions** with the same real participants in the same sessions, rather than conflating them or studying only one.
- A large, decision-level dataset (387 delegation + 1,440 adoption decisions) from real expert humans paired with a diverse pool of 16 AI agents, enabling statistical analysis of reliance patterns rather than a handful of qualitative observations.
- Quantifying **confirmation bias** as a specific, sizeable driver of under-reliance, and showing that AI confidence is least informative exactly where humans need it most (in disagreement cases).
- Distinguishing what makes an explanation *correlate with AI correctness* from what makes an explanation *persuasive to a human* — a concrete, measurable gap rather than a general observation that "explanations matter."

## Limitations and open questions

- The task domain is a **quizbowl trivia game** — a specific, competitive, incremental-question-answering setting. It is not established from available sources how well these delegation/adoption patterns transfer to slower-paced, higher-stakes, or less game-like collaborative work (e.g., long-horizon coding or research tasks).
- We could not confirm from available sources the exact demographic composition of the 23 human experts, how the 16 AI agents differed from one another (models, prompting, or confidence-calibration methods), or the full statistical tests behind each reported percentage, since the full PDF could not be fetched in this session — readers who need precise methodology and numbers should consult the paper directly.
- The paper's own proposed fixes (calibrated confidence, evidence-grounded explanations, mechanisms to help users refine trust) are framed as recommendations; it is not clear from available sources whether the paper also tests and validates such fixes experimentally, or leaves that to future work.

## Practical implications

If these findings generalize, they suggest that builders of human-AI collaborative tools should treat "should I hand this off" and "do I believe what came back" as two separate design problems needing separate support — a good delegation interface (e.g., calibrated pre-commitment signals) is not automatically a good adoption interface (e.g., trustworthy post-hoc explanations), and confirmation bias is a specific, nameable failure mode worth designing against directly, for instance by flagging when a human's initial guess and an AI's suggestion happen to agree so the person double-checks rather than reflexively trusting the agreement.

## Why you should care

This paper puts numbers on something a lot of human-AI collaboration research gestures at qualitatively: people don't reliably know when to trust an AI teammate, and the failure isn't random — it's driven by identifiable biases (like trusting an AI more when it happens to agree with what you already believed) and by AI confidence signals that go quiet exactly when they're needed most. That's a concrete, actionable diagnosis for anyone designing systems where a human and an AI agent are supposed to make joint calls under time pressure — not just quizbowl, but any setting where "should I let the AI take this one" is a decision made over and over, in real time.
