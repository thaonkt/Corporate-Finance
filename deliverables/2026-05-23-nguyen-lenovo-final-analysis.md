# Lenovo Group Limited — Financial Ratio Analysis FY2025

**Prepared by:** Nguyen Khong Thanh Thao
**Course:** BUS-629 VEMBA | Instructor: Adam Stauffer
**Company:** Lenovo Group Limited | HKSE: 992.HK
**Reporting Standard:** HKFRS | Currency: USD thousands
**Fiscal Year End:** March 31
**Date:** 2026-05-23

> **Editorial note:** This document is the evaluated and corrected version
> of the LLM-generated raw output (`deliverables/2026-05-23-nguyen-lenovo-llm-raw.md`).
> Annotations are marked **[CORRECTION]** or **[ANNOTATION]** inline.
> One material error was identified and corrected: FY2024 TIE.
> All ratio values verified against the manual verification table
> (`analysis/validation/2026-05-23-nguyen-lenovo-stage5-verification.md`).

---

## 0. Company & Data Summary

| Field | Detail |
|-------|--------|
| Company | Lenovo Group Limited |
| Ticker / Exchange | 992.HK / HKSE |
| Reporting Standard | HKFRS (substantially equivalent to IFRS) |
| Reporting Currency | USD |
| Units | USD thousands throughout |
| Fiscal Year End | March 31 |
| Current Year | FY2025 (April 1, 2024 — March 31, 2025) |
| Prior Year | FY2024 (April 1, 2023 — March 31, 2024) |
| Source | Lenovo FY2025 Annual Report, investor.lenovo.com |
| Share Price | USD 1.102 (HKD 8.58 ÷ 7.78, March 31, 2025) |
| Shares Outstanding | 12,200,000 thousand |
| Market Cap | USD 13,444,400 thousand (~USD 13.4B) |

**Key modelling assumptions verified before analysis:**
- Balance sheet ties both years: FY2025 (44,230,812) and FY2024 (38,750,954) ✅
- D&A of USD 708,376 thousand derived algebraically — not disclosed separately
- NCI (USD 590,930 thousand) combined into retained earnings per template structure
- All named ranges populated at 100% — zero formula errors on Ratios tab
- Spec retrospective: `deliverables/2026-05-23-nguyen-lenovo-spec-retrospective.md`
- Verification table: `analysis/validation/2026-05-23-nguyen-lenovo-stage5-verification.md`

---

## 1. Executive Summary

Lenovo enters FY2025 in measurably better financial shape than twelve months
prior, but the underlying structure remains fragile in three specific ways
that management must address before the next debt maturity cycle.

The business mix shift is beginning to register in the numbers. Net margin
expanded from 1.94% to 2.12%, driven by SSG's 21.1% operating margin and
ISG's return to profitability after a loss-making FY2024. Revenue grew 21%
to USD 69.1B — the group's second-highest in history — while assets grew
only 14%, producing genuine efficiency gains across every turnover metric.
This is the clearest positive in the FY2025 data.

The risk picture is more nuanced than the LLM's raw output suggested.
Leverage remains the dominant ROE driver: the equity multiplier of 6.51x
accounts for the majority of Lenovo's 22.95% ROE. Times Interest Earned of
2.80x sits below the 3.0x comfort threshold — though the year-on-year
improvement is more modest than initially computed (from 2.63x, not 1.40x —
see Section 5 correction). The 45% operating cash flow decline from USD 2.0B
to USD 1.1B is the most important single number in this analysis and is
directly linked to ISG's rapid growth consuming working capital.

The analytical backbone of this analysis — the classic technology hardware
paradox — holds: Lenovo generates USD 69.1B in revenue on USD 44.2B of
assets (1.66x turnover) yet produces only 2.12% net margin. High efficiency
masking thin returns. The path to durable value creation runs through SSG
margin expansion, not through additional leverage. As a six-year employee
in Lenovo's Vietnam Commercial Segment, I have direct visibility into how
this paradox plays out operationally — the SSG attach rate in IDG commercial
accounts is the single highest-leverage variable in the model.

---

## 2. Performance Ratios

*Market data as of March 31, 2025. Share price: USD 1.102 (HKD 8.58 ÷ 7.78).
Shares: 12,200,000 thousand.*

| Metric | FY2024 | FY2025 | Change | Interpretation |
|--------|--------|--------|--------|----------------|
| MVA (USD 000s) | N/A | 6,784,483 | — | Market values Lenovo USD 6.8B above book |
| Market-to-Book | N/A | 2.02x | — | Moderate premium; Dell ~3.5x, HP ~5.0x |
| EVA (USD 000s, est.) | N/A | ~(1,623,000) | — | Negative at 8.5% WACC — see note |

