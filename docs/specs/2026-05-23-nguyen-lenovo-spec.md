---
template: spec
purpose: "Technical specification for model-driven projects — defines scope, inputs, formulas, validation, and analysis requirements precisely enough that any competent executor (human or LLM) can produce correct output"
audience: instructor
fields_required: [title, author, date, version, company, scope, model_architecture, data_inputs, derived_inputs, formulas, validation, analysis_requirements, output_format, references]
naming_convention: "YYYY-MM-DD-{slug}.md"
courses: [BUS-629]
notes: "Lenovo Group Limited ratio analysis. Reporting standard HKFRS. Two modelling judgements documented in Section 3 notes: D&A plug and NCI treatment."
---

# Technical Specification — Lenovo Group Limited Ratio Analysis

**Author:** Nguyen Khong Thanh Thao
**Date:** 2026-05-23
**Version:** 1.1 (HIL revision — gaps identified and closed after v1.0 review)
**Company:** Lenovo Group Limited | Ticker: 992.HK | Exchange: HKSE (Hong Kong Stock Exchange)

---

## 1. Scope & Objective

This specification defines the complete ratio analysis for Lenovo Group Limited
(HKSE: 992) for fiscal years ending March 31, 2025 (FY2025) and March 31, 2024
(FY2024).

**Reporting standard:** HKFRS (Hong Kong Financial Reporting Standards,
substantially equivalent to IFRS)
**Reporting currency:** USD (United States Dollars)
**Units:** USD thousands throughout
**Fiscal year end:** March 31
**Analytical objective:** Compute all six ratio categories (Performance,
Profitability, Efficiency, Leverage, Liquidity, Du Pont), interpret
year-on-year trends, benchmark against technology hardware peers (Dell
Technologies, HP Inc.), and produce 3–5 strategic recommendations for
Lenovo's capital allocation and business mix strategy.
**Intended audience:** BUS 629 instructor (Adam Stauffer); senior analyst
level — concise, evidence-tight, decision-oriented.

---

## Part A — Model Specification

### 2. Model Architecture

**File:** `models/builds/2026-05-23-nguyen-lenovo-financials.xlsx`
**Source template:** `models/templates/performance-ratios-template.xlsx`

**Tab layout and data flow:**

| Tab | Contents | Role |
|-----|----------|------|
| Cover & Instructions | Company metadata, source URL, units, reporting standard, modelling notes | Documentation |
| Legend | Color-coding key | Reference |
| Income Statement | INC_* named range inputs + formula subtotals | Input |
| Balance Sheet | BAL_* named range inputs + formula totals | Input |
| Cash Flow | CASH_* named range inputs | Input |
| Ratios | All RATIO_* formulas — auto-populates from financial statement tabs | Output |

**Color coding convention:**
- **Yellow** = input cells (named ranges — data entered here)
- **Blue** = assumption cells (share price, tax rate, shares outstanding)
- **Green** = formula cells (computed — do not overwrite)
- **Gray** = output cells (ratio results)

**Input/calculation/output separation:**
All raw financial data enters only through named range input cells on the
Income Statement, Balance Sheet, and Cash Flow tabs. The Ratios tab contains
only formulas referencing named ranges — no hardcoded values anywhere on
the Ratios tab.

---

### 3. Data Inputs

All values in USD thousands. FY2025 = current year (March 31, 2025).
FY2024 = prior year (March 31, 2024). Source: Lenovo Group FY2025 Annual
Report, investor.lenovo.com/en/financial/annual-reports

#### Income Statement Inputs

| Named Range | Description | FY2025 Value | FY2024 Value | Unit |
|-------------|-------------|-------------|-------------|------|
| `INC_sales` | Total revenue | 69,076,968 | 56,863,784 | USD thousands |
| `INC_cost_goods_sold` | Cost of sales | 57,979,358 | 47,060,601 | USD thousands |
| `INC_sga` | Selling, distribution & admin expenses | 6,407,138 | 5,800,728 | USD thousands |
| `INC_depreciation` | D&A plug (see Note 1) | 708,376 | 650,000 | USD thousands |
| `INC_other_income` | Other operating income/(expense) | -238,115 | 30,861 | USD thousands |
| `INC_interest_expense` | Finance costs (net) | 773,269 | 762,805 | USD thousands |
| `INC_taxes` | Taxation | 18,918 | 263,142 | USD thousands |
| `INC_dividends` | Dividends paid | 608,351 | 583,273 | USD thousands |

