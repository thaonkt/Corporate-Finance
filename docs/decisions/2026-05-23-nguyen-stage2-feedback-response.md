---
stage: 5
type: feedback-response
author: Nguyen Khong Thanh Thao
date: 2026-05-23
re: Response to instructor Stage 2 feedback on company selection memo
original_memo: docs/decisions/2026-05-23-nguyen-lenovo-selection.md
course: BUS-629
---

# Stage 2 Feedback Response Memo

**To:** Adam Stauffer, Instructor, BUS 629 VEMBA
**From:** Nguyen Khong Thanh Thao
**Date:** 2026-05-23
**Re:** Response to Stage 2 feedback — Lenovo Group company selection memo

---

## Summary

This memo documents how I incorporated the instructor's Stage 2 feedback
into the revised memo and into the subsequent stages of the project. Six
specific feedback points were received. All six have been addressed.

---

## Feedback Point 1 — Fill in YAML frontmatter with real data

**Feedback:** Replace template instructions with actual values for stage,
author, date, company, ticker, exchange, course, to, from, re.

**Action taken:** YAML frontmatter fully replaced in v2 of the memo.
All fields populated with project-specific values. Committed at
`docs/decisions/2026-05-23-nguyen-lenovo-selection.md`.

---

## Feedback Point 2 — Tighten word count from ~804 to under 600

**Feedback:** Background section's segment descriptions could be condensed
into a 2-sentence overview with a table.

**Action taken:** Background section restructured into a summary table
covering ticker, exchange, industry, market cap, currency, reporting
standard, fiscal year end, and FY2025 revenue. Segment descriptions
compressed from three paragraphs to two sentences. Final prose word
count brought under 600 words.

---

## Feedback Point 3 — Rename section headings to match spec's six numbered sections

**Feedback:** Content maps cleanly to the spec structure — headings should
reflect it.

**Action taken:** All section headings renumbered and renamed to match
the six required sections exactly: 1. Executive Summary, 2. Company
Overview, 3. Selection Rationale, 4. Data Availability & Sources,
5. Preliminary Observations, 6. Ratio Categories Preview & Data
Collection Plan.

---

## Feedback Point 4 — Add access dates to source citations

**Feedback:** Primary filings are always the stronger source for an
analyst memo.

**Action taken:** Access date "Accessed 2026-05-23" added to all three
references. Simply Wall St removed entirely — replaced with HKEX filing
portal as the primary market data source.

---

## Feedback Point 5 — The "classic technology hardware paradox" synthesis is excellent

**Feedback:** Carry this through to Stage 5 where it becomes the analytical
backbone of recommendations. The direct parallel to the Vietnam commercial
segment evaluation framework makes it genuinely dual-purpose.

**Action taken:** The hardware paradox framing was carried through
explicitly into every subsequent stage:
- Stage 4 spec (Section 7): named as the cross-category analytical thread
- Stage 5 final analysis (Executive Summary): stated as the analytical
  backbone in the opening paragraph
- Stage 5 recommendations (Rec 2): directly connected to SSG attach rate
  in the Vietnam Commercial Segment — the operational manifestation of
  the paradox

---

## Feedback Point 6 — Consider citing HKEX filing rather than Simply Wall St

**Feedback:** Primary filings are always the stronger source for an
analyst memo.

**Action taken:** Simply Wall St removed from all references across the
project. HKEX disclosure portal (hkexnews.hk) is now the primary market
data source in the memo, the spec, and the final analysis. All share
price and shares outstanding data traced to HKEX filings, not aggregator
sites.

---

## Carry-Forward Impact

The feedback improvements at Stage 2 had a measurable effect on later
stages. The tighter memo structure became the model for the Stage 4 spec's
analysis requirements — concise, evidence-tight, section-structured. The
hardware paradox framing gave the Stage 5 final analysis a coherent
analytical backbone that the raw LLM output lacked before my editorial
pass. The source discipline (primary filings over aggregators) was applied
consistently from Stage 3 onward — all financial data sourced directly
from investor.lenovo.com and HKEX, not from secondary sources.