MVA of USD 6.8B is positive — the market assigns value to Lenovo's brand,
SSG pipeline, and ISG turnaround narrative beyond book value. However,
2.02x M/B is materially below Dell (~3.5x) and HP (~5.0x), reflecting
market skepticism about margin sustainability in competitive hardware markets.

**[ANNOTATION — EVA]:** EVA is negative at the estimated WACC of 8.5%
(CAPM: Rf 4.3% + β 0.85 × ERP 5.0%). EBIT after tax (~USD 2.14B) is
insufficient to cover the capital charge on USD 44.2B total assets. This
is mathematically consistent with the hardware paradox: thin margins on a
large asset base structurally destroy economic value at any reasonable WACC.
Positive EVA is not achievable without either a margin step-change above 4%
or a significant asset base reduction. EBIT margin trend is the most
reliable EVA proxy — target 4%+ consolidated EBIT margin by FY2028 for
EVA breakeven at 8.5% WACC.

---

## 3. Profitability Ratios

*ROA uses average assets (USD 41,490,883 thousand). ROE uses average equity
(USD 6,370,552 thousand).*

| Metric | FY2024 | FY2025 | Change | Interpretation |
|--------|--------|--------|--------|----------------|
| Net Profit Margin | 1.94% | 2.12% | +0.18pp | Thin but improving |
| ROA | 2.84% | 3.52% | +0.68pp | Below Dell ~8%, HP ~10% |
| ROC | N/A | 19.43% | — | Strong pre-financing return |
| ROE | 18.12% | 22.95% | +4.83pp | Multiplier-driven — see Du Pont |

ROA's structural deficit versus peers reflects Lenovo's supply chain model,
not management failure. Lenovo retains more manufacturing and distribution
assets than Dell or HP, inflating the denominator. The +68 bps improvement
— 21% revenue growth on 14% asset growth — is a genuine efficiency signal.

ROE at 22.95% appears strong against a cost of equity of ~8.6%. The critical
caveat: the equity multiplier of 6.51x is doing most of the work. Net margin
and asset turnover together produce only 3.52% ROA — the remaining ~19
percentage points of ROE is pure leverage effect. A 1pp deterioration in
net margin reduces ROE by approximately 6.5pp. This fragility is the central
finding of the Du Pont analysis.

---

## 4. Efficiency Ratios

*FY2025 uses average balances. FY2024 uses year-end balances (no prior-prior
year data available).*

| Metric | FY2024 | FY2025 | Change | Interpretation |
|--------|--------|--------|--------|----------------|
| Asset Turnover | 1.47x | 1.66x | +0.19x | Revenue growing faster than assets |
| Receivables Turnover | 6.98x | 7.41x | +0.43x | Faster enterprise collection |
| DSO | 52.3 days | 49.3 days | −3.0 days | ~USD 568M annual cash acceleration |
| Inventory Turnover | 7.02x | 7.93x | +0.91x | Tighter supply chain execution |
| DIO | 52.0 days | 46.0 days | −6.0 days | ~USD 956M working capital released |

The efficiency picture is the most unambiguous positive in FY2025. DSO
compression of 3 days on USD 69.1B revenue frees approximately USD 568M
of annual cash. DIO compression of 6 days on USD 58B COGS releases
approximately USD 956M of working capital. These improvements partially
offset the ISG-driven OCF decline discussed in Section 6.

The sustainability question is ISG capital intensity. Server infrastructure
has structurally longer payment cycles and larger project receivables than
PC distribution. Asset turnover compression toward 1.55x by FY2027 is the
expected mechanical outcome if ISG continues scaling at its current rate.
Management's USD 200M+ cost savings programme is designed to partially
offset this — but investors should monitor asset turnover quarterly as ISG
grows toward 25% of revenue.

---

## 5. Leverage Ratios

*Total debt ratio = total liabilities / total assets.*

| Metric | FY2024 | FY2025 | Change | Interpretation |
|--------|--------|--------|--------|----------------|
| Total Debt Ratio | 84.31% | 84.94% | +0.63pp | Stable; driven by payables float |
| TIE | 2.63x | 2.80x | +0.17x | Modest improvement; still below 3.0x |
| Debt Burden | 68.0% | 68.4% | +0.4pp | Broadly stable |

