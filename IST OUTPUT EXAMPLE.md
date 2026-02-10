# PHYSICAL AI INFRASTRUCTURE
## INVESTMENT THESIS
### Updated with Quantitative Engineering Analysis

**Mapping Elon Musk / Dwarkesh Patel Interview**
**Technical Calculations to Publicly-Tradeable Equities**

*February 6, 2026 | For Informational Purposes Only*

---

## I. Executive Summary

This report maps the specific engineering calculations and first-principles reasoning from Elon Musk's extended interview with Dwarkesh Patel to a concentrated portfolio of publicly-tradeable, Robinhood-accessible equities. The thesis is built on a single recursive insight: AI compute demand is growing exponentially while the physical infrastructure to support it — energy, cooling, memory, minerals, robotics, and space — is governed by linear, capital-intensive, and geographically constrained supply chains.

This updated version incorporates detailed quantitative data from the interview, including Musk's 1GW cluster sizing formula, the 1.4x cooling multiplier, the 1.25x maintenance availability penalty, the 5x/10x space solar arbitrage, and the $2.50/kg stainless steel economics of Starship. These numbers are not rhetorical — they are engineering specifications that imply specific, investable supply chain bottlenecks.

### Updated Consolidated Screen: 14 Equities Across 7 Pillars

The screen has expanded from 4 original names to 14, organized into three conviction tiers and seven investable pillars that emerge directly from Musk's engineering calculations.

Tier 1 = High conviction, unloved or structurally mispriced. Tier 2 = On thesis but fully valued; watchlist for pullback. Tier 3 = Speculative, small position size only (1-2% max).

| Ticker | Company | Price | 52-Wk Range | Fwd P/E | vs. High | Pillar | Tier |
|--------|---------|-------|-------------|---------|----------|--------|------|
| ATKR | Atkore Inc. | ~$71 | $50-$82 | ~12x | -13% | Grid Infrastructure | 1 |
| CGNX | Cognex Corp. | ~$36 | $23-$50 | ~35x | -28% | Robotics Vision | 1 |
| ST | Sensata Tech. | ~$26 | $21-$41 | ~10x | -37% | Robotics Sensors | 1 |
| GNRC | Generac | ~$161 | $120-$200 | ~20x | -20% | Energy/Power Gen | 1 |
| MU | Micron Tech. | ~$381 | $62-$456 | ~10x | -16% | Memory Wall / HBM | 1 |
| MP | MP Materials | ~$65 | $19-$100 | N/A | -35% | Critical Minerals | 1 |
| MOD | Modine Mfg. | ~$199 | $65-$199 | ~32x | ATH | DC Cooling [NEW] | 2 |
| NVT | nVent Electric | ~$120 | $42-$120 | ~32x | ATH | DC Cooling [NEW] | 2 |
| VRT | Vertiv Holdings | ~$179 | $53-$179 | ~59x | -5% | DC Cooling [NEW] | 2 |
| HWM | Howmet Aero. | ~$210 | $105-$227 | ~55x | -7% | Turbine Castings | 2 |
| GEV | GE Vernova | ~$397 | $164-$447 | ~72x | -11% | Gas Turbine OEM | 2 |
| NUE | Nucor Corp. | ~$191 | $98-$191 | ~25x | ATH | Steel / Starship [NEW] | 2 |
| RKLB | Rocket Lab | ~$62 | $15-$100 | N/A | -38% | Space Launch | 3 |
| UFO | Procure Space | ~$33 | $16-$40 | N/A | -18% | Space ETF | 3 |

---

## II. Pillar-by-Pillar Analysis

### Pillar 1: Energy Is THE Bottleneck (Not Silicon)

Musk's central claim is that by end of 2026, more AI accelerator chips will exist than available electricity to power them. Electricity generation outside China has been roughly flat, while AI chip production is scaling exponentially. This creates a binding physical constraint that no amount of software optimization can overcome.

**The 1 GW Unit: Sizing the Opportunity**

Musk provides a specific bottom-up calculation. To reliably power approximately 330,000 Nvidia GB300 (Blackwell) GPUs, you need 1 Gigawatt of committed generation capacity. The calculation is not simply summing chip TDP values. It requires accounting for:

