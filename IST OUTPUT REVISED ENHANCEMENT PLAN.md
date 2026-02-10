# IST Workflow Output Enhancement Plan -- REVISED

> **Original Plan:** `IST Workflow Output Enhancement.md`
> **Revision Date:** 2026-02-06
> **Reviewer:** Claude Code (Opus 4.6)
> **Purpose:** Document gaps in the original enhancement plan and provide the corrected implementation spec

---

## Summary of Enhancement

The IST workflow currently ends with 7 separate structured documents (templates 08-11 + `.ist/` files). This enhancement adds a unified narrative Investment Thesis Report (`screening_template/12_INVESTMENT_THESIS.md`) as the final deliverable -- a polished, self-contained document suitable for an informed investor audience, synthesized from all prior screening work.

---

## Original Plan Review

### What the Original Plan Got Right

1. **Gap analysis is accurate** -- the structural differences table correctly identifies that current output is internal process artifacts, not an investor-readable report
2. **Screen_Synthesizer is the correct owner** -- it already reads all 00-11 files plus both dialectic reviews, so it has all context needed
3. **"Synthesis only, no new analysis"** principle correctly preserves anti-hallucination compliance
4. **Quality requirements** (8 criteria) are well-defined and enforceable
5. **Template structure** mirrors the example output faithfully
6. **Scaffolding and version check scripts require no code changes** -- `new_project.py` copies all files from the source `screening_template/` directory dynamically, and `version_check.py` hashes from the manifest, so both handle the new template automatically

### Issues Found in the Original Plan

#### Issue 1: Gate 3 Sequencing Error (CRITICAL)

The original plan adds three Gate 3 criteria:
- "Investment thesis report (12) is complete and self-contained"
- "Report pillars align with bottleneck map phases"
- "All Tier 1 names have narrative analysis in the report"

But the plan places template 12 generation at **step 5.7** -- which is AFTER Gate 3 at **step 5.5** and AFTER certification at **step 5.6**. Gate 3 cannot verify a file that doesn't exist yet.

**Original (broken) sequence:**
```
5.1-5.4: Templates 08-11
5.5: SCREEN COHERENCE GATE  <-- checks template 12 here...
5.6: Certification + Handoff
5.7: Template 12 generated   <-- ...but it's generated here
5.8: Commander notification
```

**Fixed sequence:**
```
5.1-5.4: Templates 08-11
5.5: Template 12 generated   <-- moved BEFORE gate
5.6: SCREEN COHERENCE GATE   <-- can now verify template 12
5.7: Certification + Handoff
5.8: Commander notification
```

This ensures the thesis report is verified by Gate 3 before certification, which is the logically correct order -- you certify the *complete* output.

#### Issue 2: IST_Commander.md Not Listed as a File to Modify (HIGH)

The IST Commander agent at `~/.claude/agents/IST_Commander.md` hardcodes:

1. The Phase 5 workflow diagram:
   ```
   Phase 5: Final Synthesis -> @Screen_Synthesizer (08, 09, 10, 11)
                             -> SCREEN COHERENCE GATE
                             -> @Screen_Synthesizer (SCREEN_CERTIFICATION, HFRT_HANDOFF)
   ```

2. The Gate 3 checklist (8 items, none referencing template 12)

Without updating the Commander, it will skip the thesis report step entirely -- the Commander drives the workflow and won't know to request template 12.

#### Issue 3: INVESTMENT_SCREENING_TEAM_GUIDE.md Not Listed (HIGH)

This is the authoritative reference document (800 lines). Multiple sections needed updating:

| Section | Line(s) | What Changed |
|---------|---------|-------------|
| Architecture diagram | ~103 | `(08, 09, 10, 11)` -> `(08, 09, 10, 11, 12)` |
| Agent Summary table | ~125 | `08-11` -> `08-12` |
| Phase 5 workflow table | ~341-349 | New step 5.5 for template 12, renumber 5.5-5.7 -> 5.6-5.8 |
| Screening Templates table | ~601-614 | Add row for template 12 |
| Folder structure | ~550-579 | Add `12_INVESTMENT_THESIS.md` to file listing |
| @Screen_Synthesizer description | ~276-283 | `08-11` -> `08-12` |

#### Issue 4: CLAUDE.md Template Count (LOW)

The global `~/.claude/CLAUDE.md` Workflow Mappings table shows:
```
| IST | ... | 12 `screening_template/` | ...
```
Should be `13 `screening_template/``. Cosmetic but creates confusion.

#### Issue 5: Auto Memory Template Count (LOW)

`MEMORY.md` states "12 templates (00-11)" for IST. Should become "13 templates (00-12)".

---

## Corrected File Modification List

| # | File | Change Type | In Original Plan? |
|---|------|------------|-------------------|
| 1 | `screening_template/12_INVESTMENT_THESIS.md` | CREATE | Yes |
| 2 | `~/.claude/agents/Screen_Synthesizer.md` | EDIT | Yes |
| 3 | `~/.claude/IST_WORKFLOW.md` | EDIT (with reorder fix) | Yes (sequencing fixed) |
| 4 | `~/.claude/agents/IST_Commander.md` | EDIT | **MISSING from original** |
| 5 | `INVESTMENT_SCREENING_TEAM_GUIDE.md` | EDIT (5+ sections) | **MISSING from original** |
| 6 | `~/.claude/CLAUDE.md` | EDIT (template count) | **MISSING from original** |
| 7 | `MEMORY.md` (auto memory) | EDIT (template count) | **MISSING from original** |