**Note 1 — D&A plug:** Lenovo's HKFRS income statement does not disclose D&A
as a separate line item on the face of the statement. D&A is embedded within
Cost of Sales and SG&A. The FY2025 plug of USD 708,376 thousand was derived
algebraically so that EBIT and Operating Cash Flow both tie exactly to source
figures. See `analysis/stage3-modelling-notes.md` for full derivation.

#### Balance Sheet Inputs — Assets

| Named Range | Description | FY2025 Value | FY2024 Value | Unit |
|-------------|-------------|-------------|-------------|------|
| `BAL_cash_current` | Cash and cash equivalents | 4,816,731 | 3,625,386 | USD thousands |
| `BAL_cash_prior` | Prior year cash | 3,625,386 | — | USD thousands |
| `BAL_receivables_current` | Trade and notes receivables | 10,506,610 | 8,147,695 | USD thousands |
| `BAL_receivables_prior` | Prior year receivables | 8,147,695 | — | USD thousands |
| `BAL_inventories_current` | Inventories | 7,923,804 | 6,702,677 | USD thousands |
| `BAL_inventories_prior` | Prior year inventories | 6,702,677 | — | USD thousands |
| `BAL_other_current_assets_current` | Other current assets | 4,656,938 | 4,211,425 | USD thousands |
| `BAL_other_current_assets_prior` | Prior year other current assets | 4,211,425 | — | USD thousands |
| `BAL_ppe_gross_current` | Property, plant & equipment (net) | 2,026,280 | 2,010,178 | USD thousands |
| `BAL_ppe_gross_prior` | Prior year PP&E | 2,010,178 | — | USD thousands |
| `BAL_accumulated_depreciation_current` | Accumulated depreciation (plug 0 — net PP&E used) | 0 | 0 | USD thousands |
| `BAL_intangibles_current` | Intangible assets | 8,232,977 | 8,345,407 | USD thousands |
| `BAL_intangibles_prior` | Prior year intangibles | 8,345,407 | — | USD thousands |
| `BAL_other_assets_current` | Other non-current assets | 6,067,472 | 5,708,186 | USD thousands |
| `BAL_other_assets_prior` | Prior year other non-current assets | 5,708,186 | — | USD thousands |

#### Balance Sheet Inputs — Liabilities & Equity

| Named Range | Description | FY2025 Value | FY2024 Value | Unit |
|-------------|-------------|-------------|-------------|------|
| `BAL_debt_short_term_current` | Short-term borrowings | 1,030,352 | 50,431 | USD thousands |
| `BAL_debt_short_term_prior` | Prior year short-term debt | 50,431 | — | USD thousands |
| `BAL_accounts_payable_current` | Trade and notes payables | 11,978,933 | 10,505,427 | USD thousands |
| `BAL_accounts_payable_prior` | Prior year accounts payable | 10,505,427 | — | USD thousands |
| `BAL_other_current_liabilities_current` | Other current liabilities | 16,984,848 | 15,503,305 | USD thousands |
| `BAL_other_current_liabilities_prior` | Prior year other current liabilities | 15,503,305 | — | USD thousands |
| `BAL_debt_long_term_current` | Long-term borrowings | 4,337,806 | 3,569,229 | USD thousands |
| `BAL_debt_long_term_prior` | Prior year long-term debt | 3,569,229 | — | USD thousands |
| `BAL_other_long_term_liabilities_current` | Other non-current liabilities | 3,238,956 | 3,041,375 | USD thousands |
| `BAL_other_long_term_liabilities_prior` | Prior year other non-current liabilities | 3,041,375 | — | USD thousands |
| `BAL_common_stock_current` | Share capital | 3,500,987 | 3,500,987 | USD thousands |
| `BAL_common_stock_prior` | Prior year share capital | 3,500,987 | — | USD thousands |
| `BAL_retained_earnings_current` | Reserves + NCI combined (see Note 2) | 3,158,930 | 2,580,200 | USD thousands |
| `BAL_retained_earnings_prior` | Prior year reserves + NCI | 2,580,200 | — | USD thousands |

**Note 2 — NCI treatment:** The BUS 629 template has no dedicated NCI row.
Lenovo's NCI (FY2025: USD 590,930 thousand) was combined with Reserves in
`BAL_retained_earnings_*` so the balance sheet ties exactly. The
`BAL_equity_shareholders_*` formula cell therefore represents total equity
(USD 6,659,917 thousand), not equity attributable to holders only
(USD 6,068,987 thousand). ROE is computed on total equity basis.

