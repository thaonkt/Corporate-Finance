# Stage 3 Modelling Notes — Lenovo Group (HKSE: 992)

**File:** `models/builds/2026-05-23-nguyen-lenovo-financials.xlsx`
**Prepared by:** Nguyen Khong Thanh Thao
**Date:** 2026-05-23
**Source:** investor.lenovo.com/en/financial/annual-reports

---

## Modelling Judgements

### 1. Depreciation & Amortization (D&A) — Plug Figure

Lenovo's HKFRS income statement embeds D&A within Cost of Sales and SG&A
line items and does not disclose it as a separate line on the face of the
income statement. A D&A plug of **USD 708,376 thousand** was derived
algebraically so that:

- EBIT = Revenue − COGS − SG&A − D&A computes exactly to the source figure
  of USD 2,164,153 thousand
- Operating Cash Flow = Net income + D&A + ΔWorking Capital computes exactly
  to the source figure of USD 1,099,822 thousand

**Implication for Stage 4:** The D&A assumption should be flagged as an
estimate in the spec. The full annual report (PDF) contains a D&A disclosure
in the notes to the financial statements which can be used to validate this
plug at Stage 5.

---

### 2. Non-Controlling Interests (NCI) — Combined into Retained Earnings

The BUS 629 ratios template does not have a dedicated NCI row in the equity
section. Lenovo reports two equity components:

- Equity attributable to owners of the Company: USD 6,068,987 thousand (FY2025)
- Non-controlling interests and other equity: USD 590,930 thousand (FY2025)
- **Total equity: USD 6,659,917 thousand (FY2025)**

To make the balance sheet balance exactly, NCI (590,930) was combined with
Reserves in the `BAL_retained_earnings_*` named range. As a result:

- `BAL_equity_shareholders_*` formula cell represents **total equity**
  (USD 6,659,917), not equity attributable to holders only (USD 6,068,987)
- ROE computed using total equity as denominator: **24.04%**
- If ROE using equity attributable to holders only is required:
  ROE = 1,384,445 / 6,068,987 = **22.81%**

**Implication for Stage 4:** Note this treatment in the spec. Flag that
peer comparisons should use consistent equity definitions.

---

### 3. Share Price and Market Assumptions

- Share price at March 31, 2025 fiscal year end: **HKD 8.58**
- USD/HKD exchange rate applied: **7.78**
- Share price in USD entered in template: **USD 1.102**
- Shares outstanding entered: **12,200,000 thousand** (i.e. 12.2 billion shares)
- Market capitalization computed: **USD 13,444,400 thousand (~USD 13.4 billion)**
- M/B ratio: **2.02×**
- MVA: **+USD 6,784,483 thousand**

---

## Balance Sheet Tie-Out

| Year | Total Assets | Total L+E | Difference |
|------|-------------|-----------|------------|
| FY2025 | 44,230,812 | 44,230,812 | 0 ✅ |
| FY2024 | 38,750,954 | 38,750,954 | 0 ✅ |

---

## Data Sources

| Statement | Source | Period |
|-----------|--------|--------|
| Income Statement | investor.lenovo.com — FY2025 Annual Results | FY2025, FY2024 |
| Balance Sheet | investor.lenovo.com — FY2025 Annual Results | FY2025, FY2024 |
| Cash Flow | investor.lenovo.com — FY2025 Annual Results | FY2025, FY2024 |
| Share price | HKEX — closing price March 31, 2025 | FY2025 year-end |
