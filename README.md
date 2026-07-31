# Northwind Sales Analysis — Power BI Reports

An end-to-end sales analytics dashboard built on the **Northwind OData API**, analyzing 830 orders across 21 countries to surface revenue trends, top-performing products/categories, and regional performance.

## 🔗 Live Report
[View on Power BI Service](https://app.powerbi.com/groups/59900cc1-c8a4-4cc1-9570-811a66726eac/reports/5f3a52bd-3fb1-4110-900f-1affce564971?ctid=7a95ad65-55ee-41e3-ba46-acbdf605ee3d&pbi_source=linkShare)
*(requires a Power BI account with access; screenshots below for a quick preview)*

## Screenshots

**Overview**
![Overview](docs/screenshots/overview.png)
- Total Sales: **1.35M** | Total Freight: **64.94K** | Orders: **830**
- Air Shipment Sales: **373.98K** | CY Sales: **469.77K**
- Sales by Category (donut) and Top 10 Products by Sales (bar)

**Country x Category Matrix**
![Matrix](docs/screenshots/matrix.png)
- Cross-tab of sales by Country and Category with grand totals

**Q&A / Natural Language Query**
![Q&A](docs/screenshots/qna.png)
- Power BI's built-in Q&A visual answering "total revenue" conversationally

**Sales by Country (Map)**
![Map](docs/screenshots/map.png)
- Bubble map sized by total sales per country

**Sales Trend Over Time**
![Trend](docs/screenshots/trend.png)
- Monthly/quarterly sales trend from Jul 1996–Apr 1998

> Export each report page as PNG (File → Export → Export to PDF, then screenshot each page, or use *File → Export → PowerPoint* and screenshot from there) and save them into `docs/screenshots/` using the names above.

## Data Source
- **Northwind OData API**: `https://services.odata.org/Northwind/Northwind.svc/`
- Connected in Power BI Desktop via **Get Data → OData feed**
- Key entities pulled: `Orders`, `Order_Details`, `Products`, `Categories`, `Customers`, `Shippers`

## Tools & Techniques
- **Power Query**: data cleaning, merging Orders/Order_Details/Products/Categories, type transforms
- **Data model**: star schema — `Orders` (fact) linked to `Products`, `Categories`, `Customers`, `Shippers` (dimensions)
- **DAX measures** (examples — replace with your actual ones):
  - `Sales = Order_Details[UnitPrice] * Order_Details[Quantity]`
  - `Total Sales = SUM(Order_Details[Sales])`
  - `Total Freight = SUM(Orders[Freight])`
  - `Orders Count = DISTINCTCOUNT(Orders[OrderID])`
  - `CY Sales = CALCULATE([Total Sales], YEAR(Orders[OrderDate]) = YEAR(TODAY()))`
- **Visuals**: KPI cards, donut chart, bar chart, matrix table, Q&A visual, bubble map, line chart with drill-down (Year → Quarter → Month)
- **Interactivity**: Country and City slicers driving all visuals

## Key Insights
- **Beverages** is the top-selling category (286.53K, 21.15% of total sales)
- **Côte de Blaye** is the single best-selling product (149.98K), nearly double the next product
- **Germany** is the top market by sales (2.45L), followed by Austria and Brazil
- Sales show a clear seasonal/growth pattern, peaking sharply in early 1998 before the dataset ends


## About
Built as part of my transition from Android Development into Data Analytics, to practice API-based data connections, data modeling, and DAX in Power BI.

**Author:** Sharmila Mary
