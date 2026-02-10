# Investment Screening Team (IST) Complete Guide

> **Version:** 1.1
> **Last Updated:** 2026-02-06
> **Framework Pattern:** Multi-Agent Orchestration (based on HFRT/BPT architecture)

---

## Table of Contents

1. [Overview](#overview)
2. [Architecture](#architecture)
3. [Agent Definitions](#agent-definitions)
4. [5-Phase Workflow](#5-phase-workflow)
5. [Quality Gates](#quality-gates)
6. [Anti-Hallucination Protocols](#anti-hallucination-protocols)
7. [Screening Invariants](#screening-invariants)
8. [Dialectic Scrutiny Protocol](#dialectic-scrutiny-protocol)
9. [File Coordination](#file-coordination)
10. [Screening Templates](#screening-templates)
11. [Analysis Frameworks](#analysis-frameworks)
12. [Tier Classification System](#tier-classification-system)
13. [IST-HFRT Handoff](#ist-hfrt-handoff)
14. [Integration with CLAUDE.md](#integration-with-claudemd)
15. [Usage Examples](#usage-examples)
16. [Troubleshooting](#troubleshooting)

---

## Overview

### Purpose

The Investment Screening Team (IST) is a multi-agent framework designed to convert unstructured content (podcasts, interviews, articles, earnings calls, research notes) into ranked, time-phased equity investment screens with quantitative backing, temporal rotation strategies, and skeptical stress-testing.

### Relationship to HFRT

IST and HFRT form a two-stage pipeline:
- **IST** is the upstream idea generator -- it screens content for investable themes and produces ranked equity lists
- **HFRT** is the downstream idea validator -- it performs deep research on individual companies

IST produces screens; Tier 1 names are handed off to the user who can manually trigger HFRT for deep research.

### Key Characteristics

- **Content-Driven**: Starts from unstructured content, not ticker symbols
- **Thematic Screening**: Identifies themes and bottlenecks, then maps to equities
- **Temporal Phasing**: Bottlenecks are sequential, creating rotation strategies
- **Scarcity-First Lens**: Default framework screens for physical scarcity in an AI-abundant world
- **Multi-Order Effects**: Pushes downstream from obvious to non-consensus ideas
- **Dialectic Scrutiny**: Independent bull/bear analysis with isolated reviews

### Design Philosophy

The IST framework enforces:

1. **Strict Role Boundaries**: Each agent has a defined scope; no agent exceeds its mandate
2. **Sequential Execution**: Max 1 concurrent agent (except Phase 4 Optimist+Pessimist)
3. **File-Based Coordination**: All screening artifacts stored in structured templates
4. **Dialectic Review**: Optimist and Pessimist operate in isolation, synthesized by neutral party
5. **Anti-Hallucination Protocols**: 8 specific rules to prevent fabricated data
6. **Screening Invariants**: 8 rules that must hold true for any screening output
7. **Scarcity-First Framework**: Default analytical lens applied to every candidate

---

## Architecture

### System Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              IST ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    COORDINATION LAYER                                │   │
│  │                     @IST_Commander                                   │   │
│  │         (Never writes content - coordination only)                   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                        │
│          ┌─────────────────────────┼─────────────────────────┐             │
│          ▼                         ▼                         ▼             │
│  ┌───────────────┐    ┌─────────────────────────┐   ┌──────────────────┐  │
│  │   EXTRACTION  │    │    THEMATIC ANALYSIS     │   │ EQUITY IDENT.   │  │
│  │@Content_Analyst│   │ @Bottleneck_Mapper       │   │ @Equity_Scanner │  │
│  │ (00, 01)      │    │ @External_Validator      │   │ @Effects_Analyst│  │
│  └───────────────┘    │ (02, 03, 04)             │   │ (05, 06, 07)   │  │
│                       └─────────────────────────┘   └──────────────────┘  │
│                                    │                                        │
│          ┌─────────────────────────┴─────────────────────────┐             │
│          ▼                                                   ▼             │
│  ┌──────────────────┐                              ┌──────────────────┐   │
│  │ @Screen_Optimist │  ◄─── ISOLATION BOUNDARY ──► │@Screen_Pessimist│   │
│  │   (Bull Case)    │      (Neither sees other)     │  (Bear Case)    │   │
│  └──────────────────┘                              └──────────────────┘   │
│          │                                                   │             │
│          └─────────────────────────┬─────────────────────────┘             │
│                                    ▼                                        │
│                       ┌─────────────────────────┐                          │
│                       │    SYNTHESIS LAYER       │                          │
│                       │  @Screen_Synthesizer     │                          │
│                       │  (08, 09, 10, 11, 12)    │                          │
│                       │  + Certification/Handoff │                          │
│                       └─────────────────────────┘                          │
│                                    │                                        │
│                                    ▼                                        │
│                          HFRT HANDOFF (user-triggered)                      │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Agent Summary

| Agent | Model | Role | Owns Templates |
|-------|-------|------|----------------|
| @IST_Commander | Sonnet | Coordination only | .ist/PROGRESS.md |
| @Content_Analyst | Opus | Extract investable claims, bias assessment | 00, 01 |
| @Bottleneck_Mapper | Opus | Temporal cascade + demand models | 02, 03 |
| @External_Validator | Sonnet | Cross-reference claims vs independent data | 04 |
| @Equity_Scanner | Sonnet | Identify equities + tier classification | 05, 06 |
| @Effects_Analyst | Opus | Map 2nd/3rd order downstream effects | 07 |
| @Screen_Optimist | Opus | Thematic bull case + conviction building | .ist/OPTIMIST_REVIEW.md |
| @Screen_Pessimist | Opus | Thematic bear case + stress-testing | .ist/PESSIMIST_REVIEW.md |
| @Screen_Synthesizer | Opus | Reconcile dialectic + produce final output | 08-12, .ist/ files |

### Model Selection Rationale

- **Sonnet** (Commander, External_Validator, Equity_Scanner): Coordination, web research, and structured data gathering -- procedural tasks where Sonnet is sufficient and cost-effective
- **Opus** (Content_Analyst, Bottleneck_Mapper, Effects_Analyst, Optimist, Pessimist, Synthesizer): Content parsing, causal reasoning, multi-order effects, dialectic review, and synthesis -- all require deep analytical judgment

---

## Agent Definitions

### @IST_Commander

**Model:** Sonnet
**Role:** Coordination ONLY

```
You are @IST_Commander, the coordinator for the Investment Screening Team.

CRITICAL CONSTRAINTS:
1. You NEVER use Edit, Write, or NotebookEdit tools except for .ist/PROGRESS.md
2. You NEVER write screening content -- ALL content delegated to specialists
3. You launch AT MOST ONE specialist agent per response (except Phase 4)
4. You log checkpoints to .ist/PROGRESS.md after each agent completes
5. Max 5 tool calls per response

WORKFLOW:
- Phase 1: @Content_Analyst -> CONTENT SUFFICIENCY GATE
- Phase 2: @Bottleneck_Mapper -> @External_Validator (sequential)
- Phase 3: @Equity_Scanner -> @Effects_Analyst -> RESEARCH SUFFICIENCY GATE
- Phase 4: @Screen_Optimist + @Screen_Pessimist (parallel, isolated)
         -> @Screen_Synthesizer (synthesis)
- Phase 5: @Screen_Synthesizer (final) -> SCREEN COHERENCE GATE -> Handoff
```

### @Content_Analyst

**Model:** Opus
**Role:** Extract investable claims from unstructured content

```
You are @Content_Analyst, responsible for extracting investable claims.

YOU OWN: 00_SCREENING_BRIEF.md, 01_CONTENT_EXTRACTION.md

EXTRACTION CRITERIA:
- Quantitative anchors (specific numbers)
- Temporal markers (when constraints bind)
- Named bottlenecks (what specifically is constrained)
- Causal logic (why constrained -- physics, institutional, regulatory)

MANDATORY: Source bias assessment for every content input (INV-8)
```

### @Bottleneck_Mapper

**Model:** Opus
**Role:** Temporal cascade mapping and demand modeling

```
You are @Bottleneck_Mapper, responsible for temporal cascades and demand models.

YOU OWN: 02_BOTTLENECK_MAP.md, 03_DEMAND_MODELS.md

KEY PRINCIPLE: Bottlenecks are sequential, not simultaneous.
Energy binds first, then grid infrastructure, then chips.
This creates rotation strategy, not static portfolio.

Every bottleneck MUST have temporal phasing (INV-5).
Every number needs a source tag.
```

### @External_Validator

**Model:** Sonnet
**Role:** Cross-reference claims against independent data

```
You are @External_Validator, responsible for independent claim verification.

YOU OWN: 04_EXTERNAL_VALIDATION.md

For every major claim, find 2+ independent sources.
Single-source theses CANNOT achieve Tier 1 (Protocol #7).
Contradictory evidence incorporated, NOT ignored.
```

### @Equity_Scanner

**Model:** Sonnet
**Role:** Identify equity candidates and classify into tiers

```
You are @Equity_Scanner, responsible for equity identification and tiering.

YOU OWN: 05_EQUITY_CANDIDATES.md, 06_TIER_CLASSIFICATION.md

SCARCITY FILTER: "Does this company benefit from scarcity or abundance?"
MOAT REQUIREMENT: No equity without quantified moat (INV-2)
TIER CRITERIA:
  Tier 1: Strong moat + undervalued + multi-source + verified
  Tier 2: Strong moat + fully valued
  Tier 3: Speculative/binary
```

### @Effects_Analyst

**Model:** Opus
**Role:** Map 2nd/3rd order downstream effects

```
You are @Effects_Analyst, responsible for multi-order effects mapping.

YOU OWN: 07_EFFECTS_MAP.md

PRINCIPLE: Best ideas live at 2nd/3rd order where market hasn't reached.
"Who benefits from the thing that benefits from the thing that benefits?"
Multi-order effects required for every primary thesis (INV-7).
```

### @Screen_Optimist

**Model:** Opus
**Role:** Thematic bull case (operates in ISOLATION from Pessimist)

```
You are @Screen_Optimist, developing the thematic bull case.
CRITICAL: You operate in COMPLETE ISOLATION from @Screen_Pessimist.
Build conviction through analytical parallels and market misperceptions.
OUTPUT: .ist/OPTIMIST_REVIEW.md
```

### @Screen_Pessimist

**Model:** Opus
**Role:** Thematic bear case (operates in ISOLATION from Optimist)

```
You are @Screen_Pessimist, stress-testing the investment screen.
CRITICAL: You operate in COMPLETE ISOLATION from @Screen_Optimist.
Apply 8-point stress test to every Tier 1 name.
Assess source bias, timeline risk, demand deceleration.
OUTPUT: .ist/PESSIMIST_REVIEW.md
```

### @Screen_Synthesizer

**Model:** Opus
**Role:** Reconcile dialectic, produce all final deliverables

```
You are @Screen_Synthesizer, reconciling bull/bear and producing final output.

YOU OWN: 08-12, .ist/SYNTHESIS_REPORT.md, SCREEN_CERTIFICATION.md, HFRT_HANDOFF.md

You see BOTH Optimist and Pessimist reviews.
Reconcile disagreements with documented reasoning.
Default to conservative position when evidence is equal.
```

---

## 5-Phase Workflow

### Phase 1: Content Extraction & Briefing

**Goal:** Extract investable claims from user-provided content and establish screening parameters

| Step | Agent | Action | Output | Checkpoint |
|------|-------|--------|--------|------------|
| 1.1 | User + Commander | User provides content | Raw content | - |
| 1.2 | @Content_Analyst | Extract investable claims | 01_CONTENT_EXTRACTION.md | Yes |
| 1.3 | @Content_Analyst | Source bias assessment | Included in 01 | Yes |
| 1.4 | @Content_Analyst | Build screening brief | 00_SCREENING_BRIEF.md | Yes |
| 1.5 | **CONTENT SUFFICIENCY GATE** | Evaluate | Pass/Fail | GATE 1 |

**Entry Criteria:** User provides content (quotes, excerpts, timestamps, data)
**Exit Criteria:** 3+ claims with quant anchors, 1+ temporal marker, bias assessed, brief confirmed

### Phase 2: Thematic Analysis (SEQUENTIAL)

**Goal:** Map bottleneck cascade, build demand models, validate claims

| Step | Agent | Action | Output | Checkpoint |
|------|-------|--------|--------|------------|
| 2.1 | @Bottleneck_Mapper | Temporal cascade | 02_BOTTLENECK_MAP.md | Yes |
| 2.2 | @Bottleneck_Mapper | Demand models | 03_DEMAND_MODELS.md | Yes |
| 2.3 | @External_Validator | Cross-references | 04_EXTERNAL_VALIDATION.md | Yes |

### Phase 3: Equity Identification (SEQUENTIAL)

**Goal:** Identify equity candidates, classify tiers, map downstream effects

| Step | Agent | Action | Output | Checkpoint |
|------|-------|--------|--------|------------|
| 3.1 | @Equity_Scanner | Find candidates | 05_EQUITY_CANDIDATES.md | Yes |
| 3.2 | @Equity_Scanner | Tier classification | 06_TIER_CLASSIFICATION.md | Yes |
| 3.3 | @Effects_Analyst | Effects mapping | 07_EFFECTS_MAP.md | Yes |
| 3.4 | **RESEARCH SUFFICIENCY GATE** | Evaluate | Pass/Fail | GATE 2 |

### Phase 4: Dialectic Scrutiny (PARALLEL, ISOLATED)

**Goal:** Independent bull/bear analysis followed by synthesis

**EXCEPTION:** Optimist and Pessimist run in PARALLEL but ISOLATED contexts.

| Step | Agent | Action | Output | Checkpoint |
|------|-------|--------|--------|------------|
| 4.1a | @Screen_Optimist | Bull case | .ist/OPTIMIST_REVIEW.md | Yes |
| 4.1b | @Screen_Pessimist | Bear case | .ist/PESSIMIST_REVIEW.md | Yes |
| 4.2 | @Screen_Synthesizer | Reconciliation | .ist/SYNTHESIS_REPORT.md | Yes |

### Phase 5: Final Synthesis & Handoff (SEQUENTIAL)

**Goal:** Produce all final deliverables and prepare HFRT handoff

| Step | Agent | Action | Output | Checkpoint |
|------|-------|--------|--------|------------|
| 5.1 | @Screen_Synthesizer | Master screen | 08_MASTER_SCREEN.md | Yes |
| 5.2 | @Screen_Synthesizer | Rotation strategy | 09_ROTATION_STRATEGY.md | Yes |
| 5.3 | @Screen_Synthesizer | Catalyst calendar | 10_CATALYST_CALENDAR.md | Yes |
| 5.4 | @Screen_Synthesizer | Stress tests | 11_STRESS_TESTS.md | Yes |
| 5.5 | @Screen_Synthesizer | Investment thesis report | 12_INVESTMENT_THESIS.md | Yes |
| 5.6 | **SCREEN COHERENCE GATE** | Evaluate | Pass/Fail | GATE 3 |
| 5.7 | @Screen_Synthesizer | Certification + Handoff | .ist/SCREEN_CERTIFICATION.md, .ist/HFRT_HANDOFF.md | Yes |
| 5.8 | Commander | Notify user | "N Tier 1 names ready for HFRT. Investment thesis report generated." | COMPLETE |

---

## Quality Gates

### Gate 1: Content Sufficiency (Phase 1 -> Phase 2)

**Evaluator:** @IST_Commander

| Requirement | Check |
|-------------|-------|
| 3+ investable claims with quantitative anchors | Count claims with numbers |
| 1+ temporal marker identified | Time horizon for at least one bottleneck |
| Source bias assessed for every input | INV-8 compliance |
| Screening brief confirmed by user | User acknowledged constraints |
| 1+ named bottleneck identified | Specific constraint named |

### Gate 2: Research Sufficiency (Phase 3 -> Phase 4)

**Evaluator:** @IST_Commander

| Requirement | Check |
|-------------|-------|
| Every bottleneck has temporal phasing | INV-5 compliance |
| Demand models have sourced quantitative anchors | Numbers with tags |
| External validation attempted for all major claims | INV-6 compliance |
| 5+ equity candidates identified with moat evidence | Count in 05 |
| Tier classification completed | 06 populated |
| Multi-order effects mapped | INV-7 compliance |
| All 8 screening invariants hold | Full invariant check |

### Gate 3: Screen Coherence (Phase 5, before certification)

**Evaluator:** @IST_Commander

| Requirement | Check |
|-------------|-------|
| Optimist and Pessimist reviews both complete | Both .ist/ files exist |
| Synthesis addresses all disagreements | Documented in SYNTHESIS_REPORT |
| Tier adjustments documented | Post-dialectic changes logged |
| Master Screen passes all 8 invariants | Full invariant check |
| Rotation strategy aligns with temporal phasing | Phase-allocation consistency |
| Every Tier 1 name survived stress-testing | Survival scores in 11 |
| Every Tier 1 name has catalyst | INV-3 compliance |
| No [PLACEHOLDER] or [TODO] tags remain | String search |
| Investment thesis report (12) is complete and self-contained | Report exists, all sections populated |
| Report pillars align with bottleneck map phases | Pillar-bottleneck mapping consistency |
| All Tier 1 names have narrative analysis in the report | Every Tier 1 name gets prose paragraph |

---

## Anti-Hallucination Protocols

### Protocol 1: Citation-or-Flag

Every claim must have one of these tags:

| Tag | Usage | Example |
|-----|-------|---------|
| `[SOURCE]` | Original content citation | `[SOURCE: Musk, 02:46:10, "towards end of this year"]` |
| `[EXT-SOURCE]` | Independent external data | `[EXT-SOURCE: Wood Mackenzie 2025, 30% deficit]` |
| `[MARKET-DATA]` | Exchange/market data | `[MARKET-DATA: NYSE, 2026-02-06]` |
| `[ESTIMATE(method)]` | Calculated estimate | `[ESTIMATE(1GW formula: 1.4x cooling, 1.25x maint)]` |
| `[CONSENSUS]` | Analyst consensus | `[CONSENSUS: FactSet, accessed 2026-02-06]` |
| `[GAP]` | Data not available | `[GAP: Segment margins not disclosed]` |

### Protocol 2: Source Bias Assessment

Mandatory for every content source:

| Factor | Assessment Required |
|--------|-------------------|
| Identity | Who is this person/organization? |
| Incentive | What do they gain from this narrative? |
| Bias direction | Bullish/bearish on what specifically? |
| Severity | Low/Medium/High impact on analysis |
| Mitigation | How to corroborate independently |

### Protocol 3: External Validation

Every major claim cross-referenced against independent data via @External_Validator.

### Protocol 4: Quantitative Anchoring

No thesis without numbers. Vague claims like "energy is important" must resolve to quantified assertions like "1 GW cluster requires 1.75 GW actual capacity."

### Protocol 5: Temporal Marker Requirement

Every bottleneck must have an explicit time horizon. Static analysis ("transformers are constrained") is insufficient -- must specify when and for how long.

### Protocol 6: Moat Verification

Moat claims must be verified against filings/data. Unverified moat = cannot achieve Tier 1.

### Protocol 7: Multi-Source Triangulation

Single-source theses flagged. Cannot achieve Tier 1 without corroboration from additional independent sources.

### Protocol 8: Gap Over Fabricate

Missing data = `[GAP]` tag, never fabrication. Plausible-sounding numbers are NEVER acceptable substitutes for real data.

---

## Screening Invariants

These rules must hold true for ALL screening output. ALL violations are CRITICAL severity.

### INV-1: No Equity Without Direct Bottleneck Exposure

Every equity in the screen must have direct exposure to a named bottleneck from 02_BOTTLENECK_MAP.md.

**Violation:** Stock included because "it's a good company" without bottleneck connection.

### INV-2: No Thesis Without Quantified Moat

Every equity must have a quantified moat (not just "strong competitive position").

**Violation:** "Company has a good moat" without specific evidence and measurement.

### INV-3: No Position Without Identified Catalyst

Every equity must have at least one identifiable catalyst with expected timing.

**Violation:** "Stock is cheap" without a specific event that would unlock value.

### INV-4: No Tier 1 Without Valuation Data

Tier 1 names require forward P/E, price, distance from high, and market cap at minimum.

**Violation:** Tier 1 classification without valuation data to support "undervalued" claim.

### INV-5: Every Bottleneck Must Have Temporal Phasing

Every bottleneck must specify when it binds and how long the constraint persists.

**Violation:** "Transformers are a bottleneck" without time horizon.

### INV-6: Every Demand Claim Must Have External Validation Attempt

All demand claims must be cross-referenced against independent data. Validation may result in [GAP] but the attempt is mandatory.

**Violation:** Demand claim accepted from single source without seeking corroboration.

### INV-7: Multi-Order Effects Required for Every Primary Thesis

At least 2nd order effects must be mapped for every primary thesis.

**Violation:** Only first-order (obvious) beneficiaries identified.

### INV-8: Source Bias Documented for Every Content Input

Every content source must have a bias assessment (identity, incentive, direction, mitigation).

**Violation:** Content used without acknowledging speaker's incentives and potential bias.

---

## Dialectic Scrutiny Protocol

### Purpose

The dialectic ensures balanced analysis by having independent analysts develop bull and bear cases for the entire screen without coordination.

### Isolation Mechanism

```
@IST_Commander
       │
       ├──────────────────────────────────────────┐
       ▼                                          ▼
┌──────────────────┐                    ┌──────────────────┐
│ @Screen_Optimist │     ISOLATION      │@Screen_Pessimist │
│                  │◄────BOUNDARY────►  │                  │
│ Reads: 00-07     │    (No sharing)    │ Reads: 00-07     │
│ Writes: OPTIMIST │                    │ Writes: PESSIMIST│
│         _REVIEW  │                    │         _REVIEW  │
└──────────────────┘                    └──────────────────┘
       │                                          │
       └──────────────────┬───────────────────────┘
                          ▼
              ┌─────────────────────────┐
              │  @Screen_Synthesizer    │
              │  (Sees both reviews)    │
              │  Reconciles + certifies │
              └─────────────────────────┘
```

### Key Differences from HFRT Dialectic

| Aspect | HFRT | IST |
|--------|------|-----|
| Scope | Single company | Entire screen (multi-name) |
| Bull focus | Company upside | Thematic conviction, parallels |
| Bear focus | Company downside | Null hypothesis, source bias |
| Synthesis | Conviction score | Tier adjustments, rotation |

---

## File Coordination

### Folder Structure

```
[project]/
├── screening_template/          # Working screening documents
│   ├── 00_SCREENING_BRIEF.md
│   ├── 01_CONTENT_EXTRACTION.md
│   ├── 02_BOTTLENECK_MAP.md
│   ├── 03_DEMAND_MODELS.md
│   ├── 04_EXTERNAL_VALIDATION.md
│   ├── 05_EQUITY_CANDIDATES.md
│   ├── 06_TIER_CLASSIFICATION.md
│   ├── 07_EFFECTS_MAP.md
│   ├── 08_MASTER_SCREEN.md
│   ├── 09_ROTATION_STRATEGY.md
│   ├── 10_CATALYST_CALENDAR.md
│   ├── 11_STRESS_TESTS.md
│   └── 12_INVESTMENT_THESIS.md
├── .ist/                        # Coordination files
│   ├── PROGRESS.md
│   ├── OPTIMIST_REVIEW.md
│   ├── PESSIMIST_REVIEW.md
│   ├── SYNTHESIS_REPORT.md
│   ├── SCREEN_CERTIFICATION.md
│   └── HFRT_HANDOFF.md
└── frameworks/                  # Analysis frameworks (read-only)
    ├── scarcity_abundance.md
    ├── sequential_bottleneck.md
    ├── demand_modeling.md
    ├── scar_tissue_thesis.md
    ├── analytical_parallels.md
    ├── multi_order_effects.md
    └── null_hypothesis.md
```

### Checkpoint Format

.ist/PROGRESS.md:

```markdown
## Checkpoint Log

| Timestamp | Phase | Step | Agent | Status | Output File |
|-----------|-------|------|-------|--------|-------------|
| 2026-02-06T10:00:00 | 1 | 1.2 | @Content_Analyst | COMPLETE | 01_CONTENT_EXTRACTION.md |
| 2026-02-06T10:30:00 | 2 | 2.1 | @Bottleneck_Mapper | COMPLETE | 02_BOTTLENECK_MAP.md |
```

---

## Screening Templates

### Template Summary

| # | Template | Owner | Key Sections |
|---|----------|-------|--------------|
| 00 | SCREENING_BRIEF | @Content_Analyst | Sources, Constraints, Frameworks, Hypothesis |
| 01 | CONTENT_EXTRACTION | @Content_Analyst | Claims, Bias, Bottleneck Inventory |
| 02 | BOTTLENECK_MAP | @Bottleneck_Mapper | Temporal Cascade, Phases, Dependencies |
| 03 | DEMAND_MODELS | @Bottleneck_Mapper | Quantitative Models, Gap Analysis, Sensitivity |
| 04 | EXTERNAL_VALIDATION | @External_Validator | Validation Register, Contradictions, Triangulation |
| 05 | EQUITY_CANDIDATES | @Equity_Scanner | Candidates, Scarcity Score, Moat, Catalyst |
| 06 | TIER_CLASSIFICATION | @Equity_Scanner | Tier 1/2/3 Assignment, Criteria, Detail |
| 07 | EFFECTS_MAP | @Effects_Analyst | Multi-Order Effects, Causal Chains, New Candidates |
| 08 | MASTER_SCREEN | @Screen_Synthesizer | Final Ranked Table, Invariant Compliance |
| 09 | ROTATION_STRATEGY | @Screen_Synthesizer | Phase Allocation, Triggers, Risk Limits |
| 10 | CATALYST_CALENDAR | @Screen_Synthesizer | Dated Events, Impact Ratings, Timeline |
| 11 | STRESS_TESTS | @Screen_Synthesizer | Framework + Name Tests, Survival Scores |
| 12 | INVESTMENT_THESIS | @Screen_Synthesizer | Unified Narrative Report, Pillar Analysis, Portfolio Construction |

---

## Analysis Frameworks

### Core Frameworks

| Framework | File | Purpose | Default? |
|-----------|------|---------|----------|
| Scarcity/Abundance | `scarcity_abundance.md` | Screen for physical scarcity vs digital abundance | Yes (always) |
| Sequential Bottleneck | `sequential_bottleneck.md` | Map constraints as temporal cascade | When temporal pattern evident |
| Demand Modeling | `demand_modeling.md` | Build quantitative demand models | When quant claims present |
| Scar Tissue | `scar_tissue_thesis.md` | Identify institutional under-investment | When boom-bust evidence |
| Analytical Parallels | `analytical_parallels.md` | Pattern-match for conviction | During dialectic |
| Multi-Order Effects | `multi_order_effects.md` | Map downstream consequences | Yes (always) |
| Null Hypothesis | `null_hypothesis.md` | Stress-test every thesis | Yes (always) |

### Framework Extensibility

New frameworks can be added to the frameworks/ directory at any time. Frameworks are read-only reference material -- agents read but never modify them.

---

## Tier Classification System

### Tier Definitions

| Tier | Name | Criteria | Allocation |
|------|------|----------|-----------|
| 1 | High Conviction Unloved | Scarcity score >= 4, Forward P/E < 20x OR > 15% below highs, multi-source, moat verified | 5-8% per name |
| 2 | Fully Valued Watchlist | Strong moat BUT near ATH or > 25x P/E | 3-5% (on pullback) |
| 3 | Speculative | Binary outcomes, pre-revenue, long-duration assumptions | 1-3% max |

### Tier Gates

- **Tier 1 requires:** Verified moat (Protocol #6), multi-source triangulation (Protocol #7), valuation data (INV-4), survived stress-testing (Gate 3)
- **Tier 2:** Same moat requirements but valuation prevents Tier 1
- **Tier 3:** Lower evidence bar but position size capped

---

## IST-HFRT Handoff

### Handoff Process

1. IST completes -> @Screen_Synthesizer writes `.ist/HFRT_HANDOFF.md`
2. Commander notifies user: "N Tier 1 names ready for HFRT deep research"
3. **User decides** which names to research: `@HFRT_Commander, research [TICKER]`
4. IST agents NEVER invoke HFRT agents directly
5. Main thread mediates all IST -> HFRT transitions

### Handoff Format

```markdown
## Tier 1 Names for HFRT Deep Research

| Ticker | Company | Thesis | Phase | Conviction | Primary Catalyst | Target Date |
|--------|---------|--------|-------|------------|------------------|-------------|
```

### Key Principle

IST screens broadly (themes to equities); HFRT researches deeply (single company). The user is the bridge between them.

---

## Integration with CLAUDE.md

See `CLAUDE_MD_SECTION.md` for the complete IST rules to add to your global CLAUDE.md.

Summary of 16 IST Rules:

1. IST_Commander Never Writes Content + Concurrency Limits
2. 5-Phase Workflow (Sequential Execution)
3. Agent Role Boundaries
4. Domain Separation from SDE/SST/BPT/HFRT
5. Anti-Hallucination Enforcement
6. Gate Enforcement
7. Dialectic Protocol
8. Screening Invariants Enforcement
9. User Authority
10. File Coordination
11. Resource Governance
12. Recovery Protocol
13. IST-HFRT Handoff Protocol
14. Scarcity-First Screening Lens
15. Framework Extensibility
16. Failure Transparency & Tool Verification

---

## Usage Examples

### Starting a Screen

```
@IST_Commander, screen this podcast for investment ideas:

[Paste quotes, excerpts, timestamps, or key data points here]
```

or

```
@IST_Commander, screen these interview notes for investable themes:

"Quote 1 about energy constraints [02:15:30]"
"Quote 2 about transformer shortages [02:46:10]"
"Quote 3 about chip manufacturing [03:01:45]"
```

### Providing Additional Content

```
Here's additional data to incorporate into the screen:

[New quotes, articles, or data points]
```

### Checking Progress

```
Show me .ist/PROGRESS.md
```

### Resuming a Screen

```
@IST_Commander, resume screening from Phase 2
```

### Emergency Stop

```
HALT IST
```

### Triggering HFRT for a Tier 1 Name

```
@HFRT_Commander, research CLF
```

---

## Troubleshooting

### Issue: Gate failed

**Solution:** Review gate requirements. Return to responsible agent to complete missing elements. Do not proceed until gate passes.

### Issue: Missing source tags

**Solution:** Enforce Protocol 1 (Citation-or-Flag). Every claim needs [SOURCE], [EXT-SOURCE], [MARKET-DATA], [ESTIMATE(method)], or [GAP] tag.

### Issue: Screen seems one-sided

**Solution:** Review Optimist/Pessimist isolation. Ensure both ran independently. @Screen_Synthesizer must address all disagreements.

### Issue: Progress lost

**Solution:** Read .ist/PROGRESS.md to find last checkpoint. Resume from that point using recovery protocol.

### Issue: No equity candidates found

**Solution:** Check if screening constraints are too restrictive. Review 00_SCREENING_BRIEF.md constraints. Content may need more specific quantitative claims.

### Issue: All candidates are Tier 2 or 3

**Solution:** This is a valid outcome. Not all content generates Tier 1 ideas. The screen may indicate "no high-conviction unloved names" -- this is honest, not a failure.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-02-06 | Initial release |
| 1.1 | 2026-02-06 | Added template 12 (INVESTMENT_THESIS), reordered Phase 5, added Rule 16 (Failure Transparency) |

---

**Framework Owner:** IST Development Team
**Based On:** HFRT/BPT Architecture Patterns
**Upstream:** Unstructured content (podcasts, interviews, articles, earnings calls)
**Downstream:** HFRT deep research (user-triggered)
