# Stage 4 — Instructor Review

**Student:** Nguyen Thao
**Company:** Lenovo Group Limited (HKSE: 992)
**Spec:** `docs/specs/2026-05-23-nguyen-lenovo-spec.md`
**Reviewed:** 2026-05-24

---

## Observations

### Part A — Model Specification

- **Scope & Objective (Section 1):** Well-defined — correctly identifies HKFRS (substantially IFRS), USD thousands, 992.HK, FY2025/FY2024 (March fiscal year), analytical objective (six ratio categories + Du Pont + strategic recommendations), and audience (BUS-629 instructor, senior analyst level). Benchmarks named: Dell, HP.
- **Model Architecture (Section 2):** Six-tab workbook documented with color coding (Yellow = inputs, Blue = assumptions, Green = formulas, Gray = outputs), input/calculation/output separation rule, and the critical constraint: "no hardcoded values anywhere on the Ratios tab."
- **Data Inputs (Section 3):** Comprehensive — IS (8 items), BS Assets (14 items with both years), BS Liabilities & Equity (14 items with both years), CF (3 items), Market assumptions (4 items). Two well-documented modeling notes:
  - **Note 1 (D&A plug):** HKFRS doesn't disclose D&A as a separate income statement line. The USD 708,376K figure was derived algebraically so EBIT and Operating CF both tie to source. Derivation referenced in `analysis/stage3-modelling-notes.md`. This is exactly the transparency a senior reviewer needs.
  - **Note 2 (NCI treatment):** Template has no NCI row; NCI (USD 590,930K) combined with Reserves in `BAL_retained_earnings_*`. ROE computed on total equity basis (USD 6,659,917K, not USD 6,068,987K). Clearly documented with the analytical implication stated.
- **Named Range Conventions (Section 4):** Prefix table with `_current`/`_prior` suffix conventions. Critical rule: "Never enter values into `RATIO_*`, `avg_*`, `startYear_*`, `currentYear_*` — all data entry restricted to yellow and blue cells only."
- **Derived Inputs (Section 5):** 14 intermediate calculations with formulas and values — EBIT, taxable income, net income, total assets, total liabilities, equity, averages (assets, equity, inventories, receivables), market cap.

### Part A — Ratios & Validation

- **Ratio Definitions (Section 6):** ~20 ratios across all six categories — Performance (3: MVA, M/B, EVA with CAPM-derived WACC), Profitability (3: ROA avg, ROC, ROE avg), Efficiency (5: asset turnover, receivables turnover, DSO, inventory turnover, DIO), Leverage (3: total debt ratio, TIE, debt burden), Liquidity (3: current, quick, cash), Du Pont (3-factor: net profit margin, asset turnover, equity multiplier, ROE check). Each ratio includes an interpretation column — a useful enhancement.
- **Missing ratios (~9):** ROA/ROC/ROE start-year variants (3), Operating Profit Margin (1), LT debt ratio (1), LT D/E (1), Cash coverage (1), Leverage ratio (1), NWC/Assets (1). These are in the template's full 29-ratio suite.
- **Du Pont:** Uses 3-factor decomposition (margin × turnover × equity multiplier). The template's 4-factor adds a debt burden component that separates interest/tax effects from operating margin — relevant at Lenovo's 6.51x leverage.
- **Validation Rules (Section 7):** 8 rules — BS balance both years (with exact values), EBIT ties to source, net income ties, Du Pont ROE vs direct (≤0.5pp tolerance), no formula errors, all startYear populated, MVA positive. Strong coverage.

### Part B — Analysis Specification

- **Analysis Requirements (Section 7/Part B):** Detailed per-category guidance with Lenovo-specific insights that demonstrate deep company knowledge:
  - Performance: M/B benchmark against Dell (~3.5x) and HP (~5.0x)
  - Profitability: "Identify primary driver of ROE improvement" — quantify SSG margin vs hardware mix
  - Efficiency: "Assess whether 1.78x asset turnover is sustainable as ISG scales" — ISG capital intensity question
  - Leverage: Flag TIE 2.73x below 3.0x; assess short-term debt spike (50K→1,031K) — structural vs transactional?; disaggregate payables from financial debt
  - Liquidity: Explain why current ratio < 1.0 is intentional architecture (negative WC model); assess 45% OCF decline
  - Cross-category connections: hardware paradox (high leverage × thin margins × strong turnover), SSG mix-shift visibility, OCF decline + ST debt spike = liquidity question
