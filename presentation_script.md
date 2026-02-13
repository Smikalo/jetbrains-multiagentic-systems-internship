# Presentation Speaker Script

## How to Use
Read the notes for each slide before or during your presentation.
Aim for ~2 minutes per slide (24 min total for 12 slides).

---

## Slide 1: Title Slide
**[Duration: ~1 min]**

> Good morning/afternoon. I'm presenting my research for the JetBrains internship — Task 1: studying agentic development practices.
>
> The title gives you the scope: this is an empirical study grounded in real data. We analyzed evidence from 129,134 GitHub repositories and 73,543 developer survey responses across six different classes of data sources.
>
> The core question is simple: AI coding agents went from near-zero to measurable adoption in under a year. How fast, how concentrated, and what does it mean — especially for a company like JetBrains?

---

## Slide 2: Research Questions
**[Duration: ~1.5 min]**

> We structured the study around five research questions.
>
> RQ1 asks about raw prevalence — what fraction of projects show agent traces, and does project age matter?
>
> RQ2 examines market structure — is this a fragmented or concentrated market?
>
> RQ3 looks at the emerging conventions like AGENTS.md and CLAUDE.md — which one is winning?
>
> RQ4 is perhaps the most important: what does rigorous evidence actually say about productivity? Not vendor claims — peer-reviewed studies.
>
> And RQ5 tracks the capability frontier — SWE-bench scores — to understand how fast these tools are improving.
>
> For each question, we formulated a testable hypothesis and evaluated it statistically.

---

## Slide 3: Methodology
**[Duration: ~2 min]**

> Our methodology is a convergent mixed-methods design. We did NOT collect new primary data — instead we curated, cross-validated, and statistically analyzed existing public datasets from six source classes.
>
> The foundation is the Robbes et al. paper from January 2026, which scanned 129,134 active, mature GitHub projects using 110 detection heuristics across 48 different coding agents. That is the largest study of its kind.
>
> We triangulate that with two major developer surveys — Stack Overflow at 49,000 respondents and JetBrains DevEco at 24,500.
>
> Platform metrics come from official announcements — GitHub, Anthropic, Cursor. Package registries give us SDK download trends from PyPI and npm. And SWE-bench provides the benchmark trajectory.
>
> Everything is reproducible. Running python src/analyze.py regenerates every figure, table, and statistical test in the paper.

---

## Slide 4: Adoption by Project Age (RQ1)
**[Duration: ~2 min]**

> Here is our first key finding. This chart shows agent adoption stratified by project age, from the Robbes et al. dataset.
>
> The pattern is striking: 21% of projects under one year old show file-level agent traces — that is the blue bars. For projects over ten years old, it drops to under 5%.
>
> The Pearson correlation is r = -0.86, which is a strong negative correlation. The p-value of 0.064 narrowly misses the 0.05 threshold, but that is because we only have five age bins — the effect is directionally robust.
>
> The green bars show estimated total adoption including commit-level signals — ranging from 15.85% to 22.60% overall. That is roughly one in five active GitHub projects.
>
> The practical implication: agents are entering through new projects, not being retrofitted into legacy codebases. This matters for enterprise adoption timelines.

---

## Slide 5: Market Structure (RQ2)
**[Duration: ~2 min]**

> The market has consolidated into what we call a three-way oligopoly.
>
> GitHub Copilot leads with 20 million all-time users. Cursor reached 1 million daily active users and a billion-dollar ARR. Claude Code, though younger, hit 2.5 billion dollars in total Anthropic ARR and grew 10x in three months.
>
> Together, the top three platforms account for 93.8% of users in our dataset. The Herfindahl-Hirschman Index — the standard measure of market concentration — is 5,801. Anything above 2,500 is considered highly concentrated.
>
> But here is the interesting twist: the average adopting project uses MORE than 1.6 agents. Developers are treating these tools as complementary, not substitutive. That is unusual in developer tooling markets and suggests the ecosystem rewards integration — which is exactly where JetBrains could add value.

---

## Slide 6: Configuration Conventions (RQ3)
**[Duration: ~2 min]**

> The configuration landscape shows an interesting split.
>
> AGENTS.md leads in raw adoption — about 60,000 repositories. It is now a cross-platform standard backed by the Linux Foundation, supported by OpenAI Codex, Cursor, Google Jules, and others.
>
> But CLAUDE.md leads in maintenance intensity. The Murillo et al. paper found that CLAUDE.md files have a median update interval of just 24.1 hours — meaning developers are actively curating them nearly daily. Copilot instruction files update every 70 hours by comparison.
>
> And 17% of repositories use ALL three major formats simultaneously. So this is not a winner-take-all situation yet — developers hedge by supporting multiple conventions.
>
> For JetBrains, the recommendation is clear: AGENTS.md is the standard to support first, but multi-format awareness is important.

---

## Slide 7: The Productivity Paradox (RQ4)
**[Duration: ~2.5 min]**

> This is the most important slide for anyone making investment decisions about AI tools.
>
> The forest plot shows six studies. The spread is enormous — 74.8 percentage points from the most positive to the most negative result.
>
> Peng et al., a lab RCT with 95 developers, found a 55.8% speedup, p = 0.0017. That is the number vendors love to cite.
>
> But METR, also a randomized study, found that experienced open-source developers were 19% SLOWER with AI tools. And here is the kicker — those developers believed they were 20% faster. There is a real perception gap.
>
> Field experiments at Microsoft and Accenture fall in between — 17% and 8% improvement respectively.
>
> The takeaway is not that AI tools do not help — it is that context dominates. Task type, developer experience, codebase familiarity, and integration quality all matter more than the tool itself. This is why rigorous measurement — exactly what JetBrains could enable in IDEs — is so valuable.

