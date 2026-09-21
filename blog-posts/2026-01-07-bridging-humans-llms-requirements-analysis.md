# When AI Agents Draft Your Company's AI Strategy, Who Gets the Final Say?

**Authors:** Malik Abdul Sami, Zheying Zhang, Muhammad Waseem, Kai-Kristian Kemell, Zeeshan Rasheed, Tomas Herda, Pekka Abrahamsson (Tampere University; University of Jyväskylä)
**Publication date:** 2026-01-07 (published online; accepted 2026-01-04)
**Venue:** e-Informatica Software Engineering Journal, Vol. 20, No. 1, Art. 260103, pp. 1–27 (open-access, peer-reviewed)
**Paper link:** https://doi.org/10.37190/e-Inf260103 (PDF: https://www.e-informatyka.pl/EISEJ/papers/2026/1/3/eInformatica2026Art03.pdf)
**Code link:** Not available
**Project page:** Not available
**Date added:** 2026-09-21

> **A note on sourcing:** this session's outbound network access to arxiv.org, e-informatyka.pl, and the usual academic mirrors (Semantic Scholar, ResearchGate, Tampere's research portal) was blocked at the network egress layer, so this summary could not be built from a direct read of the full PDF. It is instead built from cross-checked excerpts surfaced by multiple independent web searches, including the paper's own abstract text and reported study design and findings. Facts that appeared consistently across independent searches are presented as such; anything that could not be corroborated this way is marked "Not available" or flagged as uncertain. Readers who need exact statistics, full result tables, or direct quotations should consult the published article directly (it is open access).

---

## The problem the paper addresses

When a company decides to "adopt AI," someone still has to answer a much less glamorous question first: *what, exactly, do we need this AI to do, for whom, and in what order of priority?* That's requirements engineering — normally a slow, meeting-heavy process where analysts interview stakeholders, draft requirements, argue about priorities, and revise drafts. The paper asks whether a team of LLM-based agents, working together and checking in with real humans at the right moments, can shoulder a meaningful part of that process for a very specific and high-stakes case: figuring out an organization's requirements for adopting AI itself.

## Why this problem matters

Requirements work is exactly the kind of task that's tedious to do well but costly to get wrong — vague or poorly prioritized requirements are a classic reason AI adoption projects stall, blow their budget, or ship something nobody asked for. If an AI system can competently draft and rank candidate requirements, it could free skilled people from repetitive first-pass work. But requirements for *organizational AI strategy* aren't like requirements for a single software feature: they're tied to strategic goals, industry regulation, internal politics, and tacit knowledge that live in people's heads, not in any document an LLM can read. That makes this a genuine stress test of how far you can push automation before you need a human back in the loop — and where exactly that human needs to be.

## What makes the system agentic

The authors built a multi-agent LLM system, not a single chatbot: multiple LLM-driven agents divide the work of generating candidate requirements and then prioritizing them, coordinating with each other across the process rather than producing one-shot text in response to a single prompt. The system is evaluated end-to-end, on real organizational input, as a working tool that produces artifacts (prioritized requirements) a company could actually use — not benchmarked purely as a language model.

## How humans and the AI agent collaborate

The collaboration is iterative and case-specific: the multi-agent system produces a first pass at requirements and priorities, and people at each participating company review, correct, and refine that output before it's treated as usable. The authors frame this explicitly as *human-AI collaboration*, not full automation — the system's job is to accelerate and structure the first draft; the humans' job is to catch what the system gets wrong and steer it toward what the organization actually needs.

## What role the human plays

Employees at each participating company acted as domain-expert reviewers and validators. Their role, as reported, was to clarify technical details the agents couldn't infer, ensure the generated requirements were contextually accurate for their organization, and validate (or correct) the system's prioritization of those requirements. In other words, humans supplied the ground truth about their own business that no amount of generic LLM knowledge could substitute for.

## What role the AI agent plays

The multi-agent system did the heavy lifting of drafting: generating candidate requirements from project/organizational input and then prioritizing them, mirroring — automating a chunk of — the analytical labor a human requirements engineer would normally do by hand.

## How control, initiative, and decisions are shared

Initiative starts with the agents, which produce the first structured draft of requirements and priorities. But authority over the final result rests with the human participants: the study's own framing is that human input was *necessary* to correct and validate the agents' output, meaning the system does not operate as a closed loop — it is designed to be checked and adjusted by people who know the organization, at defined checkpoints (per company, in this study) rather than continuously.

## The paper's main idea

**Claim by the authors:** an LLM-based multi-agent system, when paired with structured human input and review, can meaningfully support organizations in generating and prioritizing the requirements they need for adopting AI — provided humans remain in the loop to supply context and validate results, rather than being replaced by the system.