- **Base Load:** Chip TDP + networking + storage + CPUs
- **Cooling Penalty (1.4x):** You must size cooling for peak annual conditions (e.g., a hot summer day in Memphis). This adds a 40% multiplier to the entire power requirement. This is not a rounding error; it means every 1 GW cluster requires 400 MW of dedicated thermal management infrastructure.
- **Maintenance Availability Penalty (1.25x):** Gas turbines require scheduled maintenance. To guarantee 100% uptime for the compute cluster, you must build 20-25% excess generation capacity to allow rotation of offline units.

> **THE CORE FORMULA:** Capacity(req) = Load(cluster) x 1.4 (Cooling) x 1.25 (Maintenance) = **1 GW per 330K GB300s**
>
> Every 1 GW of AI compute requires 400 MW of dedicated cooling infrastructure and 200-250 MW of redundant generation capacity for maintenance rotation. The cooling penalty alone creates a $400M-$800M addressable market per gigawatt cluster in thermal management equipment. With 15-20 GW of AI data center capacity projected by 2028, this implies a $6B-$16B incremental TAM for cooling companies alone.

At approximately 3 kW per GPU system (chip + cooling + overhead), this implies a realistic per-GPU infrastructure cost significantly higher than the chip cost itself.

> **SKEPTIC'S STRESS TEST: The 3 kW/GPU Figure**
>
> Current H100 racks run approximately 40 kW for 8 GPUs, or roughly 5 kW per GPU system. Musk's implied 3 kW/system for GB300s assumes meaningful efficiency gains from next-gen architectures. However, even at 5 kW/system, the 1.4x cooling and 1.25x maintenance multipliers still apply identically. The absolute wattage matters less than the multipliers, which are driven by thermodynamics and mechanical engineering, not chip design.

**Investable Names: Energy Pillar**

**ATKR (Atkore Inc.) | ~$71 | 52-wk: $50-$82 | Fwd P/E: ~12x | TIER 1**

Every new megawatt of generation capacity requires physical electrical conduit, cable, and raceway to connect it to the grid and distribute it within facilities. Atkore is the dominant domestic manufacturer. Q1 FY2026 earnings just beat estimates ($0.83 vs. $0.64 consensus), the company raised full-year guidance, and it trades at approximately 12x forward earnings — a deep value multiple for what is effectively a toll-road on electrification. The stock sits 13% below its 52-week high and 48% below its 3-year high.

**GNRC (Generac Holdings) | ~$161 | 52-wk: $120-$200 | Fwd P/E: ~20x | TIER 1**

The 1.25x maintenance penalty directly validates Generac's thesis. When grid interconnection queues stretch 3-5 years, data center operators need bridge power and backup generation. Generac's industrial and commercial segment provides exactly this. The company also benefits from residential backup power demand driven by extreme weather events. At 20x forward earnings and 20% below its 52-week high, it is reasonably valued for a company with dual demand drivers (AI infrastructure + climate resilience).

**HWM (Howmet Aerospace) | ~$210 | 52-wk: $105-$227 | Fwd P/E: ~55x | TIER 2**

Only approximately three global casting houses can produce the single-crystal superalloy turbine blades required for gas turbines. Lead times run 26-32 weeks with years-long backlogs. Howmet's Engine Products segment produces investment castings for both aircraft engines and industrial gas turbines. At 55x forward earnings, the stock prices in significant growth but may still underappreciate the duration of the constraint (see Pillar 7).

**GEV (GE Vernova) | ~$397 | 52-wk: $164-$447 | Fwd P/E: ~72x | TIER 2**

GE Vernova is the gas turbine OEM sitting at the center of the energy bottleneck. Its backlog is growing from $135B toward $200B by 2028. However, at roughly 72x forward earnings and with significant institutional ownership already, this is consensus-crowded and overvalued for new entry. The maintenance penalty thesis (1.25x) supports recurring services revenue, but the stock reflects this.

---

### Pillar 2: Data Center Cooling (NEW - The 1.4x Multiplier)

This is the single most important new investable vector surfaced by Musk's quantitative detail. The 1.4x cooling multiplier means that for every 1 GW of AI compute, 400 MW must be allocated purely to thermal management. This is not a software problem; it is a thermodynamics problem requiring physical infrastructure: precision air handlers, liquid cooling loops, chillers, heat exchangers, and cooling towers.

