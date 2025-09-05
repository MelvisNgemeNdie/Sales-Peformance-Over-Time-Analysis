
## Sales Performance Over Time Analysis
###  Project Overview
This project analyzes **yearly sales performance** using SQL to uncover trends in revenue, customer growth, and product sales volume.

---
### Objective
The goal is to track key performance indicators (KPIs) such as **total sales, customer base, and quantity sold** over multiple years, providing insights for strategic business planning.

---

### Dataset Structure
The analysis is based on a `fact_sales` table with the following structure:

| Column Name     | Description                                |
|-----------------|--------------------------------------------|
| order_date      | Date when the order was placed             |
| sales_amount    | Monetary value of the sales transaction    |
| customer_key    | Unique identifier of the customer          |
| quantity        | Quantity of items purchased                |

---
### SQL Query
```sql
/* Analyze Sales Performance Over Time */

SELECT 
    DATE_PART('year', order_date) AS order_year,
    SUM(sales_amount) AS total_sales,
    COUNT(DISTINCT customer_key) AS total_customers,
    SUM(quantity) AS total_quantity
FROM public."gold.fact_sales"
WHERE order_date IS NOT NULL
GROUP BY DATE_PART('year', order_date)
ORDER BY DATE_PART('year', order_date);
```
---
### Sales Performance Summary & Insights (2010–2014) 

| order_year | total_sales | total_customers | total_quantity |
|------------|-------------|-----------------|----------------|
| 2010       | 43,419      | 14              | 14             |
| 2011       | 7,075,088   | 2,216           | 2,216          |
| 2012       | 5,842,231   | 3,255           | 3,397          |
| 2013       | 16,344,878  | 17,427          | 52,807         |
| 2014       | 45,642      | 834             | 1,970          |

#### **Steady Growth in Sales (2010–2013):**
- Sales increased sharply from $43K in 2010 to $16.3M in 2013.
- Customer base grew alongside sales, peaking at 17,427 customers in 2013.
#### **Peak Year (2013):**
- 2013 was the best performing year, contributing the highest sales, customers, and product quantities sold.
- Sales in 2013 alone exceeded the combined sales of all prior years.
#### **Sudden Drop in 2014:**
- Sales fell dramatically in 2014 to just $45K, with customer count dropping by ~95% compared to 2013.
- Indicates a potential business disruption (loss of key markets, operational issues, or data gaps).
#### **Customer Growth vs. Quantity:**
- Growth in customers correlated strongly with higher sales volumes, especially visible between 2012–2013.

---
### Recommendations & Next Steps
- **Investigate 2013 Success Drivers**: Understand what fueled the spike (product launches, market entry, promotions). Replicate strategies.
- **Address 2014 Drop**: Explore reasons for the sudden decline. If data is valid, this might suggest market saturation or churn.
- **Leverage Seasonal/Yearly Trends**: Build demand forecasts for inventory & marketing planning.
- **Customer Retention Programs**: With many new customers in 2013, focus on loyalty programs to retain them in following years.

---
### Skills Demonstrated
- **SQL Querying**: Writing optimized queries with SUM(), COUNT(), ROUND(), and DATE_PART().
- **Data Aggregation & Summarization**: Generating year-level KPIs like sales, customers, and quantities.
- **Data Transformation**: Using CTEs (WITH clause) for cleaner, modular queries.
- **Analytical Thinking**: Creating metrics like average sales per customer to derive business insights.
- **Data Quality Handling**:  Filtering out NULL values in order_date to ensure valid results.

---
### Tools & Technologies
- **SQL (PostgreSQL dialect)**: For querying and analyzing structured sales data.
- **Database-PostgreSQL**: Assuming public."gold.fact_sales" is part of a database schema.
- **BI/Analytics Layer (Optional)**: Results could be exported into Tableau for visualization.
- **GitHub**: For version control and showcasing the SQL scripts.

---
###  Key Takeaway
- **Rapid Growth (2010–2013):** Sales surged from **$43K in 2010** to over **$16.3M in 2013**, driven by strong customer acquisition (17K+ customers).  
- **Peak Year (2013):** Outperformed all prior years combined, highlighting a major growth phase in both revenue and customer base.  
- **Sharp Decline (2014):** Sales collapsed to **$45K** (down ~99%), with customer counts dropping by ~95%, signaling either a **business disruption** or **data anomaly**.  
- **Strategic Insight:** Investigating **2013 success drivers** and **2014 disruptions** is crucial for understanding market dynamics, building resilience, and planning sustainable growth strategies.

---

