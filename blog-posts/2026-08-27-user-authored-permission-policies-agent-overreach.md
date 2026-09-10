# Do User-Authored Permission Policies Improve Protection Against AI Agent Overreach?

**Authors:** Ting Yan
**Publication date:** 2026-08-27 (arXiv v1, id 2608.27443)
**Venue:** arXiv preprint (subjects: cs.HC, cs.CR) — not yet peer-reviewed at a conference/journal, as far as could be verified
**Paper link:** https://arxiv.org/abs/2608.27443 (PDF: https://arxiv.org/pdf/2608.27443)
**Code link:** Not available (no public repository found)
**Project page:** Not available
**Date added:** 2026-09-10

> **A note on sourcing:** this research session's network could not directly fetch arxiv.org, its mirrors, or other external paper-hosting sites (the outbound proxy blocked all of them by organizational policy). This summary is therefore built entirely from the paper's abstract and cross-checked secondary descriptions gathered across many independent web searches, not a direct read of the full PDF. Facts corroborated across multiple independent searches (author, dates, study design, participant count, exact effect sizes/confidence intervals, and headline findings) are reported as such; anything that could not be cross-confirmed this way is marked "Not available" or flagged as uncertain rather than invented.

---

## The problem the paper addresses

AI agents are starting to act as a general-purpose interface to your digital life — reading and sending email, touching files, moving money, handling personal data. Every one of those actions is a small decision: should the agent be allowed to do this specific thing, right now? Today's two default answers are "ask me every single time" (safe but exhausting) or "just let the model decide" (convenient but opaque). This paper asks about a third option: what if, instead of deciding case by case, people write standing rules in advance — plain-language policies like "never share my address" or "ask before any payment" — and let the agent apply those automatically?

## Why this problem matters

Ordinary people, not just developers, are the ones who will be granting AI agents access to email, files, calendars, and payment methods. If the only real safeguard is "approve every action" (tedious, and people click through it) or "trust the model's own judgment" (invisible and hard to hold accountable), agent adoption either stalls on annoyance or quietly ships harm when an agent does something the user never meant to authorize. Because permission systems for agents are being designed and shipped right now — in products like Claude, ChatGPT, and Codex — evidence about whether user-written rules actually work as a substitute for constant supervision is directly useful to the people building and regulating these systems today, not a hypothetical concern for later.

## What makes the system agentic

The paper studies an LLM-based agent that takes multi-step actions across everyday digital services (email, files, payments, personal data) rather than just answering questions. A key architectural piece is that a language model maps each candidate action the agent wants to take onto a plain-language "consequence category" (e.g., "sends a message to someone new," "spends money," "shares personal data") — and it is these categories, not raw technical actions, that permission rules are written against. Participants supervised the agent through a simulated day containing 18 actions, seven of which were deliberately "overreach" — actions that went beyond what the user had actually asked for.

## How humans and the AI agent collaborate

Three different collaboration/oversight mechanisms were compared head-to-head, each defining a different relationship between the human and the acting agent:

- **HITL (human-in-the-loop):** the agent proposes each action and the human approves or denies it individually, every time.
- **AUTO (automated review):** an automated model reviews each action against the user's standing preferences instead of the human doing it live.
- **POLICY (user-authored consequence policy):** the human writes "allow," "ask," or "never" rules in advance for each consequence category, and the agent applies those rules to future actions without a fresh check-in.

## What role the human plays

In HITL, the human is the real-time approver of every single action. In POLICY, the human is a rule-author who commits, ahead of time, to standing instructions the agent should follow later without re-asking. In AUTO, the human's own preferences are the reference point an automated reviewer is supposed to enforce, but the human isn't directly in the approval loop for each action.

## What role the AI agent plays

The agent is the one actually executing the 18-action simulated day — including the 7 overreach actions — and, depending on condition, either pauses for human approval, submits to automated review, or checks its own proposed action against the user's pre-written policy rules before proceeding.

## How control, initiative, and decisions are shared

This is precisely a study of where oversight sits on the "supervise every step" vs. "delegate in advance" spectrum. HITL keeps humans fully in the loop per action; POLICY shifts initiative to the agent by letting it self-govern against rules set earlier; AUTO removes the human from individual decisions entirely, substituting an automated reviewer. The paper's whole design is a controlled comparison of these three ways of splitting control between person and agent.

## The paper's main idea

**Claim by the author:** writing your own permission policy in advance is not, by itself, a stronger safeguard than approving actions one at a time or letting an automated reviewer check them — and the reason is behavioral, not technical: given the choice, people mostly write "ask me" rules rather than firm "allow"/"never" rules, which just pushes the decision back into a live approval moment anyway, undercutting the whole point of writing a policy ahead of time.

## How the approach works

