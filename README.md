

# 📘 W3Schools Demo Database (MySQL)

This repository contains the **W3Schools Demo Database** implemented in MySQL.  
It is designed for **SQL practice, tutorials, and beginner-friendly learning**.  
The database includes common tables like `Customers`, `Orders`, `Products`, `Employees`, and more.

---

## 📚 Overview

The W3Schools Demo Database is widely used for learning SQL queries.  
It helps beginners practice `SELECT`, `JOIN`, `GROUP BY`, `ORDER BY`, and other SQL commands.

---

## 🗂️ Database Structure

### Tables Included
- **Customers** → Stores customer details (name, country, contact info)  
- **Orders** → Contains order information (OrderID, CustomerID, EmployeeID, ShipperID, OrderDate)  
- **OrderDetails** → Line items for each order (ProductID, Quantity, Price)  
- **Products** → Product catalog with prices and supplier info  
- **Suppliers** → Supplier details (company name, country)  
- **Employees** → Employee details (name, title, reports)  
- **Categories** → Product categories (e.g., Beverages, Soft Drinks, Condiments, etc.)  
- **Shippers** → Shipping companies used for orders  

---

## ⚙️ Setup Instructions

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/w3schools-demo-database.git
   ```

2. Import the SQL dump file into MySQL:
   ```bash
   mysql -u root -p w3schools_demo < w3schools_demo.sql
   ```

3. Verify tables:
   ```sql
   USE w3schools_demo;
   SHOW TABLES;
   ```

---

## 🛠️ Example Queries

Here are some sample queries you can run:

```sql
-- Find customers from Germany
SELECT * FROM Customers WHERE Country = 'Germany';

-- Top 5 products by quantity sold
SELECT ProductID, SUM(Quantity) AS TotalSold
FROM OrderDetails
GROUP BY ProductID
ORDER BY TotalSold DESC
LIMIT 5;

-- Orders shipped by Shipper 3
SELECT * FROM Orders WHERE ShipperID = 3;
```

---

## 🎯 Purpose

- Practice SQL queries (SELECT, JOIN, GROUP BY, ORDER BY, etc.)  
- Beginner-friendly database for tutorials and exercises  
- Useful for GitHub projects, teaching, and demo applications  


--------------------------------------------------------------------------------------------------------------

Got it Nafiz 👍 — from now on I’ll keep everything in **English only**.  

Here’s a polished **README.md template** for your MySQL notes and W3Schools Demo Database practice. It’s structured, professional, and easy for anyone to follow:

---

```markdown
# 📘 MySQL Complete Notes (Beginner to Advanced)

This repository contains a **step-by-step MySQL Cheat Sheet**.  
It is designed for **beginners and intermediate learners** to practice SQL queries using the W3Schools Demo Database.

---

## 🛠 Database Management

- **Show all databases:**
```sql
SHOW DATABASES;
```

- **Select a database:**
```sql
USE w3schools_demo;
```

- **Show all tables in the selected database:**
```sql
SHOW TABLES;
```

- **View table structure:**
```sql
DESCRIBE Customers;
```

- **Count records in a table:**
```sql
SELECT COUNT(*) AS TotalRows FROM Customers;
```

---

## 🟢 Table Creation & Modification

- **Create a database:**
```sql
CREATE DATABASE my_demo;
```

- **Create a table:**
```sql
CREATE TABLE Customers (
  CustomerID INT PRIMARY KEY,
  CustomerName VARCHAR(100) NOT NULL,
  Country VARCHAR(50)
);
```

- **Add a column:**
```sql
ALTER TABLE Customers ADD Email VARCHAR(150);
```

- **Drop a column:**
```sql
ALTER TABLE Customers DROP COLUMN Email;
```

---

## 🟡 CRUD Operations (Insert, Update, Delete)

- **Insert data:**
```sql
INSERT INTO Customers (CustomerID, CustomerName, Country)
VALUES (1, 'Alfreds Futterkiste', 'Germany');
```

- **Update data:**
```sql
UPDATE Customers
SET Country = 'UK'
WHERE CustomerID = 1;
```

- **Delete data:**
```sql
DELETE FROM Customers WHERE Country = 'Brazil';
```

---

## 🔵 Filtering & Sorting

- **Filter with WHERE:**
```sql
SELECT * FROM Customers WHERE Country = 'UK';
```

- **Pattern match with LIKE:**
```sql
SELECT * FROM Customers WHERE CustomerName LIKE 'A%E';
```