> **MARKET SIZING: The Cooling TAM**
>
> Current AI-specific racks push 120-150 kW per rack, up from 10-15 kW in 2023 (a 10x increase in 3 years). With 15-20 GW of AI data center capacity projected globally by 2028, the 1.4x cooling multiplier implies 6-8 GW of cooling infrastructure demand. At $1M-$2M per MW in cooling equipment (precision systems, liquid cooling, heat rejection), this represents a $6B-$16B incremental addressable market. This is a conservative estimate that excludes retrofit/upgrade cycles for existing facilities.

**Key Risk: The Nvidia Rubin Overhang**

In January 2026, Jensen Huang stated at CES that the Vera Rubin platform will not require traditional water chillers. This triggered a 10-17% selloff in cooling stocks (MOD, VRT, NVT). However, Barclays analysts noted that this applies to the chip-level cooling approach, not the facility-level thermal management, which remains governed by thermodynamics regardless of chip architecture.

> **SKEPTIC'S NOTE: Cooling Stocks at All-Time Highs**
>
> All three cooling names (MOD, NVT, VRT) are at or near all-time highs. This directly violates the 'unloved' criterion of the original thesis. They are included as Tier 2 (watchlist) because the 1.4x multiplier is a structural, physics-based tailwind, not a cyclical one. However, buying at ATH in a sector that just experienced a 10-17% volatility event (Nvidia Rubin comments) requires acknowledging that the next such event could produce a larger, more sustained drawdown. Position sizing discipline is essential.

**Investable Names: Cooling Pillar**

**MOD (Modine Manufacturing) | ~$199 | 52-wk: $65-$199 | Fwd P/E: ~32x | TIER 2**

Modine is the most compelling pure-play on data center cooling. The company just reported Q3 FY2026 results showing data center sales up 78% YoY, overall revenue up 31% sequentially, and raised its FY2026 net sales growth guidance to 20-25% (up from 15-20%). It is actively spinning off its Performance Technologies segment to become a pure-play climate solutions company. The spin-off (expected March 2026) is a potential re-rating catalyst.

**NVT (nVent Electric) | ~$120 | 52-wk: $42-$120 | Fwd P/E: ~32x | TIER 2**

nVent provides liquid cooling solutions, enclosures, and power distribution units for data centers. It recently launched modular data center cooling products and formed a collaboration with Siemens to co-develop cooling and power architectures for hyperscale AI workloads. Q3 FY2025 revenue was up 35% in the Data Solutions segment.

**VRT (Vertiv Holdings) | ~$179 | 52-wk: $53-$179 | Fwd P/E: ~59x | TIER 2**

Vertiv is the most widely followed name in the data center cooling space, with a $62B+ market cap, a $9.5B backlog, and a potential S&P 500 inclusion catalyst in Q1 2026. Q3 2025 net sales were up 29% YoY, with organic orders growing approximately 21% and a book-to-bill of 1.4x. However, at 59x earnings, the risk/reward is significantly worse than MOD or NVT. S&P 500 inclusion would create forced index buying — a one-time catalyst.

---

### Pillar 3: The Memory Wall (HBM > Logic)

Musk explicitly states that memory (DRAM/HBM) is a bigger long-term constraint than logic chips. This is counterintuitive to most investors focused on Nvidia, but it reflects a hardware engineering reality: AI training and inference workloads are increasingly memory-bandwidth-bound, not compute-bound.

**MU (Micron Technology) | ~$381 | 52-wk: $62-$456 | Fwd P/E: ~10x | TIER 1**

Micron's Q1 FY2026 results were extraordinary: revenue of $13.64B (up 57% YoY, 21% sequentially), EPS of $4.78 (21% above consensus), gross margin of 56.8%, and record quarterly free cash flow of $3.9B. Q2 FY2026 guidance projects revenue of $18.7B and EPS of $8.42. HBM 2026 capacity is 100% sold out.

At roughly 10x forward earnings despite near-doubling revenue, Micron presents either a historic mispricing or the market correctly anticipating a cyclical downturn. The HBM TAM is forecast to grow from $35B (2025) to $100B (2028), a 40% CAGR. Micron is acquiring a fabrication plant in Taiwan and expanding in Idaho and Hiroshima to meet demand.

