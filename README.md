# 🚴‍♂️ Bike Shop Sales Analysis (SQL + Power BI)

## 📌 Project Overview

This project analyzes two years of bike shop sales and profitability data using **SQL** for data preparation and **Power BI** for visualization. The goal is to uncover revenue trends, customer behavior patterns, and provide data-driven recommendations for pricing and operational optimization.

---

## 🛠️ Tools & Technologies

* **SQL**: For cleaning, merging, and calculating key metrics (revenue, profit).
* **Power BI**: For developing an interactive dashboard to visualize insights.

---

## 🔄 Workflow

### 1. **Data Preparation (SQL)**

* Combined `bike_share_yr_0` and `bike_share_yr_1` using `UNION ALL`.
* Joined with `cost_table` to compute:

  * **Revenue** = `riders × price`
  * **Profit** = `revenue - COGS`
* Exported the cleaned dataset to CSV for visualization.

<details>
<summary>Example SQL Snippet</summary>

```sql
WITH cte AS (
    SELECT * FROM bike_share_yr_0
    UNION ALL
    SELECT * FROM bike_share_yr_1
)
SELECT 
    dteday, season, a.yr, weekday, hr, rider_type, riders, price, COGS,
    riders * price AS revenue,
    (riders * price) - COGS AS profit
FROM cte AS a
LEFT JOIN cost_table AS b ON a.yr = b.yr;
```

</details>

---

### 2. **Data Visualization (Power BI)**

Created an interactive dashboard featuring:

* **KPIs:** Total riders, revenue, and profit
* **Revenue & Profit Over Time:** Trend charts across 2 years
* **Revenue by Season:** Seasonal performance comparison
* **Rider Demographics:** Breakdown of casual vs. registered users
* **Hourly Profitability:** Heatmap of sales by day and hour

![Dashboard Preview](https://github.com/ahd-rafi/Bike-Shop-Sales-Analysis-SQL-Power-BI/blob/main/Dashboard.png)

---

## 📊 Key Insights

* **High-Earning Hours:** Peak revenue between 10:00 AM–3:00 PM
* **Top Days:** Wednesday and Friday consistently outperform
* **Seasonality:** Season 2 yields the highest revenue
* **User Contribution:** Registered riders account for 81.17% of revenue
* **Performance Summary:**

  * **Total Riders:** 3 Million
  * **Total Revenue:** \$15 Million
  * **Total Profit:** \$15.14 Million

---

## 💡 Recommendations

1. **Moderate Price Hike:**
   Test a 10–15% increase (e.g., from \$4.99 → \$5.49 or \$5.74)

2. **Segmented Pricing:**
   Tailor pricing for casual and registered riders based on usage patterns

3. **Optimize Peak Hours:**
   Allocate more resources during 10 AM – 3 PM to maximize profit

4. **Continuous Monitoring:**
   Track customer feedback and sales data post-pricing changes

---

## 📂 Repository Structure

* **SQL Scripts:** All queries used for data cleaning and analysis
* **CSV Files:** Output from SQL, used in Power BI
* **Power BI Dashboard:** `.pbix` file with interactive reports

---

## 🧾 Conclusion

This project delivers key insights into sales patterns, rider behavior, and profit drivers. With a data-backed pricing strategy and operational adjustments, the bike shop can boost revenue and enhance customer satisfaction. The dashboard enables stakeholders to explore data interactively and make informed business decisions.
