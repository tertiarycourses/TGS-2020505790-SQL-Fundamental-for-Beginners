# Lab 1 — Set Up SQLite Studio & Import the World Database

**Topic 01 — Data Modeling** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO1 — identify relevant data sources and set up the SQL workbench (A1, A2).

**Goal:** Install SQLite Studio, connect it to the world sample database and explore its tables — your data source for the whole course.

**You'll build:** A working SQLite Studio with the world database connected, showing the City, Country and CountryLanguage tables.

**Tools:** SQLite Studio, world.db sample database, LMS course materials

![Lab 1 — SQL editor](../figures/lab-01.png)

*Figure 1 — the SQL editor after running this lab's key statement.*

## Steps

1. Download SQLite Studio for your OS from the official site and install it. (Alternative: use the free cloud version at sqliteonline.com — no install needed.)

   ```sql
   https://sqlitestudio.pl
   ```

2. Download the world sample database (world.db) from the course materials on the LMS portal.

   ```sql
   https://lms-tms.tertiaryinfotech.com
   ```

3. Open SQLite Studio, click Database → Add a database, browse to the downloaded world.db and click OK.
4. In the left-hand Databases panel, right-click world and choose Connect to the database.
5. Expand the database tree: you should see the City, Country and CountryLanguage tables. Double-click City and open the Data tab to preview its rows.

## Test it

The Databases panel shows the connected world database with the City, Country and CountryLanguage tables, and the Data tab displays city rows (ID, Name, CountryCode, District, Population).
