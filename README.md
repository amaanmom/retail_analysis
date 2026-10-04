🛒 E-Commerce Sales Dashboard

This project presents an interactive sales dashboard built on the UCI Online Retail dataset, which holds the transactions of a UK-based online gift retailer from 1 Dec 2010 to 9 Dec 2011. The analysis shows how countries, products, customers and time drive revenue.

Open the live dashboard (replace after enabling GitHub Pages)

🎯 Objectives
Measure total revenue, orders, customers and average order value.
Find which countries and products drive revenue.
Compare one-time and repeat customers.
Understand monthly and weekday sales patterns.
Build a clear, interactive dashboard and derive actionable insights.
⚙️ Data Preparation
🧼 Data Cleaning
Set InvoiceNo and StockCode to Text
Removed rows with no CustomerID (135,080)
Removed rows with Quantity ≤ 0 or UnitPrice ≤ 0
Removed cancelled invoices (InvoiceNo starting with "C")
Result: 541,909 raw rows → 397,884 clean rows
🔄 Data Transformation
Created custom column Revenue = Quantity × UnitPrice
Created OrderDate, month and weekday columns
Created a Date table marked as the date table
📈 Data Enrichment (Measures)
Total Revenue = SUMX('Online Retail', 'Online Retail'[Quantity] * 'Online Retail'[UnitPrice])
Total Orders = DISTINCTCOUNT('Online Retail'[InvoiceNo])
Total Customers = DISTINCTCOUNT('Online Retail'[CustomerID])
Avg Order Value = DIVIDE([Total Revenue], [Total Orders])
Revenue LM = CALCULATE([Total Revenue], DATEADD('Date'[Date], -1, MONTH))
MoM Growth % = DIVIDE([Total Revenue] - [Revenue LM], [Revenue LM])
Running Total Revenue = CALCULATE([Total Revenue], FILTER(ALLSELECTED('Date'[Date]), 'Date'[Date] <= MAX('Date'[Date])))
📊 Dashboard Overview

The report has a Power BI-style layout: a slicer panel on the left, glowing KPI cards, and page tabs along the bottom. It consists of six interactive pages.

🟢 KPIs (on every page except Drill Down)
Total Revenue
Total Orders
Average Order Value
Customers
MoM Growth
🎛️ Slicers / Interactive Buttons
Period buttons (All, 2010, 2011)
Country
From month
To month
🧾 1. Overview

Show Image

Column Chart – Monthly revenue
Donut Chart – Revenue share, selected country vs rest
Bar Chart – Revenue by country
Bar Chart – Top 10 products by revenue
Column Chart – Orders by month
📦 2. Products

Show Image

Bar Chart – Top 10 products by revenue
Bar Chart – Top 10 products by units sold
Bar Chart – Revenue per unit
Table – Product performance
👥 3. Customers

Show Image

Donut Chart – One-time vs repeat customers
Stacked Column Chart – New vs returning customers by month
Table – Top 10 customers (click a row to drill down)
Bar Chart – Customers by country
🕒 4. Time

Show Image

Column + Line Chart – Revenue and running total
Column Chart – Orders by weekday
Column + Line Chart – Orders vs revenue by month
🔍 5. Drill Down

Show Image

Opens when you click a customer row on the Customers or Detail page. It shows the customer's ID, total revenue, orders, average order value and monthly revenue. The back arrow returns to Detail.

📋 6. Detail

Show Image

A customer-level table (top 30 by revenue) with orders, units, revenue and average order value, plus totals.

🔁 Page Navigation
Page tabs at the bottom switch between all pages
Clicking a customer row → Drill Down page
Back arrow on Drill Down → Detail page
📊 Dashboard Features
Interactive slicers and buttons that update every KPI and chart
Five dynamic KPI cards
Drill-through from customer tables to a customer page
Page tabs and a back button
Hover tooltips on charts
🔑 Key Insights
Total revenue is £8.91M from 18,532 orders and 4,338 customers, an average order value of £480.87.
The United Kingdom produces about 82% of revenue (£7.31M). The Netherlands, EIRE, Germany and France follow far behind.
Revenue climbs sharply from September: November 2011 peaked at £1.16M, about double the early-2011 level.
66% of customers (2,845) ordered more than once, and they account for about 93% of revenue.
Thursday has the most orders. No sales were recorded on Saturdays.
Top products by revenue: PAPER CRAFT, LITTLE BIRDIE (£168K) and REGENCY CAKESTAND 3 TIER (£143K).
December 2011 covers only 1 to 9 December, so it is not comparable with other months.
✅ Conclusion

Revenue depends heavily on the UK market and on repeat customers, and it peaks in the autumn before Christmas. Stock planning, retention offers and marketing for September to November would have the largest effect on sales.

🚀 How to Use
Clone this repo or download the files.
Open index.html in any browser, or visit the GitHub Pages link above.
Use the slicers, switch pages with the tabs at the bottom, and click a customer row to drill down.
To rebuild in Power BI, load data/online_retail_clean.csv into Power BI Desktop and add the measures above.
📁 Project Structure
├── index.html                       # Interactive dashboard
├── data
│   └── online_retail_clean.csv      # Cleaned dataset (397,884 rows)
│
└── images
    ├── overview.png
    ├── products.png
    ├── customers.png
    ├── time.png
    ├── drilldown.png
    └── detail.png
🛠 Tools Used
Power BI Desktop and DAX – measures and the data model specification
Power Query – data cleaning
Python (pandas) – cleaned dataset and aggregates
HTML, CSS and JavaScript – interactive dashboard
📚 Data Source

Chen, D., Sain, S. L., and Guo, K. (2012). Online Retail dataset, UCI Machine Learning Repository.

👤 Author

Amaan momin

LinkedIn: your-link
GitHub: github.com/your-username
Email: your-email
🌟 Feedback & Support

Feel free to share suggestions or compliments — your feedback is appreciated! If you found this project useful, please consider giving it a ⭐️.