- **Sort results:**
```sql
SELECT * FROM Products ORDER BY Price DESC;
```

- **Limit results:**
```sql
SELECT * FROM Customers ORDER BY CustomerName DESC LIMIT 3;
```

---

## 🟣 Aggregates & Grouping

- **Aggregate functions:**
```sql
SELECT COUNT(*) FROM Orders;
SELECT SUM(Quantity) FROM OrderDetails;
SELECT AVG(Price) FROM Products;
```

- **Group by:**
```sql
SELECT Country, COUNT(CustomerID) AS TotalCustomers
FROM Customers
GROUP BY Country;
```

- **Filter groups with HAVING:**
```sql
SELECT CustomerID, COUNT(OrderID) AS TotalOrders
FROM Orders
GROUP BY CustomerID
HAVING COUNT(OrderID) > 5;
```

---

## 🟠 Joins

- **Inner join:**
```sql
SELECT Orders.OrderID, Customers.CustomerName
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

- **Left join:**
```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

---

## 🔴 Scenario-Based Queries (Practice)

1. **Customer profile (ID=1):**
```sql
SELECT * FROM Customers WHERE CustomerID = 1;
```

2. **Products by highest price:**
```sql
SELECT * FROM Products ORDER BY Price DESC;
```

3. **Customers by country (A→Z), names (Z→A):**
```sql
SELECT * FROM Customers ORDER BY Country ASC, CustomerName DESC;
```

4. **Brazil customers with ID > 40:**
```sql
SELECT * FROM Customers WHERE Country='Brazil' AND CustomerID > 40;
```

5. **Berlin OR names start G OR Germany:**
```sql
SELECT * FROM Customers WHERE City='Berlin' OR CustomerName LIKE 'G%' OR Country='Germany';
```

6. **Top 3 last alphabet customers:**
```sql
SELECT * FROM Customers ORDER BY CustomerName DESC LIMIT 3;
```

7. **Cheapest item per category:**
```sql
SELECT CategoryID, MIN(Price) AS CheapestPrice FROM Products GROUP BY CategoryID;
```

8. **Total products:**
```sql
SELECT COUNT(*) AS TotalProducts FROM Products;
```

9. **Products per category:**
```sql
SELECT CategoryID, COUNT(ProductID) AS TotalProducts FROM Products GROUP BY CategoryID;
```

10. **Total items per order:**
```sql
SELECT OrderID, SUM(Quantity) AS TotalItems FROM OrderDetails GROUP BY OrderID;
```

11. **Average price per category:**
```sql
SELECT CategoryID, AVG(Price) AS AvgPrice FROM Products GROUP BY CategoryID;
```

12. **Customers start with N or L:**
```sql
SELECT * FROM Customers WHERE CustomerName LIKE 'N%' OR CustomerName LIKE 'L%';
```

13. **Customers start A and end E:**
```sql
SELECT * FROM Customers WHERE CustomerName LIKE 'A%E';
```

14. **Customers with at least one order:**
```sql
SELECT DISTINCT c.CustomerID, c.CustomerName
FROM Customers c JOIN Orders o ON c.CustomerID=o.CustomerID;
```

15. **Customers with no orders:**
```sql
SELECT c.CustomerID, c.CustomerName
FROM Customers c LEFT JOIN Orders o ON c.CustomerID=o.CustomerID
WHERE o.OrderID IS NULL;
```

16. **Orders in June 1995:**
```sql
SELECT * FROM Orders WHERE OrderDate BETWEEN '1995-06-01' AND '1995-06-30';
```

---

## 📝 Summary for Learners

- **SHOW** → Database/Table list  
- **USE** → Select database  
- **DESCRIBE** → Table structure  
- **CRUD** → Insert, Update, Delete  
- **WHERE/LIKE** → Filtering  
- **ORDER BY/LIMIT** → Sorting & limiting  
- **GROUP BY/HAVING** → Group summary & filter  
- **JOIN** → Combine multiple tables  
- **Aggregate Functions** → COUNT, SUM, AVG, MIN, MAX  

---

## 🎯 Purpose

- Beginner-friendly SQL practice  
- Covers database management, CRUD, filtering, grouping, joins, and scenario queries  
- Perfect for GitHub projects, tutorials, and self-study  

---

## 📌 License

This project is for **educational purposes only**.  
Data is based on the W3Schools Demo Database.
```

---








