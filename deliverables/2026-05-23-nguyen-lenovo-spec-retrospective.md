---
template: spec-retrospective
stage: 5
author: Nguyen Khong Thanh Thao
date: 2026-05-23
company: Lenovo Group Limited
ticker: 992.HK
course: BUS-629
spec_version: 1.1
spec_file: docs/specs/2026-05-23-nguyen-lenovo-spec.md
---

# Spec Retrospective — Lenovo Group Limited Ratio Analysis

**Author:** Nguyen Khong Thanh Thao
**Date:** 2026-05-23
**Spec evaluated:** `docs/specs/2026-05-23-nguyen-lenovo-spec.md` (v1.1)
**LLM evaluated:** Raw output at
`deliverables/2026-05-23-nguyen-lenovo-llm-raw.md`
**Verification table:** 
`analysis/validation/2026-05-23-nguyen-lenovo-stage5-verification.md`

---

## Overview

This retrospective evaluates how well the Stage 4 specification performed
when executed by an LLM with no additional context beyond the spec itself.
It covers four questions: what the spec got right, what gaps caused LLM
errors, what I would change in a revision, and what I learned about
spec-driven analytical work.

---

## Part A — What the Spec Got Right

### 1. Data inputs were explicit and complete

Section 3 of the spec provided every financial figure numerically, in
named-range notation, with units clearly stated (USD thousands). The LLM
did not infer, estimate, or hallucinate any input values. Every balance
sheet figure, income statement line, and cash flow total matched the
source exactly. This is the most important thing a spec can do — and it
worked.

**Evidence:** 6 of 7 ratios in the verification table matched exactly.
The one error (FY2024 TIE) was caused by the spec's FY2024 data gap,
not by input ambiguity.

### 2. Named-range convention produced clean formula execution

The decision to express every formula in named-range notation
(`INC_net / avg_assets` rather than `cell B12 / cell F4`) meant the LLM
could follow the formula logic without needing to understand the workbook
structure. Every ratio formula in Section 6 was executed correctly.

### 3. Du Pont specification was precise after HIL revision

The v1.0 spec had approximate FY2024 Du Pont values with tildes (~).
The HIL revision replaced these with exact named-range formulas. The LLM
produced a Du Pont table with zero variance between Du Pont and direct
ROE — a clean result that would not have been achievable from the v1.0
spec.

### 4. Analysis requirements produced structured, evidence-backed output

Section 7 specified that every recommendation must cite a ratio value and
a year-on-year trend. The LLM followed this instruction for all four
recommendations — each one opened with evidence before stating an action.
The output reads like a senior analyst memo, not a generic AI summary.

### 5. Modelling notes were picked up and disclosed

Notes 1 and 2 in Section 3 (D&A plug, NCI treatment) were reproduced
accurately in the LLM's limitations section. The LLM correctly flagged
these as methodological constraints rather than errors — exactly the
treatment I intended.

---

## Part B — Gaps That Caused Errors or Weak Output

### Gap 1 — FY2024 EBIT was not explicitly stated in the spec
**Severity: High — produced a material error**

The spec provided all FY2025 income statement inputs explicitly. For
FY2024, the spec provided prior-year balance sheet figures (`BAL_*_prior`)
but did not provide a complete prior-year income statement. Specifically,
FY2024 EBIT was not stated as a named-range input.

When computing FY2024 TIE, the LLM had to derive FY2024 EBIT from
partial information. It appears to have used ISG segment data or an
alternative derivation (~USD 1,069M) rather than the source consolidated
operating profit (USD 2,005,784). This produced FY2024 TIE of 1.40x
versus the correct 2.63x — a 47% understatement.

**What I would change:** Add a complete FY2024 income statement section
to the data inputs table, mirroring the FY2025 structure exactly. Every
ratio that requires a prior-year income statement figure needs an explicit
prior-year named range — not just the balance sheet prior-year data.

**Lesson:** A spec that provides current-year income data and prior-year
balance sheet data but not prior-year income data creates an asymmetry
that forces the LLM to estimate. Any estimation in a spec is a spec gap.

---

### Gap 2 — EVA computation was underspecified for the LLM
**Severity: Medium — produced a negative EVA without full explanation**

Section 6 specified EVA as:
`INC_ebit * (1 - tax_rate) - (WACC * BAL_assets_total_current)`

