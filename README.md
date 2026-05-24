# Nguyen Khong Thanh Thao — Corporate Finance Portfolio

**Program:** BUS-629 VEMBA | University of Hawaiʻi at Mānoa, Shidler College of Business
**Instructor:** Adam Stauffer
**Company analyzed:** Lenovo Group Limited (HKSE: 992)

---

## What You Will Find Here

This repository is a complete corporate finance portfolio built across five
stages. It contains a company selection memo, a populated three-statement
financial model, a technical specification for LLM-assisted ratio analysis,
and a fully evaluated final analysis of Lenovo Group's FY2025 financials.
The analytical thread running through every stage is the **classic technology
hardware paradox**: Lenovo generates USD 69.1B in revenue on USD 44.2B of
assets (1.66x turnover) yet produces only 2.12% net margin — high efficiency
masking thin capital returns. The work here documents how that paradox was
specified, modelled, executed by an LLM, verified manually, and translated
into four actionable strategic recommendations.

Every artifact is version-controlled with descriptive commit messages. All
AI-assisted sessions are logged in `deliverables/prompt-log.md`. The repo
is structured to be navigable by a manager, auditor, or collaborator with
no prior context — start with this README, then follow the stage links below.

---

## Project Status — All Five Stages Complete

| Stage | Description | Key File | Commit |
|-------|-------------|----------|--------|
| **Stage 0** | Repo setup, bio, resume, directory skeleton | `README.md`, `RESUME.md`, `BIO.md` | `251ccd8` |
| **Stage 1** | Provided ratios template uploaded | `models/templates/performance-ratios-template.xlsx` | `a64c091` |
| **Stage 2** | Company selection memo — Lenovo Group (HKSE: 992) | `docs/decisions/2026-05-23-nguyen-lenovo-selection.md` | `acc5397` |
| **Stage 3** | Populated FY2025 + FY2024 financials; balance sheet ties both years | `models/builds/2026-05-23-nguyen-lenovo-financials.xlsx` | `6ab46fb` |
| **Stage 4** | Technical specification v1.1 (HIL-revised) | `docs/specs/2026-05-23-nguyen-lenovo-spec.md` | `d89f419` |
| **Stage 5** | LLM analysis executed, verified, corrected, and evaluated | `deliverables/2026-05-23-nguyen-lenovo-final-analysis.md` | `b3db9b9` |

---

## Key Findings — Lenovo Group FY2025

| Ratio | FY2024 | FY2025 | Verdict |
|-------|--------|--------|---------|
| Net Profit Margin | 1.94% | 2.12% | Improving but structurally thin |
| ROA | 2.84% | 3.52% | Below Dell ~8%, HP ~10% |
| ROE | 18.12% | 22.95% | Leverage-driven — fragile |
| Asset Turnover | 1.47x | 1.66x | Primary Du Pont driver |
| TIE | 2.63x | 2.80x | Below 3.0x comfort threshold |
| Current Ratio | 0.87x | 0.93x | Intentional NWC model |
| M/B | — | 2.02x | Below Dell 3.5x, HP 5.0x |

---

## Repository Structure

```
Corporate-Finance/
├── README.md               ← You are here
├── RESUME.md               ← Professional resume
├── BIO.md                  ← Extended bio
├── LICENSE                 ← MIT
├── .gitignore
├── docs/
│   ├── decisions/          ← Stage 2 memo + feedback response
│   ├── specs/              ← Stage 4 technical specification
│   ├── plans/
│   └── templates/
├── models/
│   ├── templates/          ← Stage 1 unmodified template
│   └── builds/             ← Stage 3 populated financials
├── data/                   ← Source XLS files from investor.lenovo.com
├── analysis/
│   ├── stage3-modelling-notes.md
│   └── validation/         ← Stage 5 manual verification table
└── deliverables/
    ├── prompt-log.md       ← All AI sessions logged
    ├── *-llm-raw.md        ← Stage 5 unedited LLM output
    ├── *-final-analysis.md ← Stage 5 corrected final analysis
    └── *-spec-retrospective.md ← Stage 5 spec evaluation
```

---

## About Me

I am a six-year Lenovo Vietnam commercial professional currently pursuing
my MBA at the Shidler College of Business, University of Hawaiʻi at Mānoa.
My work focuses on B2B technology sales and commercial strategy in the
ASEAN market. This portfolio reflects both the analytical skills developed
in BUS-629 and the operational context I bring as an insider in the company
I analyzed.

→ Full bio: [BIO.md](BIO.md)
→ Resume: [RESUME.md](RESUME.md)
