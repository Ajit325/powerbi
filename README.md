# AdventureWorks Power BI Sales Dashboard

## Project Overview

This is a portfolio and learning project built with Microsoft Power BI using the Microsoft AdventureWorks sample dataset. The dashboard was created while as demo and was extended as a hands-on exercise in data modeling, DAX, and business reporting.

The goal is to convert raw sales, product, customer, and geography data into clear, interactive insights for business users.

> Note: AdventureWorks is Microsoft sample data. This project does not contain production or confidential business data.

## Business Questions Answered

- What are total sales, profit, order volume, and order quantity?
- How are sales trending by month, quarter, and year?
- Which product categories and products generate the most revenue and profit?
- Which customer segments contribute the most sales?
- Which geographic regions and countries perform best?
- How does actual performance compare with targets, where target data is available?

## Dashboard Pages

### 1. Executive Summary

- Total Revenue
- Total Profit
- Total Orders
- Total Quantity Sold
- Monthly sales trend
- Key performance indicators (KPIs)

### 2. Product Analysis

- Sales by product category and subcategory
- Top and bottom products by revenue
- Product-level profit analysis
- Product performance trends

### 3. Customer Analysis

- Sales by customer
- Customer contribution and ranking
- Customer demographics and segmentation
- Repeat customer analysis, where available in the source data

### 4. Geographic Analysis

- Sales by country, region, and city
- Geographic sales distribution
- Regional performance comparison

## Data Model

The report follows a star-schema approach to make relationships clear and improve reporting performance.

### Fact Tables

- `FactInternetSales` - Internet sales transactions
- `FactResellerSales` - Reseller sales transactions, if included

### Dimension Tables

- `DimDate` - Calendar and time intelligence fields
- `DimProduct` - Product information
- `DimProductCategory` - Product category hierarchy
- `DimProductSubcategory` - Product subcategory hierarchy
- `DimCustomer` - Customer details
- `DimGeography` - Country, region, and city information
- `DimSalesTerritory` - Sales territory information

## Key DAX Measures

Examples of core measures used in the report:

```DAX
Total Sales = SUM(FactInternetSales[SalesAmount])

Total Orders = DISTINCTCOUNT(FactInternetSales[SalesOrderNumber])

Total Quantity = SUM(FactInternetSales[OrderQuantity])

Total Cost = SUM(FactInternetSales[TotalProductCost])

Total Profit = [Total Sales] - [Total Cost]

Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)

Sales Previous Year =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(DimDate[Date])
)

Sales YoY % =
DIVIDE([Total Sales] - [Sales Previous Year], [Sales Previous Year], 0)
```

## Tools and Skills Demonstrated

- Microsoft Power BI Desktop
- Power Query for data preparation and transformation
