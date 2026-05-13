# Data Modelling

This folder documents the data model used for the Business 360 Power BI dashboard.

The model follows a hybrid structure, combining a fact constellation approach with partially snowflaked dimensions. This structure was used to support analysis across Finance, Sales, Marketing, Supply Chain and Executive dashboard views.

## Model Type

The data model is best described as a hybrid star/snowflake model.

It is not a pure star schema because some dimension tables are further normalised into supporting lookup tables. It is also not a pure snowflake schema because the main reporting structure still uses shared dimension tables connected to multiple fact tables.

## Why This Model Structure Was Used

The dashboard required analysis across multiple business areas, including sales performance, financial performance, forecast accuracy, market share, cost analysis and profitability. A single fact table would not have been suitable because different business metrics came from different source tables and required different levels of granularity.

To manage this, the model uses multiple fact tables connected to common dimensions such as date, product, customer and market.

## Key Fact Tables

The model includes multiple fact and transaction-level tables, including:

- `fact_actuals_estimates`
- `fact_forecast_monthly`
- `post_invoice_deductions`
- `manufacturing_cost`
- `freight_cost`
- `Operational Expense`
- `marketshare`
- `NsGmTarget`

These tables support calculations related to:

- Net sales
- Gross margin
- Net profit
- Forecast accuracy
- Net error
- Absolute error
- Market share
- Operational expense
- Manufacturing and freight cost
- Target comparison

## Key Dimension Tables

The main dimension tables include:

- `dim_date`
- `dim_product`
- `dim_customer`
- `dim_market`
- `fiscal_year`
- `category`
- `sub_zone`

These dimensions allow the dashboard to analyse performance by:

- Date
- Fiscal year
- Month
- Product
- Segment
- Category
- Customer
- Market
- Region
- Sub-zone

## Snowflaked Dimension Structure

Some dimensions are normalised into supporting lookup tables. For example:

- `dim_market` is connected with `sub_zone`
- `dim_product` is connected with `category`
- `dim_date` is connected with `fiscal_year`

This creates a partial snowflake structure and helps organise related reference data without duplicating values across multiple tables.

## Relationship Design

The model uses one-to-many relationships between dimension tables and fact tables wherever possible.

Dimension tables act as filters, while fact tables store measurable business values. This supports consistent filtering across dashboard pages and allows measures to respond correctly to slicers such as year, quarter, market, customer and product.

## Business Purpose

The data model was designed to support business questions such as:

- How are net sales, gross margin and net profit performing?
- Which customers and products are driving revenue?
- Which regions and markets are more profitable?
- How accurate is the forecast compared with last year?
- Which products or customers have higher supply chain risk?
- How does market share compare against competitors?
- Where are costs impacting profitability?

## Modelling Benefits

This structure helped achieve:

- Consistent filtering across all dashboard pages
- Reusable dimensions across multiple fact tables
- Clear separation between business measures and descriptive attributes
- Better support for DAX calculations
- Flexible analysis across customer, product, market and time dimensions
- Scalable structure for multi-page Power BI reporting


## Note

The original dataset is not included in this repository due to file size, confidentiality and data-sharing restrictions. This folder explains the modelling approach used to structure the data for reporting and analysis.
