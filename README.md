# 📊 Sales Overview Analysis | Power BI Project

---

## 🚀 Project Overview

This project presents an interactive **Sales Performance Dashboard** built using Power BI to analyze and monitor key business metrics. The dashboard provides a comprehensive view of sales performance, enabling stakeholders to track trends, compare year-over-year growth, and identify high-performing regions and products.

---

## 🎯 Problem Statement

Businesses often face challenges in:

* Tracking sales performance across different time periods
* Comparing current performance with previous years
* Identifying key drivers of revenue and profit
* Monitoring KPIs in a centralized and interactive manner

This dashboard addresses these challenges by delivering **actionable insights through data visualization**.

---

## 📌 Business Context

The dashboard is designed for:

* Sales Managers
* Business Analysts
* Decision Makers

It helps in:

* Monitoring revenue trends
* Evaluating regional and product performance
* Supporting strategic decision-making

---

## 📊 Key KPIs & Metrics

* 💰 Total Sales
* 📈 Current Year (CY) Sales
* 📉 Previous Year (PY) Sales
* 📊 Year-over-Year (YoY) Growth %
* 📦 Quantity Sold
* 💵 Profit & Profit Margin

---

## 📈 Dashboard Features

* 📅 Time-based analysis (Monthly / Yearly trends)
* 🌍 Region-wise performance breakdown
* 🛒 Product category insights
* 📊 KPI cards for quick overview
* 🎛️ Interactive slicers (Year, Region, Category)

---

## 🛠️ Tools & Technologies Used

* Power BI Desktop
* Power Query (ETL)
* DAX (Data Analysis Expressions)
* Data Modeling (Star Schema)

---

## 🧮 Important DAX Measures

### 🔹 Current Year Metrics

```DAX
CY Sales = 
VAR SelectedYear = SELECTEDVALUE('Calendar Table'[Year])
VAR CurrentYearSales = CALCULATE([Total Sales], 'Calendar Table'[Year]= SelectedYear)
RETURN CurrentYearSales```

```DAX
CY Profit =
VAR SelectedYear =
    SELECTEDVALUE ( 'Calendar Table'[Year] )
VAR CurrentYearProfit =
    CALCULATE ( [Total Profit], 'Calendar Table'[Year] = SelectedYear )
RETURN
    CurrentYearProfit```

```DAX
CY Qty =
VAR SelectedYear =
    SELECTEDVALUE ( 'Calendar Table'[Year] )
VAR CurrentYearQuantity =
    CALCULATE ( [Total Quantity], 'Calendar Table'[Year] = SelectedYear )
RETURN
    CurrentYearQuantity
```

---

### 🔹 Previous Year Metrics

```DAX
PY Sales = 
VAR SelectedYear = MAX('Calendar Table'[Year])
VAR PreviousYearSales = 
CALCULATE(
    [Total Sales],
    FILTER(
        ALL('Calendar Table'),
        'Calendar Table'[Year] = SelectedYear - 1
    )
)
RETURN PreviousYearSales
```

```DAX
PY Profit = 
VAR SelectedYear = MAX('Calendar Table'[Year])
VAR PreviousYearProfit = 
CALCULATE(
    [Total Profit],
    FILTER(
        ALL('Calendar Table'),
        'Calendar Table'[Year] = SelectedYear - 1
    )
)
RETURN PreviousYearProfit
```

```DAX
PY Qty = 
VAR SelectedYear = MAX('Calendar Table'[Year])
VAR PreviousYearQuantity = 
CALCULATE(
    [Total Quantity],
    FILTER(
        ALL('Calendar Table'),
        'Calendar Table'[Year] = SelectedYear - 1
    )
)
RETURN PreviousYearQuantity
```

---

### 🔹 Year-over-Year (YoY) Metrics

```DAX
YoY Sales = 
VAR CurrentYearSales = [CY Sales]
VAR PreviousYearSales = [PY Sales] 
VAR YoYChange = DIVIDE(CurrentYearSales - PreviousYearSales, PreviousYearSales)
VAR PRINT = 
    IF(
        YoYChange > 0,
        UNICHAR(9650) & " " & FORMAT(YoYChange, "0%"),
        UNICHAR(9660) & " " & FORMAT(YoYChange, "0%")
    )
RETURN PRINT
```

```DAX
YoY Qty = 
VAR CurrentYearQuantity = [CY Qty]
VAR PreviousYearQuantity = [PY Qty] 
VAR YoYChange = DIVIDE(CurrentYearQuantity - PreviousYearQuantity, PreviousYearQuantity)
VAR PRINT = 
    IF(
        YoYChange > 0,
        UNICHAR(9650) & " " & FORMAT(YoYChange, "0%"),
        UNICHAR(9660) & " " & FORMAT(YoYChange, "0%")
    )
RETURN PRINT
```

```DAX
YoY Profit = 
VAR CurrentYearProfit = [CY Profit]
VAR PreviousYearProfit = [PY Profit] 
VAR YoYChange = DIVIDE(CurrentYearProfit - PreviousYearProfit, PreviousYearProfit)
VAR PRINT = 
    IF(
        YoYChange > 0,
        UNICHAR(9650) & " " & FORMAT(YoYChange, "0%"),
        UNICHAR(9660) & " " & FORMAT(YoYChange, "0%")
    )
RETURN PRINT
```

---

## 🔍 Findings

* Sales show **seasonal patterns**, with certain months contributing significantly higher revenue
* A few regions consistently outperform others, indicating **strong market presence**
* Some product categories generate high sales volume but **lower profit margins**
* YoY comparison highlights both **growth opportunities and declining segments**

---

## 💡 Key Insights

* 📈 **Top-performing regions** drive the majority of total revenue
* 📉 Certain regions require **strategic intervention to improve performance**
* 🛒 High-selling products are not always the most profitable — **margin optimization needed**
* 📊 YoY metrics help quickly identify **business growth trends and risks**
* 🎯 Data-driven decisions can significantly improve **sales strategy and profitability**

---

## 📬 Conclusion

This dashboard enables stakeholders to make informed decisions by providing a **clear, interactive, and data-driven view of sales performance**. It helps in identifying opportunities, addressing inefficiencies, and driving business growth.

---


