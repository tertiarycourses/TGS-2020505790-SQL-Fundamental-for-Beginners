# Lab 6 — Insert, Update and Delete Records

**Topic 02 — Data Processing and Analysis** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO2 — process data by inserting, updating and deleting records (A3, A5).

**Goal:** Change data safely: INSERT new city rows, UPDATE them with a WHERE clause, DELETE a specific record, and load the sample database from the provided insert script.

**You'll build:** A modified City table proving you can add, change and remove records — plus a fully-loaded sample database.

**Tools:** SQLite Studio, world & sample databases, insert script from the LMS

![Lab 6 — SQL editor](../figures/lab-06.png)

*Figure 6 — the SQL editor after running this lab's key statement.*

## Steps

1. Insert a new city into the City table, supplying just the columns you know — the rest take their defaults.

   ```sql
   INSERT INTO City (Name, CountryCode)
   VALUES ('Singapore', 'SGP');
   ```

2. Verify the insert — find your new row.

   ```sql
   SELECT * FROM City WHERE Name = 'Singapore';
   ```

3. Update records with a WHERE clause — rename every city in the Kabol district.

   ```sql
   UPDATE City
   SET Name = 'Kabol'
   WHERE District = 'Kabol';
   ```

4. Delete one specific record by its primary key. (Never run DELETE without WHERE — it removes every row.)

   ```sql
   DELETE FROM City WHERE ID = 3285;
   ```

5. Load the sample database: download the insert-data script (world-inserts.sql) from the course materials on the LMS, open it in the sample database's SQL editor and execute it to populate City, Country and CountryLanguage.
6. Confirm the load with row counts.

   ```sql
   SELECT COUNT(*) FROM City;
   SELECT COUNT(*) FROM Country;
   SELECT COUNT(*) FROM CountryLanguage;
   ```


## Test it

The Singapore row appears after the INSERT; the Kabol-district rows show the updated name; row ID 3285 is gone; and the three COUNT(*) queries return non-zero row counts in the sample database.
