# Equity Candidates

<!-- This file is created/managed by @Equity_Scanner -->
<!-- Purpose: Identify equity candidates per bottleneck with moat evidence -->
<!-- Phase: Created during Phase 3 -->
<!-- Framework: scarcity_abundance.md -->

## Candidate Summary

| # | Ticker | Company | Bottleneck Exposure | Scarcity Score | Moat Type | Phase |
|---|--------|---------|---------------------|---------------|-----------|-------|
| 1 | [TICKER] | [Name] | [Bottleneck] | [1-5] | [Type] | [1/2/3/CC] |

## Screening Criteria Applied

| Criterion | Threshold | Required? |
|-----------|-----------|-----------|
| Brokerage availability | [Per 00_SCREENING_BRIEF.md] | Yes |
| Not mega-cap consensus | [Per constraints] | Yes |
| Direct bottleneck exposure | >10% revenue from relevant business | Yes (INV-1) |
| Demonstrable moat | Quantified evidence required | Yes (INV-2) |
| Identifiable catalyst | Named event with date | Yes (INV-3) |
| Scarcity filter pass | Score >= 3 on scarcity framework | Yes |

## Candidate Detail

### [TICKER]: [Company Name]

#### Company Overview

| Field | Value | Source |
|-------|-------|--------|
| **Ticker** | [TICKER] | |
| **Current Price** | $[X] | [MARKET-DATA: Date] |
| **Market Cap** | $[X]B | [MARKET-DATA] |
| **Forward P/E** | [X]x (or N/A if unprofitable) | [MARKET-DATA/CONSENSUS] |
| **52-Week Range** | $[Low] - $[High] | [MARKET-DATA] |
| **Distance from High** | -[X]% | [MARKET-DATA] |

#### Bottleneck Exposure

| Attribute | Value |
|-----------|-------|
| **Primary Bottleneck** | [Name from 02] |
| **Exposure Type** | [Direct producer / Supplier / Enabler] |
| **Revenue Relevance** | [X]% of revenue from relevant segment |
| **Phase Alignment** | Phase [1/2/3/Cross-cut] |

#### Scarcity Assessment

| Factor | Score (1-5) | Evidence | Source |
|--------|------------|---------|--------|
| Physical constraint | [Score] | [Evidence] | [Tag] |
| Time-to-replicate | [Score] | [Evidence] | [Tag] |
| Pricing power | [Score] | [Evidence] | [Tag] |
| AI demand sensitivity | [Score] | [Evidence] | [Tag] |
| Supply response lag | [Score] | [Evidence] | [Tag] |
| **Average** | **[Score]** | | |

#### Moat Evidence

| Moat Type | Present? | Evidence | Verified? | Source |
|-----------|----------|---------|-----------|--------|
| Sole/dominant producer | [Y/N] | [Evidence] | [Y/N] | [Tag] |
| Top 1-3 constrained industry | [Y/N] | [Evidence] | [Y/N] | [Tag] |
| Multi-year lead time | [Y/N] | [Evidence] | [Y/N] | [Tag] |
| Regulatory/certification | [Y/N] | [Evidence] | [Y/N] | [Tag] |
| National security/strategic | [Y/N] | [Evidence] | [Y/N] | [Tag] |

**Moat Summary:** [Quantified moat statement per INV-2]

#### Catalyst

| Catalyst | Date | Type | Impact | Source |
|----------|------|------|--------|--------|
| [Event] | [Date] | [Earnings/Commission/Policy/Index] | [HIGH/MED/LOW] | [Tag] |

#### Bull Case (Brief)
[2-3 sentences]

#### Bear Case (Brief)
[2-3 sentences]

---

### [TICKER 2]: [Company Name]
[Same structure repeated for each candidate]

## Candidates Rejected

| Ticker | Company | Reason for Rejection | Could Revisit? |
|--------|---------|---------------------|----------------|
| [TICKER] | [Name] | [Failed criterion X] | [Yes if.../No] |

## Invariant Compliance

- [ ] INV-1: Every equity has direct bottleneck exposure
- [ ] INV-2: Every thesis has quantified moat
- [ ] INV-3: Every position has identified catalyst

---

## Data Sources and Citations

| # | Data Point | Source | Type |
|---|-----------|--------|------|
| 1 | [data] | [source] | MARKET-DATA / EXT-SOURCE / SOURCE |

## Data Gaps

| ID | Description | Impact | Resolution Path |
|----|-------------|--------|-----------------|
| GAP-001 | [description] | [Low/Medium/High] | [How to resolve] |

---

**Created:** [Date]
**Last Updated:** [Date]
**Owner:** @Equity_Scanner
**Status:** Draft / Complete
**Phase:** 3
