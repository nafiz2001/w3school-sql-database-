

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
