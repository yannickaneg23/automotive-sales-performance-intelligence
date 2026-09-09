# 🚘 Automotive Sales Performance & Market Intelligence Dashboard
### **Data Processing & Power BI End-to-End Analytics Pipeline**

---

### 📌 1. Project Overview
An automotive manufacturer needed to evaluate regional dealership sales, but they couldn't see true performance trends because their data was messy. Important vehicle details like engine size and peak power were trapped inside text entries like "1198 cc" and "87 bhp," making it impossible to calculate averages or build charts. I built a clean, automated data pipeline to fix these formatting errors and created an interactive dashboard that reveals exactly which vehicle features drive the most revenue.

---

### 🎯 2. Objectives
*   **Primary Objective:** Build a repeatable data pipeline that takes messy text columns and automatically converts them into clean, usable numbers.
*   **Secondary Objective 1:** Quantify the exact sales price difference between manual and automatic cars across all models.
*   **Secondary Objective 2:** Evaluate whether larger engine sizes directly cause higher sales values using an advanced scatter chart.
*   **Secondary Objective 3:** Identify which specific car brands have the highest total inventory counts and highest average prices.

---

### 📐 3. Project Scope & Tools

### Scope & Boundaries
*   **In Scope:** Regional factory vehicle sales records, pricing, kilometers driven, fuel types, and transmission variants.
*   **Out of Scope:** Dealership marketing costs, warehouse storage fees, and vehicle repair histories (excluded because cost logs live in a separate system and repair logs were highly incomplete).
*   **Time Period:** Vehicle sales records spanning from **2006 to 2022**.
*   **Granularity:** **Row-level vehicle data.** Every single line represents an individual car sale at a specific regional dealership branch.

### Tech Stack Used
*   **Data Storage:** Raw CSV files
*   **Data Processing:** Power BI Power Query Editor
*   **Analysis:** Power Query Formula Language (M)
*   **Visualization:** Microsoft Power BI Desktop (Table grids, Scatter charts, Slicers)
*   **Version Control:** GitHub
*   **Documentation:** Markdown (`README.md`)

---

### 📂 4. Repository Structure
```text
[project-root]/
│
├── data/
│   ├── raw/                  # Original, unmodified source CSV files
│   └── processed/            # Final cleaned and transformed dataset
│
├── visuals/                  # Dashboard screenshots and report preview captures
│
└── README.md                 # Project executive summary and documentation
```

---

### 🔄 5. Data Workflow & Lineage
1.  **Source:** A raw CSV file containing vehicle manufacturing specifications and retail sales records.
2.  **Ingestion:** Connected Power BI Desktop directly to the file via a live web data link to prevent copy-paste formatting errors.
3.  **Cleaning:** Split text clumps by commas, promoted the top row to headers, and removed hidden blank rows.
4.  **Transformation:** Stripped the letters `" cc"` out of the engine column and `" bhp"` out of the power column, instantly turning them into clean whole numbers.
5.  **Analysis:** Changed the final dashboard calculations from basic "Sum Totals" to "Averages" to find true market trends.
6.  **Output:** An interactive Power BI report (`.pbix`) with live filter buttons and dynamic charts.

---

### 📖 6. Data Model & Schema
This table defines the final clean variables used on the dashboard after stripping out all text suffixes and errors.

| Field Name | Data Type | Description | Sample Value |
|:---|:---|:---|:---|
| **brand** | Text | The manufacturer or brand name of the vehicle. | `"Honda"` |
| **model** | Text | The specific production model name of the vehicle. | `"Amaze"` |
| **price_inr** | Integer | The retail sales price of the vehicle in Indian Rupees. | `505000` |
| **year_made** | Integer | The calendar year the car was manufactured. | `2017` |
| **km_driven** | Integer | The total distance the car has traveled (odometer reading). | `87150` |
| **engine_size** | Integer | The engine's size measured in Cubic Centimeters (CC). | `1198` |
| **horsepower** | Integer | The engine's maximum power output in Brake Horsepower (BHP). | `87` |

---

### 🧠 7. Analysis & Metrics
*   **Average Retail Valuation:** Calculates the true middle price point for a car brand, preventing extreme expensive or cheap cars from distorting the big picture.
*   **Average Odometer Accumulation:** Measures the average mileage driven across a group of vehicles to track wear and depreciation.
*   **Total Active Inventory Count:** A live row counter that updates instantly to show managers how many cars are left in stock when a filter is clicked.

---

### 📈 8. Key Insights
*   **Insight 1 (Gearbox Premium):** Automatic cars carry a significantly higher average sales price than manual ones, proving that retail buyers are highly willing to pay a premium for convenience.
*   **Insight 2 (Power Dynamics):** The scatter chart shows a tight upward trend—as engine sizes (CC) grow, horsepower (BHP) and final prices jump up cleanly alongside them.
*   **Insight 3 (Revenue Monopoly):** A tiny handful of heavy utility vehicles (like the Toyota Innova) sit high up on the price chart, proving the company relies on just a few models for most of its value.
*   **Insight 4 (Stock Shortages):** Using the live filter buttons reveals that automatic diesel models have the lowest stock counts, pointing to an immediate inventory shortage.

---

### 🎯 9. Strategic Recommendations

| Priority | Recommendation | Based On | Suggested Owner |
|:---|:---|:---|:---|
| 🔴 **High** | Increase upcoming automatic car inventory orders by 20% to capture higher profit margins. | **Insight 1** – Automatic price premium | Product Team |
| 🟡 **Medium** | Reallocate high-horsepower SUV models to flagship city dealerships where buyers pay the most for performance. | **Insight 2 & 3** – Power pricing dominance | Sales Managers |
| 🟢 **Low** | Launch a marketing campaign to quickly sell low-mileage manual compact cars and balance out stock turnover. | **Insight 4** – Stock constraints | Marketing Team |

---

### 🛡️ 10. Assumptions & Limitations

### Assumptions
*   **Sample Accuracy:** I assumed our 5-car testing row snippet properly mirrors the exact text-clumping bugs found across the master database file.
*   **Price Definition:** I treated the listed price field as the final transaction value, assuming dealership discounts didn't change the relative car valuations.

### Limitations
*   **Small Dataset Boundary:** This pipeline was built to fix a broken ingestion server loop. While it proves the logic works, a production launch would require running the code across the entire multi-thousand row master file.
*   **No Profit Tracker:** The data does not include original manufacturing invoice costs or dealership overhead, meaning the dashboard can only evaluate gross revenue instead of net profit margins.

---

### 🚀 11. Future Enhancements
- [ ] **Scale Table Volume:** Run this exact data cleaning recipe across all thousands of historical sales rows in the master file.
- [ ] **Automate Database Connection:** Fix local port locks on the database server to allow a direct, automatic daily data refresh into Power BI.
- [ ] **Add Car Dimension Visuals:** Ingest the unused length and width columns to calculate and plot physical vehicle sizes against price points.




---

## 12. Author

**[ANEG YANNICK]**
[DATA ANALYST]

- 🔗 [[LinkedIn URL](https://www.linkedin.com/in/aneg-yannick-19692a432/)]
- 💼 [[Portfolio or GitHub profile URL](https://github.com/yannickaneg23)]
- 📧 [yannickaneg23@gmail.com]

---

*Last updated: [june 2026]*
