# Lab 9 — Group Data with GROUP BY and HAVING

**Topic 03 — Data Transformation** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO3 — transform data by grouping and filtering groups (A4, A6).

**Goal:** Aggregate per group: average city population by country code with GROUP BY, then keep only the populous groups with HAVING — and see why HAVING exists where WHERE cannot go.

**You'll build:** Grouped summaries of the world data — per-country averages, filtered to the groups that matter.

**Tools:** SQLite Studio, world database

![Lab 9 — SQL editor](../figures/lab-09.png)

*Figure 9 — the SQL editor after running this lab's key statement.*

## Steps

1. Retrieve the average city population grouped by country code.

   ```sql
   SELECT CountryCode, AVG(Population)
   FROM City
   GROUP BY CountryCode;
   ```

2. Add a readable alias and order the summary, largest first.

   ```sql
   SELECT CountryCode,
          AVG(Population) AS AvgPop
   FROM City
   GROUP BY CountryCode
   ORDER BY AvgPop DESC;
   ```

3. Keep only groups whose average exceeds 1,000,000 — WHERE cannot filter aggregates, HAVING can.

   ```sql
   SELECT CountryCode, AVG(Population) AS AvgPop
   FROM City
   GROUP BY CountryCode
   HAVING AVG(Population) > 1000000
   ORDER BY AvgPop DESC;
   ```

4. Combine everything: count cities per country, but only for countries with more than 50 recorded cities.

   ```sql
   SELECT CountryCode, COUNT(*) AS Cities
   FROM City
   GROUP BY CountryCode
   HAVING COUNT(*) > 50
   ORDER BY Cities DESC;
   ```


## Test it

The GROUP BY query returns one row per country code; the HAVING queries return only the qualifying groups (every AvgPop > 1,000,000; every Cities > 50), sorted descending.
