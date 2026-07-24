## Milestone 2: Inventory Analytics & Delivery Performance

## 1. Project Overview

This project focuses on developing a Supply Chain Visibility and Optimization solution using Microsoft Power BI.

The objective of Milestone 2 is to analyze two important areas of supply chain operations:

1. Inventory Analytics
2. Delivery Performance

The project transforms operational supply chain data into interactive dashboards that help organizations monitor inventory efficiency, identify slow-moving products, analyze stock levels, evaluate reorder requirements, and measure delivery performance.

The Power BI solution uses data modeling, Power Query transformations, calculated columns, DAX measures, relationships, interactive filters, drill-down functionality, and visual analytics.

## 2. Objectives

The main objectives of this milestone are:

- Analyze inventory turnover performance.
- Identify slow-moving and dead stock.
- Identify active and fast-moving inventory.
- Monitor stock quantities and inventory value.
- Compare stock levels with safety stock and reorder levels.
- Analyze inventory performance by warehouse.
- Analyze inventory performance by region.
- Analyze inventory performance by product category.
- Analyze inventory trends over time.
- Analyze on-time and delayed deliveries.
- Measure actual and scheduled delivery lead times.
- Evaluate late delivery risk.
- Analyze delivery performance by region.
- Analyze delivery performance by shipping mode.
- Analyze delivery trends over time.
- Implement regional and product-level drill-down analysis.
- Provide actionable business recommendations based on the analysis.

---

# 3. Technology Stack

The following technologies and tools were used:

- Microsoft Power BI
- Power Query
- DAX

# 4. Data Sources

The project uses supply chain operational data containing information about:

- Orders
- Customers
- Products
- Product Categories
- Departments
- Shipping
- Locations
- Warehouses
- Inventory
- Suppliers
- Delivery performance

The data was loaded into Power BI and transformed using Power Query before being used for data modeling and analysis.

# 5. Data Preparation and Data Model

The data was transformed in Power Query to create a dimensional data model.

The model contains a central fact table and multiple dimension tables.

### Fact_table

The fact table contains transactional and operational supply chain data, including:

- Order information
- Product information
- Customer information
- Sales
- Profit
- Quantity
- Shipping information
- Delivery status
- Delivery risk
- Inventory information
- Warehouse information
- Regional information

The fact table is used as the primary source for transactional analysis.

---

# 6. Dimension Tables

The following dimension tables were created:

## Dim_Customer

Contains customer-related information such as:
- Customer ID
- Customer city
- Customer country
- Customer first name
- Customer last name
- Customer segment
- Customer street
- Customer ZIP code
- Customer state

## Dim_Product

Contains product-related information such as:
- Product Card ID
- Product Category ID
- Product Name
- Product Price
- Product Status
- Category ID
- Department ID

## Dim_Category

Contains category-level information.

## Dim_Department

Contains department-level information.

## Dim_Shipping

Contains shipping-related information such as:
- Days for shipping
- Days for shipment
- Delivery status
- Late delivery risk
- Shipping date
- Shipping mode
- Shipping ID

## Dim_Location

Contains geographical information such as:
- Market
- Order city
- Order country
- Order region
- Order state
- Location ID

## Dim_Date

A dedicated date table was created using DAX.
The date table contains:
- Date
- Year
- Month Number
- Month
- Quarter
- Week
- Day
- Day Name

The date table is used for time-based analysis and trend analysis.

## Dim_Supplier

Contains supplier performance information such as:
- Supplier name
- Lead time
- Quality score
- Reliability percentage

## Dim_Warehouse

Contains warehouse-related information such as:
- Warehouse ID
- Warehouse Name
- Region
- Capacity
- Utilization Percentage

## Dim_Inventory

Contains inventory-related information such as:
- Warehouse ID
- Product Card ID
- Stock Quantity
- Safety Stock
- Reorder Level
- Inventory Level
- Last Restock Date
- Inventory ID

# 7. Data Model Relationships

The data model connects the fact table with the dimension tables to support filtering and analytical reporting.

Important relationships include:

Dim_Customer (1) ─────── (*) Fact_table

Dim_Product (1) ──────── (*) Fact_table

Dim_Category (1) ─────── (*) Dim_Product

Dim_Department (1) ──── (*) Dim_Product

Dim_Shipping (1) ─────── (*) Fact_table

Dim_Location (1) ─────── (*) Fact_table

Dim_Date (1) ─────────── (*) Fact_table

Dim_Warehouse (1) ───── (*) Fact_table