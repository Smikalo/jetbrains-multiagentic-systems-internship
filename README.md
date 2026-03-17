# Agentic Development Practices in Open-Source Repositories

**An Empirical Study of Adoption, Tooling, and Productivity Across 129,134 GitHub Projects and 73,543 Developer Survey Responses**

> JetBrains Internship Application — [Project #1757: Multi-Agentic Systems Best Practices](https://internship.jetbrains.com/projects/1757)

---

## Overview

AI coding agents went from research prototype to measurable adoption in under a year. This repository contains the complete research submission for JetBrains Internship Task 1 — a convergent mixed-methods study that triangulates six classes of public data sources to answer five research questions about the current state of agentic development.

**Key findings at a glance:**

- **15–23%** of active GitHub projects show agent traces, with a strong inverse correlation to project age (*r* = −0.86)
- The market has consolidated into a **three-way oligopoly** (Copilot, Cursor, Claude Code) with HHI = 5,801
- Reported productivity effects vary from **−19% to +55.8%** depending on study design — context dominates
- SWE-bench automated bug-fixing capability grew **19.5×** in 21 months (*r*<sub>log</sub> = 0.95, *p* = 0.004)
- **AGENTS.md** leads in raw adoption (~60K repos) while **CLAUDE.md** leads in maintenance intensity (24.1h median update interval)

## Repository Contents

```
.
├── paper.pdf                    # Full academic paper (PDF)
├── presentation.pptx            # 12-slide presentation deck
├── presentation_script.md       # Speaker notes with timing cues (~24 min)
├── agentic-dev-study-code.zip   # Reproducible analysis pipeline
│   ├── src/analyze.py           #   → Generates all figures, tables, and stats
│   ├── src/make_presentation.js #   → Builds the .pptx programmatically
│   ├── paper/paper.tex          #   → LaTeX source for the paper
│   ├── SOURCES.md               #   → Full provenance chain for every data point
│   └── requirements.txt         #   → Python dependencies
└── README.md                    # You are here
```

## Reproducing the Analysis

The entire pipeline — every figure, table, and statistical test in the paper — regenerates from a single command.

```bash
# 1. Extract the code archive
unzip agentic-dev-study-code.zip -d code && cd code

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the full pipeline
python src/analyze.py
```

**Requirements:** Python 3.10+, ~200 MB disk, no GPU. Runs in under 30 seconds on all major platforms (Linux, macOS 14+, Windows 11 via WSL2 or native).

All outputs land in `output/`:

| Directory | Contents |
|-----------|----------|
| `output/figures/` | 8 publication-quality PNG + PDF figures (300 dpi) |
| `output/tables/` | 7 CSV tables matching every table in the paper |
| `output/analysis_results.json` | Hypothesis-test statistics with *p*-values and effect sizes |

## Research Questions and Hypotheses

| # | Research Question | Hypothesis | Result |
|---|-------------------|------------|--------|
| RQ1 | How prevalent are agent traces, and does project age matter? | Strong inverse age–adoption correlation | ✅ Confirmed (*r* = −0.86, *p* = 0.064) |
| RQ2 | Is the market fragmented or concentrated? | Three-platform oligopoly dominates | ✅ Confirmed (HHI = 5,801) |
| RQ3 | Which configuration convention is winning? | AGENTS.md vs CLAUDE.md split | ⚠️ Partially confirmed (volume vs intensity) |
| RQ4 | What does rigorous evidence say about productivity? | High variance across study designs | ✅ Confirmed (74.8 pp spread) |
| RQ5 | How fast is the capability frontier advancing? | Near-exponential SWE-bench growth | ✅ Confirmed (*r* = 0.95, *p* = 0.004) |

## Methodology

This study uses a **convergent mixed-methods design** — no new primary data was collected. Instead, existing public datasets were curated, cross-validated, and statistically analyzed from six source classes:

1. **Empirical GitHub analysis** — Robbes et al. (2026): 129,134 repos, 110 detection heuristics, 48 agents
2. **Developer surveys** — Stack Overflow (49K respondents) + JetBrains DevEco (24.5K respondents)
3. **Platform metrics** — Official announcements from GitHub, Anthropic, Cursor, Cognition
4. **Package registries** — SDK download trends from PyPI and npm
5. **Benchmark trajectories** — SWE-bench Verified leaderboard progression
6. **Configuration-file studies** — Murillo et al. (2025) on AGENTS.md / CLAUDE.md maintenance patterns

Every data point traces to a publicly verifiable source. See `SOURCES.md` inside the code archive for URLs, access dates, and suggested Wayback Machine snapshots.

## Figures Produced

| # | Figure | Description |
|---|--------|-------------|
| 1 | `fig1_adoption_by_age` | Agent adoption rate by project age (*N* = 129,134) |
| 2 | `fig2_platform_landscape` | Users vs ARR scatter plot across platforms |
| 3 | `fig3_config_adoption` | Configuration-file convention repo counts |
| 4 | `fig4_productivity_forest` | Forest plot of 6 productivity studies (−19% to +55.8%) |
| 5 | `fig5_sdk_trends` | Anthropic vs OpenAI SDK download trends |
| 6 | `fig6_swebench` | SWE-bench score progression (Oct 2023 – mid 2025) |
| 7 | `fig7_tool_stars` | GitHub stars for agentic ecosystem tools |
| 8 | `fig8_beads_ecosystem` | Beads community ecosystem (15 third-party projects, 7 languages) |

## Implications for JetBrains

The paper concludes with three actionable recommendations:

1. **AGENTS.md support in IntelliJ IDEs** — With 60K+ repos and Linux Foundation backing, AGENTS.md is the configuration standard to support first: parsing, validation, auto-generation, and intelligent suggestions by project type.

2. **Persistent memory integration** — The "50 First Dates" problem (agents forgetting context between sessions) is real. IDE hooks for persistent agent memory — dependency visualization, onboarding flows, task-graph views — represent a valuable new product surface.

3. **Benchmark-aware AI features** — With SWE-bench capability doubling roughly every few months, IDE AI features should dynamically adjust what they delegate versus what they suggest. Today's "too complex for AI" task may be routine in six months.

These align with JetBrains' [membership in the Agentic AI Foundation](https://blog.jetbrains.com/blog/2025/12/09/jetbrains-joins-the-agentic-artificial-intelligence-foundation/) and the vision behind [JetBrains Air](https://www.jetbrains.com/help/air/quick-start-with-air.html) — positioning JetBrains as the intelligent integration layer between developers and the rapidly evolving agent ecosystem.

## Tech Stack

| Component | Technology |
|-----------|------------|
| Analysis pipeline | Python 3.10+ — matplotlib, seaborn, pandas, scipy |
| Presentation generator | Node.js — pptxgenjs |
| Paper typesetting | LaTeX — lmodern, booktabs, hyperref |
| Statistical methods | Pearson correlation, HHI concentration index, log-linear regression |

<p align="center">
  <i>Built for the <a href="https://internship.jetbrains.com/projects/1757">JetBrains Internship</a> — February 2026</i>
</p>