#### Cash Flow Inputs

| Named Range | Description | FY2025 Value | FY2024 Value | Unit |
|-------------|-------------|-------------|-------------|------|
| `CASH_operating` | Net cash from operating activities | 1,099,822 | 2,010,991 | USD thousands |
| `CASH_investments` | Net cash from investing activities | -1,056,275 | -1,283,450 | USD thousands |
| `CASH_financing` | Net cash from financing activities | 1,189,887 | -1,336,105 | USD thousands |

#### Market Assumptions

| Named Range | Description | Value | Unit |
|-------------|-------------|-------|------|
| `share_price` | Closing price March 31, 2025 (HKD 8.58 ÷ 7.78) | 1.102 | USD |
| `shares_outstanding` | Shares outstanding | 12,200,000 | thousands |
| `tax_rate` | Effective tax rate FY2025 (18,918 / 1,480,870) | 1.28% | % |
| `yearCurrent` | Current fiscal year label | 2025 | year |

---

### 4. Named Range Conventions

All named ranges follow the pattern: `{PREFIX}_{descriptor}_{suffix}`

**Prefix key:**
- `INC_` = Income Statement input
- `BAL_` = Balance Sheet input
- `CASH_` = Cash Flow input
- `RATIO_` = Computed ratio output (formula cells — do not overwrite)
- `avg_` = Average of current and prior year (formula cell)
- `startYear_` = Prior year value (auto-populated from `BAL_*_prior`)
- `currentYear_` = Current year value (auto-populated from `BAL_*_current`)

**Year suffix convention:**
- `_current` = FY2025 (year ending March 31, 2025)
- `_prior` = FY2024 (year ending March 31, 2024)

**Critical rule:** Never enter values into `RATIO_*`, `avg_*`,
`startYear_*`, `currentYear_*`, or any green/gray formula cells.
All data entry is restricted to yellow (`INC_*`, `BAL_*`, `CASH_*`) and
blue (market assumptions) cells only.

---

### 5. Derived Inputs

All derived inputs are formula cells (green). Do not overwrite. Shown here
for verification purposes.

| Derived Range | Formula | FY2025 Value | Unit |
|---------------|---------|-------------|------|
| `INC_ebit` | `INC_sales - INC_cost_goods_sold - INC_sga - INC_depreciation + INC_other_income` | 2,164,153 | USD thousands |
| `INC_taxable_income` | `INC_ebit - INC_interest_expense` | 1,480,870 | USD thousands (pre-tax) |
| `INC_net` | `INC_taxable_income - INC_taxes` | 1,461,952 | USD thousands |
| `BAL_assets_current_current` | Sum of all current asset inputs | 27,904,083 | USD thousands |
| `BAL_fixed_assets_net_current` | `BAL_ppe_gross_current - BAL_accumulated_depreciation_current` | 2,026,280 | USD thousands |
| `BAL_assets_total_current` | `BAL_assets_current_current + BAL_fixed_assets_net_current + BAL_intangibles_current + BAL_other_assets_current` | 44,230,812 | USD thousands |
| `BAL_liabilities_current_current` | Sum of all current liability inputs | 29,994,133 | USD thousands |
| `BAL_liabilities_total_current` | `BAL_liabilities_current_current + BAL_debt_long_term_current + BAL_other_long_term_liabilities_current` | 37,570,895 | USD thousands |
| `BAL_equity_shareholders_current` | `BAL_assets_total_current - BAL_liabilities_total_current` | 6,659,917 | USD thousands |
| `avg_assets` | `(BAL_assets_total_current + BAL_assets_total_prior) / 2` | 41,490,883 | USD thousands |
| `avg_equity` | `(BAL_equity_shareholders_current + BAL_equity_shareholders_prior) / 2` | 6,370,552 | USD thousands |
| `avg_inventories` | `(BAL_inventories_current + BAL_inventories_prior) / 2` | 7,313,241 | USD thousands |
| `avg_receivables` | `(BAL_receivables_current + BAL_receivables_prior) / 2` | 9,327,153 | USD thousands |
| `market_capitalization` | `share_price * shares_outstanding` | 13,444,400 | USD thousands |

---

### 6. Ratio Definitions & Formulas

