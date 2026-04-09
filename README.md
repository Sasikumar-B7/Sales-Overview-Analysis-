# Sales-Overview-Analysis | Power BI Project
## 🚀 Project Overview
This project presents an interactive **Sales Performance Dashboard** built using Power BI to analyze and monitor key business metrics.  The dashboard provides a comprehensive view of sales performance, enabling stakeholders to track trends, compare year-over-year growth, and identify high-performing regions and products.

## 🎯 Problem Statement
Businesses often face challenges in:
- Tracking sales performance across different time periods
- Comparing current performance with previous years
- Identifying key drivers of revenue and profit
- Monitoring KPIs in a centralized and interactive manner

This dashboard addresses these challenges by delivering **actionable insights through data visualization**.
---
## 📌 Business Context
The dashboard is designed for:
- Sales Managers
- Business Analysts
- Decision Makers

It helps in:
- Monitoring revenue trends
- Evaluating regional and product performance
- Supporting strategic decision-making

---

## 📊 Key KPIs & Metrics
- 💰 Total Sales
- 📈 Current Year (CY) Sales
- 📉 Previous Year (PY) Sales
- 📊 Year-over-Year (YoY) Growth %
- 📦 Quantity Sold
- 💵 Profit & Profit Margin

---

## 📈 Dashboard Features
- 📅 Time-based analysis (Monthly / Yearly trends)
- 🌍 Region-wise performance breakdown
- 🛒 Product category insights
- 📊 KPI cards for quick overview
- 🎛️ Interactive slicers (Year, Region, Category)

---

## 🧠 Key Insights
- Identified **top-performing regions** contributing maximum revenue
- Analyzed **sales trends over time**
- Highlighted **growth/decline using YoY metrics**
- Detected **low-performing categories for improvement**

---

## 🛠️ Tools & Technologies Used
- Power BI Desktop
- Power Query (ETL)
- DAX (Data Analysis Expressions)
- Data Modeling (Star Schema)

---

## 🧮 Important DAX Measures

### 🔹 Current Year Metrics

```CY Sales = 
VAR SelectedYear = SELECTEDVALUE('Calendar Table'[Year])
VAR CurrentYearSales = CALCULATE([Total Sales], 'Calendar Table'[Year]= SelectedYear)
RETURN CurrentYearSales```


``` CY Profit =
VAR SelectedYear =
    SELECTEDVALUE ( 'Calendar Table'[Year] )
VAR CurrentYearProfit =
    CALCULATE ( [Total Profit], 'Calendar Table'[Year] = SelectedYear )
RETURN
    CurrentYearProfit ```

``` CY Qty =
VAR SelectedYear =
    SELECTEDVALUE ( 'Calendar Table'[Year] )
**VAR CurrentYearQuantity =
    CALCULATE ( [Total Quantity], 'Calendar Table'[Year] = SelectedYear )
RETURN
    CurrentYearQuantity```
---

**🔹 Previous Year Metrics **

```PY Sales = 
VAR SelectedYear = MAX('Calendar Table'[Year])
VAR PreviousYearSales = 
CALCULATE(
        [Total Sales],
        FILTER(
            ALL('Calendar Table'),
            'Calendar Table'[Year] = SelectedYear - 1
        )
    )
RETURN PreviousYearSales```

```PY Profit = 
VAR SelectedYear = MAX('Calendar Table'[Year])
VAR PreviousYearProfit = 
CALCULATE(
        [Total Profit],
        FILTER(
            ALL('Calendar Table'),
            'Calendar Table'[Year] = SelectedYear - 1
        )
    )
RETURN PreviousYearProfit ```

```PY Qty = 
VAR SelectedYear = MAX('Calendar Table'[Year])
VAR PreviousYearQuantity = 
CALCULATE(
        [Total Quantity],
        FILTER(
            ALL('Calendar Table'),
            'Calendar Table'[Year] = SelectedYear - 1
        )
    )
RETURN PreviousYearQuantity```