- **Du Pont Decomposition (Section 8):** Full FY2024 vs FY2025 side-by-side with instructions for the executor: compute both years, identify which factor drove the largest ROE change, state explicitly whether improvement is margin-driven, efficiency-driven, or leverage-driven, assess sustainability. Narrative framing: "a leverage-driven ROE is fragile; a margin-driven ROE is durable."
- **Strategic Recommendations (Section 9):** 4 required topics — leverage management, margin improvement pathway, capital efficiency, liquidity management. Evidence standard: ratio value + YoY trend. Action specificity: concrete (not "improve margins" — "accelerate SSG attach rate in IDG accounts to lift consolidated operating margin above 4% by FY2027").
- **Output Format (Section 10):** 9-section structure, 1,200–1,800 word target, tone ("senior analyst writing to a managing director — concise, evidence-tight, no filler phrases"), ratio presentation format.

### Prompt Log & HIL Iteration

- **Prompt log:** 7 sessions spanning Stages 2–5. Each session documents context, prompt summary, what model produced, what accepted/rejected/revised. Professional format throughout. Stage 3 documents shares_outstanding unit error catch (12,200 vs 12,200,000 — M/B corrected from 0.002x to 2.02x). Stage 4 documents v1.0→v1.1 iteration with three specific gap closures.
- **HIL iteration (Stage 4, Session 4):** Three material catches identified and corrected:
  1. **EVA formula incomplete:** Referenced WACC but WACC was undefined in the spec. An executor would be unable to compute EVA. Added CAPM estimate (Rf 4.3% + β 0.85 × ERP 5.0% = 8.5%).
  2. **FY2024 Du Pont values were approximations:** v1.0 showed "~1.94%", "~1.58x" with tildes. Replaced with exact named-range formulas. Caught material error: asset turnover was 1.47x, not ~1.58x — a difference that changes the primary Du Pont driver conclusion (turnover is +0.31x improvement, not +0.20x).
  3. **DSO/DIO formulas missing:** Analysis Requirements instructed the executor to "calculate days receivables and days inventory outstanding explicitly" but Ratio Definitions section contained no DSO or DIO formulas. Added with named-range notation and expected outputs.

---

## Kindly-worded suggestions for improvement

- **The two modeling notes (D&A plug and NCI treatment) are outstanding documentation.** A senior analyst reviewing this spec immediately understands *why* certain numbers don't match HKFRS face-of-statement disclosure — that's the level of transparency a managing director wants. Carry these notes through to Stage 5's limitations section.
- **The asset turnover correction in the HIL review (1.58x→1.47x) is a material analytical catch.** This changed the Du Pont driver identification from "margin is primary" to "turnover is primary" — a fundamentally different strategic conclusion. This is exactly the kind of human verification that prevents materially wrong executive recommendations.
- **The per-category analysis requirements show deep company knowledge.** The negative-working-capital model explanation, the SSG mix-shift question, the payables disaggregation requirement — these pre-empt generic LLM analysis and force domain-specific output.

**Three improvements that would close the ratio coverage gap:**

1. **Add the missing ~9 ratios from the template's 29-ratio suite.** Specifically: ROA start-year (`INC_net / BAL_assets_total_prior`), ROC avg, ROE start-year; Operating Profit Margin (`after_tax_operating_income / INC_sales`); LT debt ratio (`BAL_debt_long_term_current / (BAL_debt_long_term_current + BAL_equity_shareholders_current)`), LT D/E, Cash coverage (`(INC_ebit + INC_depreciation) / INC_interest_expense`), Leverage ratio (`BAL_assets_total_current / BAL_equity_shareholders_current`); NWC/Assets. Your workbook's Ratios tab likely computes most of these already.
2. **Upgrade to 4-factor Du Pont.** At Lenovo's leverage level (6.51x equity multiplier), the 4th factor (debt burden = `INC_net / after_tax_operating_income`) provides critical insight: how much of operating profit is consumed by interest and taxes? Given TIE of 2.80x (below 3.0x comfort), isolating the debt burden factor makes the interest-coverage risk visible within the Du Pont framework.
3. **Fix the EVA expected value.** The spec shows "~478,000 (estimated)" positive, but the formula (`INC_ebit × (1−tax_rate) − WACC × BAL_assets_total_current`) at 8.5% WACC on $44.2B total assets produces approximately −$1.6M. If EVA should use invested capital (LT debt + equity ≈ $11B) as the capital base rather than total assets, specify that clearly. Otherwise update the expected value to negative.

**Looking ahead to Stage 5:** Your prompt log shows you've already completed Stage 5 with a strong final analysis. The three-way verification approach (manual / LLM / template) and the FY2024 TIE correction (1.40x→2.63x) demonstrate exactly the kind of analytical judgment the Stage 5 rubric rewards.
