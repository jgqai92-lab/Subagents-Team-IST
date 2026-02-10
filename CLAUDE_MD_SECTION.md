# IST Rules for CLAUDE.md

Copy the section below into your global CLAUDE.md file at `~/.claude/CLAUDE.md`.

---

```markdown
<!-- ============================================================ -->
<!-- TOPIC AREA: INVESTMENT SCREENING                              -->
<!-- Investment Screening Team (IST) Workflow                      -->
<!-- ============================================================ -->

## Investment Screening Team (IST) Workflow Enforcement

> IST Version: 1.0 | Last Updated: 2026-02-06

When the user references @IST_Commander, asks to screen investment ideas from content, or triggers any IST-related workflow, the following rules are MANDATORY:

### IST Rule 1: IST_Commander Never Writes Content + Concurrency Limits
When invoking the IST_Commander agent, ALWAYS include this instruction in the prompt:
> "You are a coordinator ONLY. You must NEVER use Edit, Write, or NotebookEdit tools to modify or create ANY files except `.ist/PROGRESS.md` for checkpoint logging.
>
> **CONCURRENCY LIMIT:** You may launch AT MOST ONE specialist agent per response (EXCEPTION: Phase 4 Screen_Optimist + Screen_Pessimist may run in parallel but isolated). After launching an agent, you MUST STOP and wait for its output before launching the next.
>
> **TOOL CALL LIMIT:** You may queue AT MOST 5 tool calls per response.
>
> ALL content extraction must be delegated to @Content_Analyst. ALL thematic analysis to @Bottleneck_Mapper and @External_Validator. ALL equity identification to @Equity_Scanner and @Effects_Analyst. ALL dialectic review to @Screen_Optimist and @Screen_Pessimist. ALL synthesis to @Screen_Synthesizer. If you write screening content directly or launch multiple agents simultaneously (except Phase 4), you are violating the IST workflow."

### IST Rule 2: 5-Phase Workflow (SEQUENTIAL EXECUTION)
Every screening project must follow this progression with **STRICT SEQUENTIAL EXECUTION**:

1. **Phase 1 (Content Extraction):** @Content_Analyst -> 00, 01 -> **CONTENT SUFFICIENCY GATE**
2. **Phase 2 (Thematic Analysis - SEQUENTIAL):** @Bottleneck_Mapper -> 02, 03 -> @External_Validator -> 04
3. **Phase 3 (Equity Identification - SEQUENTIAL):** @Equity_Scanner -> 05, 06 -> @Effects_Analyst -> 07 -> **RESEARCH SUFFICIENCY GATE**
4. **Phase 4 (Dialectic Scrutiny):** @Screen_Optimist + @Screen_Pessimist (parallel, ISOLATED) -> @Screen_Synthesizer (synthesis)
5. **Phase 5 (Final Synthesis):** @Screen_Synthesizer -> 08, 09, 10, 11, 12 -> **SCREEN COHERENCE GATE** -> Certification + HFRT Handoff

### IST Rule 3: Agent Role Boundaries
- **@IST_Commander**: Coordination ONLY. Never writes content.
- **@Content_Analyst**: Extracts investable claims, source bias. Owns 00, 01.
- **@Bottleneck_Mapper**: Temporal cascade, demand models. Owns 02, 03.
- **@External_Validator**: Cross-references claims. Owns 04.
- **@Equity_Scanner**: Identifies equities, tier classification. Owns 05, 06.
- **@Effects_Analyst**: Maps 2nd/3rd order effects. Owns 07.
- **@Screen_Optimist**: Bull case. ISOLATED from Pessimist. Writes OPTIMIST_REVIEW.md.
- **@Screen_Pessimist**: Bear case. ISOLATED from Optimist. Writes PESSIMIST_REVIEW.md.
- **@Screen_Synthesizer**: Reconciles, produces final deliverables. Owns 08-12 + .ist/ files.

### IST Rule 4: Domain Separation from SDE/SST/BPT/HFRT
IST is completely separate from other frameworks:
- IST agents NEVER invoke SDE, SST, BPT, or HFRT agents
- Different triggers: IST triggers on "screen content," "screen ideas from," or "@IST_Commander"
- Different file paths: IST uses screening_template/ and .ist/
- IST-HFRT Bridge: IST produces .ist/HFRT_HANDOFF.md; user manually triggers HFRT

### IST Rule 5: Anti-Hallucination Enforcement
All IST agents must follow the 8 anti-hallucination protocols:
1. **Citation-or-Flag**: [SOURCE], [EXT-SOURCE], [MARKET-DATA], [ESTIMATE(method)], [CONSENSUS], or [GAP]
2. **Source Bias Assessment**: Identity, incentive, bias direction, mitigation for every source
3. **External Validation**: Major claims cross-referenced against independent data
4. **Quantitative Anchoring**: No thesis without numbers
5. **Temporal Marker Requirement**: Every bottleneck needs time horizon
6. **Moat Verification**: Unverified moat = cannot be Tier 1
7. **Multi-Source Triangulation**: Single-source cannot be Tier 1
8. **Gap Over Fabricate**: Missing data = [GAP], never fabrication

### IST Rule 6: Gate Enforcement
Three mandatory gates:
- **Content Sufficiency Gate** (Phase 1->2): 3+ claims with quant anchors, temporal markers, bias assessed
- **Research Sufficiency Gate** (Phase 3->4): Bottlenecks phased, demand quantified, 5+ candidates, effects mapped
- **Screen Coherence Gate** (Phase 5): Both reviews complete, invariants pass, Tier 1 stress-tested

### IST Rule 7: Dialectic Protocol
@Screen_Optimist and @Screen_Pessimist in complete isolation:
- Both launched parallel but separate contexts
- Neither sees the other's review
- Only @Screen_Synthesizer sees both

### IST Rule 8: Screening Invariants (8, ALL CRITICAL)
1. No equity without direct bottleneck exposure
2. No thesis without quantified moat
3. No position without identified catalyst
4. No Tier 1 without valuation data
5. Every bottleneck must have temporal phasing
6. Every demand claim must have external validation attempt
7. Multi-order effects required for every primary thesis
8. Source bias documented for every content input

### IST Rule 9: User Authority
All IST decisions are recommendations -- user has final authority.
Users decide which Tier 1 names to send to HFRT.
Users cannot override anti-hallucination violations.

### IST Rule 10: File Coordination
```
[project]/
  screening_template/  -- 13 working screening documents (00-12)
  .ist/               -- PROGRESS.md, reviews, synthesis, certification, handoff
  frameworks/         -- Analysis frameworks (read-only reference)