The WACC of 8.5% was provided (fixed in HIL revision v1.1). However,
the spec did not specify what NOPAT (Net Operating Profit After Tax)
should use as the tax rate denominator — whether to use the effective
tax rate (1.28%, effectively zero) or a normalised rate. The LLM used
the effective rate, producing NOPAT ≈ EBIT, which then generated a
deeply negative EVA (~−USD 1.6B) that required a lengthy note to explain.

**What I would change:** Specify in the EVA formula note that the effective
tax rate for Lenovo FY2025 (1.28%) is anomalously low due to deferred
tax asset utilisation, and instruct the executor to use a normalised rate
of 17% (Hong Kong corporate tax rate) for EVA computation. This would
produce a more economically meaningful EVA figure without requiring
the LLM to make a judgement call.

**Lesson:** Formula specifications must anticipate edge cases in the
underlying data — an anomalous tax rate is exactly the kind of edge case
that turns a clean formula into a confusing output.

---

### Gap 3 — Section 7 analysis requirements were strong but peer benchmarks
were one-sided
**Severity: Low — produced good output but missed an opportunity**

Section 7 instructed the LLM to benchmark against Dell (~8% ROA, ~3.5x
M/B) and HP (~10% ROA, ~5.0x M/B). The LLM followed this correctly.
However, the spec did not instruct the LLM to explain *why* the structural
gap exists — it only said "explain structural differences."

The LLM correctly attributed the ROA gap to Lenovo's supply chain model,
but it did not connect this to the broader question of whether the gap
is *closing* over time — which is the more strategically useful question
for a company in the middle of a business model transition.

**What I would change:** Add a specific instruction in Section 7:
"For each peer benchmark gap, state whether the gap is widening,
stable, or narrowing based on the FY2024→FY2025 trend, and what the
trend implies for Lenovo's competitive positioning over three years."
This turns a static benchmark comparison into a dynamic strategic question.

---

### Gap 4 — Output format specification could have been tighter on length
**Severity: Low — output was good but long**

Section 10 specified 1,200–1,800 words excluding ratio tables. The LLM
produced approximately 2,800 words including all tables and notes. The
output was high quality but exceeded the target length, which in a
professional context would require editing before distribution.

**What I would change:** Add a per-section word target: Executive Summary
150–200 words, each ratio section 150–250 words, recommendations 100–150
words each. Giving the LLM section-level constraints produces more
disciplined output than a document-level total.

---

## Part C — Overall Verdict

| Dimension | Grade | Evidence |
|-----------|-------|---------|
| Data inputs — completeness | Strong | 6/7 ratios exact; only gap was missing FY2024 IS |
| Formula specification | Strong | All 17 ratios executed correctly in FY2025 |
| Analysis requirements | Good | 4 recs with evidence; peer benchmarks used |
| Output format | Adequate | Correct structure; exceeded length target |
| HIL revision value | High | v1.1 fixes (WACC, Du Pont precision, DSO/DIO) all used by LLM |

**Overall:** The spec performed well for a first production run. The
single material error (FY2024 TIE) is a direct consequence of an
identified and fixable gap. The HIL revision at Stage 4 demonstrably
improved output quality — the LLM's Du Pont table was exact, DSO and
DIO were computed correctly, and EVA had a WACC to work with. A v1.2
spec incorporating the four gaps above would likely produce a fully
clean output on the first run.

---

## Part D — What I Learned About Spec-Driven Work

Three durable lessons from this exercise:

**1. Completeness symmetry matters more than completeness itself.**
The spec was complete for FY2025. It was incomplete for FY2024 in one
specific dimension (income statement). That asymmetry — not the overall
completeness level — caused the only material error. In professional
spec writing, every data dimension must be symmetric across time periods,
segments, and scenarios. A spec that is 95% complete in a non-symmetric
way will produce errors in exactly the 5% gap.

**2. The executor will make a decision at every ambiguity — and you will
not know which decision it made until you verify.**
The LLM did not flag that it was using an approximate FY2024 EBIT. It
simply used one. The output looked clean. Without the manual verification
table, I would not have caught the TIE error. This is why the verification
step is not optional — it is the only feedback mechanism that closes the
spec-execution loop. In any real analytical workflow using AI, verification
is where the analyst earns their value.

**3. A spec that worked once is a first draft.**
The v1.1 spec produced a strong first run. A v1.2 spec — with the four
gaps above addressed — would produce a cleaner run with less post-
execution editing required. In a professional context where this analysis
would be re-run quarterly against updated financials, investing in spec
quality compounds: each improvement eliminates a recurring manual
correction. The four fixes above would save approximately 90 minutes of
verification and correction work per quarter.
