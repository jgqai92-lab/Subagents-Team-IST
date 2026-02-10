# IST Workflow Output Enhancement Plan

## Problem Statement

The IST workflow currently ends with 7 separate structured documents (templates 08-11 + `.ist/` files). There is no step that synthesizes all accumulated analysis into a single, unified investment thesis report. The desired final output is a polished narrative document — not a collection of filled-in template forms.

## Reference

See `IST OUTPUT EXAMPLE.md` in this folder for the exact output format the workflow must produce.

## Gap Analysis

### What the workflow currently produces (Phase 5):

| Step | Output | Format |
|------|--------|--------|
| 5.1 | `08_MASTER_SCREEN.md` | Ranked equity table + per-name attribute cards |
| 5.2 | `09_ROTATION_STRATEGY.md` | Phase-based allocation tables |
| 5.3 | `10_CATALYST_CALENDAR.md` | Chronological catalyst table |
| 5.4 | `11_STRESS_TESTS.md` | Framework + name-level stress test tables |
| 5.5 | Screen Coherence Gate | Pass/fail validation |
| 5.6 | `.ist/SCREEN_CERTIFICATION.md` + `.ist/HFRT_HANDOFF.md` | Certification badge + handoff table |
| 5.7 | Commander notification | "N Tier 1 names ready for HFRT" |

### What the example output is:

A **unified narrative investment thesis report** with these sections:

1. **Executive Summary** — Unified thesis statement, consolidated screen table (all tickers with price/P-E/tier/pillar)
2. **Pillar-by-Pillar Analysis** — Bottlenecks reframed as "investable pillars," each containing:
   - Thesis narrative in prose (not attribute/value tables)
   - Quantitative formulas/calculations woven into the narrative
   - Inline "Skeptic's Stress Test" callout boxes (`> **SKEPTIC'S STRESS TEST:**`)
   - Market sizing / TAM estimates inline
   - Investable names WITH full narrative per name (not just table rows)
3. **Second & Third-Order Effects** — Organized by "If X remains the binding constraint" with cascading implications across multiple scenarios
4. **Civilizational Framing** (optional) — Big-picture context when the source content warrants it
5. **Portfolio Construction Guidance** — Tier-based allocation percentages, key upcoming catalysts table
6. **Disclaimer** — Standard investment disclaimer

### Key structural differences:

| Aspect | Current Templates (08-11) | Example Output |
|--------|--------------------------|----------------|
| Organization | Flat tables, one per concern | Narrative organized by "pillar" (bottleneck theme) |
| Equity detail | Attribute/value table cards | Prose paragraphs with data woven in |
| Stress tests | Separate Phase 5 table (template 11) | Inline callout boxes within each pillar |
| Effects | Separate template (07) | Integrated narrative section with "If X" scenarios |
| Rotation/Allocation | Separate template (09) | Integrated into Portfolio Construction section |
| Catalysts | Separate template (10) | Simple table in Portfolio Construction section |
| Tone | Structured/analytical | Analytical but narrative/readable |
| Audience | Internal working document | External-facing research report |

---

## Enhancement Plan

### Change 1: Create new template `screening_template/12_INVESTMENT_THESIS.md`

This is the final deliverable template. Its structure must match the example output:

