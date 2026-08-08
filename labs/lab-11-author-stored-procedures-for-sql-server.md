# Lab 11 — Author Stored Procedures for SQL Server

**Topic 04 — Introduction to Data Warehouse** · SQL Fundamental for Beginners (TGS-2020505790)

**Objective:** LO4 — operate data-warehouse platform capabilities with reusable stored procedures (A7, A8, A9).

**Goal:** Write stored procedures in SQL Server syntax — a plain procedure and a parameterised one — and understand where they run (SQL Server / MySQL, not SQLite) and why warehouses use them for repeatable batch work.

**You'll build:** Two stored-procedure scripts (plain and parameterised) ready to run on SQL Server, plus the EXEC calls that invoke them.

**Tools:** SQL Editor, SQL Server syntax (sqliteonline.com's MS SQL engine, or any SQL Server)

![Lab 11 — SQL editor](../figures/lab-11.png)

*Figure 11 — the SQL editor after running this lab's key statement.*

## Steps

1. Stored procedures are not available in SQLite — author these scripts against SQL Server. (Free option: sqliteonline.com and switch the engine to MS SQL, which provides a Customers demo table.)
2. Write a stored procedure that returns all customers, then save it.

   ```sql
   CREATE PROCEDURE SelectAllCustomers
   AS
   SELECT * FROM Customers
   GO;
   ```

3. Execute the stored procedure by name.

   ```sql
   EXEC SelectAllCustomers;
   ```

4. Write a parameterised version that filters customers by city through a @City parameter.

   ```sql
   CREATE PROCEDURE SelectCustomersByCity
     @City nvarchar(30)
   AS
   SELECT * FROM Customers
   WHERE City = @City
   GO;
   ```

5. Execute it, passing the parameter value.

   ```sql
   EXEC SelectCustomersByCity @City = 'London';
   ```


## Test it

Both procedures create without error; EXEC SelectAllCustomers returns the full customer list, and EXEC SelectCustomersByCity @City = 'London' returns only the London rows.
