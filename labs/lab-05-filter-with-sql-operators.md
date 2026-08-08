# Lab 5 — Filter with SQL Operators

**Topic 02 — Data Processing and Analysis** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO2 — analyse data with operators, patterns and sorting (A3, A5).

**Goal:** Sharpen your WHERE clauses with AND/OR/NOT, IN, BETWEEN, LIKE wildcards, NULL tests and aliases to slice the world data precisely.

**You'll build:** A query toolkit covering every SQL operator, answering pattern- and range-based questions on the world database.

**Tools:** SQLite Studio, world database

![Lab 5 — SQL editor](../figures/lab-05.png)

*Figure 5 — the SQL editor after running this lab's key statement.*

## Steps

1. Combine conditions with AND, OR and NOT — cities in Afghanistan with population above 1,000,000.

   ```sql
   SELECT * FROM City
   WHERE CountryCode = 'AFG' AND Population > 1000000;
   ```

2. Match a list of values with IN — cities in Afghanistan or the Netherlands.

   ```sql
   SELECT * FROM City
   WHERE CountryCode IN ('AFG', 'NLD');
   ```

3. Select a range with BETWEEN — cities with population between 500,000 and 1,000,000.

   ```sql
   SELECT Name, Population FROM City
   WHERE Population BETWEEN 500000 AND 1000000;
   ```

4. Find patterns with LIKE — countries whose name contains 'island' (the % wildcard matches any characters).

   ```sql
   SELECT Name, Continent, Population
   FROM Country
   WHERE Name LIKE '%island%'
   ORDER BY Name;
   ```

5. Answer: countries' name, continent and population where the continent is Europe or Asia, ordered by name.

   ```sql
   SELECT Name, Continent, Population
   FROM Country
   WHERE Continent IN ('Europe', 'Asia')
   ORDER BY Name;
   ```

6. Test for missing values with IS NULL — countries with no recorded independence year — and rename a column with an alias.

   ```sql
   SELECT Name AS CountryName, IndepYear
   FROM Country
   WHERE IndepYear IS NULL;
   ```


## Test it

The IN query returns only AFG and NLD cities; the LIKE query lists island nations (Iceland, Marshall Islands, …); the IS NULL query returns countries with an empty IndepYear, shown under the alias CountryName.
