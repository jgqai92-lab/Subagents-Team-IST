# IST Quick Start Guide

> Get up and running with the Investment Screening Team in 5 minutes.

---

## What is IST?

The Investment Screening Team (IST) is a multi-agent framework that converts unstructured content (podcasts, interviews, articles, earnings calls) into ranked, time-phased equity investment screens. It uses 9 specialized agents coordinated through a 5-phase workflow.

**IST screens broadly; HFRT researches deeply.** IST produces ranked equity lists. You can then send Tier 1 names to HFRT for deep research.

---

## Prerequisites

1. Claude Code CLI installed
2. Agents created via `/agents` command
3. IST rules added to your global CLAUDE.md

---

## Creating Agents

### Step 1: Open Agent Manager

```
/agents
```

### Step 2: Create Each Agent

Create these 9 agents using the definitions in the `agents/` folder:

| Agent | Model | Definition File |
|-------|-------|-----------------|
| @IST_Commander | Sonnet | agents/IST_Commander.md |
| @Content_Analyst | Opus | agents/Content_Analyst.md |
| @Bottleneck_Mapper | Opus | agents/Bottleneck_Mapper.md |
| @External_Validator | Sonnet | agents/External_Validator.md |
| @Equity_Scanner | Sonnet | agents/Equity_Scanner.md |
| @Effects_Analyst | Opus | agents/Effects_Analyst.md |
| @Screen_Optimist | Opus | agents/Screen_Optimist.md |
| @Screen_Pessimist | Opus | agents/Screen_Pessimist.md |
| @Screen_Synthesizer | Opus | agents/Screen_Synthesizer.md |

---

## Starting a Screen

### Basic Command

```
@IST_Commander, screen this content for investment ideas:

[Paste your quotes, excerpts, timestamps, or data here]
```

**Examples:**
```
@IST_Commander, screen this podcast for investable themes:

"Quote about energy constraints" [02:15:30]
"Quote about transformer shortages" [02:46:10]

@IST_Commander, screen these earnings call notes for investment ideas
```

### What Happens Next

1. **Phase 1:** @Content_Analyst extracts investable claims and assesses source bias
2. **Phase 2:** @Bottleneck_Mapper builds temporal cascade; @External_Validator cross-references
3. **Phase 3:** @Equity_Scanner identifies equities; @Effects_Analyst maps downstream effects
4. **Phase 4:** @Screen_Optimist and @Screen_Pessimist review independently (parallel, isolated)
5. **Phase 5:** @Screen_Synthesizer produces master screen, rotation strategy, catalyst calendar, investment thesis report

---

## Project Setup

### For Each Screening Project

1. Copy screening templates to your project:
```
cp -r "Investment Screening Team/screening_template" ./[project]/
```

2. Create coordination folder:
```
mkdir ./[project]/.ist
```

3. Start screening:
```
@IST_Commander, screen this content for investment ideas: [content]
```

### Folder Structure

```
[your-project]/
├── screening_template/
│   ├── 00_SCREENING_BRIEF.md
│   ├── 01_CONTENT_EXTRACTION.md
│   ├── ... (13 templates total)
│   └── 12_INVESTMENT_THESIS.md
├── .ist/
│   ├── PROGRESS.md
│   ├── OPTIMIST_REVIEW.md
│   ├── PESSIMIST_REVIEW.md
│   ├── SYNTHESIS_REPORT.md
│   ├── SCREEN_CERTIFICATION.md
│   └── HFRT_HANDOFF.md
└── frameworks/
    ├── scarcity_abundance.md
    ├── ... (7 frameworks total)
    └── null_hypothesis.md
```

---

## Checking Progress

### View Progress Log

```
Show me .ist/PROGRESS.md
```

### Sample Progress Log

```markdown
## Checkpoint Log

| Timestamp | Phase | Step | Agent | Status | Output File |
|-----------|-------|------|-------|--------|-------------|
| 2026-02-06T10:00:00 | 1 | 1.2 | @Content_Analyst | COMPLETE | 01_CONTENT_EXTRACTION.md |
| 2026-02-06T10:30:00 | 2 | 2.1 | @Bottleneck_Mapper | COMPLETE | 02_BOTTLENECK_MAP.md |
| 2026-02-06T11:00:00 | 2 | 2.2 | @Bottleneck_Mapper | IN_PROGRESS | 03_DEMAND_MODELS.md |
```

---

## Resuming a Screen

If screening is interrupted, resume from last checkpoint:

```
@IST_Commander, resume screening from Phase [X]
```

**Example:**
```
@IST_Commander, resume screening from Phase 2
```

---

## Emergency Stop

