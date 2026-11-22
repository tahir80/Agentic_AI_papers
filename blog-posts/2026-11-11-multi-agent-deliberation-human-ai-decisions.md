**Paper title:** Understanding the Effects of Multi-Agent Deliberation for Human-AI Decision-Making
**Authors:** Harry Yizhou Tian, Ming Yin (Purdue University)
**Publication date:** 2026-11-11 (arXiv v1)
**Venue:** arXiv preprint (cs.HC / cs.AI). A camera-ready PDF under a closely related title, "Multi-Agent Debate for Human-AI Decision-Making," appears in Collective Intelligence (CI) 2026 / HCOMP 2026 conference proceedings materials — this venue match could not be independently confirmed from the arXiv listing alone.
**Paper link:** https://arxiv.org/abs/2611.14901
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-11-22

> **A note on sourcing:** This network environment could not directly reach arxiv.org to download the PDF. The summary below is built from the paper's own abstract text and multiple verbatim excerpts (methods, results, and limitations passages) surfaced through search, not from a full read of the paper. Numbers and quotes are reproduced as found; anywhere the underlying detail could not be confirmed, that is flagged explicitly rather than guessed.

---

# When AI "Debates Itself" in Front of You, Do You Decide Better?

## The problem the paper addresses

Imagine you ask an AI assistant to check whether a claim is true, or to double-check another AI's answer for mistakes. One increasingly popular trick to make AI more accurate is "multi-agent deliberation" (sometimes called multi-agent debate, MAD): instead of asking one AI model for an answer, you set up two or more AI models to discuss the question with each other — proposing answers, critiquing each other, revising their positions — before settling on a final answer.

Researchers have shown this kind of AI-only "committee discussion" often raises accuracy on benchmark tests. But the authors point out a gap: almost all of that evidence measures whether the AI committee gets the *right answer*, not whether a *human* who is watching or reading that AI debate ends up making a *better decision*. Those are not the same question — a person could still misread, over-trust, or be confused by a wall of AI disagreement even when the underlying AI answer improved.

## Why this problem matters

AI decision-support tools — fact-checking assistants, code-review bots, medical or financial second-opinion systems — are increasingly built so a human has the final say. If product teams add "multi-agent debate" purely because it helps AI benchmarks, they may be adding complexity and cognitive load to the human's side of the interaction without actually improving the decisions those humans make. Knowing whether, when, and why multi-agent deliberation helps *people* (not just models) is directly relevant to anyone designing AI-assisted verification, review, or decision tools.

## What makes the system agentic

