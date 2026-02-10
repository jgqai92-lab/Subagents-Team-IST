# Bottleneck Map

<!-- This file is created/managed by @Bottleneck_Mapper -->
<!-- Purpose: Map bottlenecks into a temporal cascade with sequential dependencies -->
<!-- Phase: Created during Phase 2 -->
<!-- Framework: sequential_bottleneck.md -->

## Temporal Cascade Overview

```
[Phase 1: Description] (Now - Xmo)
    ↓ resolves partially, releasing...
[Phase 2: Description] (X - Ymo)
    ↓ resolves partially, releasing...
[Phase 3: Description] (Y+ mo)

Cross-cutting: [Description] (all phases)
```

## Phase 1: [Binding Constraint Name] (Now - [X] months)

### Constraint Description
[What is constrained and why]

### Quantitative Evidence

| Metric | Value | Source | Confidence |
|--------|-------|--------|------------|
| [Demand metric] | [Value] | [SOURCE/EXT-SOURCE] | [High/Med/Low] |
| [Supply metric] | [Value] | [SOURCE/EXT-SOURCE] | [High/Med/Low] |
| [Gap metric] | [Value] | [ESTIMATE(method)] | [High/Med/Low] |

### Sub-Constraints

| # | Sub-Constraint | Binding? | Lead Time | Source |
|---|---------------|----------|-----------|--------|
| 1 | [Sub-constraint] | [Yes/Partial/No] | [Duration] | [Source] |

### Temporal Markers

| Marker | Date/Range | Source | Confidence |
|--------|-----------|--------|------------|
| [Event] | [When] | [SOURCE] | [High/Med/Low] |

### Resolution Triggers
[What events signal this phase is resolving?]

## Phase 2: [Next Constraint Name] ([X] - [Y] months)
[Same structure as Phase 1]

## Phase 3: [Downstream Constraint Name] ([Y]+ months)
[Same structure as Phase 1]

## Cross-Cutting Constraints
[Constraints that persist across all phases]

| Constraint | Affects Phases | Quantitative Impact | Source |
|-----------|---------------|---------------------|--------|
| [Name] | [1,2,3] | [Multiplier/value] | [Source] |

## Sequential Dependency Validation

| Dependency | Evidence | Causal or Coincidental? | Confidence |
|-----------|----------|------------------------|------------|
| Phase 1 -> Phase 2 | [Evidence] | [Causal/Coincidental] | [High/Med/Low] |
| Phase 2 -> Phase 3 | [Evidence] | [Causal/Coincidental] | [High/Med/Low] |

## Invariant Compliance

- [ ] INV-5: Every bottleneck has temporal phasing
- [ ] INV-8: Source bias documented for every content input

---

## Data Sources and Citations

| # | Data Point | Source | Type |
|---|-----------|--------|------|
| 1 | [data] | [source] | SOURCE / EXT-SOURCE / MARKET-DATA / ESTIMATE(method) |

## Data Gaps

| ID | Description | Impact | Resolution Path |
|----|-------------|--------|-----------------|
| GAP-001 | [description] | [Low/Medium/High] | [How to resolve] |

---

**Created:** [Date]
**Last Updated:** [Date]
**Owner:** @Bottleneck_Mapper
**Status:** Draft / Complete
**Phase:** 2
