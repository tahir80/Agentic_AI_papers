# Early Adoption of Agentic Coding Tools by GitHub Projects

**Authors:** Maliha Noushin Raida, Daqing Hou (Rochester Institute of Technology)
**Publication date:** 2026-07-15 (arXiv v1, id 2607.14037)
**Venue:** KDD 2026 Workshop on Agentic Software Engineering (SE 3.0); presented 2026-08-09, Jeju, South Korea (peer-reviewed workshop paper)
**Paper link:** https://arxiv.org/abs/2607.14037 (PDF: https://arxiv.org/pdf/2607.14037)
**Code link:** Not available (the study builds on the public **AIDev-pop** dataset of real-world agentic pull requests; no separate code/data repository for this paper's own analysis scripts could be confirmed from available sources)
**Project page:** Not available
**Date added:** 2026-08-12

> **A note on sourcing:** This session's outbound network access to arxiv.org and related mirror/API hosts (export.arxiv.org, ar5iv, Hugging Face, Semantic Scholar) was blocked by organizational egress policy, so this summary could not be built from a direct read of the full PDF. It is instead built by triangulating across multiple independent web searches — including the arXiv abstract page's indexed text, a third-party news writeup (Help Net Security) that appears to have read the full paper, and author/affiliation lookups — cross-checking facts across sources where possible. Facts consistent across sources are reported as such; anything that could not be cross-confirmed is flagged below or marked "not available" rather than invented. Readers should verify exact figures against the primary PDF before citing them.

---

## The problem the paper addresses

AI coding agents — GitHub Copilot's agent mode, OpenAI Codex, Claude Code, and similar tools — no longer just autocomplete a line of code inside an editor. They now open their own branches, write multi-file changes, and submit full pull requests (PRs) to real software projects, the same way a human contributor would. Plenty of prior work has looked at individual agent-authored PRs in isolation — was this one PR good, was it merged, was it buggy. This paper asks a different, more structural question: once a project starts letting these tools submit PRs, **how does the project as a whole absorb that work?** Who actually ends up reviewing and merging agent-written code, how often does this happen, and does the answer depend on whether the project is a two-person side project or a large team with dozens of contributors?

## Why this problem matters

An agent that can write a plausible-looking PR is only useful if a project's human maintainers can realistically fold that PR into their existing workflow without it becoming a review bottleneck or a quality risk. Understanding *how* real projects are currently managing this — who signs off on agent work, how concentrated that responsibility is, and whether small teams handle it differently than large ones — matters for two audiences: tool builders deciding what oversight features to build into agentic coding tools, and open-source maintainers deciding how much of this work to accept and how to structure review before it overwhelms a small number of reviewers.

## What makes the system agentic

The subjects of the study are commercial agentic coding tools — GitHub Copilot's agent mode, OpenAI Codex, and Claude Code — operating in their real, deployed form: given a task, they read repository context, plan and write multi-step, multi-file code changes, and autonomously open a pull request against a live GitHub repository, without a human writing the code line-by-line. This is squarely agentic behavior (planning and taking multi-step actions in an external environment, not a single text response), and the paper studies these agents exactly as they behave "in the wild," across thousands of real repositories, rather than in a controlled sandbox.

## How humans and the AI agent collaborate

The collaboration studied here happens through GitHub's own pull-request workflow: an agent opens a PR, and one or more human project members then read the agent's diff, comment on it, push fixes or revisions, and ultimately merge or reject it. The paper's central contribution is characterizing *the shape* of this collaboration at the project level — not a single PR's back-and-forth, but the aggregate pattern of who within a project ends up doing this reviewing and merging work, and how that pattern shifts with team size.

## What role the human plays

Humans are the gatekeepers: real open-source maintainers and contributors on real GitHub projects who receive agent-authored PRs, review the code, request or make corrections, and decide whether to merge. The paper reports that the great majority of this work — **78.9% of the agentic PRs in the dataset** — passes through a single human reviewer who reads the agent's code, fixes what needs fixing, and merges it alone, rather than being spread across a review team.

## What role the AI agent plays

The agent is the initiator and author of the contribution: it autonomously produces the PR's code changes and submits them for human review, playing the same role a human contributor would when opening a PR, but without a human writing the underlying diff.

## How control, initiative, and decisions are shared

Initiative to *start* the work sits with the agent — it opens the PR unprompted by a specific line-by-line human instruction — while final authority to accept the work rests entirely with a human reviewer, who can accept, request changes, or reject. The paper's key finding is about how that human-side authority is distributed: **small projects (1–5 contributors) concentrate this review-and-merge responsibility even more heavily in a single person than larger projects do**, and even the small projects that use agentic tools most heavily still overwhelmingly rely on that same single-reviewer pattern rather than distributing it. Larger teams spread the reviewing role across more people, but according to the paper this doesn't mean they use agentic PRs any less — it means more individuals within the team take a turn at the gatekeeper role.

## The paper's main idea

**Claim by the authors:** studying agent-authored pull requests one at a time misses an important project-level story. Once you aggregate across a project's full history of agentic PRs, clear patterns emerge in *how* projects absorb this work — patterns that differ systematically by team size — and understanding them is necessary for reasoning about how agentic coding tools are actually being managed in practice, as opposed to how individual PRs perform in isolation.

## How the approach works

The authors built on **AIDev-pop**, a public dataset of real-world agentic pull requests, and analyzed **25,264 agentic PRs from 2,361 popular GitHub repositories**, generated by GitHub Copilot, OpenAI Codex, and Claude Code over a roughly three-month observation window. They grouped repositories by contributor-team size (small: 1–5 contributors; medium; large) and measured, for each group: how many agentic PRs a typical repository generates, what share of a project's overall PR activity these represent, and — for the human-agent collaboration question — how many distinct people within a project take on the reviewer/merger role for agentic PRs, versus how often that role falls to one person repeatedly.

## Human study or evaluation design

**Demonstrated in the paper:** this is not a lab experiment with recruited participants; it is a large-scale, naturalistic observational study of real human maintainers' actual behavior on public GitHub repositories, reconstructed from PR metadata (reviewer identity, commits, merge events) rather than from surveys or self-report instruments. The "human evaluation" here is behavioral and archival, not experimental or self-reported.

## Participants and study setting

**Real-world setting, not recruited participants.** The "participants" are the actual maintainers and contributors of 2,361 popular open-source GitHub repositories who reviewed and merged (or rejected) the 25,264 agentic PRs in the dataset during the observed ~3-month period. No demographic information about these individuals is reported or applicable — they are identified only by their role (reviewer, committer) within each repository's real PR history.

## Experiments or benchmarks

There is no public leaderboard-style benchmark; the "experiment" is the large-scale empirical analysis of the AIDev-pop-derived dataset itself, organized around three research questions: (RQ1) how are agentic coding tools being adopted across projects, (RQ2) what is project-level agentic PR productivity, and (RQ3) how do human-agent collaboration patterns — specifically, who reviews and merges agentic PRs — differ across projects of different team sizes.

## Main results

**Demonstrated in the paper (per cross-checked secondary descriptions; verify against the primary PDF):**
- The median repository generated only **one to two agentic PRs over the ~3-month window** — intensive adoption remains concentrated in a small subset of projects rather than being spread evenly.
- **78.9% of agentic PRs** in the dataset were reviewed and merged by a single human developer acting alone, rather than by a review team.
- **Small projects (1–5 contributors) showed higher participation ratios and higher average agentic-PR activity** than medium or large projects — proportionally more of a small team's contributors get involved with agentic PRs.
- Even the most active small repositories (those with more than 30 agentic PRs) continued to rely predominantly on this single-reviewer pattern rather than shifting to distributed review as volume grew.

## Effects on human performance, trust, workload, safety, or decision quality

**Demonstrated:** the paper does not report trust, workload (e.g., NASA-TLX), or safety survey measures — it has no self-report instrument at all. Its human-related outcome is behavioral: *how review/merge responsibility for agent-authored code is distributed across a project's human contributors*, and how concentrated that responsibility is. **Our interpretation:** the dominance of solo review (79% of PRs) is a meaningful signal about real-world oversight capacity — it suggests that, in practice, agentic contributions are mostly being vetted by exactly one pair of human eyes rather than a team, which is directly relevant to concerns about review quality and reviewer workload, even though the paper itself does not measure workload or review quality directly. Readers should treat any claim about whether this concentration is "good" or "risky" for code quality as our interpretation, not a measured finding of the paper.

## What is genuinely new

- The first analysis (that these searches could identify) to look at agentic PR adoption and review patterns at the **project level**, aggregating across a repository's whole history, rather than scoring individual PRs one at a time.
- The empirical finding that **solo review is the overwhelmingly dominant human-oversight pattern (78.9%)** for agent-authored code across thousands of real repositories, and that this pattern is even more pronounced in small teams.
- A team-size-stratified view of adoption showing that small teams are proportionally the heaviest adopters and users of agentic coding tools relative to their size, not just large, well-resourced projects.

## Limitations and open questions

- This is an observational, archival study of GitHub metadata — it cannot capture reviewers' actual confidence, effort, or reasoning; "one person merged it" does not by itself tell us how carefully that person reviewed it.
- The ~3-month observation window and the specific tool set (Copilot, Codex, Claude Code) mean results may not generalize to other tools, longer time horizons, or private/enterprise repositories not represented in the public AIDev-pop dataset.
- Because this is a workshop paper, the reviewing and publication bar (KDD 2026 Workshop on Agentic Software Engineering) is lighter than a full conference or journal track; findings should be treated as an early empirical signal rather than a fully settled result.
- No participant self-report data exists to say whether solo reviewers felt they had adequate time, confidence, or support — this is an open question the paper itself does not address.
- This session could not verify RQ2 (project-level productivity) results in detail, additional statistical tests, or a data-availability statement for the paper's own analysis code from the accessible secondary sources; readers should check the primary PDF directly.

## Practical implications

If a single human reviewer is, in practice, the primary line of defense for the large majority of agent-authored code entering real projects — and disproportionately so in small teams with the fewest people to spare — then tool builders and maintainers may want to treat "who else besides the one reviewer sees this" as a deliberate design and process question, rather than an incidental side effect of how PR review happens to be organized today. For maintainers of small projects specifically, the findings suggest that adopting agentic coding tools currently means concentrating more oversight responsibility in fewer people, not less.

## Why you should care

This paper doesn't claim agents are good or bad collaborators — it simply measures, across thousands of real repositories, how the human side of "human-agent collaboration" in software engineering is actually organized right now: mostly one person, reviewing alone, especially on the smallest teams. That's a useful, sobering data point for anyone assuming that human oversight of AI-written code is being distributed across a team by default — in the projects studied here, it usually isn't.
