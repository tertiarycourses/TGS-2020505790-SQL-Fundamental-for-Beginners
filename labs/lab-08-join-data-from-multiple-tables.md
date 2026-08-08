# Lab 8 — Join Data from Multiple Tables

**Topic 03 — Data Transformation** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO3 — transform data from multiple sources with joins and unions (A4, A6).

**Goal:** Combine tables: INNER JOIN City to Country on the country code, see how LEFT JOIN keeps unmatched rows, and emulate a FULL OUTER JOIN in SQLite using LEFT JOIN + UNION on a pair of practice tables.

**You'll build:** Joined result-sets linking cities to their countries, plus a full-outer-join of two practice tables showing matched and unmatched rows.

**Tools:** SQLite Studio, world & sample databases

![Lab 8 — SQL editor](../figures/lab-08.png)

*Figure 8 — the SQL editor after running this lab's key statement.*

## Steps

1. Inner join City and Country on city.CountryCode = country.Code, retrieving the country code and district.

   ```sql
   SELECT Country.Code, City.District
   FROM City
   INNER JOIN Country
     ON City.CountryCode = Country.Code;
   ```

2. Extend the join to name both sides — each city with its country's name.

   ```sql
   SELECT City.Name AS CityName,
          Country.Name AS CountryName
   FROM City
   INNER JOIN Country
     ON City.CountryCode = Country.Code
   LIMIT 20;
   ```

3. LEFT JOIN keeps every row of the left table even without a match — every country and (where present) its capital city.

   ```sql
   SELECT Country.Name, City.Name AS Capital
   FROM Country
   LEFT JOIN City
     ON Country.Capital = City.ID
   ORDER BY Country.Name;
   ```

4. Create two small practice tables to demonstrate a full outer join.

   ```sql
   CREATE TABLE left_t ( id INTEGER, description TEXT );
   CREATE TABLE right_t ( id INTEGER, description TEXT );
   INSERT INTO left_t VALUES (1,'left 01'),(2,'left 02'),(3,'left 03'),(4,'left 04');
   INSERT INTO right_t VALUES (3,'right 03'),(4,'right 04'),(5,'right 05'),(6,'right 06');
   ```

5. SQLite has no FULL OUTER JOIN keyword — emulate it with a LEFT JOIN in each direction combined by UNION.

   ```sql
   SELECT l.id, l.description, r.description
   FROM left_t l LEFT JOIN right_t r ON l.id = r.id
   UNION
   SELECT r.id, l.description, r.description
   FROM right_t r LEFT JOIN left_t l ON l.id = r.id
   ORDER BY id;
   ```


## Test it

The inner join returns only matched city–country rows; the LEFT JOIN lists every country (NULL capital where unmatched); and the full-join emulation returns ids 1–6 with NULLs on the sides that have no match.
