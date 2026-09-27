# Project 3: SQL Data Analysis

## Project Objective

Use SQL queries to extract insights from the cleaned sales dataset by applying fundamental SQL commands for data retrieval, filtering, sorting, grouping, and aggregation.

## Dataset and Environment

- **Dataset:** Cleaned Sales Data
- **Records:** 1,200 orders
- **Database:** `DecodeLabs_SQL_Project`
- **Table:** `Sales_Data`
- **Tool:** SQL Server Management Studio (SSMS)

## SQL Analysis Performed

### SELECT — Retrieve all records

```sql
SELECT *
FROM Sales_Data;
```

**Result/Insight:** Retrieved records from the Sales_Data table.

### SELECT — Retrieve selected columns

```sql
SELECT OrderID, Date, CustomerID, Product, Quantity, TotalPrice
FROM Sales_Data;
```

**Result/Insight:** Retrieved selected fields relevant to sales analysis.

### SELECT TOP — Inspect sample records

```sql
SELECT TOP 10 OrderID, Date, Product, Quantity, TotalPrice
FROM Sales_Data;
```

**Result/Insight:** Displayed the first 10 records for inspection.

### WHERE — Delivered orders

```sql
SELECT *
FROM Sales_Data
WHERE OrderStatus = 'Delivered';
```

**Result/Insight:** Returned 231 Delivered orders.

### WHERE + ORDER BY — Potential high-value orders

```sql
SELECT OrderID, Date, Product, Quantity, TotalPrice, OrderStatus
FROM Sales_Data
WHERE TotalPrice > 3330.4075
ORDER BY TotalPrice DESC;
```

**Result/Insight:** Returned 8 orders above the Project 2 IQR upper boundary.

### WHERE — Online payment orders

```sql
SELECT OrderID, Date, Product, PaymentMethod, TotalPrice
FROM Sales_Data
WHERE PaymentMethod = 'Online';
```

**Result/Insight:** Returned 258 Online-payment orders.

### ORDER BY — Highest-value orders

```sql
SELECT OrderID, Date, Product, Quantity, PaymentMethod, OrderStatus, TotalPrice
FROM Sales_Data
ORDER BY TotalPrice DESC;
```

**Result/Insight:** Sorted orders from highest to lowest TotalPrice; the highest order was approximately $3,456.40.

### COUNT — Total orders

```sql
SELECT COUNT(*) AS TotalOrders
FROM Sales_Data;
```

**Result/Insight:** Returned 1,200 orders.

### SUM — Total revenue

```sql
SELECT SUM(TotalPrice) AS TotalRevenue
FROM Sales_Data;
```

**Result/Insight:** Returned approximately $1,264,761.96.

### AVG — Average order value

```sql
SELECT AVG(TotalPrice) AS AverageOrderValue
FROM Sales_Data;
```

**Result/Insight:** Returned approximately $1,053.97.

### GROUP BY — Revenue by product

```sql
SELECT Product, SUM(TotalPrice) AS TotalRevenue
FROM Sales_Data
GROUP BY Product
ORDER BY TotalRevenue DESC;
```

**Result/Insight:** Chair generated the highest product revenue at approximately $195,620.11.

### GROUP BY — Orders by payment method

```sql
SELECT PaymentMethod, COUNT(*) AS OrderCount
FROM Sales_Data
GROUP BY PaymentMethod
ORDER BY OrderCount DESC;
```

**Result/Insight:** Online payment had the highest order count with 258.

### GROUP BY — Orders by order status

```sql
SELECT OrderStatus, COUNT(*) AS OrderCount
FROM Sales_Data
GROUP BY OrderStatus
ORDER BY OrderCount DESC;
```

**Result/Insight:** Cancelled was the largest order-status category with 250 orders.

### GROUP BY — Orders by referral source

```sql
SELECT ReferralSource, COUNT(*) AS OrderCount
FROM Sales_Data
GROUP BY ReferralSource
ORDER BY OrderCount DESC;
```

**Result/Insight:** Instagram was the largest referral source with 259 orders.

## Key SQL Insights

- The dataset contains **1,200 orders**.
- Total revenue was approximately **$1,264,761.96**.
- The average order value was approximately **$1,053.97**.
- **231 orders** were Delivered.
- **258 orders** used Online payment.
- **Chair** generated the highest product revenue at approximately **$195,620.11**.
- **Cancelled** was the largest order-status category with **250 orders**.
- **Instagram** generated the highest number of orders with **259**.
- **8 orders** had TotalPrice values above the Project 2 IQR upper boundary of **$3,330.4075**.

## Conclusion

This project demonstrated the use of SQL Server to analyze the cleaned sales dataset using fundamental SQL querying techniques. SELECT statements were used to retrieve data, WHERE was used for filtering, ORDER BY was used for sorting, GROUP BY was used to summarize categories, and COUNT, SUM, and AVG were used for basic aggregations. The analysis produced insights into sales revenue, products, payment methods, order statuses, referral sources, and high-value orders.

## Assignment Requirements Covered

- SELECT queries
- WHERE filtering
- ORDER BY sorting
- GROUP BY grouping
- COUNT()
- SUM()
- AVG()
- Extracting insights from data