## How the approach works

The team designed and built a multi-agent LLM system aimed at requirements analysis for AI adoption, then ran it through real organizational cases rather than testing it only on toy examples. Each case followed a structured cycle: the system generates and prioritizes candidate requirements from company-specific input, company representatives review and provide feedback, and the system's output is refined based on that feedback — an iterative human-AI loop rather than a single pass.

## Human study or evaluation design

The evaluation used a mixed-methods, multiple-case-study design. The system was deployed and evaluated separately at four different companies, with each case treated as its own instance of the collaboration. Data was gathered through post-session questionnaires completed by participants immediately after working with the system, plus one follow-up interview per company to go deeper on their experience and the areas that needed improvement.

## Participants and study setting

**Nine participants (N = 9) across four companies**, with the case studies conducted in real organizational settings (not a lab simulation) where the participating companies were actively considering their own AI adoption requirements. Further demographic detail about participants' roles or seniority was not confirmed from the sources available in this session.

## Experiments or benchmarks

There is no public benchmark here; this is a qualitative-leaning, multi-case field evaluation of a working system across four distinct real organizations, using each company's own AI-adoption context as the "task."

## Main results

**Reported across cross-checked search excerpts:** human input was found to be essential — not optional — for clarifying technical details the agents lacked context for, ensuring the generated requirements were accurate to each company's specific situation, and validating the system's prioritization decisions. Across all four companies, participants converged on three areas the system still needed to improve: **usability, transparency, and scalability**. The authors' overall conclusion is that LLM-based multi-agent systems can support strategic AI-adoption planning specifically when they enable iterative refinement with human experts, rather than functioning as a stand-alone drafting tool. Exact quantitative metrics (e.g., satisfaction scores, time comparisons, or agreement rates) could not be independently verified from the sources available in this session.

## Effects on human performance, trust, workload, safety, or decision quality

The paper's own framing centers on *decision quality* and *fit-for-purpose accuracy*: the recurring finding across companies was that outputs only became organizationally trustworthy once humans had corrected and validated them. This is a qualitative, not quantified, oversight effect — the study appears to report *why* and *where* human review mattered (technical clarification, contextual accuracy, prioritization validation) more than it reports standardized quantitative measures like trust scales or workload instruments. That distinction should be treated as an interpretation flag rather than a confirmed fact, since the full paper could not be read directly in this session.

## What is genuinely new

- A concrete demonstration of an LLM-based multi-agent system applied to a strategically important but understudied flavor of requirements engineering: figuring out an organization's own requirements *for adopting AI*, rather than requirements for a conventional software product.
- Evaluation across **four real companies** rather than a single company case study or a synthetic benchmark, giving some (limited) cross-organizational signal.
- An explicit, empirically grounded argument for *where* human input is load-bearing in this kind of system: technical clarification, contextual accuracy, and prioritization validation, rather than a vague appeal to "human oversight" in the abstract.

## Limitations and open questions

- **Small, qualitative-scale sample.** Nine participants across four companies (roughly two per company) is enough to surface themes but not to support statistical claims about how well the system performs in general.
- **Self-reported, single-timepoint data.** Post-session questionnaires plus one interview per company capture immediate impressions rather than sustained use over time.
- **Usability, transparency, and scalability remain open problems**, by the authors' own account — meaning the paper documents a promising direction more than a finished, deployment-ready system.
- **Sourcing caveat (this summary).** Because full-text access was blocked in this research session, exact statistics, direct participant quotations, and the fine-grained system architecture could not be verified beyond what surfaced in cross-checked search excerpts. Readers should consult the open-access article for the full methodology and results tables.

## Practical implications

For organizations exploring AI adoption, this paper offers a tested pattern rather than a theory: don't ask a multi-agent LLM system to define your AI strategy requirements alone, but don't do it entirely by hand either. Structuring the process as generate-review-refine, with named checkpoints where domain experts correct and validate machine-drafted output, appears to be where the real value showed up across four independent companies — and where the current rough edges (usability, transparency, scalability) still need work before this becomes a turnkey tool.

## Why you should care

Most "agentic AI meets the enterprise" stories focus on agents executing tasks — writing code, filing tickets, answering customers. This paper is about agents further upstream, helping define *what an organization should even be building* with AI in the first place, and it's refreshingly honest that this only worked because real people at real companies caught what the agents got wrong. As more organizations reach for agentic tools to plan their own AI rollouts, this is a concrete, if early and small-scale, data point on how to structure that human-agent handoff so the humans stay meaningfully in charge of the outcome.
