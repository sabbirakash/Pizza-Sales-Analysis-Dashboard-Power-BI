# 🍕 Pizza Sales Analysis Dashboard | Power BI

> An interactive **Power BI dashboard** analyzing pizza sales data — covering revenue trends, top and bottom-selling pizzas, category performance, order patterns, peak ordering hours, and size-wise distribution. Built using **Power Query**, **advanced DAX**, and a **star-schema data model** to transform raw transactional data into actionable business insights.

---

<p align="center">
  <img src="Images/Pizza%20Sales%20Banner.png" alt="Pizza Sales Analysis Banner" width="100%">
</p>

---

# 📌 Project Overview

Pizza restaurants generate thousands of transactions every week — each carrying valuable information about customer preferences, peak hours, best-selling items, and revenue drivers. Turning this raw data into insight is what helps a business grow.

This project presents an **interactive Power BI dashboard** built on pizza sales records containing over **21,000+ orders** and **$800K+ in revenue**. It provides a comprehensive view of sales performance by **pizza name, category, size, and time of order**, allowing stakeholders to identify growth opportunities, optimize the menu, and improve operational efficiency.

---

# 🎯 Project Objectives

- Analyze overall revenue and sales performance
- Identify **Top 5** and **Bottom 5** pizzas by revenue, quantity, and total orders
- Compare revenue contribution across **pizza categories** (Classic, Supreme, Chicken, Veggie)
- Evaluate **size-wise sales distribution** (S, M, L, XL, XXL)
- Analyze **order patterns by day of week** and **month**
- Detect **peak ordering hours** across a typical day
- Calculate key KPIs: **Total Revenue, Avg Order Value, Avg Pizzas per Order, Total Orders, Total Pizzas Sold**
- Enable dynamic filtering with interactive slicers

---

# 📊 Dashboard Preview

<p align="center">
  <img src="Images/Pizza%20Sales%20Dashboard.png" alt="Pizza Sales Dashboard" width="100%">
</p>

<p align="center">
  <img src="Images/Pizza%20Sales%20Dashboard%20-%20Best%20Worst%20Sellers.png" alt="Best & Worst Sellers" width="100%">
</p>

---

# 📁 Dataset Information

The dataset contains **pizza order-level transactional records**, including:

- Pizza ID
- Order ID
- Pizza Name ID
- Quantity
- Order Date
- Order Time
- Unit Price
- Total Price
- Pizza Size
- Pizza Category
- Pizza Ingredients
- Pizza Name

**Key Dataset Metrics:**

| Metric | Value |
|--------|-------|
| Total Orders | 21,350 |
| Total Pizzas Sold | 49,574 |
| Total Revenue | $817,860 |
| Avg Order Value | $38.31 |
| Avg Pizzas per Order | 2.32 |
| Categories | 4 (Classic, Supreme, Chicken, Veggie) |
| Sizes | 5 (S, M, L, XL, XXL) |
| Pizzas on Menu | 32 |

---

# 🛠️ Tools & Technologies

- Microsoft Power BI Desktop
- Power Query (Data Cleaning & Transformation)
- DAX (Advanced Measures & KPIs)
- Star-Schema Data Modeling
- Custom Date Table
- Interactive Slicers & Cross-Filtering Visuals

---

# 📐 Data Modeling

The project follows a **star-schema style data model** with a central fact table connected to supporting dimension tables.

Main tables include:

- **Pizza Sales** (Fact table — order-level transactions)
- **Date Table** (Custom calendar for time intelligence)
- **Pizza Name** (Dimension with pizza metadata)
- **Pizza Category** (Dimension)
- **Pizza Size** (Dimension)

A **custom Date Table** was created using `CALENDARAUTO()` with additional **Year, Month, Month Name, Quarter, Weekday, Week Number, and Week Type** columns to support time intelligence analysis.

---

# ⚙️ DAX Measures

Several custom DAX measures were created to power the dashboard's KPIs and visuals.

### Core Sales Measures