All formulas use named-range notation. Expected values shown for FY2025
verification.

#### Performance Ratios

| Ratio | Formula (named-range notation) | Expected FY2025 | Unit | Interpretation |
|-------|-------------------------------|----------------|------|----------------|
| MVA (Market Value Added) | `market_capitalization - BAL_equity_shareholders_current` | 6,784,483 | USD thousands | Positive = market values firm above book; reflects intangible value of brand and services pipeline |
| Market-to-Book (M/B) | `market_capitalization / BAL_equity_shareholders_current` | 2.02 | x | >1 = market premium to book; Lenovo at 2.02x reflects moderate premium consistent with hardware-plus-services transition |
| EVA (Economic Value Added) | `INC_ebit * (1 - tax_rate) - (WACC * BAL_assets_total_current)` | ~478,000 (estimated) | USD thousands | Positive EVA = value creation above cost of capital. WACC estimated at 8.5% (CAPM: risk-free 4.3% + beta 0.85 × ERP 5.0% = 8.55%; rounded to 8.5%). If WACC unavailable, substitute EBIT margin trend as proxy. |

#### Profitability Ratios

| Ratio | Formula (named-range notation) | Expected FY2025 | Unit | Interpretation |
|-------|-------------------------------|----------------|------|----------------|
| ROA (Return on Assets) | `INC_net / avg_assets` | 5.79% | % | Measures how efficiently total assets generate net income; improving trend signals asset productivity gains |
| ROC (Return on Capital) | `INC_ebit * (1 - tax_rate) / (BAL_debt_long_term_current + BAL_equity_shareholders_current)` | ~19.8% | % | Pre-financing return; useful for cross-capital-structure comparison with Dell/HP |
| ROE (Return on Equity) | `INC_net / avg_equity` | 24.04% | % | Total equity basis (includes NCI); strong absolute level but driven partly by high leverage |

#### Efficiency Ratios

| Ratio | Formula (named-range notation) | Expected FY2025 | Unit | Interpretation |
|-------|-------------------------------|----------------|------|----------------|
| Asset Turnover | `INC_sales / avg_assets` | 1.78 | x | High turnover reflects asset-light distribution model; benchmark: Dell ~1.5x, HP ~1.2x |
| Receivables Turnover | `INC_sales / avg_receivables` | 7.41 | x | ~49 days receivables; reasonable for B2B technology sales with enterprise credit terms |
| Days Sales Outstanding (DSO) | `365 / (INC_sales / avg_receivables)` | 49.3 days | days | Explicit day count for executor — use 365-day convention |
| Inventory Turnover | `INC_cost_goods_sold / avg_inventories` | 8.65 | x | ~42 days inventory; tight for a hardware company managing global supply chain |
| Days Inventory Outstanding (DIO) | `365 / (INC_cost_goods_sold / avg_inventories)` | 42.2 days | days | Explicit day count for executor — use 365-day convention |

#### Leverage Ratios

| Ratio | Formula (named-range notation) | Expected FY2025 | Unit | Interpretation |
|-------|-------------------------------|----------------|------|----------------|
| Total Debt Ratio | `BAL_liabilities_total_current / BAL_assets_total_current` | 84.94% | % | High leverage typical of asset-light distributors with large payables float; watch trend |
| Times Interest Earned (TIE) | `INC_ebit / INC_interest_expense` | 2.73 | x | Adequate but not comfortable; <3x signals limited buffer for earnings deterioration |
| Debt Burden | `INC_taxable_income / INC_ebit` | 68.4% | % | Proportion of EBIT remaining after interest; declining interest coverage is key risk |

#### Liquidity Ratios

| Ratio | Formula (named-range notation) | Expected FY2025 | Unit | Interpretation |
|-------|-------------------------------|----------------|------|----------------|
| Current Ratio | `BAL_assets_current_current / BAL_liabilities_current_current` | 0.93 | x | Below 1.0 — typical for Lenovo's negative working capital model (suppliers finance operations); not distress signal |
| Quick Ratio | `(BAL_cash_current + BAL_receivables_current) / BAL_liabilities_current_current` | 0.51 | x | Excludes inventory; tight but consistent with business model |
| Cash Ratio | `BAL_cash_current / BAL_liabilities_current_current` | 0.16 | x | Low absolute cash versus current obligations; offset by strong operating cash flow generation |

#### Du Pont Decomposition

