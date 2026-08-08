# Lab 10 — Map an E-R Model to Database Tables (SMRT Case Study)

**Topic 04 — Introduction to Data Warehouse** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO4 — apply data mapping from an E-R model to a data warehouse schema (A7, A8, A9).

**Goal:** Take the SMRT public-transport E-R model (Routes, Timetables, DisruptedRoutes) and map it to physical tables: create each entity with its primary key, wire the foreign-key relationships, and verify the model with joined queries.

**You'll build:** A three-table transport schema in SQLite that faithfully implements the SMRT E-R model with PK/FK mappings.

**Tools:** SQLite Studio, sample database

![Lab 10 — SQL editor](../figures/lab-10.png)

*Figure 10 — the SQL editor after running this lab's key statement.*

## Steps

1. Review the E-R model: Routes (route_id PK) 1—many Timetables (timetable_id PK, route_id FK) 1—many DisruptedRoutes (disrupt_no PK, timetable_id FK). Identify each entity's attributes before writing any SQL.
2. Create the Routes parent table.

   ```sql
   CREATE TABLE Routes (
     route_id CHARACTER(4) NOT NULL PRIMARY KEY,
     route_type CHARACTER(15) NOT NULL,
     route_code VARCHAR(3) NOT NULL,
     route_name VARCHAR(125) NOT NULL,
     route_direction CHARACTER(10) NOT NULL,
     remarks VARCHAR(255)
   );
   ```

3. Create the Timetables child table — its route_id column references Routes.

   ```sql
   CREATE TABLE Timetables (
     timetable_id INTEGER NOT NULL PRIMARY KEY,
     route_id CHARACTER(4) NOT NULL,
     station_code CHARACTER(4) NOT NULL,
     frequency VARCHAR(20) DEFAULT '',
     days_operation VARCHAR(30) NOT NULL,
     stop_no NUMERIC(3) NOT NULL,
     first_trip CHAR(10) NOT NULL,
     last_trip CHAR(10) NOT NULL,
     FOREIGN KEY (route_id) REFERENCES Routes(route_id)
   );
   ```

4. Create the DisruptedRoutes table — its timetable_id references Timetables.

   ```sql
   CREATE TABLE DisruptedRoutes (
     disrupt_no INTEGER NOT NULL PRIMARY KEY,
     disrupt_date CHAR(10) NOT NULL,
     disrupt_type VARCHAR(20) NOT NULL,
     disrupt_name VARCHAR(50) NOT NULL,
     disrupt_details VARCHAR(300) NOT NULL,
     start_datetime CHAR(12) NOT NULL,
     duration CHAR(20) NOT NULL,
     timetable_id INTEGER NOT NULL,
     alternatives VARCHAR(3000) NOT NULL,
     FOREIGN KEY (timetable_id) REFERENCES Timetables(timetable_id)
   );
   ```

5. Load one row into each table to exercise the relationship chain.

   ```sql
   INSERT INTO Routes VALUES ('R001','Train','NSL','North South Line','North','');
   INSERT INTO Timetables VALUES (1,'R001','NS01','5 min','Mon-Sun',1,'05:30','23:30');
   INSERT INTO DisruptedRoutes VALUES (1,'2024-03-14','system','Signal fault','Signalling fault at NS01','202403140800','45 min',1,'Bridging bus 1A');
   ```

6. Verify the mapping end-to-end: join all three tables from disruption back to route.

   ```sql
   SELECT r.route_name, t.station_code,
          d.disrupt_name, d.duration
   FROM DisruptedRoutes d
   INNER JOIN Timetables t ON d.timetable_id = t.timetable_id
   INNER JOIN Routes r ON t.route_id = r.route_id;
   ```


## Test it

The three tables exist with their PK/FK constraints visible in the DDL, and the three-way join returns one row linking 'North South Line' → 'NS01' → 'Signal fault'.