> **STRESS TEST: The Cyclical Discount**
>
> Memory has historically been the most cyclical subsector in semiconductors, with brutal boom-bust cycles. The market is applying a 'cyclical discount' to Micron's forward P/E, pricing in a mean reversion that has occurred in every prior cycle. The bull case is that HBM represents a structural shift (not cyclical) because AI demand creates a permanently higher floor for memory bandwidth. The null hypothesis is that Samsung and SK Hynix are aggressively expanding HBM capacity, and the current supply constraint resolves by late 2027, triggering the usual price compression. The $62-$456 52-week range (a 7.4x spread) tells you the market has no consensus on which scenario is correct.

---

### Pillar 4: Critical Minerals / Domestic Refining

China controls approximately 98% of global gallium refining and 2x global rare earth refining capacity. The U.S. mines these materials but ships the ore to China for processing, creating a strategic dependency that is increasingly untenable in a world of AI-driven military applications, EV motors, and advanced electronics.

**MP (MP Materials) | ~$65 | 52-wk: $19-$100 | Fwd P/E: N/A (unprofitable) | TIER 1**

MP Materials is the only scaled rare earth mining and processing operation in the Western Hemisphere. It is currently unprofitable (EPS -$0.10 in Q3), but the investment case is binary: if it successfully commissions magnet production in H2 2026, it transitions from a mining company to a vertically integrated magnetics manufacturer with dramatically higher margins.

Key de-risking events: DoD $400M equity investment (Pentagon now 15% owner) with a 10-year supply agreement including a $110/kg price floor; Saudi Arabia JV refinery; Apple prepayment for magnets; Trump's Project Vault ($12B critical minerals stockpile). NdPr production grew 51% YoY. Analyst consensus targets range from $25-$56, all below the current price, suggesting the market is pricing in magnet commissioning success that analysts have not yet modeled.

This fits the 'unloved' screen perfectly: volatile, unprofitable, 35% below highs, sovereign-backed, and physically scarce. The key risk is execution on the magnet commissioning timeline and policy risk (a price floor rollback caused a 7% single-day drop).

---

### Pillar 5: Robotics / Optimus Supply Chain

Musk disclosed that Tesla designed all actuators, motors, sensors, gearboxes, and end effectors for Optimus from scratch because the required supply chain simply did not exist. The human hand is described as the hardest engineering challenge, and Optimus uses the AI5 inference chip (same as Tesla vehicles). As this technology matures and competitors emerge, a broader supplier ecosystem will develop.

**CGNX (Cognex Corporation) | ~$36 | 52-wk: $23-$50 | Fwd P/E: ~35x | TIER 1**

Every robot in Optimus Academy requires machine vision for quality control, part identification, and spatial navigation. Cognex is the global leader in industrial machine vision. At $36, it sits 28% below its 52-week high and 64% below its 3-year high of $102. The factory automation cycle has been depressed, making this a contrarian entry point before the robotics supply chain ramp. Q4 2025 revenue was up 17% YoY. Multiple expansion from a robotics narrative could drive 50-100% upside.

**ST (Sensata Technologies) | ~$26 | 52-wk: $21-$41 | Fwd P/E: ~10x | TIER 1**

Sensata manufactures mission-critical sensors: force, torque, position, thermal, and pressure. As the robotics supply chain matures beyond Tesla's vertical integration, every third-party robot manufacturer will need these sensors. At roughly 10x forward earnings and 37% below its 52-week high, Sensata is deeply out of favor in the market. The sensor content per robot is structurally higher than sensor content per vehicle.

---

### Pillar 6: Space-Based AI Compute (Speculative)

Musk's space solar arbitrage is built on specific physics:

- **Solar irradiance in space:** constant 1,360 W/m² (no atmosphere, no night in appropriate orbits)
- **Solar panels in space are roughly 5x more effective** per square meter than on Earth
- **Earth solar capacity factor:** approximately 25% (atmosphere absorbs/scatters 30%, night cycle eliminates 50%, weather/angle further reduces)
- **The Battery Deleverage:** On Earth, 1 TW of solar requires massive battery storage for nighttime. In space, batteries are eliminated entirely
- **Net result:** Musk estimates space power is 10x cheaper when factoring in battery elimination + 5x yield