**[CORRECTION — FY2024 TIE]:** The LLM's raw output stated FY2024 TIE
of 1.40x, using an approximate EBIT of ~USD 1,069M. Manual verification
against the source income statement (operating profit: USD 2,005,784;
interest expense: USD 762,805) yields FY2024 TIE of 2.63x. The LLM
appears to have used ISG segment operating data rather than consolidated
EBIT. The corrected improvement (2.63x → 2.80x, +0.17x) is materially
less dramatic than the LLM presented (1.40x → 2.80x, +1.40x). The
directional conclusion holds — TIE is improving and remains below 3.0x —
but the urgency narrative changes: Lenovo's interest coverage has been
adequate in both years, not recovering from genuine stress.

The total debt ratio of 84.94% demands context. Trade payables (USD 11.98B)
and other current liabilities (USD 16.98B) account for USD 28.96B of the
USD 37.57B total liabilities — 77%. Strip out trade obligations and
Lenovo's financial debt ratio falls to approximately 15% of assets. The
headline ratio overstates financial risk; the real leverage concern is TIE.

The short-term debt spike (USD 50M → USD 1,031M) is most likely
transactional — coinciding with the USD 2B convertible bond issuance in
FY2025. Full confirmation requires the maturity schedule in the Notes to
the Financial Statements, which were not available in the summary inputs.

---

## 6. Liquidity Ratios

| Metric | FY2024 | FY2025 | Change | Interpretation |
|--------|--------|--------|--------|----------------|
| Current Ratio | 0.87x | 0.93x | +0.06x | Below 1.0x; intentional NWC model |
| Quick Ratio | 0.45x | 0.51x | +0.06x | Tight but improving |
| Cash Ratio | 0.14x | 0.16x | +0.02x | Low absolute cash |
| Operating Cash Flow | 2,010,991 | 1,099,822 | −45.3% | Primary liquidity concern |

A current ratio below 1.0x is intentional architecture for Lenovo. The
company collects from enterprise customers in 49 days and pays suppliers
in approximately 75 days — a negative cash conversion cycle where suppliers
finance working capital. Both ratios improved year-on-year, confirming the
model is functioning as designed.

The 45% OCF decline is the most operationally significant number in this
analysis. ISG revenue grew approximately 65% in FY2025; server and storage
projects require upfront inventory and project receivables that do not
monetize in the same period. This working capital build depressed OCF
despite strong net income growth. The combined picture — lower OCF plus
a short-term debt spike in the same year — warrants active monitoring in
FY2026 disclosures. OCF of USD 1,100M minus interest expense of USD 773M
leaves only USD 327M to cover capex and dividends (USD 608M paid) — a
structural shortfall before any growth investment.

---

## 7. Du Pont Decomposition

*FY2025 uses average balances. FY2024 uses year-end balances.*

| Component | FY2024 | FY2025 | Change | Driver? |
|-----------|--------|--------|--------|---------|
| Net Profit Margin | 1.94% | 2.12% | +0.18pp | Minor |
| Asset Turnover | 1.47x | 1.66x | +0.19x | **Primary** |
| Equity Multiplier | 6.37x | 6.51x | +0.14x | Minor |
| ROE (Du Pont) | 18.12% | 22.95% | +4.83pp | — |
| ROE (Direct) | 18.12% | 22.95% | +4.83pp | — |
| Du Pont variance | 0.00pp | 0.00pp | — | ✅ Within tolerance |

**Driver identification:** Asset turnover is the primary driver of ROE
improvement in FY2025. The 0.19x increase in turnover contributed
approximately +3pp to ROE (amplified through 6.44x average leverage).
Net margin's +0.18pp contributed approximately +1.7pp. The equity
multiplier's minor expansion (+0.14x) reflects balance sheet growth
slightly outpacing equity accumulation.

**Sustainability assessment:** Asset turnover improvement (efficiency-driven)
is more durable than leverage expansion (fragility-driven) — this is the
right kind of ROE improvement. However, ISG capital intensity threatens
asset turnover going forward. The most strategically important variable
is net margin: every 0.5pp of consolidated margin improvement adds
approximately 5pp of ROE at current leverage, making SSG attach rate
the single highest-return strategic lever available.

Lenovo's ROE is leverage-dependent today. The path to durable ROE runs
through SSG margin expansion. At 3% net margin and 1.65x turnover,
ROE would reach ~32% — on a structurally sounder basis than the current
2.12% × 1.66x × 6.51x composition.

---

## 8. Strategic Recommendations