113 participants without professional software backgrounds were assigned across the three conditions (HITL, AUTO, POLICY) and each supervised the same simulated 18-action day, which included 7 actions that overreached beyond the user's original request. In the POLICY condition, participants authored "allow"/"ask"/"never" rules per consequence category before the simulated day ran; the language model then classified each of the agent's actions into a consequence category and applied the matching rule.

## Human study or evaluation design

**Demonstrated in the paper:** a controlled, between-subjects human-participant experiment (not a simulated-user study) comparing three real oversight mechanisms on an identical task, with overreach-blocking rates as the primary quantitative outcome, plus an exploratory analysis of which specific rules participants chose to write.

## Participants and study setting

**Real recruited participants:** N = 113 people without professional software backgrounds, assigned across the HITL, AUTO, and POLICY conditions. According to descriptions found by this session, the study was independently funded without institutional or employer sponsorship, and — because the research was not conducted through an institution with access to an ethics review board — it received no formal ethics review or exemption determination. Detailed demographics (age, recruitment platform, compensation) were not available from the sources this session could access.

## Experiments or benchmarks

Not a public benchmark — a custom, purpose-built simulated "day" of 18 agent actions (7 of them overreach) used identically across all three conditions, inside the author's own study platform.

## Main results

**Demonstrated in the paper (per available descriptions, not independently verified against the full PDF):**
- POLICY blocked significantly *less* overreach than HITL (a drop of 20.1 percentage points, 95% CI [-32.1, -8.1]) and less than AUTO (a drop of 14.5 percentage points, 95% CI [-25.8, -3.2]).
- Of 140 total POLICY rules participants wrote, 114 were "ask" rules rather than firm "allow" or "never" rules — meaning most of the time, a written policy just deferred the decision back to a live prompt instead of settling it in advance.
- Of the 148 overreach actions that were ultimately executed under POLICY, 133 happened after a human approved them in the moment (via an "ask" rule) and only 15 ran fully automatically under a standing "allow" rule.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the paper directly measures safety/oversight effectiveness — the rate at which each mechanism blocked unwanted ("overreach") agent actions — as its primary human-relevant outcome, and shows POLICY performing worse on this measure than either real-time human approval or automated review. **Our interpretation:** the practical safety implication is that letting people write standing permission rules doesn't reduce their oversight burden the way it's marketed to — people still end up approving most of the risky actions live, because they overwhelmingly choose "ask" rather than commit to a firm rule, so the promised convenience of "set it and forget it" delegation may be closer to per-action approval in disguise, with an added false sense that a policy has already handled it.

## What is genuinely new

- A direct, controlled, three-way comparison of live approval, automated review, and user-authored standing policy for the same agent tasks — rather than proposing and advocating for just one mechanism, as much prior permission-system work does.
- The counterintuitive empirical finding that writing your own rules in advance performs *worse*, not better, at blocking overreach than simply being asked each time.
- A concrete behavioral explanation for that gap: people's revealed preference is overwhelmingly to keep the "ask" option open rather than commit to allow/never rules, which the paper frames as a tension between wanting case-by-case choice and needing a policy to actually settle decisions ahead of time.

## Limitations and open questions

- This session could not fetch the full PDF, so exact statistical methods beyond the reported percentage-point differences and confidence intervals, the specific LLM(s) used to power the agent and the consequence-classification step, and the author's own stated limitations could not be independently confirmed — readers who need precise methodology should consult the paper directly.
- The study used a simulated 18-action "day" rather than participants' own real accounts/data, so it is not established how these findings hold up when the stakes and context are the user's actual email, files, or money rather than a scripted scenario.
- The study appears to be independently conducted and, per available descriptions, did not go through a formal institutional ethics review — worth weighing when interpreting participant-protection standards.
- No code repository or public dataset was found, limiting independent replication at this time; the paper does not yet appear to have a peer-reviewed venue.

## Practical implications

For teams designing permission systems for AI agents (browser agents, computer-use agents, personal assistants), this study is a caution against treating "let users write their own rules in advance" as a lower-friction substitute for live approval or automated review. If most users write "ask me" rules anyway, a policy-authoring UI may deliver the appearance of upfront control while actually just relocating the same live decisions to a different screen — so designers may need to actively encourage firmer allow/never commitments, or accept that policies will not meaningfully reduce how often people are interrupted for approval.

## Why you should care

As agent permission systems get built into mainstream products right now, it's tempting to assume that giving users a rules-editor is strictly better than making them approve things one at a time — it feels more efficient and more "in control." This paper's controlled, 113-participant test says that assumption doesn't hold up in practice: people default to keeping their options open rather than committing to rules, so a policy-based safeguard can end up blocking less than the tedious approve-everything approach it was meant to replace. That's a concrete, actionable finding for anyone shipping agent permission UX today.
