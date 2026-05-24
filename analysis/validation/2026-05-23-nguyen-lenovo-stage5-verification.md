# Manual Ratio Verification Table — Stage 5
**Company:** Lenovo Group Limited (HKSE: 992)
**Author:** Nguyen Khong Thanh Thao
**Date:** 2026-05-23
**Course:** BUS-629 VEMBA

---

## Purpose

This table verifies the LLM's ratio outputs against manually recomputed
values drawn directly from the Stage 3 financial data
(`models/builds/2026-05-23-nguyen-lenovo-financials.xlsx`). Three sources
are compared:

| Source | Origin |
|--------|--------|
| **Template auto-computed** | Excel Ratios tab formulas from Stage 3 workbook |
| **LLM stated** | Raw output from Stage 5 LLM session |
| **Manual (this table)** | Hand-computed from Stage 3 named-range inputs |

The graded comparison is **Manual vs. LLM**. Template values serve as
a secondary sanity check.

---

## Ratio 1 — Return on Assets (ROA) — Profitability
*Chosen because it uses average assets — the most common LLM averaging error.*

**Formula:** `INC_net / avg_assets`
where `avg_assets = (BAL_assets_total_current + BAL_assets_total_prior) / 2`

**Manual arithmetic:**
- BAL_assets_total_current = 44,230,812
- BAL_assets_total_prior = 38,750,954
- avg_assets = (44,230,812 + 38,750,954) / 2 = **41,490,883**
- INC_net = 1,461,952
- ROA = 1,461,952 / 41,490,883 = **3.52%**

| Source | Value | Match? |
|--------|-------|--------|
| Manual | **3.52%** | — |
| LLM stated | 3.52% | ✅ Exact |
| Template auto-computed | 5.79% | ⚠️ Template uses year-end assets, not average |

**Note:** LLM correctly used average assets per spec. Template uses year-end
convention. LLM is right per spec instructions.

---

## Ratio 2 — Asset Turnover — Efficiency
*Chosen because FY2024 comparison drives the Du Pont driver conclusion.*

**Formula:** `INC_sales / avg_assets`

**Manual arithmetic FY2025:**
- INC_sales = 69,076,968 / avg_assets = 41,490,883 = **1.66x**

**Manual arithmetic FY2024** (LLM used year-end — no prior-prior year):
- INC_sales_FY2024 = 56,863,784 / BAL_assets_total_FY2024 = 38,750,954 = **1.47x**

| Source | FY2025 | FY2024 | Match? |
|--------|--------|--------|--------|
| Manual | **1.66x** | **1.47x** | — |
| LLM stated | 1.66x | 1.47x | ✅ Exact both years |
| Template auto-computed | 1.78x | — | ⚠️ Year-end vs. average convention |

---

## Ratio 3 — Times Interest Earned (TIE) — Leverage
*Chosen because FY2024 TIE uses an approximate EBIT — key test of accuracy.*

**Formula:** `INC_ebit / INC_interest_expense`

**Manual FY2025:**
- INC_ebit = 2,164,153 (verified against source)
- INC_interest_expense = 773,269
- TIE = 2,164,153 / 773,269 = **2.80x**

**Manual FY2024:**
- Source income statement operating profit = 2,005,784
- INC_interest_expense_FY2024 = 762,805
- TIE = 2,005,784 / 762,805 = **2.63x**

| Source | FY2025 | FY2024 | Match? |
|--------|--------|--------|--------|
| Manual | **2.80x** | **2.63x** | — |
| LLM stated | 2.80x | 1.40x | ✅ FY2025 / ⚠️ **FY2024 discrepancy** |

**Finding — material error:** LLM used approximate EBIT of ~USD 1,069M
for FY2024, producing TIE of 1.40x. Manual computation using source
operating profit of USD 2,005,784 yields 2.63x. The LLM's FY2024 TIE
is wrong. This overstates the improvement narrative (1.40x → 2.80x vs.
the correct 2.63x → 2.80x). Corrected in final analysis.