To halt screening immediately:

```
HALT IST
```

or

```
STOP
```

---

## Output Files

### Final Deliverables

| Template | Content |
|----------|---------|
| 08_MASTER_SCREEN.md | Ranked equity table with all data |
| 09_ROTATION_STRATEGY.md | Time-phased allocation model |
| 10_CATALYST_CALENDAR.md | Dated catalysts with impact ratings |
| 11_STRESS_TESTS.md | Framework and name-level stress tests |
| 12_INVESTMENT_THESIS.md | Unified narrative investment thesis report |
| .ist/HFRT_HANDOFF.md | Tier 1 names ready for HFRT research |

### Key Output: Master Screen

The primary output is `12_INVESTMENT_THESIS.md`, a unified narrative report. The structured data lives in `08_MASTER_SCREEN.md`, which includes:

- Ranked equity table (Tier 1/2/3)
- Scarcity scores
- Moat evidence
- Catalyst with dates
- Bull/bear cases per name
- Phase alignment
- Suggested allocation

---

## Understanding Tiers

| Tier | Name | Criteria | Allocation |
|------|------|----------|-----------|
| 1 | High Conviction Unloved | Strong moat + undervalued + multi-source | 5-8% |
| 2 | Fully Valued Watchlist | Strong moat + expensive | 3-5% (on pullback) |
| 3 | Speculative | Binary/pre-revenue | 1-3% max |

---

## Sending Names to HFRT

After IST completes, send Tier 1 names to HFRT for deep research:

```
@HFRT_Commander, research [TICKER]
```

**Example:**
```
@HFRT_Commander, research CLF
@HFRT_Commander, research ATKR
```

IST screens broadly (themes to equities); HFRT researches deeply (single company).

---

## Common Commands

| Command | Purpose |
|---------|---------|
| `@IST_Commander, screen [content]` | Start new screen |
| `@IST_Commander, resume from Phase [X]` | Continue interrupted screen |
| `Show .ist/PROGRESS.md` | Check progress |
| `HALT IST` | Emergency stop |
| `@HFRT_Commander, research [TICKER]` | Deep research on Tier 1 name |

---

## Quality Gates

Screening cannot proceed until gates pass:

### Gate 1: Content Sufficiency (Phase 1 -> 2)
- 3+ claims with quantitative anchors
- 1+ temporal marker
- Source bias assessed
- Brief confirmed by user

### Gate 2: Research Sufficiency (Phase 3 -> 4)
- Bottlenecks temporally phased
- Demand models quantified
- External validation attempted
- 5+ candidates with moats
- Effects mapped

### Gate 3: Screen Coherence (Phase 5)
- Optimist + Pessimist complete
- All disagreements addressed
- Tier 1 names stress-tested
- No placeholders remaining
- Investment thesis report complete and self-contained
- All Tier 1 names have narrative analysis in report

---

## Anti-Hallucination Tags

Every claim must be tagged:

| Tag | Use |
|-----|-----|
| `[SOURCE: speaker, time, quote]` | Original content citation |
| `[EXT-SOURCE: source, date, data]` | Independent external data |
| `[MARKET-DATA: exchange, date]` | Exchange/market data |
| `[ESTIMATE(method)]` | Calculated estimate with methodology |
| `[CONSENSUS: source, date]` | Analyst consensus |
| `[GAP: reason]` | Data not available |

---

## Troubleshooting

### "Gate failed"
Check gate requirements. Return to responsible agent to complete missing work.

### "Missing source tags"
Add [SOURCE], [EXT-SOURCE], [ESTIMATE], or [GAP] tags to all claims.

### "Progress lost"
Read .ist/PROGRESS.md and resume from last checkpoint.

### "Screen seems one-sided"
Verify Optimist/Pessimist isolation. @Screen_Synthesizer must balance both.

### "No Tier 1 names"
This is a valid outcome. Not all content generates high-conviction ideas.

---

## Reference Documents

| Document | Location |
|----------|----------|
| Complete Guide | `INVESTMENT_SCREENING_TEAM_GUIDE.md` |
| CLAUDE.md Rules | `CLAUDE_MD_SECTION.md` |
| Agent Definitions | `agents/` folder |
| Screening Templates | `screening_template/` folder |
| Analysis Frameworks | `frameworks/` folder |

---

## Next Steps

1. Create agents using `/agents` command
2. Copy IST rules to your global CLAUDE.md (see CLAUDE_MD_SECTION.md)
3. Start your first screen: `@IST_Commander, screen [content]`

---

**Need more detail?** See `INVESTMENT_SCREENING_TEAM_GUIDE.md` for complete documentation.
