# Prompt Log — BUS 629 Corporate Finance Project
**Author:** Nguyen Khong Thanh Thao
**Company:** Lenovo Group Limited (HKSE: 992)
**Last updated:** 2026-05-23

---

## Purpose

This log records every meaningful AI-assisted prompt used across the BUS 629
project stages. Per course requirements, any prompt longer than two lines is
logged here with context, the prompt itself, what the model produced, and
what I accepted, rejected, or revised. This is the evidence trail for Stage 5
grading.

---

## Stage 2 — Company Selection Memo

### Session 1 — Memo drafting
**Date:** 2026-05-23
**Tool:** Claude (claude.ai)
**Context:** Drafting the Stage 2 company selection memo for Lenovo Group
using the instructor's memo template.

**Prompt summary:**
> I'm drafting a Stage 2 company selection memo for BUS 629. My company is
> Lenovo Group Limited (HKSE: 992). I work at Lenovo Vietnam and have 6 years
> of direct commercial experience. Draft a memo following the instructor's
> template structure with all six required sections. Hypotheses must be in
> "I expect X because Y" form. Audience is a managing director.

**What the model produced:** Full 143-line memo covering all six required
sections with three falsifiable hypotheses grounded in publicly available
FY2024/25 results data.

**What I accepted:** Structure, hypothesis framing, data source identification.

**What I revised:** Verified all financial figures cited (revenue $69.1B,
net income +36%, SSG margin 21.1%) against the Lenovo investor relations
press release before committing. Confirmed HKFRS vs GAAP note was accurate.

**Committed as:** `docs/decisions/2026-05-23-nguyen-lenovo-selection.md`

---

## Stage 3 — Financial Model Population

### Session 2 — Data extraction and model population
**Date:** 2026-05-23
**Tool:** Claude Code (CLI, running in repo directory)
**Context:** Populating the BUS 629 ratios template with Lenovo FY2025 and
FY2024 financials from three XLS source files downloaded from
investor.lenovo.com.

**Prompt summary:**
> Read income_statement.xls, balance_sheet.xls, and cash_flow.xls from
> the data/ folder. Extract FY2025 and FY2024 figures. Populate all named
> ranges in models/builds/2026-05-23-nguyen-lenovo-financials.xlsx. Verify
> balance sheet ties (Assets = L+E) both years. Check Ratios tab for errors.
> Do not modify any formulas.

**What the model produced:** 30 named ranges populated at 100% success rate.
Balance sheet tied exactly both years (FY2025: 44,230,812; FY2024:
38,750,954). Zero formula errors on Ratios tab. Key ratios computed: ROA
5.79%, ROE 24.04%, M/B 2.02x, TIE 2.73x.

**Two modelling judgements the model flagged (accepted after review):**

1. **D&A plug (USD 708,376 thousand):** Lenovo does not disclose D&A as a
   separate income statement line under HKFRS. The model derived a plug
   algebraically so that EBIT and Operating CF both tie to source figures.
   I verified this is consistent with the HKFRS disclosure approach — D&A
   is embedded in COGS and SG&A. Accepted and documented in
   `analysis/stage3-modelling-notes.md`.

2. **NCI combined into retained earnings:** The template has no NCI row.
   Non-controlling interests (FY2025: USD 590,930 thousand) were absorbed
   into `BAL_retained_earnings_*` so the balance sheet ties. This means
   ROE is computed on a total equity basis. Accepted — noted in spec Section 3.

**What I rejected:** The model initially entered shares_outstanding as
12,200 (millions) rather than 12,200,000 (thousands), causing a unit
mismatch that produced a nonsensical M/B ratio of 0.002x. I identified this
error, understood the unit convention mismatch, and directed the correction.
The corrected M/B of 2.02x is economically sensible for a large-cap
technology company.

**Committed as:** `models/builds/2026-05-23-nguyen-lenovo-financials.xlsx`

---

