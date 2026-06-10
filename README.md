# 📊 Sales & Customer Intelligence Dashboard

## 📌 Project Overview

The Sales & Customer Intelligence Dashboard is an interactive Power BI solution designed to provide actionable insights into sales performance, customer behavior, and product analytics. The dashboard enables stakeholders to monitor key business metrics, identify trends, evaluate product performance, and make data-driven decisions through dynamic visualizations and filtering capabilities.

The report consists of three dedicated pages:

1. Executive Dashboard
2. Customer Dashboard
3. Product Dashboard

---

# 🎯 Project Objectives

- Build a robust Star Schema data model.
- Create interactive dashboards using Power BI.
- Implement DAX Measures and Calculated Columns.
- Apply Time Intelligence calculations.
- Analyze Sales, Customers, Returns, and Products.
- Enable dynamic filtering and drill-down analysis.
- Provide business insights through KPI tracking.

---

# 🗂 Dataset Tables

The project uses the following tables:

| Table Name | Description |
|------------|-------------|
| Customer_Dim | Customer information |
| Product_Dim | Product information |
| Date_Dim | Calendar and date attributes |
| Sales_Fact | Sales transaction records |
| Returns_Fact | Product return transactions |
| Region_Dim | Regional information |

---

# 🔑 Data Model

## Primary Keys

| Table | Primary Key |
|---------|------------|
| Customer_Dim | CustomerID |
| Product_Dim | ProductID |
| Date_Dim | DateID |
| Sales_Fact | SaleID |
| Returns_Fact | ReturnID |
| Region_Dim | RegionID |

---

## Foreign Keys

| Fact Table | Foreign Key | Related Table |
|------------|------------|---------------|
| Sales_Fact | CustomerID | Customer_Dim |
| Sales_Fact | ProductID | Product_Dim |
| Sales_Fact | DateID | Date_Dim |
| Returns_Fact | SaleID | Sales_Fact |
| Customer_Dim | Region | Region_Dim |

---

# ⭐ Star Schema Relationship

```text
Region_Dim
     |
     ▼
Customer_Dim
     |
     ▼
Sales_Fact ◄──── Returns_Fact
     ▲
     |
 ┌───┴────┐
 ▼        ▼
Date_Dim Product_Dim
```

Relationship Type:

```text
Region_Dim (1) → Customer_Dim (*)

Customer_Dim (1) → Sales_Fact (*)

Product_Dim (1) → Sales_Fact (*)

Date_Dim (1) → Sales_Fact (*)

Sales_Fact (1) → Returns_Fact (*)
```

---

# 📈 DAX Measures Created

## Sales Measures

- Total Sales
- Total Orders
- Total Customers
- Total Returns
- Return Rate %
- Total Units Sold
- Average Order Value
- Average Product Price

---

## Time Intelligence Measures

- Sales YTD
- Sales MTD
- Sales QTD
- Previous Month Sales
- Previous Month Orders
- Previous Month Returns
- Previous Year Sales
- YOY Growth %

---

## Ranking Measures

- Product Rank
- Customer Rank

---

# 🧮 Calculated Columns Created

## Customer_Dim

```DAX
Full Name =
Customer_Dim[FirstName] &
" " &
Customer_Dim[LastName]
```

---

## Date_Dim

```DAX
Year Month =
FORMAT(Date_Dim[Date],"YYYY-MMM")
```

---

## Sales_Fact

```DAX
Product Price =
RELATED(Product_Dim[Price])
```

```DAX
Category =
RELATED(Product_Dim[Category])
```

```DAX
Customer Segment =
RELATED(Customer_Dim[Segment])
```

---

# 📄 Dashboard Pages

---

# 1️⃣ Executive Dashboard

### Purpose

Provides a high-level overview of overall sales performance and business metrics.

### KPIs

- Total Sales
- Total Orders
- Total Customers
- Total Returns
- Return Rate %

### Visualizations

- Monthly Sales Trend
- Sales by Category
- Top 10 Products
- Monthly Revenue KPI
- Monthly Orders KPI
- Monthly Returns KPI

### Key Insights

- Track overall business performance.
- Monitor sales trends over time.
- Identify best-performing product categories.
- Analyze return performance.

---

# 2️⃣ Customer Dashboard

### Purpose

Provides detailed insights into customer behavior and purchasing patterns.

### KPIs

- Total Customers
- Total Orders
- Average Order Value
- Return Rate %

### Visualizations

- Customer Segment Distribution
- Customer Sales Trend
- Top 10 Customers by Sales
- Customer Detail Matrix
- Best Customer (Most Orders)
- Highest Revenue Customer

### Key Insights

- Identify valuable customers.
- Analyze customer segments.
- Monitor purchasing behavior.
- Evaluate customer contribution to revenue.

---

# 3️⃣ Product Dashboard

### Purpose

Provides product-level performance analysis and sales effectiveness insights.

### KPIs

- Total Units Sold
- Total Sales
- Average Product Price

### Visualizations

- Monthly Product Sales Trend
- Monthly Product Returns Trend
- Product Performance Metrics
- Dynamic KPI Parameter Selection

### Key Insights

- Evaluate product demand.
- Track product sales performance.
- Monitor return trends.
- Identify opportunities for product optimization.

---

# 🎨 Dashboard Features

### Interactive Filters

- Date Range Filter
- Dynamic KPI Selector
- Page Navigation Buttons

### Visual Enhancements

- Conditional Formatting
- KPI Cards
- Trend Lines
- Dynamic Titles
- Interactive Charts

### User Experience

- Multi-page Navigation
- Clean Dashboard Layout
- Business-Oriented Design
- Responsive Visual Structure

---

# 🛠 Tools Used

- Microsoft Power BI Desktop
- Power Query
- DAX (Data Analysis Expressions)

---

# 📋 Business Value

This dashboard transforms raw transactional data into meaningful business insights. It helps management monitor organizational performance, understand customer behavior, analyze product effectiveness, and make informed strategic decisions through an intuitive and interactive reporting experience.

---