### Recommendation 1 — Strengthen Interest Coverage Before Next Debt Maturity Cycle

**Evidence:** TIE improved from 2.63x (FY2024) to 2.80x (FY2025) — a
modest +0.17x gain, not the dramatic recovery suggested by the LLM's
uncorrected 1.40x baseline. The absolute level remains below 3.0x.
Short-term borrowings spiked 20x to USD 1,031M in the same year.

**Action:** Target TIE ≥ 3.5x by FY2027 by prioritising EBIT growth
over additional financial leverage: (a) retire the short-term debt spike
within 12 months; (b) restrict further convertible issuance until EBIT
reaches USD 2.8B; (c) direct ISG cost savings (USD 200M+ annualised)
to interest service before new capex.

**Risk if unaddressed:** A 10%+ revenue shock would reduce EBIT by
~USD 400–500M, bringing TIE below 2.0x and triggering covenant review.
At current margins, there is no cushion.

---

### Recommendation 2 — Accelerate SSG Attach Rate to Drive Consolidated Margin Above 3% by FY2027

**Evidence:** Net margin improved from 1.94% to 2.12% (+0.18pp) but
remains below Dell (3.5%) and HP (6.0%). SSG's 21.1% operating margin
is ~10x IDG's blended margin yet represents only 15–18% of revenue.
Every 1pp revenue mix shift from IDG to SSG adds ~0.19pp to consolidated
operating margin.

**Action:** Target SSG revenue at 22% of total by FY2027: (a) mandate
SSG solution bundling in all IDG enterprise deals above USD 100K;
(b) convert top-100 IDG commercial accounts per geography to SSG hybrid
contracts within 24 months; (c) tie 20% of commercial segment manager
compensation to SSG attach rate in IDG accounts. (This recommendation
draws directly on six years of operational visibility in the Vietnam
Commercial Segment — the attach rate gap at the account level is real
and addressable with the right incentive structure.)

**Risk if unaddressed:** Consolidated margins plateau below 2.5%
regardless of revenue growth. A 3% margin target requires deliberate
SSG acceleration — it will not occur organically from IDG volume alone.

---

### Recommendation 3 — Protect Asset Turnover as ISG Scales

**Evidence:** Asset turnover improved from 1.47x to 1.66x (+0.19x) —
the primary Du Pont ROE driver in FY2025. ISG infrastructure contracts
require higher PP&E and longer receivables cycles. Asset turnover
compression toward 1.55x by FY2027 is the expected mechanical outcome
at ISG's current growth rate.

**Action:** Establish a capital efficiency gate for ISG investments:
any commitment above USD 50M must demonstrate projected asset-turn
contribution of ≥ 1.2x within 24 months. Prefer managed-service
contracts (recurring revenue, off-balance-sheet) over capital-sale
contracts where IRR is within 15%. Publish asset turnover by segment
quarterly to make the trade-off visible to investors.

**Risk if unaddressed:** Asset turnover reverting to 1.47x would reduce
ROE by approximately 3pp through the Du Pont mechanism, partially
erasing FY2025 efficiency gains.

---

### Recommendation 4 — Rebuild Operating Cash Flow to USD 2B+ by FY2027

**Evidence:** OCF declined 45.3% from USD 2,011M (FY2024) to USD 1,100M
(FY2025). OCF minus interest expense (USD 773M) leaves only USD 327M
before dividends (USD 608M paid) — a structural shortfall of ~USD 280M.
The current ratio of 0.93x and cash ratio of 0.16x provide minimal
balance sheet buffers.

**Action:** Target OCF restoration to USD 2,000M+ by FY2027: (a) implement
milestone-based billing on all ISG project contracts above USD 10M
(30% upfront, 40% at go-live); (b) standardise ISG payment terms at
Net-30 with 0.5% early-payment incentive; (c) require ISG procurement
to negotiate 75-day supplier terms (vs. ~60 days estimated), adding
USD 200–300M of free float. Report OCF/net income conversion ratio
quarterly as a management KPI.

**Risk if unaddressed:** If OCF does not recover and financing rates
rise, Lenovo faces a genuine liquidity event — USD 1,100M OCF is
structurally insufficient to cover interest, dividends, and growth
investment simultaneously.

---

## 9. Limitations & Methodology Notes

- **HKFRS vs. U.S. GAAP:** Peer benchmarks (Dell, HP) report under U.S.
  GAAP. Development cost capitalisation and lease treatment differ — cross-
  company ratios are directional, not precise comparisons.