## Stage 4 — Technical Specification

### Session 3 — Spec drafting (v1.0)
**Date:** 2026-05-23
**Tool:** Claude (claude.ai)
**Context:** Drafting the Stage 4 technical specification using the
instructor's spec template and all verified Stage 3 financial data.

**Prompt summary:**
> Using the instructor's spec-template.md and all verified Lenovo FY2025
> and FY2024 figures from Stage 3, draft a complete 11-section technical
> specification. Include all named ranges, all ratio formulas in named-range
> notation, Du Pont decomposition, validation rules, and analysis requirements.
> All input values must be explicit — the executor should not need to look
> anything up.

**What the model produced:** Full 430-line spec (v1.0) covering all 11
required sections with named-range formulas for 17 ratios across six
categories, explicit data input tables with all financial values, validation
rules with expected outputs, and analysis requirements with peer benchmarks.

---

### Session 4 — HIL Review and Spec Revision (v1.0 → v1.1)
**Date:** 2026-05-23
**Tool:** Claude (claude.ai) + my own review
**Context:** Human-in-the-loop review pass on the v1.0 spec before committing.

**My review process:** I read through the v1.0 spec systematically, checking
each section against the rubric criteria: (1) are all inputs explicit with
no gaps an executor would have to fill by inference? (2) are all formulas
in exact named-range notation? (3) would the analysis requirements produce
the output the instructor expects?

**Three gaps I identified:**

**Gap 1 — EVA formula incomplete (Section 6, Performance Ratios):**
The EVA formula referenced WACC but WACC was not defined anywhere in the
spec. An executor — human or LLM — running this spec at Stage 5 would be
unable to compute EVA without WACC. This violates the spec's own standard:
"the executor does not look up, infer, or estimate any data."

*Revision made:* Added WACC estimate of 8.5% derived via CAPM (risk-free
rate 4.3% + beta 0.85 × equity risk premium 5.0% = 8.55%, rounded to 8.5%).
Added estimated EVA output value (~USD 478,000 thousand) for verification.

**Gap 2 — FY2024 Du Pont values were approximations, not formulas
(Section 8):**
The v1.0 spec showed FY2024 Du Pont components as "~1.94%", "~1.58x" —
approximate estimates with tildes. A technical specification must be precise.
The prior-year named ranges exist in the template and should have been used.

*Revision made:* Replaced all approximate FY2024 values with exact
named-range formulas (`INC_net_prior / INC_sales_prior` etc.) and computed
exact outputs. Also corrected the asset turnover figure — v1.0 showed ~1.58x
for FY2024 but the correct value using named-range inputs is 1.47x. This was
a material error that would have produced an incorrect Du Pont driver
conclusion (turnover improvement was +0.31x, not +0.20x as v1.0 showed —
asset turnover is the primary ROE driver, not a secondary one).

**Gap 3 — DSO and DIO formulas missing (Section 6, Efficiency Ratios):**
Section 7 (Analysis Requirements) instructed the executor to "calculate days
receivables and days inventory outstanding explicitly" but Section 6 contained
no formulas for DSO or DIO. The executor would have had to derive the formula
independently — inconsistent with the spec standard.

*Revision made:* Added explicit DSO and DIO rows to the Efficiency Ratios
table with named-range formulas and expected day-count outputs (DSO: 49.3
days, DIO: 42.2 days).

**Version bumped:** 1.0 → 1.1 after all three revisions confirmed correct.

---

## Notes for Stage 5

- The D&A plug (USD 708,376 thousand) should be validated against the D&A
  disclosure in the FY2025 Annual Report notes before Stage 5 analysis.
- WACC of 8.5% is an estimate. If a more precise WACC is available from
  analyst reports or course materials, update the EVA computation accordingly.
- All ratio outputs in this log reflect HKFRS basis. Peer comparisons
  (Dell, HP) use US GAAP — note standard differences when interpreting gaps.
