# SQL Fundamental for Beginners — WSQ Courseware

**WSQ Course Code:** TGS-2020505790
**Conducted by:** Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
**Trainer:** Dr. Alfred Ang
**Duration:** 1 day · 8 training hours (9:30 am – 6:30 pm, 1-hour lunch)
**Skills Framework:** Data Engineering — ICT-DIT-3005-1.1 (ICT Skills Framework)
**Version:** v14 · 11 August 2026
**Course page:** https://www.tertiarycourses.com.sg/wsq-sql-fundamental-for-beginners.html

A hands-on introduction to SQL: model data, query and analyse it, transform it across
multiple tables, and map it into a data warehouse — all in SQLite Studio against the
**SG Mart** sample database, a fictitious Singapore retail chain supplied with the course.

## Contents

| Artifact | Path |
|---|---|
| Trainer slide deck (132 slides) | [courseware/SQL Fundamental for Beginners-v14.pptx](courseware/SQL%20Fundamental%20for%20Beginners-v14.pptx) |
| Learner slides (PDF) | [courseware/SQL Fundamental for Beginners-v14.pdf](courseware/SQL%20Fundamental%20for%20Beginners-v14.pdf) |
| Lesson Plan | [courseware/LP-SQL Fundamental for Beginners.docx](courseware/LP-SQL%20Fundamental%20for%20Beginners.docx) · [PDF](courseware/LP-SQL%20Fundamental%20for%20Beginners.pdf) |
| Learner Guide | [courseware/LG-SQL Fundamental for Beginners.docx](courseware/LG-SQL%20Fundamental%20for%20Beginners.docx) · [PDF](courseware/LG-SQL%20Fundamental%20for%20Beginners.pdf) |
| Learner Guide (Markdown mirror) | [LG-SQL Fundamental for Beginners.md](LG-SQL%20Fundamental%20for%20Beginners.md) |
| Hands-on labs (11) | [labs/](labs/) — see [labs/README.md](labs/README.md) |
| Mock datasets | inside each lab's own folder — CSV + SQL seeds; full set in [labs/_all/](labs/_all/) (Excel workbook + prebuilt `sgmart.db`) |

The slide deck is **visual only** — every detailed step-by-step procedure lives in the
Learner Guide and the `labs/` files, by design.

## Learning outcomes

- **LO1** — Apply data modeling for business processes.
- **LO2** — Apply data processing and analysis using SQL.
- **LO3** — Apply data transformation from multiple data sources.
- **LO4** — Apply data mapping to data warehouse.

## Topics and labs

| Topic | TSC mapping | Labs |
|---|---|---|
| 1 · Data Modeling | A1, A2, K1, K2 | 1 — SQLite Studio setup · 2 — Create a database and tables · 3 — Constraints and keys |
| 2 · Data Processing and Analysis | A3, A5, K4 | 4 — Query with SELECT · 5 — SQL operators · 6 — Insert, update, delete |
| 3 · Data Transformation | A4, A6, K5, K6 | 7 — Aggregate functions · 8 — Joins · 9 — GROUP BY and HAVING |
| 4 · Introduction to Data Warehouse | A7, A8, A9, K3, K7 | 10 — Map an E-R model (SMRT case study) · 11 — Stored procedures |

## Tools

- **SQLite Studio** — https://sqlitestudio.pl (free, cross-platform)
- **sqliteonline.com** — browser alternative, also provides an MS SQL engine for Lab 11
- **SG Mart mock dataset** — each lab folder under [labs/](labs/) carries its own CSVs and seed scripts beside the instructions; the complete set, with an Excel workbook and a prebuilt `sgmart.db`, is in [labs/_all/](labs/_all/). Also downloadable from the LMS with the course materials.

## The course dataset — SG Mart Pte Ltd

Every lab queries one continuous business story: **SG Mart Pte Ltd**, a fictitious
Singapore retail chain with 8 outlets, 42 staff, 60 loyalty members, 9 suppliers,
25 products, 180 orders and 685 order lines. Topic 4 switches to an **SMRT**
public-transport model (routes, stations, timetables, disruptions) for the
data-warehouse case study.

**Each lab is one self-contained folder** under [labs/](labs/) holding the instructions,
the data and the SQL together — `lab-NN-<slug>.md`, only the tables that lab needs as CSV
(Excel-friendly), and `seed_sqlite.sql` / `seed_mysql.sql` that create and fill everything
in one execution. Open the folder, run the seed script, follow the markdown. The complete
set, including `SG-Mart-Mock-Data.xlsx` and a prebuilt `sgmart.db`, is in
[labs/_all/](labs/_all/).

Some columns are deliberately empty (walk-in orders with no member, staff without a work
email, products without a reorder level) so `IS NULL`, `LEFT JOIN` and `COUNT()` behave
the way they do on real data. All data is invented for training and identifies no real
person or organisation.

The original sample databases from earlier versions of the course (`world.db`, `album.db`
and their SQL scripts) are kept in [labs/legacy-datasets/](labs/legacy-datasets/).

## Assessment

Final assessment is **Practical Performance (PP, 70 minutes, open book)** followed by
**Oral Questioning (OQ, 20 minutes, one-to-one)**. A minimum 75% attendance and a result
of *Competent* are required for funding eligibility.

> Assessment papers and answer keys are **confidential** and are distributed via Google
> Drive and the LMS only — they are deliberately **not** in this repository.

## Course materials and attendance

Learners download the slides, Learner Guide and the course datasets from the LMS/TMS portal at
**https://lms-tms.tertiaryinfotech.com**, where the mandatory TRAQOM feedback survey and
e-certificate also live. AM, PM and Assessment digital attendance is mandatory for
WSQ-funded courses.

## Rebuilding the courseware

Every artifact is generated from one source of truth
(`.claude/skills/courseware-build/build/course_data.py` + `data_domain1..4.py`), so the
deck, Lesson Plan, Learner Guide and labs can never drift apart:

```bash
bash .claude/skills/courseware-build/build/build_courseware.sh
```

This regenerates the lab figures, the lab files, the PPT, the LP and the LG (DOCX +
Markdown), renders every PDF, and injects the page-numbered tables of contents.

---

© 2026 Tertiary Infotech Academy Pte Ltd. All rights reserved.