```markdown
# [SCREEN TITLE]
## INVESTMENT THESIS
### [Subtitle reflecting analytical approach]

**Mapping [Source Content Title]**
**[Analytical Method] to Publicly-Tradeable Equities**

*[Date] | For Informational Purposes Only*

---

## I. Executive Summary

[2-3 paragraph narrative: core insight, why it matters, what the screen found]

### Consolidated Screen: [N] Equities Across [N] Pillars

[Prose explaining tier methodology]

| Ticker | Company | Price | 52-Wk Range | Fwd P/E | vs. High | Pillar | Tier |
|--------|---------|-------|-------------|---------|----------|--------|------|
| [All equities from master screen, ordered by tier then pillar] |

---

## II. Pillar-by-Pillar Analysis

### Pillar [N]: [Pillar Name / Bottleneck Theme]

[Narrative thesis: what is constrained and why. Weave in quantitative evidence from
02_BOTTLENECK_MAP and 03_DEMAND_MODELS. Use actual numbers, formulas, multipliers.]

> **[KEY FORMULA / INSIGHT NAME]**
>
> [Quantitative formula or insight from demand models, formatted as blockquote.
> Include TAM/market sizing calculation if applicable.]

> **SKEPTIC'S STRESS TEST: [Specific Claim Being Tested]**
>
> [Inline stress test from 11_STRESS_TESTS. What's the null hypothesis?
> What would break this? What's the base rate? Keep it concise.]

**Investable Names: [Pillar] Pillar**

**[TICKER] ([Company Name]) | ~$[Price] | 52-wk: $[Low]-$[High] | Fwd P/E: ~[X]x | TIER [N]**

[Narrative paragraph: Why this company? What's the moat? What's the catalyst?
What's the valuation case? 3-5 sentences of analytical prose, not bullet points.]

[Repeat for each equity in this pillar]

---

[Repeat Pillar sections for each major bottleneck theme]

---

## III. Second and Third-Order Effects

> **[MASTER THESIS NAME]: The [Unifying Pattern]**
>
> [Narrative connecting all pillars into a recursive or self-reinforcing loop,
> if one exists. From 07_EFFECTS_MAP.]

### If [Thesis/Bottleneck 1] Remains the Binding Constraint

- **2nd Order:** [Effect + equity exposure if applicable]
- **3rd Order:** [Effect + equity exposure if applicable]

### If [Thesis/Bottleneck 2] Compounds

- **2nd Order:** [Effect]
- **3rd Order:** [Effect]

[Repeat for major theses from effects map]

---

## IV. [Optional: Civilizational / Big-Picture Framing]

[Only if the source content warrants it. Long-term context, Kardashev-scale thinking,
structural shifts. Include timeline/horizon framing. Mark speculative content clearly.]

---

## V. Portfolio Construction Guidance

### Tier 1: Core Positions ([X-Y]% of allocation)

[Prose: which names, why they're highest conviction, what makes them "unloved"]

### Tier 2: Watchlist / Pullback Entry ([X-Y]%)

[Prose: on thesis but fully valued, what would make them actionable]

### Tier 3: Speculative ([X-Y]%)

[Prose: binary outcomes, position size discipline]

### Key Upcoming Catalysts

| Date | Ticker | Event |
|------|--------|-------|
| [From 10_CATALYST_CALENDAR, simplified to most important catalysts] |

---

## VI. Disclaimer

This document is for informational and educational purposes only. It does not constitute
investment advice, a recommendation to buy or sell any security, or a solicitation of any
kind. All analysis is based on publicly available information and the author's interpretation
of interview content. The equities mentioned in this report are high-risk investments and
may result in significant loss of capital.

All stock prices are approximate as of [Date] and may have changed significantly by the time
this document is read. Forward P/E ratios, analyst estimates, and price targets are subject
to revision. Past performance is not indicative of future results. Investing in equities
involves risk of loss.

[Specific risk callouts for any unprofitable, highly volatile, or ATH names on the screen.]

Sources include: [List all source types used]. All figures labeled 'Extrapolated/No Source'
should be treated as estimates.
```

**Key design principles for this template:**
- **Pillars = Bottlenecks reframed** — Group equities by their bottleneck theme, not alphabetically or by tier
- **Inline stress tests** — Pull relevant stress tests from template 11 into blockquote callouts within each pillar, rather than a separate section
- **Prose over tables** — Equity analysis is narrative paragraphs, not attribute/value cards. The consolidated screen table in the Executive Summary provides the structured data view
- **Effects as scenarios** — Reframe effects map (template 07) as "If X remains..." conditional scenarios
- **Simplified catalysts** — The Portfolio Construction section gets a simplified catalyst table (most important only). The full detail lives in template 10

---

### Change 2: Update @Screen_Synthesizer agent definition

**File:** `~/.claude/agents/Screen_Synthesizer.md`

Add a new **Step 8** after Step 7 (HFRT Handoff):

```markdown
**Step 8: Investment Thesis Report (12)**
1. Read ALL screening_template/ files (00-11), .ist/SYNTHESIS_REPORT.md, and .ist/OPTIMIST_REVIEW.md + .ist/PESSIMIST_REVIEW.md
2. Identify the major "pillars" (thematic groupings of bottlenecks) — each bottleneck or cluster of related bottlenecks becomes a pillar
3. Write `screening_template/12_INVESTMENT_THESIS.md` as a unified narrative report:
   - Executive Summary: core insight in 2-3 paragraphs + consolidated screen table
   - Pillar-by-Pillar Analysis: group equities under their bottleneck theme, write analytical prose per equity (not attribute tables), embed key quantitative formulas as blockquotes, embed inline Skeptic's Stress Test callouts
   - Second & Third-Order Effects: reframe effects map (07) as "If X remains the binding constraint" scenarios
   - Optional Civilizational Framing: only if source content warrants big-picture context
   - Portfolio Construction Guidance: tier-based allocation prose + simplified catalyst table
   - Disclaimer: standard investment disclaimer with date and source list
4. The report must be SELF-CONTAINED — a reader should understand the entire thesis without needing to read templates 00-11
5. Every quantitative claim in the report must trace back to a sourced claim in templates 00-04. No new analysis — this step is SYNTHESIS only
6. Tone: analytical but readable. Written for an informed investor, not for internal process tracking
```

