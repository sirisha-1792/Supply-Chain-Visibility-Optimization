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

## 3. Technology Stack

The following technologies and tools were used:

- Microsoft Power BI
- Power Query
- DAX

## 4. Data Sources

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

## Inventory Turnover Calculation Approach

Inventory turnover was calculated to measure how efficiently inventory is being utilized.

The inventory turnover ratio was calculated using:

Inventory Turnover Ratio = Total Sales / Average Inventory Value

The DAX measure used was:

Inventory Turnover Ratio =
DIVIDE(
    [Total Sales],
    [Avg Inventory Value],
    0
)

# Slow-Moving and Fast-Moving Inventory Identification Logic

Inventory performance was analyzed using the number of days since the last sale.

The inventory status classification logic was:

Out of Stock: Stock quantity is equal to zero.
Dead Stock: No sale for more than 90 days and stock quantity is greater than zero.
Slow-Moving: No sale for more than 30 days and up to 90 days.
Active / Fast-Moving: Products with sales activity within 30 days.

The DAX logic used was:

Stock Status =
VAR DaysIdle =
    Fact_table[Days Since Last Sale (Col)]
VAR Qty =
    Fact_table[stock_qty]
RETURN
SWITCH(
    TRUE(),
    Qty = 0,
        "Out of Stock",
    DaysIdle > 90 && Qty > 0,
        "Dead Stock",
    DaysIdle > 30 && DaysIdle <= 90,
        "Slow-Moving",
    "Active"
)

## Slow-moving inventory was identified using:

Days Since Last Sale > 30 days
AND
Days Since Last Sale <= 90 days

## Dead stock was identified using:

Days Since Last Sale > 90 days
AND
Stock Quantity > 0

Products classified as Active and having high sales quantity, high sales volume, and high inventory turnover were considered fast-moving or strong-performing products.

This classification helps identify products that may require promotional activities, inventory reduction, demand analysis, or replenishment planning.

# Delivery Performance Analysis Methodology

Delivery performance was analyzed using order delivery status, actual shipping time, scheduled shipping time, delivery risk indicators, region, shipping mode, and time-based trends.

The main delivery performance measures included:

On-Time Delivery %
Late Delivery %
Advance Shipping %
Average Days for Shipping (Real)
Average Days for Shipment (Scheduled)
Lead Time Variance
Late Delivery Risk %
Risk vs Actual Accuracy
Regional Late Rate

On-time, late, and advance shipping performance were analyzed based on delivery status.

## The delivery lead time analysis compared actual shipping time with scheduled shipping time:

Lead Time Variance = Average Actual Shipping Days-Average Scheduled Shipping Days

A positive lead time variance indicates that actual shipping took longer than scheduled.

## Late delivery risk was analyzed using the late delivery risk indicator. The percentage of risk-flagged orders was calculated as:

Late Delivery Risk % =
Total Risk Flagged Orders / Total Orders

Delivery performance was also analyzed by:
Region
Shipping Mode
Product Category
Product
Date

This allows delivery issues to be analyzed from a regional level down to the product level using drill-down functionality.

Delivery trends over time were analyzed using the date dimension and the Late Delivery % Trend measure.

# Key Insights and Business Recommendations
## Key Insights

The dashboards provide insights into inventory and delivery performance.

-- Inventory analysis helps identify:

Products with high inventory turnover.
Slow-moving inventory that has not been sold for more than 30 days.
Dead stock that has not been sold for more than 90 days.
Products that are below safety stock levels.
Products that require replenishment based on reorder levels.
Inventory value and stock concentration across warehouses and regions.
Product categories with stronger or weaker sales performance.

-- Delivery analysis helps identify:

The percentage of on-time deliveries.
The percentage of late deliveries.
The percentage of advance shipments.
Regions with higher late delivery rates.
Shipping modes with differences between actual and scheduled delivery time.
Orders that have been flagged as having late delivery risk.
Changes in delivery performance over time.

# Business Recommendations

-- Inventory Recommendations

Monitor slow-moving products regularly and consider promotions, discounts, bundling, or inventory redistribution.
Review dead stock and consider liquidation or other strategies to reduce tied-up capital.
Prioritize replenishment for products below safety stock levels.
Use reorder levels to improve inventory planning and reduce the risk of stockouts.
Monitor fast-moving products closely to maintain sufficient inventory availability.
Redistribute inventory between warehouses based on regional demand and product performance.

-- Delivery Recommendations

Investigate regions with high late delivery rates and identify transportation or operational issues.
Monitor orders with high late delivery risk and take proactive action before delays occur.
Compare shipping modes based on actual delivery time, scheduled delivery time, and lead time variance.
Improve delivery planning in areas where actual shipping times consistently exceed scheduled times.
Use regional and product-level drill-down analysis to identify the specific causes of delivery delays.
Continuously monitor delivery trends to identify recurring or seasonal performance issues.