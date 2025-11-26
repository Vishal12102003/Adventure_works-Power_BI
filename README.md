# 📊 Adventure Works Sales Dashboard

This is an end-to-end Power BI project analyzing sales performance for **Adventure Works**, a fictional bicycle and accessories company. The dashboard highlights product trends, customer segments, and regional performance to help stakeholders optimize marketing strategies and expand their business to other regions, and drive revenue growth.



---

## 🎯 Project Objective

To analyze sales performance, product trends, regional demand, and customer segments for Adventure Works, with the goal of optimizing marketing strategies and boosting revenue across targeted categories.

---

## 🧩 Problem Statement

Adventure Works Cycles is looking to broaden its market share by targeting their sales to their best customers, extending their product availability through an external Web site, and reducing their cost of sales through lower production costs. 
The business needs a clear understanding of:
- Which **products** are top or under-performers.
- Which **regions** drive the most revenue.
- Which **customer segments** yield the highest profits.
- How to make **data-driven marketing and sales decisions** based on these insights.
---

## 🚀 Steps Followed

### 🔹 Step 1: Data Import
- Loaded the `.xlsx` dataset into **Excel** for initial review.
- Then imported into **Power BI** via **Power Query Editor**.

### 🔹 Step 2: Data Profiling in Power Query
- Enabled the following options in the **View** tab:
  - `Column distribution`
  - `Column quality`
  - `Column profile`
- Changed profiling mode to:  
  ✅ **Column profiling based on entire dataset**

### 🔹 Step 3: Data Transformation
- **Appended** `Fact_Internet_Sales_New` to `FactInternetSales` → named the resulting table: `Sales`.

### 🔹 Step 4: Data Enrichment via Lookups
Performed multiple **lookup operations** to bring in relevant details:
- `ProductName` from the **Product** table to **Sales**
- `CustomerFullName` from the **Customer** table to **Sales**
- `Unit Price` from **Product** table to **Sales**

### 🔹 Step 5: Date Table and Time Intelligence
Created a **Date dimension** from the `OrderDateKey` and generated the following fields:

| Column Name | Description |
|-------------|-------------|
| `Year` | Extracted using `YEAR([OrderDateKey])` |
| `MonthNo` | `FORMAT([OrderDateKey], "mm")` |
| `MonthName` | `FORMAT([OrderDateKey], "mmmm")` |
| `Quarter` | `CONCATENATE("Q", QUARTER([OrderDateKey]))` |
| `WeekdayNo` | `WEEKNUM([OrderDateKey])` |
| `WeekdayName` | `FORMAT([OrderDateKey], "DDDD")` |
| `FinancialMonth` | Custom fiscal month calculation |
| `FinancialYear` | Custom fiscal year calculation |

### Fiscal Logic:
```DAX
FinancialMonth = IF(MONTH([OrderDateKey]) >= 4, MONTH([OrderDateKey]) - 3, MONTH([OrderDateKey]) + 9)

FinancialYear = IF(MONTH([OrderDateKey]) >= 4, YEAR([OrderDateKey]), YEAR([OrderDateKey]) - 1)

SalesAmt = [UnitPrice] * [OrderQuantity] - [UnitPriceDiscountPct]

ProductionCost = [ProductStandardCost] * [OrderQuantity]

Profit = [SalesAmt] - [ProductionCost]

```
---

Open the live dashboard here:  
[View Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiYWJkODEwMWMtZDRiOC00NTFlLWFhNWEtZGI4OGVkMTc2MGQyIiwidCI6ImE3NTk3ZTk2LTE1NDAtNDVmZi05ZGE5LTg5NWY5NzRhZDYyYSJ9)
---

### 📊 Sales Dashboard
![Dashboard Screenshot](https://github.com/user-attachments/assets/392d7d0b-531d-4b52-bc95-fc340f5f7086)

### 📊 Region Analysis 
![Image](https://github.com/user-attachments/assets/f8f72080-1289-4d94-9b6c-efac43ec08f8)

### 📊 Customer Analysis 
![Image](https://github.com/user-attachments/assets/8a8eb97d-d2c9-4337-b893-65a003766ff1)

### 📊 Product Analysis 
![Image](https://github.com/user-attachments/assets/0b301dfe-f8f9-4800-aa68-b98983fffbe6)

### 📊 Bottom 10 Product Analysis 
![Image](https://github.com/user-attachments/assets/76ca5dde-e21a-42ba-b1c3-75a2399126c8)