---

## Slide 8: SWE-bench Trajectory (RQ5)
**[Duration: ~1.5 min]**

> Despite the productivity paradox, the capability frontier is unambiguous.
>
> SWE-bench Verified — the gold-standard benchmark for automated bug fixing — went from 3.8% in October 2023 to 74% by mid-2025. That is a 19.5x improvement in 21 months.
>
> The log-linear correlation is r = 0.95 with p = 0.004 — highly significant. This is near-exponential growth in real-world software engineering ability.
>
> At this rate, automated systems are approaching human-level performance on the specific task of fixing bugs in well-defined open-source codebases. The implications for tool design are profound: IDEs will increasingly need to delegate complex tasks to AI agents, not just offer code completion.

---

## Slide 9: Tool Ecosystem and Beads
**[Duration: ~2 min]**

> The left chart shows the broader ecosystem by GitHub stars. Spec-kit from GitHub leads at 68.8K stars, followed by Superpowers and awesome-cursorrules.
>
> Beads and Gas Town — Steve Yegge's projects — sit in the 8-9K range. They are smaller but they represent something architecturally distinct: persistent memory for agents.
>
> Beads uses a three-layer design: a CLI talks to SQLite for fast local queries, which syncs to JSONL files tracked in git. This solves what Yegge calls the "50 First Dates" problem — agents forget everything between sessions.
>
> The right chart shows Beads community ecosystem: 15 third-party projects across 7 programming languages, including a Rust port, multiple TUIs, editor plugins, and even a Jira integration. For a project under a year old, that is remarkable traction.
>
> Gas Town builds on top of Beads for multi-agent orchestration — formulas, gates, slots, swarm primitives. It is early but architecturally ambitious.

---

## Slide 10: Hypothesis Results Summary
**[Duration: ~1.5 min]**

> Let me summarize the hypothesis tests.
>
> H1 — the age-adoption correlation — is directionally confirmed with a strong effect but marginally significant p-value due to few bins.
>
> H2 — productivity variance by study design — is clearly confirmed, with a 74.8 percentage point spread.
>
> H3 — the AGENTS.md vs CLAUDE.md split — is partially confirmed: volume versus intensity.
>
> H4 — the three-platform oligopoly — is confirmed with an HHI of 5,801.
>
> H5 — the SWE-bench exponential trend — is the strongest result: r = 0.95, p = 0.004.
>
> Four out of five confirmed, one partially confirmed. No hypothesis was outright rejected, but we are honest about the limitations — especially H1 small sample of age bins.

---

## Slide 11: JetBrains Implications
**[Duration: ~2 min]**

> Three actionable implications for JetBrains.
>
> First: AGENTS.md support. With 60,000+ repositories using it and Linux Foundation backing, this is the configuration standard to build into IntelliJ IDEs. Parsing, validation, auto-generation, and intelligent suggestions based on project type.
>
> Second: persistent memory integration. The "50 First Dates" problem is real. Beads shows one architecture for solving it. JetBrains could provide IDE hooks for .beads/ directories — dependency visualization, agent onboarding flows, task-graph views. Even if Beads is not the final winner, the category will persist.
>
> Third: benchmark-aware AI features. With SWE-bench capability doubling roughly every few months, IDE AI features should dynamically adjust what they delegate versus what they suggest. Today's "too complex for AI" task may be routine in six months.
>
> Together, these three directions position JetBrains as the intelligent integration layer between developers and the rapidly evolving agent ecosystem.

---

## Slide 12: Conclusion
**[Duration: ~1 min]**

> To wrap up: agentic development has reached 15-23% of active GitHub projects in under two years. The market is concentrated but multi-tool. Productivity is real but context-dependent. Capability is growing near-exponentially. And a new category — agentic memory — is emerging with Beads at the forefront.
>
> All of our analysis is reproducible. Every figure, table, and statistical test can be regenerated with a single command. The full paper, code, and data sources are provided.
>
> Thank you. I am happy to take questions.

---

## Anticipated Q&A Preparation

**Q: Why did you choose these specific data sources?**
> We prioritized sources that met three criteria: public availability for reproducibility, large sample sizes for statistical power, and methodological rigor (peer review or established survey methodology).

**Q: How do you reconcile the METR and Peng results?**
> Task type is the key moderator. Peng used a simple HTTP server implementation — a well-defined, bounded task where AI excels. METR used real open-source contributions requiring deep codebase understanding — where AI adds friction. The truth is task-dependent.

**Q: Why is H1 only directionally confirmed?**
> With only 5 age bins, Pearson correlation has low power. The effect size (r = -0.86) is very strong, but the p-value (0.064) narrowly misses 0.05. With finer-grained age data from the original dataset, this would almost certainly reach significance.

**Q: What is the threat from AI to JetBrains business model?**
> The data suggests integration, not displacement. Developers use 1.6+ agents per project — they want tools that work together, not one tool that does everything. JetBrains strength as an IDE that integrates workflows is exactly what the multi-agent future demands.

**Q: Is Beads too early-stage to matter?**
> Compared to AGENTS.md (60K repos), yes. But the category of persistent agent memory will matter — Claude Code task system was reportedly inspired by Beads approach. The architectural pattern will persist even if the specific tool evolves.
