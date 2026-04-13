# Superstore Sales Analysis Dashboard — Power BI

## Overview
An interactive business intelligence dashboard built on a real-world 
retail dataset of 9,800 rows and 18 columns spanning 2015–2018. 
The project transforms raw CSV sales data into actionable insights 
through advanced DAX measures, time intelligence, and drill-through 
navigation — demonstrating end-to-end Power BI development skills.

---

## Dashboard Preview

### Page 1 — Sales Analysis Dashboard
Superstore_Dashboard_Page1.png

### Page 2 — Category Details Drill Through
Superstore_Dashboard_Page2_Technology.png
Superstore_Dashboard_Page2_Furniture.png
---

## Project Workflow

### 1. Data Import & Cleaning (Power Query)
- Imported raw CSV dataset (9,800 rows, 18 columns) into Power BI
- Removed unnecessary columns — Row ID and Postal Code
- Corrected data types for all columns
- Resolved date format issues in Order Date and Ship Date columns
- Loaded clean data into the data model

### 2. Data Modeling (Star Schema)
- Created a separate Date_Table with Date, Month, Month Number, 
  Quarter and Year columns
- Established a Many-to-One relationship between train[Order Date] 
  and Date_Table[Date]
- Enabled proper time intelligence calculations across all visuals

### 3. DAX Measures
| Measure | Formula |
|---------|---------|
| Total Sales | SUM(train[Sales]) |
| Total Orders | COUNT(train[Order ID]) |
| Average Order Value | DIVIDE([Total Sales], [Total Orders]) |
| Previous Month Sales | CALCULATE([Total Sales], DATEADD(Date_Table[Date], -1, MONTH)) |
| MoM Growth % | DIVIDE([Total Sales] - [Previous Month Sales], [Previous Month Sales]) * 100 |
| Previous Year Sales | CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Date_Table[Date])) |
| Best Region | FIRSTNONBLANK(TOPN(1, VALUES(train[Region]), [Total Sales], DESC), 1) |
| Top Category | FIRSTNONBLANK(TOPN(1, VALUES(train[Category]), [Total Sales], DESC), 1) |

### 4. Dashboard — Page 1 (Sales Analysis Dashboard)
**KPI Cards:**
- Total Sales — 2.26M
- Total Orders — 4,922
- Average Order Value — 459.48
- MoM Growth % — 3.81%
- Best Region — West
- Top Category — Technology

**Visuals:**
- Top 5 Products horizontal bar chart using TopN filter
- Sales Contribution by Category Treemap
- Sales by State bubble Map visual
- Monthly Sales Trend line chart (Jan–Dec)
- YoY KPI visual — 321.48K vs Goal 238.45K (+34.82%)

**Slicers:**
- Filter by Category (dropdown)
- Filter by Region (list)
- Filter by Year (range slider — 2015 to 2018)

### 5. Dashboard — Page 2 (Category Details — Drill Through)
Implemented drill-through functionality — right click any category 
on Page 1 to navigate to a dedicated Category Details page filtered 
to that specific category.

**Visuals:**
- Total Sales KPI card — filtered to drilled category
- Sales by Region horizontal bar chart
- Sales by Sub-Category horizontal bar chart
- Sales by Ship Mode pie chart
- Top 10 Customers by Sales table with conditional formatting data bars
- Back button to return to Page 1

---

## Key Business Insights
- Total revenue of $2.26M across 4,922 orders from 2015–2018
- Technology is the highest revenue category
- West region generates the most sales overall
- Canon imageCLASS 2200 Advanced Copier is the top revenue product
- MoM Growth of 3.81% shows steady month on month improvement
- YoY growth of +34.82% confirms strong year on year expansion
- Sales peak in Q4 (Sep–Nov) suggesting holiday season demand surge

---

## Advanced Features
- Star Schema data model with Many-to-One relationship
- Time intelligence DAX — SAMEPERIODLASTYEAR, DATEADD, CALCULATE
- TopN filtering for Top 5 products
- Category-level Drill Through navigation between pages
- Conditional formatting — data bars on customer table
- Dynamic DAX text measures — Best Region and Top Category update 
  with slicers
- Map visual with geographic bubble sizing by sales
- Treemap for proportional category breakdown
- KPI visual with goal tracking and trend sparkline
- Year range slider slicer

---

## Tools & Skills
| Tool | Usage |
|------|-------|
| Power BI Desktop | End-to-end dashboard development |
| Power Query | Data cleaning and transformation |
| DAX | 8 custom measures including time intelligence |
| Star Schema | Data modeling and relationships |
| Data Visualization | 10+ visual types across 2 pages |

---

## Dataset
- Source: Superstore Sales Dataset
- Rows: 9,800
- Columns: 18
- Period: 2015–2018
- Fields: Order ID, Order Date, Ship Date, Ship Mode, Customer Name, 
  Segment, Region, Category, Sub-Category, Product Name, Sales

---

## Author
**Mohammed Taqi Uddin Faraz**
- GitHub: github.com/taqi-jpg
- LinkedIn: linkedin.com/in/mohammed-taqi-uddin-faraz-719722349