- **Total Revenue** — `SUM(Pizza Sales[total_price])`
- **Total Orders** — `DISTINCTCOUNT(Pizza Sales[order_id])`
- **Total Pizzas Sold** — `SUM(Pizza Sales[quantity])`
- **Avg Order Value** — `DIVIDE([Total Revenue], [Total Orders])`
- **Avg Pizzas per Order** — `DIVIDE([Total Pizzas Sold], [Total Orders])`

### Time Intelligence Measures

- **Total Orders by Day Name**
- **Total Orders by Month**
- **Total Orders by Hour**
- **Revenue YTD / MTD (if applicable)**

### Analytical Measures

- **Revenue % by Category**
- **Revenue % by Size**
- **Rank by Revenue** — for Top/Bottom 5 analysis
- **Pizza Contribution %**

Key functions used:

- `SUM()`
- `SUMX()`
- `DIVIDE()`
- `CALCULATE()`
- `DISTINCTCOUNT()`
- `RANKX()`
- `TOPN()`
- `CALENDARAUTO()`
- `SELECTEDVALUE()`

### Example DAX Pattern (Top N Ranking)

```dax
Top 5 Pizza Revenue =
CALCULATE(
    [Total Revenue],
    TOPN(5, ALL(Pizza Sales[pizza_name]), [Total Revenue], DESC)
)
```

---

# 📈 Dashboard Features

### Executive KPI Cards

- Total Revenue — **$817.86K**
- Average Order Value — **$38.31**
- Total Pizzas Sold — **49,574**
- Total Orders — **21,350**
- Avg Pizzas per Order — **2.32**

---

### Interactive Visualizations

- **Busiest Days & Times** — Orders by Day of Week & Hour of Day
- **Sales by Category** — Classic, Supreme, Chicken, Veggie
- **Sales by Size** — S, M, L, XL, XXL
- **Total Pizzas Sold by Category** — Monthly trend
- **Top 5 Pizzas** — By Revenue, Quantity, and Total Orders
- **Bottom 5 Pizzas** — By Revenue, Quantity, and Total Orders
- Interactive Slicers — Date range, Pizza Category, Pizza Size

---

# 💡 Key Business Insights

### 💰 Revenue Performance

- Total revenue generated: **$817,860**
- Average order value: **$38.31** — healthy ticket size for a pizza business
- Average of **2.32 pizzas per order** suggests group/family orders dominate

---

### 🍕 Best Sellers

**Top 5 by Revenue:**

1. **The Thai Chicken Pizza** — $43,434
2. **The Barbecue Chicken Pizza** — $42,768
3. **The California Chicken Pizza** — $41,410
4. **The Classic Deluxe Pizza** — $38,181
5. **The Spicy Italian Pizza** — $34,831

**Top 5 by Quantity:**

1. The Classic Deluxe Pizza
2. The Barbecue Chicken Pizza
3. The Hawaiian Pizza
4. The Pepperoni Pizza
5. The Thai Chicken Pizza

**Top 5 by Total Orders:**

1. The Classic Deluxe Pizza — 2,329 orders
2. The Hawaiian Pizza — 2,280 orders
3. The Pepperoni Pizza — 2,281 orders
4. The Barbecue Chicken Pizza — 2,273 orders
5. The Thai Chicken Pizza — 2,371 orders

---

### 📉 Worst Sellers

**Bottom 5 by Revenue:**

1. The Brie Carre Pizza — $11,588
2. The Mediterranean Pizza — $15,360
3. The Calabrese Pizza — $15,940
4. The Spinach Supreme Pizza — $15,943
5. The Soppressata Pizza — $17,913

**Bottom 5 by Quantity Sold:**

1. The Brie Carre Pizza
2. The Mediterranean Pizza
3. The Calabrese Pizza
4. The Spinach Supreme Pizza
5. The Soppressata Pizza

**Bottom 5 by Total Orders:**

1. The Brie Carre Pizza — 490 orders
2. The Mediterranean Pizza — 934 orders
3. The Calabrese Pizza — 937 orders
4. The Spinach Supreme Pizza — 950 orders
5. The Soppressata Pizza — 961 orders

---

