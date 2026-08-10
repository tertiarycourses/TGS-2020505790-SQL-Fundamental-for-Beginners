# Lab 7 — Aggregate Data with COUNT, AVG and SUM: Mock Data

**SQL Fundamental for Beginners** (TGS-2020505790) · v13 · Tertiary Infotech Academy Pte Ltd

Fictitious data for classroom use. **SG Mart Pte Ltd** is an invented Singapore retail chain; all names, phone numbers, emails and badge numbers are made up and do not identify any real person or company.

## Tables in this folder

| Table | Rows | CSV | What it holds |
|---|---:|---|---|
| `Products` | 25 | [Products.csv](Products.csv) | 25 SKUs with cost, retail price, category, supplier and reorder level (some NULL). |
| `Orders` | 180 | [Orders.csv](Orders.csv) | 180 sales orders across 2025 — outlet, member (NULL for walk-ins), cashier, channel, payment and status. |
| `OrderItems` | 685 | [OrderItems.csv](OrderItems.csv) | Order lines (the fact table) — quantity, unit price, discount and line total. Makes SUM/AVG/GROUP BY meaningful. |

## How to load

**Option A — run the seed script (fastest).** Open `seed_sqlite.sql` in the SQLite Studio SQL editor (or paste it into <https://sqliteonline.com>) and execute the whole script. It drops, creates and fills every table above. Use `seed_mysql.sql` instead if you are on MySQL or SQL Server.

**Option B — import the CSVs.** In SQLite Studio use *Tools → Import*, pick the CSV, tick *First line represents CSV column names*, and choose the target table. The CSVs open directly in Excel too (UTF-8).

**Option C — use the prebuilt database.** `../_all/sgmart.db` already contains every table for the whole course; just add it in SQLite Studio and connect.

## Note on NULLs

Some columns are deliberately left empty (staff emails, customer birth years, product reorder levels, walk-in orders with no member). That is intentional — it is what makes `IS NULL`, `LEFT JOIN` and `COUNT()` behave interestingly.
