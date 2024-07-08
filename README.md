# Manufacturer Analysis Power BI Project

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Sources](#data-sources)
3. [Data Cleaning and Preparation](#data-cleaning-and-preparation)
4. [Data Modeling](#data-modeling)
5. [DAX Measures and Calculations](#dax-measures-and-calculations)
6. [Visualizations](#visualizations)
7. [Key Insights](#key-insights)
8. [Future Improvements](#future-improvements)
9. [Acknowledgements](#acknowledgements)

## Project Overview

This Power BI project provides a Manufacturer Analysis dashboard with insights into:

- Urban vs. rural market performance
- Revenue by product category and country
- Year-over-year growth trends
- Manufacturer contributions comparison

Key features:
- Interactive visualizations with drill-down capabilities
- Year-over-year comparisons
- Geographical revenue distribution maps
- Product category performance metrics

The project demonstrates skills in data modeling, DAX calculations, and creating visualizations, turning raw data into actionable insights for business decisions.

## Data Sources
- Sales data (CSV file)
- Product catalog (Excel file)
- Geographic information (CSV file)

## Data Cleaning and Preparation
1. Removed duplicate entries in the sales data
2. Standardized date formats across all tables
3. Created a custom column 'ZipCountry' by concatenating Zip and Country fields
4. Handled missing values in the product catalog by imputing with category averages

## Data Modeling
The data model consists of the following tables and relationships:
- Sales (fact table)
- Product (dimension table)
- Manufacturer (dimension table)
- Geography (dimension table)
- Date (dimension table)

Key relationships:
- Sales to Product (many-to-one on ProductID)
- Sales to Geography (many-to-one on ZipCountry)
- Sales to Date (many-to-one on Date)
- Product to Manufacturer (many-to-one on ManufacturerID)

## DAX Measures and Calculations
1. Total Revenue: `Total Revenue = SUM(Sales[Revenue])`
2. PY Sales: `PY Sales = CALCULATE(SUM(Sales[Revenue]), SAMEPERIODLASTYEAR('Date'[Date]))`
3. Year-over-Year Growth: `YoY Growth = DIVIDE(SUM(Sales[Revenue]) - [PY Sales], [PY Sales])`
4. % Growth: `% Growth = DIVIDE(SUM(Sales[Revenue]) - [PY Sales], [PY Sales])`

Key measures explained:
- Total Revenue: Calculates the sum of all revenue in the Sales table.
- PY Sales: Calculates the sales for the same period in the previous year.
- YoY Growth: Calculates the year-over-year growth in absolute terms.
- % Growth: Calculates the year-over-year growth as a percentage.

These measures form the foundation for our trend analysis and performance comparisons across different time periods.

## Visualizations
1. Revenue by Category (Stacked Bar Chart)
2. Sum of Revenue by Country (Map)
3. Revenue and Growth Trend by Year (Combo Chart)
4. Top Manufacturers by Revenue (Tree Map)
5. Sales Distribution: Urban vs Rural (Pie Chart)
6. Key Performance Indicators (Card Visuals)

## Key Insights
1. Urban sales contribute to 97.28% of total revenue
2. The 'Extreme' category shows the highest growth at 61.94%
3. USA is the top market by revenue
4. There's a consistent upward trend in revenue from 2014 to 2021

## Future Improvements
1. Incorporate more granular geographic data for deeper regional analysis
2. Add predictive analytics for sales forecasting
3. Implement what-if parameters for scenario analysis