> **SKEPTIC'S STRESS TEST: Space Solar Assumptions**
>
> Musk's 'no batteries' claim requires specific orbits (Dawn-Dusk Sun-Synchronous or high orbits). In Low Earth Orbit, satellites experience approximately 45 minutes of darkness per 90-minute orbit, requiring batteries unless a constellation passes power via laser/microwave interconnects. The 36-month timeline requires 10,000 Starship launches per year (27/day versus approximately 1/week currently, a 1,000x increase). Even by Musk timeline standards, this is aggressive. Additionally, space-based compute at scale would create stranded asset risk for terrestrial power generation plants with 10-15 year payback periods. This is a 5-10 year thesis at minimum, not 36 months.

**Starship Steel Economics**

Musk details the calculation to switch from carbon fiber ($130/kg) to stainless steel ($2.50/kg), a 50x cost reduction per kilogram. At cryogenic temperatures (liquid oxygen, liquid methane), stainless steel undergoes strain hardening that brings its strength-to-weight ratio approximately equal to carbon fiber, meaning the 50x cost advantage comes with near-zero weight penalty. This is the structural innovation that makes 10,000 flights/year economics feasible.

**Investable Names: Space & Steel Pillars**

**RKLB (Rocket Lab) | ~$62 | 52-wk: $15-$100 | Fwd P/E: N/A | TIER 3**

$816M Space Force contract, revenue growing 34%, but cash-flow negative and 38% below its 52-week high. Extreme volatility with rotation risk ahead of a potential SpaceX IPO. Speculative sleeve only (1-2% max portfolio allocation).

**NUE (Nucor Corporation) [NEW] | ~$191 | 52-wk: $98-$191 | Fwd P/E: ~25x | TIER 2**

This is a second/third-order derivative of Starship economics. If Starship scales to 10,000 flights per year, the demand for 300-series stainless steel at $2.50/kg becomes enormous. Nucor is the largest U.S. steel producer with an 18.1% domestic market share and the lowest-cost Electric Arc Furnace (EAF) operations. Data centers also require massive structural steel for facilities. At all-time highs, this is a watchlist name, but the structural demand from both data center construction and potential Starship scaling creates an unusual confluence.

---

### Pillar 7: Turbine Blade Casting Bottleneck

The 1.25x maintenance availability penalty reinforces the turbine supply chain thesis. Every GW of gas turbine capacity requires scheduled maintenance rotations, which means demand for replacement blades, vanes, and hot-section components is not a one-time event but a recurring revenue stream. With only approximately three casting houses globally capable of producing single-crystal superalloy blades, and lead times of 26-32 weeks, this is a multi-year structural constraint.

Howmet Aerospace (HWM) remains the primary publicly-tradeable exposure to this constraint (see Pillar 1 for details). Precision Castparts, the other major player, is owned by Berkshire Hathaway and not directly investable.

---

## III. Second and Third-Order Effects

> **THE RECURSIVE ENERGY LOOP: The Master Thesis**
>
> Robots need energy. AI needs energy. Building energy infrastructure needs robots and AI. Mining critical minerals needs energy and robots. Every pillar converges on the same bottleneck: the physical capacity to generate and distribute electricity. This self-reinforcing loop means the energy/grid infrastructure names (GNRC, ATKR, GEV, HWM) form the highest-conviction core of the portfolio, with memory (MU), minerals (MP), robotics sensors (CGNX, ST), and cooling (MOD, NVT, VRT) providing diversified exposure to adjacent constraints.

### If Energy Remains the Binding Constraint

- **2nd Order:** Natural gas demand spikes as the bridge fuel for turbine generation. Williams Companies (WMB) and Kinder Morgan (KMI) as pipeline/midstream beneficiaries.
- **3rd Order:** Energy-efficient chip architectures (ARM Holdings) gain structural advantage over power-hungry designs. GPU architectures that optimize performance-per-watt command premium pricing.

### If the 1.4x Cooling Multiplier Compounds

