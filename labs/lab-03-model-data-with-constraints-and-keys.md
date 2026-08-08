# Lab 3 — Model Data with Constraints and Keys

**Topic 01 — Data Modeling** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO1 — apply data modeling for business processes with constraints, keys and relationships (A1, A2).

**Goal:** Build a Persons–Orders mini-model: enforce data rules with NOT NULL, UNIQUE, DEFAULT and CHECK, link the tables with a PRIMARY KEY / FOREIGN KEY relationship, and speed up searches with an index.

**You'll build:** A two-table data model (Persons ← Orders) with working constraints, a foreign-key relationship and an index.

**Tools:** SQLite Studio, SQL Editor

![Lab 3 — SQL editor](../figures/lab-03.png)

*Figure 3 — the SQL editor after running this lab's key statement.*

## Steps

1. In the sample database's SQL editor, create a Persons table that enforces NOT NULL, UNIQUE, DEFAULT and CHECK rules.

   ```sql
   CREATE TABLE Persons (
     ID INTEGER NOT NULL UNIQUE,
     LastName TEXT NOT NULL,
     FirstName TEXT,
     Age INTEGER CHECK (Age >= 18),
     City TEXT DEFAULT 'Singapore',
     PRIMARY KEY (ID)
   );
   ```

2. Prove the constraints work: this insert succeeds and fills City with the default value.

   ```sql
   INSERT INTO Persons (ID, LastName, FirstName, Age)
   VALUES (1, 'Tan', 'Alice', 30);
   SELECT * FROM Persons;
   ```

3. Now try to break the rules — each of these statements must FAIL (duplicate ID, NULL LastName, under-age CHECK).

   ```sql
   INSERT INTO Persons (ID, LastName, Age) VALUES (1, 'Lim', 25);
   INSERT INTO Persons (ID, Age) VALUES (2, 40);
   INSERT INTO Persons (ID, LastName, Age) VALUES (3, 'Lee', 15);
   ```

4. Create the Orders table whose PersonID column is a FOREIGN KEY referencing Persons — the child table pointing at the parent.

   ```sql
   CREATE TABLE Orders (
     OrderID INTEGER NOT NULL,
     OrderNumber INTEGER NOT NULL,
     PersonID INTEGER,
     PRIMARY KEY (OrderID),
     FOREIGN KEY (PersonID) REFERENCES Persons(ID)
   );
   ```

5. Add a column to an existing table with ALTER TABLE.

   ```sql
   ALTER TABLE Persons ADD Email TEXT;
   ```

6. Create an index so searches on LastName are fast.

   ```sql
   CREATE INDEX idx_lastname ON Persons (LastName);
   ```


## Test it

The valid insert appears in Persons with City = 'Singapore'; the three rule-breaking inserts each raise a constraint error; Orders shows a foreign key to Persons in its DDL; and idx_lastname is listed under Indexes.
