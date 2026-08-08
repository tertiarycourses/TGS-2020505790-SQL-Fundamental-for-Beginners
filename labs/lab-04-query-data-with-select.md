# Lab 4 — Query Data with SELECT

**Topic 02 — Data Processing and Analysis** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO2 — apply data processing and analysis using SQL queries (A3, A5).

**Goal:** Query the world database with SELECT: retrieve all columns, chosen columns, distinct values and filtered rows, then combine sorting and limits to answer real questions.

**You'll build:** A set of working queries answering questions about world cities and countries, run against the world database.

**Tools:** SQLite Studio, world database

![Lab 4 — SQL editor](../figures/lab-04.png)

*Figure 4 — the SQL editor after running this lab's key statement.*

## Steps

1. In the world database's SQL editor, retrieve every row and column of City, then only the Name and Population columns.

   ```sql
   SELECT * FROM City;
   SELECT Name, Population FROM City;
   ```

2. List each country code just once with SELECT DISTINCT.

   ```sql
   SELECT DISTINCT CountryCode FROM City;
   ```

3. Filter rows with WHERE — all cities in the district of Kabol.

   ```sql
   SELECT * FROM City WHERE District = 'Kabol';
   ```

4. Answer: what are the top 10 cities by population, largest first?

   ```sql
   SELECT * FROM City
   ORDER BY Population DESC
   LIMIT 10;
   ```

5. Answer: show 5 countries' name, continent and region where the continent is Europe, ordered by name.

   ```sql
   SELECT Name, Continent, Region
   FROM Country
   WHERE Continent = 'Europe'
   ORDER BY Name
   LIMIT 5;
   ```


## Test it

Each query runs without error; the top-10 query returns 10 rows led by the world's most populous cities, and the Europe query returns 5 alphabetically-ordered European countries.
