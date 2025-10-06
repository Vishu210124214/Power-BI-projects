# Power-BI-projects
# 🍕 Pizza Sales Analysis Dashboard (Power BI)

## 📘 Project Overview
This project presents a comprehensive **Pizza Sales Analysis Dashboard** built using **Microsoft Power BI**.  
It provides key business insights into sales performance, product popularity, and revenue trends, helping stakeholders make data-driven decisions.

The dashboard visualizes and analyzes pizza sales data to identify top-performing pizza types, order patterns, and revenue distribution.

---

## 🎯 Objectives
- Analyze total revenue and order volume trends.
- Identify the most popular pizza types and categories.
- Track daily and cumulative revenue growth over time.
- Measure average pizzas sold per order.
- Understand category-wise contribution to overall sales.

---

## 📊 Dashboard Features

### 🔹 **Key Performance Indicators (KPIs)**
- **Total Revenue** – Overall income generated from pizza sales.
- **Total Orders** – Total number of orders placed.
- **Total Pizzas Sold** – Aggregate quantity of pizzas sold.
- **Average Pizzas per Order** – Insights into average order size.

### 🔹 **Visual Insights**
- **Bar Chart:** Top 5 most ordered pizza types.
- **Line Chart:** Running total of revenue (day-by-day growth).
- **Pie Chart:** Category-wise revenue share.
- **Column Chart:** Cumulative revenue over time.

---

## 🧠 Insights Gained
- **Cheese and Classic pizzas** contribute the highest share to total revenue.  
- Sales show a steady **growth trend** over time, with clear peaks during weekends.  
- The **average pizzas per order** indicates strong customer engagement and larger order sizes.  
- **Certain categories dominate** in both order volume and revenue, signaling high customer preference.

---

## ⚙️ Tools & Technologies
- **Power BI Desktop** – Data modeling and visualization  
- **SQL Server / PostgreSQL** – Data cleaning and transformation  
- **Excel / CSV** – Initial dataset storage  
- **DAX** – Used for creating measures (Total Revenue, Running Total, Averages, etc.)

---

## 🧩 Data Model
- **Tables Used:**
  - `orders`
  - `order_details`
  - `pizzas`
  - `pizza_types`

- **Relationships:**
  - One-to-many between `pizzas` and `order_details`
  - One-to-many between `orders` and `order_details`
  - One-to-one between `pizza_types` and `pizzas`

---

## 📈 DAX Measures Used
```DAX
Total Revenue = SUMX(order_details, order_details[quantity] * RELATED(pizzas[price]))

Total Orders = DISTINCTCOUNT(orders[order_id])

Total Pizzas Sold = SUM(order_details[quantity])

Average Pizzas per Order = DIVIDE([Total Pizzas Sold], [Total Orders])

Running Total Revenue =
CALCULATE(
    [Total Revenue],
    FILTER(ALLSELECTED(orders), orders[date] <= MAX(orders[date]))
)

<img width="1338" height="740" alt="Screenshot 2025-10-05 181741" src="https://github.com/user-attachments/assets/766dac21-a52c-4ece-9894-a162350818c7" />
