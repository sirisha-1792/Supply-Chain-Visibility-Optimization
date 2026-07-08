# Supply Chain Visibility Optimization - Milestone 1

## Objective

The objective of this milestone is to build a clean and efficient data model for the DataCo Smart Supply Chain dataset using Power BI. The work includes importing the dataset, performing data preprocessing, applying transformations in Power Query, designing a star schema, and creating reusable DAX measures to support future analytics and dashboard development.

## Dataset Source

**Dataset Name:** DataCo Smart Supply Chain for Big Data Analysis

**Source:** Kaggle

https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis

## Data Cleaning and Transformation Steps

The following preprocessing and transformation steps were performed using Power Query Editor:

- Imported the Supply Chain dataset into Power BI Desktop.
- Renamed the main table as **Fact_table**.
- Removed unnecessary columns:
  - Customer Email
  - Customer Password
  - Order Zipcode
- Created the following dimension tables by duplicating the Fact_table:
  - Dim_Customer
  - Dim_Product
  - Dim_Category
  - Dim_Department
  - Dim_Shipping
  - Dim_Location
- Selected only the required columns for each dimension table.
- Removed duplicate records from all dimension tables.
- Created **Shipping_id** and **Location_id** using Index Columns.
- Merged Dim_Shipping and Dim_Location with the Fact_table.
- Verified and corrected data types wherever required.
- Created a **Dim_Date** table using DAX.
- Added Year, Month Number, Month, Quarter, Week, Day, and Day Name columns to the Date table.
- Established relationships between the Fact_table and all dimension tables.

## Data Model Overview

A Star Schema data model was designed to improve query performance and simplify reporting.

### Fact Table
- Fact_table

### Dimension Tables
- Dim_Customer
- Dim_Product
- Dim_Category
- Dim_Department
- Dim_Shipping
- Dim_Location
- Dim_Date

### Relationships
- One-to-Many relationships were created between each dimension table and the Fact_table.
- An active relationship was created between **Dim_Date[Date]** and **Fact_table[order date (DateOrders)]**.
- An inactive relationship was created between **Dim_Date[Date]** and **Fact_table[shipping date (DateOrders)]** to support shipping date analysis using DAX.

## Tools Used

- Microsoft Power BI Desktop
- Power Query Editor
- DAX (Data Analysis Expressions)

## Author

Submitted as part of the *Supply Chain Visibility Optimization* project - Milestone_1