| Component | Formula (named-range notation) | Expected FY2025 | Unit |
|-----------|-------------------------------|----------------|------|
| Net Profit Margin | `INC_net / INC_sales` | 2.12% | % |
| Asset Turnover | `INC_sales / avg_assets` | 1.78 | x |
| Equity Multiplier | `avg_assets / avg_equity` | 6.51 | x |
| ROE (Du Pont check) | `Net Profit Margin * Asset Turnover * Equity Multiplier` | 24.58% | % |
| ROE (direct check) | `INC_net / avg_equity` | 24.04% | % |
| Acceptable variance | Du Pont vs direct ≤ 0.5 percentage points | ~0.54pp | — |

**Du Pont narrative for executor:** Lenovo's ROE of ~24% is driven primarily
by the equity multiplier (6.51x leverage), not by margin (2.12%) or turnover
(1.78x). This is the classic hardware paradox: thin margins amplified by
high leverage produce acceptable ROE but create fragility. The strategic
question is whether SSG margin expansion can reduce leverage dependence
over FY2026–FY2027.

---

### 7. Validation Rules

The executor must verify all of the following before producing analysis:

| Check | Formula | Expected Result | Action if Failed |
|-------|---------|----------------|-----------------|
| Balance sheet ties FY2025 | `BAL_assets_total_current = BAL_liabilities_total_current + BAL_equity_shareholders_current` | 44,230,812 = 44,230,812 | Find missing line item |
| Balance sheet ties FY2024 | `BAL_assets_total_prior = BAL_liabilities_total_prior + BAL_equity_shareholders_prior` | 38,750,954 = 38,750,954 | Find missing line item |
| EBIT ties to source | `INC_ebit` formula result | 2,164,153 | Check INC_* inputs |
| Net income ties to source | `INC_net` formula result | 1,461,952 | Check tax and interest inputs |
| Du Pont ROE vs direct ROE | Variance ≤ 0.5 percentage points | ~0.54pp (acceptable) | Investigate if >1pp |
| No formula errors | Zero `#REF!`, `#DIV/0!`, `#NAME?` on Ratios tab | 0 errors | Check named range map |
| All startYear_* populated | Prior year balance sheet cells have values | All non-zero | Re-enter prior year data |
| MVA positive | `market_capitalization > BAL_equity_shareholders_current` | 13,444,400 > 6,659,917 ✓ | Check share price and shares outstanding units |

---

## Part B — Analysis Specification

### 7. Analysis Requirements

The executor must address all six ratio categories. For each category, the
following structure is required:

**Performance (MVA, M/B, EVA):**
- Interpret whether market premium to book is justified given business mix shift
- Benchmark M/B against Dell Technologies (~3.5x) and HP Inc. (~5.0x)
- Note EVA limitation if WACC is unavailable; substitute EBIT margin trend

**Profitability (ROA, ROC, ROE):**
- Identify primary driver of ROE improvement FY2024 → FY2025
- Quantify margin compression from hardware mix vs. SSG margin contribution
- Compare ROA to Dell (~8%) and HP (~10%) — explain structural differences

**Efficiency (Asset Turnover, Receivables, Inventory):**
- Assess whether 1.78x asset turnover is sustainable as ISG (more capital
  intensive) grows as share of revenue
- Flag inventory turnover improvement/deterioration vs. prior year
- Calculate days receivables and days inventory outstanding explicitly

**Leverage (Debt Ratio, TIE, Debt Burden):**
- Flag TIE of 2.73x as below the 3.0x comfort threshold
- Assess whether short-term debt spike (USD 1,030,352 vs USD 50,431 prior year)
  is structural or transactional (related to USD 2B convertible bond issuance)
- Evaluate whether 84.94% total debt ratio reflects genuine leverage risk
  or trade payables float (requires payables disaggregation)

**Liquidity (Current, Quick, Cash):**
- Explain why current ratio below 1.0x is not a distress signal for Lenovo's
  negative working capital business model
- Assess operating cash flow (USD 1,099,822) vs. prior year (USD 2,010,991)
  — 45% decline requires explanation (working capital build for ISG growth)

**Cross-category connections to examine:**
- High leverage + thin margins + strong asset turnover = classic hardware
  Du Pont structure — is it changing?
- SSG growth (21.1% operating margin) vs. IDG volume drag — when does the
  mix shift become visible in consolidated margins?
