# Rotation Strategy

<!-- This file is created/managed by @Screen_Synthesizer -->
<!-- Purpose: Time-phased allocation model with rotation triggers -->
<!-- Phase: Created during Phase 5 -->
<!-- Framework: sequential_bottleneck.md -->

## Allocation Model

### Phase-Based Allocation

| Phase | Description | Time Horizon | Allocation % | Names |
|-------|-----------|-------------|-------------|-------|
| Phase 1 | [Binding constraint] | Now - [X]mo | [X-Y]% | [TICKERS] |
| Phase 2 | [Next constraint] | [X] - [Y]mo | [X-Y]% | [TICKERS] |
| Phase 3 | [Downstream] | [Y]+ mo | [X-Y]% | [TICKERS] |
| Cross-Cut | [Persistent] | All phases | [X-Y]% | [TICKERS] |
| Speculative | [Binary] | Varies | [X-Y]% | [TICKERS] |
| **Total** | | | **100%** | |

### Individual Position Sizing

| Ticker | Tier | Phase | Allocation | Rationale |
|--------|------|-------|-----------|-----------|
| [TICKER] | [1/2/3] | [1/2/3/CC] | [X]% | [Brief] |

## Rotation Triggers

### Phase 1 -> Phase 2 Rotation

| Trigger Event | Signal | Action | Timeline |
|--------------|--------|--------|----------|
| [Event] | [What to watch for] | [Reduce Phase 1 by X%, add to Phase 2] | [When expected] |

### Phase 2 -> Phase 3 Rotation

| Trigger Event | Signal | Action | Timeline |
|--------------|--------|--------|----------|
| [Event] | [What to watch for] | [Reduce Phase 2 by X%, add to Phase 3] | [When expected] |

## Rebalancing Rules

| Rule | Description |
|------|-----------|
| **Trigger** | Rebalance when any phase allocation drifts >5% from target |
| **Earnings** | Review position after each earnings report |
| **Catalyst** | Adjust after catalyst confirmation/disappointment |
| **Tier change** | Rebalance if tier classification changes |
| **New information** | Re-screen if material new content emerges |

## Risk Limits

| Limit | Value | Rationale |
|-------|-------|-----------|
| Max single position | [X]% | [Tier-based] |
| Max single phase | [X]% | [Diversification] |
| Max speculative | [X]% | [Risk management] |
| Stop-loss guidance | -[X]% from entry | [Position-level risk] |

---

## Data Sources and Citations

| # | Data Point | Source | Type |
|---|-----------|--------|------|
| 1 | [data] | [source] | ESTIMATE(method) / SOURCE |

---

**Created:** [Date]
**Last Updated:** [Date]
**Owner:** @Screen_Synthesizer
**Status:** Draft / Complete
**Phase:** 5
