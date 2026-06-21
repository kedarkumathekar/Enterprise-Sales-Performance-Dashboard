# Enterprise Sales Performance Dashboard (QBR Report)

## Project Overview
This repository contains a full-scale Power BI implementation designed to deliver a single-page executive sales dashboard for Quarterly Business Reviews (QBR). The project processes fragmented multi-year sales directories, automates analytical data cleaning via low-level M functions, standardizes geospatial data types, structures a strict star-schema model, and outputs advanced time-intelligence metrics via DAX.

---

## Technical Specifications & Requirements

### 1. Robust Data Integration (ETL)
* **Dynamic Folder Loading**: Implemented a dynamic binary file combiner targeting the year-partitioned `Sales` directory. 
* **Folder Resilience**: Engineered data refresh pipelines to be strictly resilient to environmental changes:
  * Deleting or missing an existing historical file will not interrupt or trigger schema breaking errors during processing.
  * Dropping new automated yearly sales tracking spreadsheets into the source folder dynamically aggregates, maps, and updates the fact table directly upon refresh.
* **Geospatial Processing**: Parsed composite spatial string metrics to structurally isolate and clean `Country` and `City` properties from individual raw `Location` vectors. Data fields have been hard-typed to map attributes to support native interactive geometric geographic mapping elements.

## Analytical DAX Measures
* The following foundational KPI engines and advanced operational time-intelligence calculation blocks were compiled inside the model framework:
* **Financial Performance Indicators**

Total Revenue: Combines dimensional properties against raw volumetric transactional facts.
### Total Revenue = sum(Sales[Units] x 'Product'[Retail Price])

* Total Cost: Maps direct expenditures across material dimensions
 ### TotalCost = sum(Sales[Units] x 'Product'[StandardCost])
Gross Profit: Direct calculated operational spread margin.
### GrossProfit = [Total Revenue] - [Total Cost]