---

## Corrected Change Specifications

### Change 1: Create `screening_template/12_INVESTMENT_THESIS.md`

*(Unchanged from original plan -- the template structure is correct)*

### Change 2: Update @Screen_Synthesizer Agent Definition

*(Unchanged from original plan -- add Step 8, add template 12 to ownership)*

### Change 3: Update IST_WORKFLOW.md (CORRECTED SEQUENCING)

**Rule 2, Phase 5 -- Corrected order:**

```
5.1: @Screen_Synthesizer COMPLETES -> 08_MASTER_SCREEN.md -> CHECKPOINT
5.2: @Screen_Synthesizer COMPLETES -> 09_ROTATION_STRATEGY.md -> CHECKPOINT
5.3: @Screen_Synthesizer COMPLETES -> 10_CATALYST_CALENDAR.md -> CHECKPOINT
5.4: @Screen_Synthesizer COMPLETES -> 11_STRESS_TESTS.md -> CHECKPOINT
5.5: @Screen_Synthesizer COMPLETES -> 12_INVESTMENT_THESIS.md (unified narrative) -> CHECKPOINT
5.6: SCREEN COHERENCE GATE evaluation
5.7: @Screen_Synthesizer COMPLETES -> .ist/SCREEN_CERTIFICATION.md + .ist/HFRT_HANDOFF.md -> CHECKPOINT
5.8: Commander notifies user: "N Tier 1 names ready for HFRT. Investment thesis report generated." -> COMPLETE
```

**Rule 3:** `Owns 08-12` (was `08-11`)

**Rule 6, Gate 3:** Add three new criteria (thesis report completeness)

### Change 4: Update @IST_Commander Agent Definition (NEW -- missed by original)

Update Phase 5 workflow diagram to include template 12:
```
Phase 5: Final Synthesis -> @Screen_Synthesizer (08, 09, 10, 11, 12)
                          -> SCREEN COHERENCE GATE
                          -> @Screen_Synthesizer (SCREEN_CERTIFICATION, HFRT_HANDOFF)
```

Update Gate 3 checklist to add thesis report criteria.

Update final notification message.

### Change 5: Update INVESTMENT_SCREENING_TEAM_GUIDE.md (NEW -- missed by original)

Six sections need updating:
1. Architecture diagram: `(08, 09, 10, 11)` -> `(08, 09, 10, 11, 12)`
2. Agent Summary: `08-11` -> `08-12`
3. Phase 5 table: Add step 5.5, renumber subsequent steps
4. Gate 3 table: Add thesis report criteria
5. Template Summary table: Add row 12
6. Folder structure: Add file listing

### Change 6: Update CLAUDE.md (NEW -- missed by original)

Template count: `12` -> `13`

### Change 7: Update MEMORY.md (NEW -- missed by original)

Template count: `12 templates (00-11)` -> `13 templates (00-12)`

---

## Unchanged from Original Plan

- **Quality requirements for the report** (8 criteria) -- fully correct as written
- **Template structure/content** -- matches the example output
- **Anti-hallucination compliance** preserved
- **No script changes needed** -- `new_project.py`, `handoff.py`, `version_check.py` all handle the new template dynamically
- **No invariant changes needed** -- the 8 invariants apply to the thesis report via the "synthesis only" constraint

---

## Verification Checklist (Expanded)

1. [ ] `screening_template/12_INVESTMENT_THESIS.md` exists with full template structure
2. [ ] `Screen_Synthesizer.md` includes Step 8 and owns template 12
3. [ ] `IST_WORKFLOW.md` Rule 2 Phase 5 places template 12 at step 5.5 (BEFORE Gate 3)
4. [ ] `IST_WORKFLOW.md` Rule 3 shows @Screen_Synthesizer owns 08-12
5. [ ] `IST_WORKFLOW.md` Rule 6 Gate 3 includes report completeness checks
6. [ ] `IST_Commander.md` Phase 5 flow includes template 12
7. [ ] `IST_Commander.md` Gate 3 checklist includes thesis report criteria
8. [ ] `INVESTMENT_SCREENING_TEAM_GUIDE.md` architecture diagram updated
9. [ ] `INVESTMENT_SCREENING_TEAM_GUIDE.md` agent summary updated
10. [ ] `INVESTMENT_SCREENING_TEAM_GUIDE.md` Phase 5 table updated with correct step ordering
11. [ ] `INVESTMENT_SCREENING_TEAM_GUIDE.md` template summary table has 13 rows (00-12)
12. [ ] `INVESTMENT_SCREENING_TEAM_GUIDE.md` folder structure includes template 12
13. [ ] `CLAUDE.md` shows 13 templates for IST
14. [ ] Template count is 13 (00-12), not 12 (00-11), in all references
15. [ ] Run a test: invoke @IST_Commander on a sample screen and confirm template 12 is produced as the final deliverable before Gate 3

---

*Revised: 2026-02-06*
*Target: IST Workflow v1.1*
*Scope: Add unified Investment Thesis Report as final IST deliverable (with sequencing fix and 4 additional file dependencies)*