Also add `screening_template/12_INVESTMENT_THESIS.md` to the **YOU OWN** list.

---

### Change 3: Update IST_WORKFLOW.md

**File:** `~/.claude/IST_WORKFLOW.md`

In **Rule 2**, Phase 5, insert a new step between current 5.6 and 5.7:

**Current:**
```
5.6: @Screen_Synthesizer COMPLETES -> .ist/SCREEN_CERTIFICATION.md + .ist/HFRT_HANDOFF.md -> CHECKPOINT
5.7: Commander notifies user: "N Tier 1 names ready for HFRT" -> COMPLETE
```

**Updated:**
```
5.6: @Screen_Synthesizer COMPLETES -> .ist/SCREEN_CERTIFICATION.md + .ist/HFRT_HANDOFF.md -> CHECKPOINT
5.7: @Screen_Synthesizer COMPLETES -> 12_INVESTMENT_THESIS.md (unified narrative report) -> CHECKPOINT
5.8: Commander notifies user: "N Tier 1 names ready for HFRT. Investment thesis report generated." -> COMPLETE
```

In **Rule 3** (Agent Role Boundaries), update the @Screen_Synthesizer line:
```
- **@Screen_Synthesizer**: Reconciles dialectic, produces all final deliverables. Owns 08-12, .ist/SYNTHESIS_REPORT.md, .ist/SCREEN_CERTIFICATION.md, .ist/HFRT_HANDOFF.md.
```

(Changed `08-11` to `08-12`)

---

### Change 4: Update Rule 6 Gate 3 (Screen Coherence)

Add to the Gate 3 checklist:
```
- Investment thesis report (12) is complete and self-contained
- Report pillars align with bottleneck map phases
- All Tier 1 names have narrative analysis in the report
```

---

### Change 5: Quality requirements for the report

The Investment Thesis Report (template 12) must satisfy these quality criteria:

1. **Self-contained**: A reader should understand the full thesis without reading any other template
2. **Synthesis only**: No new analysis — all content traces back to templates 00-11 and dialectic reviews
3. **Every equity gets narrative**: Each name on the screen must have a prose paragraph (not just a table row)
4. **Inline stress tests**: At least one Skeptic's Stress Test callout per pillar, pulled from template 11
5. **Quantitative anchors preserved**: Key formulas and numbers from the source content must appear in the report
6. **Anti-hallucination compliance**: All data points in the report must have appeared in prior templates. The report introduces NO new numbers, estimates, or claims
7. **Pillar coherence**: Equities grouped by thematic pillar (bottleneck theme), not alphabetically
8. **Effects integration**: Second/third-order effects from template 07 appear as "If X" scenario sections

---

## Files to Modify (Summary)

| File | Change |
|------|--------|
| `screening_template/12_INVESTMENT_THESIS.md` | **CREATE** — New template with structure above |
| `~/.claude/agents/Screen_Synthesizer.md` | **EDIT** — Add Step 8, add template 12 to ownership list |
| `~/.claude/IST_WORKFLOW.md` | **EDIT** — Add step 5.7 (renumber 5.7->5.8), update Rule 3 ownership, update Gate 3 checklist |

---

## Verification

After implementation, verify:

1. [ ] `screening_template/12_INVESTMENT_THESIS.md` exists with the full template structure
2. [ ] `Screen_Synthesizer.md` agent definition includes Step 8 and owns template 12
3. [ ] `IST_WORKFLOW.md` Rule 2 Phase 5 includes step 5.7 for template 12
4. [ ] `IST_WORKFLOW.md` Rule 3 shows @Screen_Synthesizer owns 08-12
5. [ ] `IST_WORKFLOW.md` Rule 6 Gate 3 includes report completeness checks
6. [ ] Template count is now 13 (00-12), not 12 (00-11)
7. [ ] Run a test: invoke @IST_Commander on a sample screen and confirm template 12 is produced as the final deliverable

---

*Plan created: 2026-02-06*
*Target: IST Workflow v1.1*
*Scope: Add unified Investment Thesis Report as final IST deliverable*