- **D&A plug:** FY2025 D&A of USD 708,376 thousand was derived algebraically
  (not directly disclosed on the face of the income statement). Any error
  flows into EBIT, ROC, TIE, and EVA. Source validation against the Notes
  to the Financial Statements is recommended before citing these figures
  in a professional context.

- **NCI treatment:** Non-controlling interests (USD 590,930 thousand) were
  combined with reserves per the BUS 629 template structure. ROE is computed
  on total equity. ROE on equity attributable to Lenovo shareholders only
  (~USD 6,069M) would be approximately 1–2pp higher.

- **FY2024 TIE correction:** The LLM raw output stated FY2024 TIE of 1.40x
  using an approximate consolidated EBIT of ~USD 1,069M. Manual verification
  against the source income statement yields 2.63x. The corrected value is
  used throughout this document. See the verification table for full
  arithmetic.

- **Two-period limitation:** FY2024 was an atypically weak year (ISG
  loss-making); FY2025 was atypically strong (ISG normalisation + PC
  refresh). The comparison captures a trough-to-recovery transition that
  may overstate the sustainability of improvements observed. A five-year
  series would provide more reliable trend signals.

---

## 10. LLM Evaluation & Annotations

**What the LLM executed correctly:**

The LLM followed the spec precisely on every FY2025 ratio. All six ratio
categories were computed using the correct named-range convention. The
Du Pont decomposition produced zero variance between the three-factor
product and the direct ROE computation — a clean result that required
exact averaging conventions. The four strategic recommendations each
opened with specific ratio evidence before stating an action, exactly
as Section 9 of the spec required. The limitations section correctly
reproduced both modelling notes (D&A plug and NCI treatment) from the
spec's data inputs section. Overall, 6 of 7 ratios in the verification
table matched exactly on the first run — a strong spec execution result.

**Where the LLM deviated — one material error:**

FY2024 TIE was stated as 1.40x, derived from an approximate FY2024 EBIT
of ~USD 1,069M. This figure appears to have come from ISG segment data
or an alternative public disclosure, not from the consolidated source
income statement (operating profit: USD 2,005,784). The correct FY2024
TIE using source data is 2.63x. This error was caused by a **spec gap**
— the Stage 4 spec provided FY2025 income statement inputs explicitly
but did not include a complete FY2024 income statement section. The LLM
was forced to estimate, and it estimated incorrectly. This is documented
in the spec retrospective as Gap 1.

**Errors caused by spec gaps vs. LLM limitations:**

| Error | Cause | Type |
|-------|-------|------|
| FY2024 TIE 1.40x (correct: 2.63x) | Missing FY2024 IS in spec | Spec gap |
| EVA negative without full explanation | Anomalous tax rate not flagged | Spec gap |
| Output exceeded 1,800 word target | No per-section word limits | Spec gap |

No evidence of hallucination — every number the LLM produced was either
correct or traceable to a specific input the spec provided. The LLM did
not invent data; it estimated from incomplete inputs. This is the
meaningful distinction between a spec gap and an LLM limitation.

---

## 11. Executive Justification

*In my own voice — not the LLM's.*

I have worked inside Lenovo's Vietnam Commercial Segment for six years.
The hardware paradox this analysis surfaces is not an abstraction — I
live it operationally every quarter. We sell high volumes of IDG product
at thin margins to enterprise accounts while SSG attach rates remain
lower than they should be. The ratio analysis quantifies what I have
observed directionally: Lenovo is an extraordinarily efficient revenue
machine that has not yet converted that efficiency into durable
profitability.

The most important number in this analysis is not ROE (22.95%) or asset
turnover (1.66x). It is the SSG operating margin (21.1%) sitting inside
a consolidated net margin of 2.12%. That gap — between what the
services business earns and what the consolidated entity reports — is
the entire strategic story. Every percentage point of revenue mix shift
from IDG to SSG adds approximately 0.19 percentage points to
consolidated operating margin. At current leverage, that translates
to approximately 1.2 percentage points of ROE improvement per point
of mix shift.

The four recommendations in this analysis are not generic prescriptions
— they are the levers I would pull if I were advising the commercial
leadership team in Vietnam: tie manager compensation to SSG attach rate,
implement milestone billing on ISG projects, ring-fence capital for ISG
investments, and prioritise TIE improvement over new convertible
issuance. These are actions that a commercial professional with six
years of Lenovo operational context would recognise as both analytically
justified and practically executable.

The LLM produced a technically competent first draft. The judgment —
what to correct, what to emphasise, what to connect to operational
reality — is mine.
