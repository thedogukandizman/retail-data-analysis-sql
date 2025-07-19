# Retail Data Analysis with SQL 

## Project Overview
This project demonstrates comprehensive SQL data analysis skills by examining e-commerce retail data for H+ Sports. Using MySQL, I performed in-depth analysis of customer behavior, sales trends, and product performance to generate actionable business insights.

**Dataset:** H+ Sports e-commerce data including customer information, orders, products, and sales transactions.

##  Key Business Questions Answered

### Customer Analysis
- **Customer Segmentation:** Identified customers by purchase frequency and total spending
- **One-time vs. Repeat Customers:** Analyzed customer loyalty patterns
- **Customer Lifetime Value:** Calculated total spending and order frequency per customer
- **Customer with Zero Orders:** Found customers who registered but never purchased

### Sales Performance
- **Average Daily Sales:** Calculated daily sales volume and trends
- **Total Sales Days:** Determined active selling periods
- **Monthly Sales Patterns:** Analyzed sales by month using date functions
- **Product Performance:** Identified top-selling products by quantity and revenue

### Product Insights  
- **Best-Selling Products:** Found top 3 products by total quantity sold
- **Product Combinations:** Discovered which products are frequently bought together
- **Inventory Analysis:** Analyzed product varieties and sizes in demand

## Technical Skills Demonstrated

### Advanced SQL Techniques
- **Complex JOIN Operations:** LEFT OUTER JOIN, INNER JOIN, Self-joins
- **Aggregate Functions:** COUNT, SUM, AVG with GROUP BY
- **Window Functions:** Date manipulation with MONTH(), MONTHNAME()
- **Subqueries and CTEs:** Nested queries for complex analysis
- **Data Filtering:** WHERE vs HAVING clause usage
- **Data Deduplication:** DISTINCT for accurate counting

### Database Management
- **Database Setup:** Created and configured MySQL database locally
- **Data Import:** Imported structured data from SQL files
- **Table Relationships:** Understanding of foreign key relationships
- **Query Optimization:** Efficient query writing and performance considerations


##  Sample SQL Queries

### Customer Lifetime Value Analysis
```sql
SELECT 
    FirstName,
    LastName,
    COUNT(DISTINCT Orders.OrderID) AS TotalOrders,
    SUM(Quantity) AS TotalQuantity,
    SUM(TotalDue) AS TotalAmount
FROM Orders
LEFT OUTER JOIN OrderItem ON Orders.OrderID = OrderItem.OrderID
LEFT OUTER JOIN Customer ON Orders.CustomerID = Customer.CustomerID
GROUP BY Customer.CustomerID
ORDER BY TotalAmount DESC;
```

### Products Frequently Bought Together
```sql
SELECT 
    p1.Variety AS Product1,
    p2.Variety AS Product2,
    COUNT(*) AS TimesOrderedTogether
FROM OrderItem oi1
JOIN OrderItem oi2 ON oi1.OrderID = oi2.OrderID 
    AND oi1.ProductID < oi2.ProductID
JOIN Product p1 ON oi1.ProductID = p1.ProductID
JOIN Product p2 ON oi2.ProductID = p2.ProductID
GROUP BY p1.ProductID, p2.ProductID
ORDER BY TimesOrderedTogether DESC
LIMIT 5;
```

### Average Daily Sales Calculation
```sql
SELECT 
    SUM(Quantity) AS TotalQuantity,
    COUNT(DISTINCT DATE(CreationDate)) AS TotalSalesDays,
    ROUND(SUM(Quantity) / COUNT(DISTINCT DATE(CreationDate)), 2) AS AvgDailySales
FROM Orders
LEFT JOIN OrderItem ON Orders.OrderID = OrderItem.OrderID;
```

## Screenshots

**Include these 4 key screenshots in your repository:**

1. **Database Schema Overview** 
<img width="244" height="148" alt="image" src="https://github.com/user-attachments/assets/73fc4bbc-bc08-4b6b-8e3e-622d07338e0e" />


2. **Customer Analysis Results**
  <img width="485" height="220" alt="image" src="https://github.com/user-attachments/assets/55acf996-fbdc-4508-9508-4abb26917db9" />


3. **Product Performance Dashboard**
<img width="342" height="198" alt="image" src="https://github.com/user-attachments/assets/1160c9a6-45a7-45b9-979b-0e6385a15a65" />


4. **Products Bought Together Analysis**
<img width="311" height="201" alt="image" src="https://github.com/user-attachments/assets/21227cf6-e4b7-4c0a-b052-db8a7d3211f8" />


##  Technologies Used
- **Database:** MySQL 8.0
- **IDE:** MySQL Workbench
- **Skills:** SQL, Data Analysis, Database Design, Business Intelligence

## Database Structure
- **Customer:** Customer information and demographics
- **Orders:** Order details with dates and totals  
- **OrderItem:** Individual items within each order
- **Product:** Product catalog with varieties and sizes
- **Salesperson:** Sales team information

## Learning Outcomes
This project enhanced my ability to:
- Write complex SQL queries for business analysis
- Join multiple tables to create comprehensive reports
- Use aggregate functions and grouping for data summarization
- Apply date functions for time-based analysis
- Optimize queries for better performance
- Translate business questions into SQL solutions

##  Connect With Me
Feel free to reach out if you'd like to discuss this project or SQL analysis techniques!

