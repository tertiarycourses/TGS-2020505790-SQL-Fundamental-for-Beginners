# Lab 10 — Map an E-R Model to Database Tables (SMRT Case Study): Mock Data

**SQL Fundamental for Beginners** (TGS-2020505790) · v13 · Tertiary Infotech Academy Pte Ltd

Fictitious data for classroom use. **SG Mart Pte Ltd** is an invented Singapore retail chain; all names, phone numbers, emails and badge numbers are made up and do not identify any real person or company.

## Tables in this folder

| Table | Rows | CSV | What it holds |
|---|---:|---|---|
| `Routes` | 8 | [Routes.csv](Routes.csv) | 8 SMRT routes (6 MRT lines + 2 bus services) — the parent entity of the transport E-R model. |
| `Stations` | 14 | [Stations.csv](Stations.csv) | 14 MRT stations with line position, interchange flag and opening date. |
| `Timetables` | 42 | [Timetables.csv](Timetables.csv) | 42 timetable rows — first/last trip and frequency per station for weekday, Saturday and Sunday/PH. |
| `DisruptedRoutes` | 6 | [DisruptedRoutes.csv](DisruptedRoutes.csv) | 6 service disruptions in 2025 — type, details, start time, duration and the alternative arrangements offered. |

## How to load

**Option A — run the seed script (fastest).** Open `seed_sqlite.sql` in the SQLite Studio SQL editor (or paste it into <https://sqliteonline.com>) and execute the whole script. It drops, creates and fills every table above. Use `seed_mysql.sql` instead if you are on MySQL or SQL Server.

**Option B — import the CSVs.** In SQLite Studio use *Tools → Import*, pick the CSV, tick *First line represents CSV column names*, and choose the target table. The CSVs open directly in Excel too (UTF-8).

**Option C — use the prebuilt database.** `../_all/sgmart.db` already contains every table for the whole course; just add it in SQLite Studio and connect.

## Note on NULLs

Some columns are deliberately left empty (staff emails, customer birth years, product reorder levels, walk-in orders with no member). That is intentional — it is what makes `IS NULL`, `LEFT JOIN` and `COUNT()` behave interestingly.
