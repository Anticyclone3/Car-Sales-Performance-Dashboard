# Comprehensive Car Sales Performance Dashboard (Power BI)

## 📌 Project Overview
This end-to-end Power BI project delivers a dynamic, interactive executive dashboard designed for a car dealership network. The business objective is to transform disjointed, daily transactional automotive sales data into real-time operational insights. 

By developing this business intelligence tool, stakeholders can instantly track key performance metrics (KPIs) regarding revenue, sales volumes, pricing structures, and geographic distribution to make data-driven inventory and marketing choices.

---

## 🛠️ Tech Stack & Skills Demonstrated
*   **Business Intelligence Tool:** Microsoft Power BI Desktop
*   **Data Modeling:** Star Schema architecture with distinct Fact and Dimension relationships.
*   **Data Transformation:** Power Query (ETL, data cleaning, datatype alignment, and column mapping).
*   **Analytical Calculations:** Advanced DAX (Data Analysis Expressions) leveraging time-intelligence functions.
*   **UX/UI Design:** Custom layout creation, clean corporate color theory, interactive navigation buttons, global side-panel filtering, and reactive hover tooltips.

---

## 📈 Business Requirements Breakdown

### 1. Key Performance Indicators (KPIs) Requirement
The dashboard tracks real-time shifts across three core commercial pillars:
*   **Sales Overview:** Year-to-Date (YTD) Total Sales, Month-to-Date (MTD) Total Sales, Year-over-Year (YoY) Sales Growth, and numeric variance between YTD and Previous Year-to-Date (PTYD) metrics.
*   **Average Price Analysis:** YTD/MTD Average Price per vehicle sold, YoY pricing growth percentage, and the distinct variance to PTYD averages.
*   **Cars Sold Metrics:** YTD/MTD total units moved, YoY unit growth, and volume differences compared to the prior period.

### 2. Visualization & Reporting Matrix
*   **Temporal Trends:** A weekly timeline tracking cumulative YTD sales growth.
*   **Product Distribution:** Breakdown of sales and volume concentration by vehicle body styles and exterior colors.
*   **Geographic Analysis:** An interactive map plotting units sold by dealer region to evaluate local market performance.
*   **Granular Ledgers:** Corporate grid summaries for company performance alongside an exhaustive transactional details page for operational lookups.

---

## 📊 Dashboard Architecture & Layout

### 🎛️ Page 1: Main Executive Overview
The **Overview** view provides a high-level summary of operational performance. It features a top KPI banner displaying key financial summaries, a central weekly sales trajectory graph, product segments, a regional map layout, and a quick-glance company ledger.

<img width="1256" height="723" alt="image" src="https://github.com/user-attachments/assets/d72ef6d4-afce-4c7b-a3fc-dec0791e0827" />


### 💬 Page 1.1: Contextual Hover Tooltips
Hovering cursor points over specific charts triggers custom tooltip view overlays. This provides deep diagnostic metrics (such as average pricing variances and MTD benchmarks) on the fly without cluttering the canvas.

<img width="1257" height="754" alt="image" src="https://github.com/user-attachments/assets/81055641-d20d-4abb-b57b-da15f3381b9f" />



### 📋 Page 2: Transactional Details Ledger
The **Details** grid provides a complete data log. It allows sales managers to audit line-by-line transactions, filtering fields like Car ID, Date, Customer Profiles, Dealer Names, and granular item specifics.

<img width="1170" height="729" alt="image" src="https://github.com/user-attachments/assets/c1822c1e-f5fb-4a88-86a2-e65ce7a2ec19" />


---

## 🧮 Data Engineering & DAX Calculations

To deliver dynamic time-intelligence capabilities, the project avoids basic aggregations and relies on optimized, custom DAX metrics. Key calculations include:

### 1. Year-to-Date (YTD) Sales Revenue
```dax
YTD_Sales = 
TOTALYTD(
    SUM('Car Sales Data'[Price]), 
    'Calendar Table'[Date]
)
```

### 2. Previous Year-to-Date (PTYD) Sales Revenue
```dax
PTYD_Sales = 
CALCULATE(
    [YTD_Sales], 
    SAMEPERIODLASTYEAR('Calendar Table'[Date])
)
```

### 3. Year-over-Year (YoY) Sales Revenue Growth
```dax
YoY_Sales_Growth = 
VAR Sales_Variance = [YTD_Sales] - [PTYD_Sales]
RETURN
DIVIDE(
    Sales_Variance, 
    [PTYD_Sales], 
    0
)
```

*(Note: Similar robust structures using `TOTALMTD` and `DIVIDE` handle safe calculations for Average Price and Unit Volume metrics across the entire dataset).*

---

## 💡 Strategic Data-Driven Recommendations
Based on the dashboard's current state, several commercial opportunities stand out for leadership:

*   **Capitalize on SUV Market Dominance:** **SUVs account for 26.91% of total sales revenue**, followed closely by Hardtops (19.85%). Procurement and marketing teams should prioritize premium SUV inventory placement to sustain this core engine.
*   **Optimize Color Inventory Production:** Vehicles with **Pale White paint configurations drive $71.41M (19.24%) of total sales**. Reallocating manufacturing runs or ordering allocations away from slower-moving colors toward Pale White can lower floor-plan holding costs.
*   **Address Margin Deviations:** Although overall sales revenue is stable, the interactive tooltip shows that **YoY growth for Average Vehicle Price fell by ($0.02)**. Dealership management should evaluate if this is driven by high-volume discounting or shifting model mixes to protect bottom-line margins.

---

## 🚀 How to Setup and Run This Project

### Prerequisites
*   [Microsoft Power BI Desktop](https://microsoft.com) (Free download)

### Step-by-Step Installation
1.  Clone this repository to your local system:
    ```bash
    git clone https://github.com
    ```
2.  Open the `/Dashboard/` folder directory.
3.  Launch the `Skoda_Car_Sales_Report.pbix` project file inside Power BI Desktop.
4.  If data sources require reconnecting, navigate to **Transform Data > Data Source Settings** to point the dataset links to the primary spreadsheet located in your cloned data folder path.