The system in this paper is not a single chatbot answering a question. It is built from LLM-based agents that:
- pursue a defined task (verify a claim, or judge whether an AI's response contains an error);
- can be configured to work alone or with another AI agent;
- when working together, exchange multiple rounds of argument and critique — a structured, multi-step discussion rather than a single-shot response;
- are assigned different "personas" (a neutral "Base" stance, an "Expert" stance, or a "Devil's Advocate" stance) that change how they argue;
- produce a recommendation that is handed to a human, who then issues the final verdict.

This qualifies as agentic behavior under the task's own working definition: an LLM-centered system pursuing a goal through multi-step, multi-round interaction and coordination with other AI agents, evaluated here specifically as a decision-support agent system rather than as a single-turn language model.

## How humans and the AI agent collaborate

A human participant is shown the AI agent(s)' deliberation (in multi-round conditions) or a single AI response (in simpler baseline conditions), and is then asked to render a final judgment — is the claim true or false, does the AI response contain an error or not. The AI's output is explicitly a recommendation; the human's judgment is the final decision measured in the study.

## What role the human plays

The human is the decision-maker of record. Crucially, the study also manipulates *how* the human engages with the AI's deliberation:
- **Active engagement:** the participant can take part in the discussion (e.g., asking questions, responding to points raised).
- **Passive engagement:** the participant simply reads/observes the AI agents' discussion and then decides.

This makes the human's level of initiative itself an experimental variable, not just a passive consumer of AI output.

## What role the AI agent plays

The AI agent(s) generate candidate answers, and — in multi-round and multi-agent conditions — argue, critique, and revise across multiple turns before presenting a recommendation. Depending on the condition, the agent takes on a persona that shapes its argumentative stance (neutral, expert-flavored, or deliberately contrarian).

## How control, initiative, and decisions are shared

The authors deliberately separate two ingredients that are normally bundled together in "multi-agent debate": (1) how many AI agents are involved (one vs. two), and (2) how many rounds of back-and-forth happen (single-shot vs. multi-round). On the human side, they separately vary whether the person can actively participate or must passively observe. The final decision authority always sits with the human; what varies is how much the AI side deliberates, and how much initiative the human is given to join that deliberation.

## The paper's main idea

The authors' central claim is that multi-agent deliberation's apparent benefit in prior work conflates two different mechanisms, and that these matter differently for *human* decision-making:
- **Multiple rounds of interaction** (even with a single AI) are, in the authors' framing, the main driver of improved human decision accuracy.
- **A second AI agent** mainly adds value when the single AI is relatively weak — i.e., when there is "room to improve" — rather than unconditionally helping.

They also report that giving an AI agent a "Devil's Advocate" persona backfires, reducing human decision accuracy relative to a neutral or expert persona, regardless of whether the human engaged actively or passively.

## How the approach works

The study design is a controlled, between/within-subjects factorial experiment. Conditions include a multi-agent, multi-round "deliberation" setup (referred to as MAD, with Active/Passive and persona variants such as MAD-Active-Base) compared against simpler baselines that isolate single features: a single AI giving one response (Static), a single AI engaged in multi-round interaction with the user (labeled Chatbot / Chatbot-R1 in the reported conditions), and two independent AIs each giving a single response with no discussion between them. By comparing across this set of conditions, the authors can attribute any accuracy gain specifically to "more rounds" versus "more agents" versus "more human engagement," rather than treating "multi-agent debate" as one unanalyzed bundle.

## Human study or evaluation design

This is an evaluation with real human participants making real judgment calls, not a simulated-user or LLM-as-judge evaluation. Participants were shown AI output (ranging from a single static answer to a multi-round, multi-agent discussion, depending on their assigned condition) and asked to produce their own final answer to the task.

## Participants and study setting

According to excerpts of the paper's methods section, the authors recruited **167 participants from Prolific**, restricted to **US-based workers**, with each participant permitted to take the study only once per dataset/task. The study was **approved by the authors' institutional IRB**. The exact demographic breakdown and per-condition group sizes could not be confirmed from the material available to this write-up.

## Experiments or benchmarks

Two tasks were used:
1. **Fact-checking** — participants judged the veracity of claims.
2. **ReaLMistake** — a benchmark for detecting mistakes in LLM-generated responses, used here to have participants judge whether an AI response contains an error.

## Main results

Based on the excerpts available:
- On the fact-checking task, the **MAD-Active-Base** condition reached a mean accuracy of **0.948 (SD = 0.075)**, significantly higher than the **Chatbot-R1** baseline at **0.849 (SD = 0.170)**, and higher than the Static baseline (reported as statistically significant, p < .001, using Student's t-tests with Holm–Bonferroni correction).
- Participants who **actively engaged** with the AI deliberation scored higher than those who only **passively observed** it (reported figures: 0.698 vs. 0.619 on one of the two tasks; which exact task this figure belongs to could not be fully confirmed from available excerpts).
- The **Devil's Advocate** persona underperformed both the **Base** and **Expert** personas on both tasks, regardless of the human's engagement level.
- Overall, the authors report that **multi-round interaction**, more than **the number of AI agents**, drove the accuracy benefit; a second AI agent helped mainly when the single AI's own accuracy had room to improve. The relative advantage of two-AI deliberation over single-AI multi-round interaction was task-dependent rather than universal.

## Effects on human performance, trust, workload, safety, or decision quality

- **Decision quality:** The authors report that multi-agent deliberation improved participants' final-decision accuracy relative to simpler, single-round AI assistance, and helped users adopt the AI's correct answers more often.
- **Workload:** The same excerpts state that the design features which improved accuracy — specifically, more rounds and more agents — also **increased participants' cognitive load**, i.e., the benefit was not free.
- **Reliance and error correction:** The authors explicitly report that deliberation did **not** help reduce AI agents' *shared* or correlated errors, did not help users spot those shared errors, and did not reliably help users **arbitrate** when AI agents disagreed with each other — a meaningful boundary on how far this kind of AI "debate" helps calibrated human reliance.
- These are the authors' own reported findings based on their experimental conditions; this write-up has not independently verified the statistics beyond what is quoted above.

## What is genuinely new

The paper's distinguishing contribution, as the authors frame it, is methodological: rather than treating "multi-agent deliberation" as a single bundled intervention and asking only "does it help," it factorially separates *number of AI agents*, *number of interaction rounds*, and *human engagement mode* (active vs. passive), and measures effects on real human decision accuracy rather than AI-only benchmark accuracy. The persona manipulation (Base/Expert/Devil's Advocate) adds a further, underexplored dimension: *how* an AI agent is instructed to argue shapes whether its "debate" helps or hurts the human on the other end.

## Limitations and open questions

- The benefit of multi-agent deliberation appears to be **conditional**: it depended on which baseline AI's accuracy was being improved on, and the relative value of "more agents" vs. "more rounds" was task-dependent rather than uniform across the two tasks studied.
- Deliberation did not address **correlated/shared errors** across AI agents, nor did it reliably help humans resolve AI **disagreement** — exactly the situations where human oversight arguably matters most.
- The approach **raised cognitive load**, a cost that is easy to overlook if one only looks at accuracy.
- This is a preprint; as of this write-up it had not yet gone through formal peer review (a possibly related camera-ready document for CI 2026 / HCOMP 2026 was found under a slightly different title, but this venue connection is unconfirmed).
- Full demographic detail on the 167 Prolific participants, exact per-condition sample sizes, and the complete statistical appendix were not accessible to this summary and should be checked directly in the paper before citing specific numbers.

## Practical implications

For teams building AI-assisted verification or review tools — fact-checkers, coding-agent output review, content moderation triage — this paper's reported findings suggest that simply adding a second "debating" AI agent is not automatically worth it. The reported results point toward **giving a single AI model multiple rounds of interaction with the user**, and **designing for active human participation**, as comparatively higher-leverage investments than scaling up the number of AI debaters. It also cautions against persona designs (like a scripted "devil's advocate") that are intended to stress-test an answer but may instead degrade the human's final judgment.

## Why you should care

This paper sits squarely in the gap between "AI agents talking to each other" and "AI agents helping a person decide." Its value for human-AI collaboration research is that it refuses to treat "humans in the loop" as a given benefit of agentic AI — it tests, with real people making real judgment calls, which specific design choices (more agents? more rounds? more human participation? which persona?) actually move the needle on human decision quality, and which ones just add noise and effort. That kind of disaggregated, human-centered evaluation is exactly what is needed as more products ship "multi-agent" features on the assumption that AI-benchmark gains automatically translate into better outcomes for the people using them.

---

*Disclaimer: This summary distinguishes, where possible, between the authors' own stated claims, the specific quantitative results found in available excerpts, and this write-up's own interpretation (clearly marked above). Because the full PDF could not be retrieved directly in this environment, readers who want to cite exact statistics, sample breakdowns, or the full limitations section should consult the original paper at the link above.*