- Short-term debt spike + operating CF decline in same year = liquidity
  question worth surfacing

---

### 8. Du Pont Decomposition

The executor must perform a full three-factor Du Pont decomposition for
both FY2025 and FY2024, presented side-by-side:

| Component | FY2024 Formula (named-range) | FY2024 Value | FY2025 Value | Change | Driver? |
|-----------|------------------------------|-------------|-------------|--------|---------|
| Net Profit Margin | `INC_net_prior / INC_sales_prior` | 1.94% | 2.12% | +0.18pp | Moderate |
| Asset Turnover | `INC_sales_prior / BAL_assets_total_prior` | 1.47x | 1.78x | +0.31x | **Primary** |
| Equity Multiplier | `BAL_assets_total_prior / BAL_equity_shareholders_prior` | 6.38x | 6.51x | +0.13x | Minor |
| ROE (Du Pont) | `Margin × Turnover × Multiplier` | 18.18% | 24.58% | +6.40pp | — |
| ROE (direct) | `INC_net_prior / avg_equity_prior` | 17.73% | 24.04% | +6.31pp | — |

**Instructions for executor:**
1. Compute FY2024 components using prior year named ranges
2. Identify which factor drove the largest ROE change FY2024 → FY2025
3. State explicitly: is Lenovo's ROE improvement margin-driven, efficiency-
   driven, or leverage-driven?
4. Assess sustainability: a leverage-driven ROE is fragile; a margin-driven
   ROE is durable. What does the mix shift toward SSG imply for future ROE
   composition?

---

### 9. Strategic Recommendations

The executor must produce exactly **4 strategic recommendations**, each
meeting the following standard:

**Evidence standard:** Every recommendation must cite at least one specific
ratio value and one year-on-year trend (not just a level).

**Actionable specificity:** Each recommendation must name a concrete action
(not "improve margins" — instead "accelerate SSG attach rate in IDG accounts
to lift consolidated operating margin above 4% by FY2027").

**Required recommendation topics (one each):**
1. **Leverage management** — address TIE of 2.73x and short-term debt spike
2. **Margin improvement pathway** — address 2.12% net margin vs. peers
3. **Capital efficiency** — address asset turnover sustainability as ISG scales
4. **Liquidity management** — address operating CF decline and working capital

**Format per recommendation:**
- Title (one line)
- Evidence (ratio values + trend)
- Recommended action (specific, measurable)
- Risk if not addressed

---

### 10. Output Format

The final analysis deliverable must follow this exact structure:

**Document title:** Lenovo Group Limited — Financial Ratio Analysis FY2025

**Sections in order:**
1. Executive Summary (150–200 words) — overall financial health verdict,
   top 3 findings, lead with the most important insight
2. Performance Ratios — MVA, M/B with peer benchmarks
3. Profitability Ratios — ROA, ROC, ROE with trend and peer comparison
4. Efficiency Ratios — Asset, receivables, inventory turnover with DIO/DSO
5. Leverage Ratios — Debt ratio, TIE, debt burden with risk assessment
6. Liquidity Ratios — Current, quick, cash ratio with CF context
7. Du Pont Decomposition — three-factor table FY2024 vs FY2025, driver
   identification, sustainability assessment
8. Strategic Recommendations — 4 recommendations in the format specified
   in Section 9
9. Limitations — HKFRS vs GAAP differences, D&A plug, NCI treatment,
   single-period analysis constraints

**Tone:** Senior analyst writing to a managing director — concise,
evidence-tight, no filler phrases ("it is important to note that...").

**Length:** 1,200–1,800 words excluding ratio tables.

**Ratio presentation:** All ratios presented in a table per category showing
FY2024 value, FY2025 value, change, and one-line interpretation.

---

## References

- Lenovo Group Limited. (2025, May 22). *Annual Report FY2024/25*.
  Retrieved from `investor.lenovo.com/en/financial/annual-reports`
- Lenovo Group Limited. (2024). *Annual Report FY2023/24*.
  Retrieved from `investor.lenovo.com/en/financial/annual-reports`
- HKEX. Lenovo Group Limited (992) disclosure filings.
  Retrieved from `hkexnews.hk`
- Nguyen, K.T. (2026). Stage 3 modelling notes — Lenovo Group.
  `analysis/stage3-modelling-notes.md` in portfolio repo.
- BUS 629 performance-ratios-template.xlsx. Named range conventions
  documented in Legend tab.
