# Demand Models

<!-- This file is created/managed by @Bottleneck_Mapper -->
<!-- Purpose: Build quantitative demand models with sourced anchors -->
<!-- Phase: Created during Phase 2 -->
<!-- Framework: demand_modeling.md -->

## Model Summary

| # | Model Name | Bottleneck | Demand-Supply Gap | Confidence | Phase |
|---|-----------|-----------|-------------------|------------|-------|
| 1 | [Name] | [Bottleneck] | [Quantified gap] | [High/Med/Low] | [1/2/3] |

## Model 1: [Name]

### Base Demand Calculation

| Component | Value | Source | Tag |
|-----------|-------|--------|-----|
| Raw demand input | [Value] | [Source] | [SOURCE/EXT-SOURCE] |
| Cooling multiplier | [X.Xx] | [Source] | [SOURCE/ESTIMATE(method)] |
| Maintenance/availability | [X.Xx] | [Source] | [SOURCE/ESTIMATE(method)] |
| Redundancy factor | [X.Xx] | [Source] | [ESTIMATE(method)] |
| **Total effective demand** | **[Value]** | **Calculated** | **[ESTIMATE(formula)]** |

### Supply Analysis

| Component | Value | Source | Tag |
|-----------|-------|--------|-----|
| Current installed capacity | [Value] | [Source] | [EXT-SOURCE/MARKET-DATA] |
| Committed additions | [Value] | [Source] | [EXT-SOURCE] |
| Realistic delivery timeline | [Value] | [Source] | [ESTIMATE(method)] |
| **Total available supply** | **[Value]** | **Calculated** | **[ESTIMATE(formula)]** |

### Gap Analysis

| Metric | Value |
|--------|-------|
| Demand - Supply | [Value] |
| Gap as % of demand | [X]% |
| Gap duration | [Months/Years] |
| Price impact evidence | [Evidence] |

### Sensitivity Analysis

| Scenario | Key Variable Change | Impact on Gap | Implication |
|----------|-------------------|---------------|-------------|
| Bull | [Variable +20%] | [New gap] | [Investment implication] |
| Base | [As calculated] | [Base gap] | [Investment implication] |
| Bear | [Variable -20%] | [New gap] | [Investment implication] |

## Model 2: [Name]
[Same structure as Model 1]

## Cross-Model Dependencies

| Model A | Model B | Dependency | Direction |
|---------|---------|-----------|-----------|
| [Model 1] | [Model 2] | [How they relate] | [A feeds B / B constrains A] |

## Anti-Hallucination Checklist

- [ ] Every number has a source tag
- [ ] No assumed values without [ESTIMATE(method)] tag
- [ ] Sensitivity analysis performed
- [ ] Cross-model dependencies documented
- [ ] All gaps marked [GAP]

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
