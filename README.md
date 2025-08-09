# SQL_Data_Analysis_Business_Insights 

## Overview
This project uses SQL to analyze company performance data and provide actionable insights for key business decisions. 
The goal was to simulate a real-world scenario where a data analyst supports management in choosing the most profitable and strategic path forward.

## Scenario 
As a data analyst, I was tasked with evaluating a company that buys products and resells them to customers. The first objective was to use data to inform which employees should receive bonuses for their sales performance. The second objective was to find out how many orders have been placed by each customer in order for the sales manager to assign customer accounts to new sales representatives.

The dataset contained **932** records with fields such as **customers, categories, employees, orderdetails, orders, products, shippers, suppliers**.

## Tools & Skills Used
- **SQL** for querying and analysis
- **Data cleaning & transformation** using SQL functions
- **Aggregations, filtering, and joins** for deeper insights
- **Business problem framing** and recommendations

## Preliminary Processes
1. **Data Understanding**  
   - Examined the tables 
   - Checked for missing/duplicate values  

2. **Data Cleaning**  
   - Removed invalid entries   
   - Standardized date formats  

## Key SQL Queries
**Joining 4 tables**

SELECT lastname, firstname, orders, orderid, products.productid, quantity, price
From employees
 inner join orders
  on employees.employeeid = orders.employeeid
 inner join orderdetails
  on orders.orderid= orderdetails.orderid
 inner join products
  on orderdetails.productid = products.productid
ORDER BY lastname, firstname

**Joining customers and orders tables together**

SELECT CustomerName, OrderID, OrderDate
FROM Customers
inner join Orders
on Customer.CustomerID = Orders.CustomerID

**Calculating and summarizing sales for each order**

SELECT lastname, firstname, orders, orderid, products.productid, quantity, price, sum(quantity * price) AS sales_amount
From employees
 inner join orders
  on employees.employeeid = orders.employeeid
 inner join orderdetails
  on orders.orderid= orderdetails.orderid
 inner join products
  on orderdetails.productid = products.productid
GROUP BY orders.order.id

**First objective final code**

SELECT lastname, firstname, orders, orderid, products.productid, quantity, price, sum(quantity * price) AS sales_amount
From employees
 inner join orders
  on employees.employeeid = orders.employeeid
 inner join orderdetails
  on orders.orderid= orderdetails.orderid
 inner join products
  on orderdetails.productid = products.productid
GROUP BY orders.order.id
ORDER BY sales_amount desc
LIMIT 5

**Second objective final code**

SELECT CustomerName, count(OrderID) as Number_of_Orders
from Customers
inner join Orders
on Customers.CustomerID = Orders.CustomerID
group by Customers.CustomerID
order by Number_of_Orders desc

## Results
- Identified the **The five highest sales amounts**, only three employees were responsible for these, so the code was adapted to list **five employees** responsible.
- Discovered **how many orders were placed by each customer.**
- Yielded key insights to support business decisions.


## Author
**Mpilenhle Mkhize**  
[LinkedIn](https://linkedin.com/in/mpilenhle-mkhize-327694229) | [GitHub](https://github.com/Mpilenhle-Mkhize)