- **2nd Order:** Water consumption for data center cooling becomes a political and regulatory constraint. Companies with air-cooled and dry-cooling solutions (Modine's evaporative free cooling) gain competitive advantage in water-stressed regions.
- **3rd Order:** Data center location decisions shift from 'proximity to users' to 'proximity to cold climates and abundant water,' favoring Nordic countries, Canada, and northern U.S. states. Real estate and construction companies in these geographies benefit.

### If Space-Based AI Materializes (5-10 Year Horizon)

- **2nd Order:** Terrestrial power generation becomes stranded asset risk for plants with 10-15 year payback periods. This is bearish for long-cycle utility-scale solar and nuclear investments if space solar genuinely achieves 10x cost advantage.
- **3rd Order:** Domestic steel producers (NUE, STLD) see unexpected demand surge if Starship scales. The lunar mass driver concept (1 PW vs. 1 TW from Earth launches) implies that space-based manufacturing of raw materials could eventually bypass terrestrial supply chains entirely.

### If Optimus Economics Reach Scale

- **2nd Order:** Labor cost curves collapse. Companies that DEPLOY robots (Amazon, Walmart) gain disproportionately over companies that SELL them, because the deployment flywheel generates training data that improves the robots.
- **3rd Order:** If robots build robots, manufacturing capacity becomes self-referentially unbounded. The binding constraint shifts entirely to raw materials and energy, which reinforces the energy bottleneck thesis recursively. This is the 'recursive energy loop' that ties all seven pillars together.

---

## IV. The Petawatt Scale: Civilizational Framing

Musk uses a Kardashev-style metric to define the long-term goal. Earth currently captures approximately 0.5 billionths (0.5 x 10⁻⁹) of the Sun's energy. The target is to harness 1 millionth (10⁻⁶), representing roughly 100,000x the current energy output of human civilization.

The launch constraints are instructive for investment horizons:

- **Earth launch limit:** approximately 1 Terawatt (TW) of AI hardware per year
- **Lunar mass driver limit:** approximately 1 Petawatt (PW) of AI hardware per year

A lunar mass driver (electromagnetic catapult) works because the Moon has no atmosphere and 1/6th Earth's gravity, allowing launch without chemical rockets. This is a 20-50 year investment horizon and is included for intellectual completeness, not actionable portfolio construction.

---

## V. Portfolio Construction Guidance

### Tier 1: Core Positions (60-70% of allocation)

ATKR, CGNX, ST, GNRC, MU, MP. These names are either unloved, structurally mispriced, or both. They represent the highest risk-adjusted expected returns because the market is either ignoring the structural demand driver or applying an inappropriate cyclical discount.

### Tier 2: Watchlist / Pullback Entry (20-30%)

MOD, NVT, VRT, HWM, GEV, NUE. These names are on thesis but fully valued. The cooling names (MOD, NVT, VRT) in particular are at all-time highs following the most obvious AI infrastructure trade. Entry requires either a catalyst-driven pullback (Nvidia chip announcements, earnings misses) or patience.

### Tier 3: Speculative (0-5%)

RKLB, UFO. These are venture-style bets on space infrastructure with binary outcomes and extreme volatility. Position size accordingly.

### Key Upcoming Catalysts

| Date | Ticker | Event |
|------|--------|-------|
| Feb 11 | VRT | Vertiv Q4 2025 earnings; key test for AI cooling demand and backlog trajectory |
| Feb 12 | HWM | Howmet Aerospace earnings; turbine casting backlog visibility |
| Feb 19 | MP | MP Materials earnings; magnet commissioning timeline update |
| Mar 2026 | MOD | Modine Performance Technologies spin-off catalyst |
| Q1 2026 | VRT | Potential S&P 500 inclusion (massive index fund buying) |
| Apr 1 | MU | Micron Q2 FY2026 earnings; HBM demand/pricing validation |
| H2 2026 | MP | Magnet production commissioning (binary revenue inflection) |

---

## VI. Disclaimer

This document is for informational and educational purposes only. It does not constitute investment advice, a recommendation to buy or sell any security, or a solicitation of any kind. All analysis is based on publicly available information and the author's interpretation of interview content. The equities mentioned in this report are high-risk investments and may result in significant loss of capital.

All stock prices are approximate as of February 6, 2026 and may have changed significantly by the time this document is read. Forward P/E ratios, analyst estimates, and price targets are subject to revision. Past performance is not indicative of future results. Investing in equities involves risk of loss.

Several names on this screen are unprofitable (MP, RKLB), highly volatile (all), or at all-time highs (MOD, NVT, NUE). Position sizing, diversification, and risk management are the responsibility of the individual investor. The author may hold positions in securities mentioned in this document.

Sources include: SEC filings, Robinhood, Morningstar, Seeking Alpha, StockAnalysis.com, Yahoo Finance, CNBC, TradingView, company earnings releases, and web search results as of February 6, 2026. All figures labeled 'Extrapolated/No Source' should be treated as estimates.
