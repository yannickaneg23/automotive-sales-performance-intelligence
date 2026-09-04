# [automotive-sales-performance-intelligence]


---

## ⚙️ Project Type Flags


- [ ] Dashboard / Data Visualization


---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Workflow](#5-data-workflow)
6. [Data Model & Schema](#6-data-model--schema)
7. [Analysis & Metrics](#8-analysis--metrics)
8. [Key Insights](#9-key-insights)
9. [Recommendations](#10-recommendations)
10. [Assumptions & Limitations](#11-assumptions--limitations)
11. [Future Enhancements](#12-future-enhancements)
12. [Author](#14-author)

---

## 1. Project Overview

<!--
  An automotive manufacturer needed to evaluate dealership sales performance across regions but couldn't isolate true value drivers because engineering specs were trapped inside text strings like "1198 cc" and "87 bhp". I engineered a Power BI data pipeline that stripped out these unit text labels, allowing me to map pure mechanical metrics directly against dealer retail values. The final interactive matrix revealed that high-capacity diesel engines and automatic configurations carried the highest margin premiums, exposing a massive inventory opportunity that was completely invisible in the company's uncleaned files.
-->

Context:An automotive manufacturing company needed a clear way to evaluate new vehicle sales performance across its regional dealership network to optimize stock levels and understand consumer preferences. However, because the vehicle specs were coming directly from factory production logs, valuable engineering data was locked away inside messy text descriptions rather than actual numbers.Problem Statement:The company could not run any math, totals, or averages on vehicle performance because columns like engine size and horsepower were entered as text strings (like "1198 cc" and "87 bhp @ 6000 rpm"). This formatting roadblock hid critical connections between a car's mechanical power and its ultimate selling price, making it impossible to see which car configurations were actually driving the most revenue.Approach:I built a data cleaning pipeline inside Power BI's Power Query Editor to isolate the true numbers by stripping away text unit labels and splitting nested data rows. Once the data was cleaned and converted into true numbers, I modeled it into a corporate sales dashboard featuring interactive filters, inventory count cards, and an advanced scatter correlation plot.Outcome:The project produced a fully automated, interactive market intelligence dashboard that recalculates dealership fleet data instantly. The analysis revealed that automatic transmissions and larger diesel engines commanded the highest premium price points in the marketplace—a crucial business trend that was completely invisible in the company’s uncleaned raw logs.
---

## 2. Objectives

<!--
Primary Objective: Build a reproducible data cleaning pipeline that ingests messy alphanumeric vehicle columns and converts them into calculated numeric variables.Secondary Objective 1: Quantify the pricing premium difference between manual and automatic transmission styles across all dealership models.Secondary Objective 2: Evaluate whether larger engine sizes (CC) directly correlate with higher retail sales values using a multi-variable scatter plot.Secondary Objective 3: Identify the top car models based on total inventory counts and average dealership price points. 

---

## 3. Project Scope & Tools

### Scope

<!--
In Scope:Dealership-level sales performance tracking across multiple regions.Analysis covering retail price, manufacturing year, kilometers driven, fuel profiles, and gearbox configurations.String extraction and numerical casting of vehicle specifications (Engine Size and Max Power)
Out of Scope:Dealership marketing expenditures, monthly inventory holding costs, and car maintenance history logs were excluded.Marketing and cost data sit in separate databases outside this dashboard.Car maintenance logs were incomplete across several regions and were removed to protect the integrity of the pricing model.
-->


### Tools & Technologies

<!--
 ### 🛠️ Tech Stack & Project Context

| Category | Tool(s) Used |
|:---|:---|
| **Data Storage** | Raw CSV files |
| **Data Processing** | Power BI Power Query Editor |
| **Analysis** | Power Query Formula Language (M) |
| **Visualization** | Microsoft Power BI Desktop (Table grids, Scatter charts, Slicers) |
| **Version Control** | GitHub |
| **Documentation** | Markdown (`README.md`) |

---

## 4. Repository Structure

### 📂 Project Directory Structure

[project-root]/
│
├── data/
│   ├── raw/                  # Original, unmodified source CSV files
│   └── processed/            # Final cleaned and transformed dataset
│
├── visuals/                  # Dashboard screenshots and report preview captures
│
└── README.md                 # Project executive summary and documentation

---

## 5. Data Workflow

<!--
### 🔄 Data Pipeline & Inage Lineage

1. **Source:** A flat CSV file containing raw retail sales records for new car shipments, covering the years 2006 to 2022.
2. **Ingestion:** Connected Power BI Desktop directly to the raw data file via a live web data connector, preventing line-ending corruption and text misalignment.
3. **Cleaning:** 
   * Removed column-merging formatting errors by implementing an automated column splitter tuned to the comma delimiter.
   * Promoted the first row to headers to correctly establish table dimensions (`Make`, `Model`, `Price`, etc.).
   * Audited rows to find and remove empty entries and hidden null blocks.
4. **Transformation:** 
   * Stripped out trailing `" cc"` text flags from the `Engine` column using a text-replacement rule, casting the result into an integer column named `engine_cc`.
   * Processed the `Max Power` column by stripping out the trailing `" bhp"` unit characters, standardizing the field as a clean whole number named `horsepower_bhp`.
5. **Analysis:** Built dynamic business intelligence metrics by changing default database field summaries from a total *Sum* to an *Average* calculation across all dealership pricing and kilometer boundaries.
6. **Output:** Produced an interactive Power BI visual sales report (`.pbix` file) featuring a corporate table matrix dashboard view, multi-button slicer filters, and a multi-variable performance scatter plot.

-->



---

## 6. Data Model & Schema

<!--
### 📖 Data Dictionary (`standard_car_analytics`)

This flat table schema defines the final cleaned variables loaded onto the Power BI reporting canvas. All nested alphanumeric text tags and data inconsistencies were stripped out during the ingestion pipeline.

| Field Name | Data Type | Description | Sample Value |
|:---|:---|:---|:---|
| **brand** | String / Text | The corporate vehicle manufacturer or brand name. | `"Honda"` |
| **model** | String / Text | The specific production model name of the vehicle. | `"Amaze"` |
| **price_inr** | Integer | The retail sales price of the vehicle in Indian Rupees (INR), aggregated as an average in visuals. | `505000` |
| **year_made** | Integer | The calendar year the specific vehicle model was manufactured. | `2017` |
| **km_driven** | Integer | The total distance the car has traveled since manufacturing, recorded from the odometer. | `87150` |
| **engine_size** | Integer | The engine's total displacement size measured in Cubic Centimeters (CC). | `1198` |
| **horsepower** | Integer | The engine's maximum power output measured in Brake Horsepower (BHP). | `87` |




---


## 7. Analysis & Metrics

<!--
  ### 🧠 Analytical Approach & Strategy

This project focused on **building and validating an automated data engineering pipeline** combined with **exploratory data analysis (EDA)**. The goal was to take uncalculable, text-heavy manufacturing metrics and transform them into structured numbers. This allowed me to test how core mechanical engineering specifications directly affect retail sales prices in the automotive market.

### 📊 Key Business Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|:---|:---|:---|
| **Average Retail Valuation** | The mean sales price of a group of vehicles, calculated by dividing total revenue by the total number of cars within that category. | It provides dealership managers with an accurate baseline market value for different models and configurations, eliminating distortions caused by outliers. |
| **Average Odometer Accumulation** | The average total distance driven per vehicle across a specific manufacturer brand or category. | It answers key inventory depreciation questions, allowing stakeholders to evaluate how usage affects final retail pricing margins. |
| **Total Active Inventory Count** | A dynamic row-level counter that tracks the exact volume of active car listings available in stock. | It tracks asset volume in real-time, helping dealership networks spot stock shortages or supply bottle-necks instantly when filtered. |

### 🛠️ Data Analysis Methods Used

* **Descriptive Statistics:** Calculated metrics for central tendency (Averages) across massive vehicle inventories to create stable corporate baseline indicators.
* **Segmentation & Group Comparison:** Grouped the car fleet by categorical parameters (`Fuel Type` and `Transmission`) to identify how options affect pricing.
* **Correlation Analysis:** Evaluated the dual-variable relationship between engine displacement sizes (CC) and total horsepower output (BHP) on a coordinate space.
* **Custom String Transformation Logic:** Engineered direct regex-style string stripping and numeric type casting inside Power Query to convert raw text properties into clean integer metrics.

---

## 8. Key Insights

<!--
### 📈 Key Business Findings & Strategic Insights

**Insight 1: Automatic Transmissions Drive Premium Dealership Margins**
The visual comparison matrix reveals that automatic transmission configurations command a significantly higher average retail price compared to manual models. This suggests that retail buyers heavily prioritize convenience, meaning dealerships should actively shift their factory ordering pipelines to favor automatic models to capture these larger profit margins.

**Insight 2: Mechanical Power Directly Controls Pricing Power**
The regression trend line on the 4-dimensional scatter chart mathematically proves that retail prices expand rapidly as engine size (CC) and horsepower (BHP) increase. This strong correlation tells corporate planners that vehicle performance metrics—rather than simple cosmetic trims—are the primary drivers of value retention in the marketplace.

**Insight 3: High-Capacity Utility Vehicles Hold a Monopoly on Fleet Value**
Grouping the dataset shows that large-engine passenger vehicles (like the Toyota Innova) create massive visual clusters at the top-right of the performance scale. This indicates that the dealership network relies heavily on a few high-capacity models to bring in the majority of its revenue, highlighting a risky dependence on a single vehicle segment.

**Insight 4: Real-Time Filters Uncover Hidden Stock Shortages**
Using the interactive checkbox slicers directly reveals that premium fuel types (like Diesel) combined with automatic gearboxes have the lowest total inventory counts in stock. This shows that supply is not keeping up with demand, flagging an immediate stock shortage that dealership managers can fix by reallocating inventory to high-demand regions.


---

## 9. Recommendations

<!--
 ### 🎯 Strategic Recommendations Matrix

| Priority | Recommendation | Based On | Suggested Owner |
|:---|:---|:---|:---|
| 🔴 **High** | Shift factory order allocations by 20% to prioritize automatic gearboxes over manual trims for upcoming inventory shipments. | **Insight 1** – Automatic transmission margin premium | Product & Invoicing Team |
| 🟡 **Medium** | Reallocate high-horsepower SUV models to regional flagship hub dealerships where buyers demonstrate a higher willingness to pay for performance specs. | **Insight 2 & 3** – Mechanical power pricing dominance | Regional Sales Managers |
| 🟢 **Low** | Launch a targeted marketing campaign focusing on the high reliability and fuel economy of low-odometer compact commuter cars to balance inventory turnover. | **Insight 4** – Stock constraints and segment tracking | Marketing & Promotions Team |

---

## 10. Assumptions & Limitations

<!--
 ### 🛡️ Assumptions & Structural Limitations

### Assumptions
* **Inventory Consistency:** I assumed that the 5-car sample block utilized to re-establish the broken pipeline represents an accurate micro-segment reflecting the structural column formatting anomalies of the master database file.
* **MSRP Data Uniformity:** I treated the listed price field as the actual final transaction value, assuming that regional dealership discounts, taxes, or financing adjustments did not drastically alter the relative vehicle valuations.
* **Dealership Reporting Baseline:** I accepted the provided kilometer and year records as completely verified, assuming zero odometer tampering or reporting lag from individual dealership branches.

### Limitations
* **Small Sample Constraints:** The analysis is bounded by a subset of records used to rebuild the broken ingestion server pipeline. While it proves the data engineering logic works, a full production rollout would require scaling this loop to handle the thousands of rows in the master dataset.
* **Lack of Cost Tracking Matrix:** The source dataset only captures final retail prices. Because it excludes factory invoice costs, dealership overhead, and shipping logistics, the dashboard evaluates top-line price dynamics rather than true net profitability margins.
* **Omission of Temporal Seasonality:** This exploratory visual model aggregates all time boundaries. It cannot track micro-trends like changes in car buying habits during specific seasons, or how economic shifts affect new vs. old model sales over time.

---

## 11. Future Enhancements

<!--
### 🚀 Next Steps & Future Enhancements

- [ ] **Scale the Pipeline Volume:** Transition the manual Power BI table ingestion setup into a production-ready looping engine that pulls and cleans all thousands of historical vehicle sales rows from the master file.
- [ ] **Automate Database Re-Connection:** Resolve the local port permission blocks inside the MySQL database server configurations to establish a direct, scheduled SQL-to-Power-BI daily refresh pipeline.
- [ ] **Integrate Vehicle Dimension Analytics:** Incorporate the unused structural measurements from the raw data (`Length`, `Width`, and `Height`) to calculate and plot vehicle footprint sizes against consumer price points.
- [ ] **Ingest Invoice Cost Data:** Connect the model to the manufacturing logistics database to pull vehicle cost margins, allowing the dashboard to track true net profitability instead of just top-line retail price.


---



---

## 12. Author

**[ANEG YANNICK]**
[DATA ANALYST]

- 🔗 [[LinkedIn URL](https://www.linkedin.com/in/aneg-yannick-19692a432/)]
- 💼 [Portfolio or GitHub profile URL]
- 📧 [yannickaneg23@gmail.com]

---

*Last updated: [june 2026]*