```

### IST Rule 11: Resource Governance
- Max 1 concurrent agent (except Phase 4 Optimist+Pessimist)
- Max 5 tool calls per Commander response
- Checkpoints logged to .ist/PROGRESS.md
- Emergency Halt: "HALT IST" at any time

### IST Rule 12: Recovery Protocol
- "HALT IST" or "STOP" for emergency halt
- Resume: `@IST_Commander, resume screening from Phase [X]`
- NORMAL MODE (default, autonomous) vs STRICT SEQUENTIAL MODE (recovery only)

### IST Rule 13: IST-HFRT Handoff Protocol
- IST produces .ist/HFRT_HANDOFF.md with Tier 1 names
- Commander notifies user
- User triggers HFRT: `@HFRT_Commander, research [TICKER]`
- IST agents NEVER invoke HFRT agents

### IST Rule 14: Scarcity-First Screening Lens
Default framework: "Does this company benefit from scarcity or abundance?"
Heuristic: "If Claude can do it in 5 minutes, it's not a moat."

### IST Rule 15: Framework Extensibility
7 initial frameworks in frameworks/. New frameworks can be added at any time.
Frameworks are read-only reference. @Content_Analyst selects applicable ones in Phase 1.

### IST Rule 16: Failure Transparency & Tool Verification
Commander performs Step 0 tool verification before Phase 1. If Write fails, return explicit error and stop.
No silent degradation. If tools are blocked, report and halt -- never produce fallback output.

## Reference
IST documentation: See `INVESTMENT_SCREENING_TEAM_GUIDE.md` in the Investment Screening Team folder.

<!-- ============================================================ -->
<!-- END OF TOPIC: INVESTMENT SCREENING                            -->
<!-- ============================================================ -->
```

---

## Installation Instructions

1. Open your global CLAUDE.md:
   ```
   C:\Users\[username]\.claude\CLAUDE.md
   ```

2. Add the section above after the existing framework sections (SDE, SST, BPT, HFRT)

3. Update the routing table at the top of CLAUDE.md to include:
   ```
   | `@IST_Commander` or screen investment ideas from content | Read `.claude/IST_WORKFLOW.md` |
   ```

4. Update Cross-Domain Rules to include IST in domain separation

5. Save the file

6. Verify by starting a new Claude Code session and running:
   ```
   @IST_Commander, screen this content for investment ideas: [test content]
   ```

---

## Verification Checklist

After adding to CLAUDE.md, verify:

- [ ] IST Rules 1-16 are present
- [ ] Domain separation from SDE/SST/BPT/HFRT is clear
- [ ] Anti-hallucination protocols are listed
- [ ] Gate requirements are specified
- [ ] Recovery protocol is documented
- [ ] IST-HFRT handoff is specified
- [ ] Routing table updated
- [ ] Cross-domain rules updated