### 📅 Time-Based Patterns

- **Busiest Days:** Thursday, Friday, and Saturday evenings
- **Peak Ordering Hours:** **12:00–13:00 PM** and **5:00–7:00 PM**
- **Highest Orders Month:** **July** (~1,935 orders)
- **Lowest Orders Month:** **October** (~1,648 orders)

---

### 🥧 Category & Size Insights

- **Classic** category contributes the highest revenue & total orders
- **Large (L) size** pizzas are the most preferred — ~45% of sales
- **Medium (M)** is the second most popular size
- **XXL** is rarely ordered — only available for The Greek Pizza

---

# 🎯 Strategic Recommendations

- **Promote Low Sellers** — Bundle offers on Brie Carre & Mediterranean pizzas to clear slow-moving inventory
- **Optimize Peak Hours** — Increase staffing from 12–1 PM and 5–7 PM to reduce wait times
- **Weekend Campaigns** — Target Thursday–Saturday evenings with combo deals
- **Loyalty Programs** — Leverage the Classic & Chicken categories which already dominate volume
- **Menu Optimization** — Consider removing or redesigning the lowest-revenue pizzas

---

# 🎨 Dashboard Highlights

- Dark Themed UI with Pizza-Inspired Accents
- Interactive KPI Cards
- Top / Bottom 5 Dynamic Ranking
- Category & Size Distribution Charts
- Day & Hour-Based Order Heatmap
- Interactive Slicers
- Clean Executive Dashboard Design

---

# 🚀 Skills Demonstrated

- Data Cleaning
- Data Modeling
- Power Query
- DAX Programming
- KPI Development
- Sales & Retail Analytics
- Dashboard Design
- Interactive Reporting
- Business Intelligence
- Time Intelligence Analysis

---

# 📂 Repository Structure

```
Pizza-Sales-Analysis-PowerBI/
│
├── Dashboard/
│   └── Pizza Sales Analysis.pbix
│
├── Dataset/
│   └── pizza_sales.csv
│
├── Images/
│   ├── Pizza Sales Banner.png
│   ├── Pizza Sales Dashboard.png
│   └── Pizza Sales Dashboard - Best Worst Sellers.png
│
├── Documents/
│   ├── Business Requirements.pdf
│   ├── Dashboard Summary.pdf
│   └── DAX & KPIs.pdf
│
└── README.md
```

---

# 🌟 Project Highlights

✔ Interactive Pizza Sales Dashboard
✔ Advanced DAX Calculations
✔ Dynamic Top/Bottom 5 Ranking
✔ Revenue & Order KPIs
✔ Time-Based Order Analysis
✔ Category & Size Distribution
✔ Responsive Dashboard Design

---

# 📚 Key Learnings

Throughout this project, I strengthened my skills in:

- Writing efficient DAX measures using `RANKX()`, `TOPN()`, and `CALCULATE()`
- Building reusable Date Tables with `CALENDARAUTO()`
- Designing interactive Power BI dashboards with drill-through
- Developing retail & sales-specific KPIs
- Implementing dynamic Top N / Bottom N filtering
- Applying business intelligence concepts to real sales data

---

# ✅ Conclusion

This project demonstrates how **Power BI** can transform raw pizza sales transactions into meaningful business insights through interactive dashboards and advanced DAX. By combining revenue KPIs, best/worst seller analysis, category performance, and time-based ordering patterns, the dashboard provides restaurant managers and analysts with a **centralized view of business performance** — supporting faster, data-driven decisions for menu optimization, staffing, and marketing strategy.

---

## 👨‍💻 Author

**Sabbir Uddin Akash**

- 💼 Aspiring Data Analyst
- 📊 Power BI | SQL | Excel | Python
- 🌐 Portfolio: [Sabbir Uddin Akash](https://sabbirakash.github.io)
- 💻 GitHub: [sabbirakash](https://github.com/sabbirakash)
- 🔗 LinkedIn: [Sabbir Uddin Akash](https://www.linkedin.com/in/sabbirakash)

If you found this project useful, consider giving it a ⭐.
