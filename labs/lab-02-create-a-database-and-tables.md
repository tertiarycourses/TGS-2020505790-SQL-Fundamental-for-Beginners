# Lab 2 — Create a Database and Tables

**Topic 01 — Data Modeling** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO1 — create and manage databases and tables with SQL DDL (A1, A2).

**Goal:** Create your own database named 'sample' and build the City, Country and CountryLanguage tables with CREATE TABLE, choosing an appropriate data type for every column.

**You'll build:** A new 'sample' database containing three empty tables whose columns, data types and defaults mirror the world schema.

**Tools:** SQLite Studio, SQL Editor

![Lab 2 — SQL editor](../figures/lab-02.png)

*Figure 2 — the SQL editor after running this lab's key statement.*

## Steps

1. In SQLite Studio click Database → Add a database, then click the green '+' (plus) icon, name the new database file sample and save it. Connect to it from the Databases panel.
2. Open the SQL editor: go to Tools → Open SQL editor. Make sure the active database (top of the editor) is sample.
3. Create the City table — run the statement, noting the INTEGER primary key and NOT NULL + DEFAULT constraints.

   ```sql
   DROP TABLE IF EXISTS City;
   CREATE TABLE City (
     ID INTEGER PRIMARY KEY,
     Name TEXT NOT NULL DEFAULT '',
     CountryCode TEXT NOT NULL DEFAULT '',
     District TEXT NOT NULL DEFAULT '',
     Population INTEGER NOT NULL DEFAULT '0'
   );
   ```

4. Create the Country table with columns for code, name, continent, region, surface area, population and government details.

   ```sql
   DROP TABLE IF EXISTS Country;
   CREATE TABLE Country (
     Code TEXT NOT NULL DEFAULT '',
     Name TEXT NOT NULL DEFAULT '',
     Continent TEXT NOT NULL DEFAULT 'Asia',
     Region TEXT NOT NULL DEFAULT '',
     SurfaceArea REAL DEFAULT NULL,
     IndepYear INTEGER DEFAULT NULL,
     Population INTEGER DEFAULT NULL,
     LifeExpectancy REAL DEFAULT NULL,
     GNP REAL DEFAULT NULL,
     LocalName TEXT NOT NULL DEFAULT '',
     GovernmentForm TEXT NOT NULL DEFAULT '',
     Capital INTEGER DEFAULT NULL,
     Code2 TEXT NOT NULL DEFAULT '',
     PRIMARY KEY (Code)
   );
   ```

5. Create the CountryLanguage table — note the composite primary key on (CountryCode, Language).

   ```sql
   DROP TABLE IF EXISTS CountryLanguage;
   CREATE TABLE CountryLanguage (
     CountryCode TEXT NOT NULL DEFAULT '',
     Language TEXT NOT NULL DEFAULT '',
     IsOfficial INTEGER NOT NULL DEFAULT '0',
     Percentage NUMERIC NOT NULL DEFAULT '0.0',
     PRIMARY KEY (CountryCode, Language)
   );
   ```

6. Right-click the sample database and choose Refresh — the three new tables appear. Open each table's Structure tab to verify the columns and data types.

## Test it

The sample database lists City, Country and CountryLanguage; each table's Structure tab shows the declared columns, data types, defaults and primary keys.