---

## Ratio 4 — Current Ratio — Liquidity
*Chosen because it uses year-end balances only — clean verification.*

**Formula:** `BAL_assets_current_current / BAL_liabilities_current_current`

**Manual FY2025:**
- 27,904,083 / 29,994,133 = **0.93x**

**Manual FY2024:**
- 22,687,183 / 26,059,163 = **0.87x**

| Source | FY2025 | FY2024 | Match? |
|--------|--------|--------|--------|
| Manual | **0.93x** | **0.87x** | — |
| LLM stated | 0.93x | 0.87x | ✅ Exact both years |
| Template auto-computed | 0.93x | — | ✅ Exact |

**Finding:** Perfect three-way match. No averaging involved — straightforward
year-end balance computation.

---

## Ratio 5 — Market-to-Book (M/B) — Performance
*Chosen because it involves unit conversion (HKD→USD, shares in thousands).*

**Formula:** `(share_price × shares_outstanding) / BAL_equity_shareholders_current`

**Manual arithmetic:**
- share_price = 1.102 USD (HKD 8.58 ÷ 7.78)
- shares_outstanding = 12,200,000 thousands
- market_cap = 1.102 × 12,200,000 = 13,444,400 USD thousands
- BAL_equity_shareholders_current = 6,659,917
- M/B = 13,444,400 / 6,659,917 = **2.02x**

| Source | Value | Match? |
|--------|-------|--------|
| Manual | **2.02x** | — |
| LLM stated | 2.02x | ✅ Exact |
| Template auto-computed | 2.02x | ✅ Exact |

**Finding:** Perfect three-way match. Unit correction made during Stage 3
(shares entered as 12,200,000 thousands not 12,200 millions) carried
through correctly.

---

## Ratio 6 — ROE Du Pont Check — Du Pont
*Chosen to verify three-factor multiplication ties to direct ROE.*

**Manual arithmetic:**
- avg_equity = (6,659,917 + 6,081,187) / 2 = 6,370,552
- Net Profit Margin = 1,461,952 / 69,076,968 = 2.117%
- Asset Turnover = 1.665x
- Equity Multiplier = 41,490,883 / 6,370,552 = 6.513x
- ROE Du Pont = 2.117% × 1.665 × 6.513 = **22.95%**
- ROE Direct = 1,461,952 / 6,370,552 = **22.95%**
- Variance = **0.00pp** ✅

| Source | ROE Du Pont | ROE Direct | Variance | Match? |
|--------|------------|-----------|---------|--------|
| Manual | **22.95%** | **22.95%** | 0.00pp | — |
| LLM stated | 22.95% | 22.95% | 0.00pp | ✅ Exact |

---

## Summary

| Ratio | Category | Manual | LLM Stated | Match? |
|-------|----------|--------|-----------|--------|
| ROA | Profitability | 3.52% | 3.52% | ✅ |
| Asset Turnover | Efficiency | 1.66x | 1.66x | ✅ |
| TIE FY2025 | Leverage | 2.80x | 2.80x | ✅ |
| TIE FY2024 | Leverage | 2.63x | 1.40x | ⚠️ **Error — overstated improvement** |
| Current Ratio | Liquidity | 0.93x | 0.93x | ✅ |
| M/B | Performance | 2.02x | 2.02x | ✅ |
| ROE Du Pont | Du Pont | 22.95% | 22.95% | ✅ |

**Overall verdict:** 6 of 7 checks pass exactly. One material discrepancy
found in FY2024 TIE (LLM: 1.40x vs. Manual: 2.63x). The LLM used a
non-standard FY2024 EBIT approximation (~USD 1,069M) instead of the
source income statement operating profit (USD 2,005,784). This error
overstates the TIE improvement story and is corrected with annotation
in the final analysis.

**Methodological note:** The LLM consistently used average balance sheet
values per spec instructions. Template auto-computed ratios use year-end
values — a simpler convention. All template vs. LLM differences stem
from this choice, not from LLM errors.
