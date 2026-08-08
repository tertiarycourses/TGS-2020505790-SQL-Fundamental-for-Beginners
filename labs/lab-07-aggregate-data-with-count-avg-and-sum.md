# Lab 7 — Aggregate Data with COUNT, AVG and SUM

**Topic 03 — Data Transformation** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO3 — transform data with aggregate functions (A4, A6).

**Goal:** Summarise the world database with COUNT, AVG and SUM: count rows, average populations, total populations, and combine aggregates with DISTINCT and WHERE for real analytical questions.

**You'll build:** A summary report of world statistics — city counts, average and total populations, and filtered aggregate answers.

**Tools:** SQLite Studio, world database

![Lab 7 — SQL editor](../figures/lab-07.png)

*Figure 7 — the SQL editor after running this lab's key statement.*

## Steps

1. Count the rows in City.

   ```sql
   SELECT COUNT(CountryCode) FROM City;
   ```

2. Average a numeric column — the mean population of a country.

   ```sql
   SELECT AVG(Population) FROM Country;
   ```

3. Total a numeric column — the world's population.

   ```sql
   SELECT SUM(Population) FROM Country;
   ```

4. Answer: how many distinct heads of state are there?

   ```sql
   SELECT COUNT(DISTINCT HeadOfState) FROM Country;
   ```

5. Answer: how many countries in Europe have a population above 100,000,000?

   ```sql
   SELECT COUNT(*) FROM Country
   WHERE Continent = 'Europe'
     AND Population > 100000000;
   ```


## Test it

Each aggregate returns a single-value result-set; the distinct head-of-state count is smaller than the country count, and the Europe query returns a small whole number.
