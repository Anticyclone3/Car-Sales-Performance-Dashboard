# Interactive Car Sales Performance Dashboard (Power BI)

## 📌 Executive Summary
An enterprise-grade **Power BI Dashboard** designed to transform raw car dealership transactional logs into actionable executive insights. This end-to-end business intelligence project delivers tracking across fundamental metrics: **Sales Revenue, Pricing Optimization, and Volume Metrics**, with integrated dynamic **Year-to-Date (YTD)**, **Month-to-Date (MTD)**, and **Year-over-Year (YOY)** time-intelligence calculations.

---

## 💼 Business Requirements Document (BRD) Overview

### 1. Objective
To design and develop a dynamic, interactive dashboard analyzing critical KPIs over time to support real-time data-driven decisions, optimize inventory distribution, and discover regional growth opportunities.

### 2. Core Tracking Architecture (KPI Requirements)
The dashboard calculates and updates real-time analytics across three foundational pillars:
*   **Sales Overview:** Tracking YTD Total Sales, MTD Total Sales, YOY Sales Growth percentage, and the absolute difference between current YTD and Previous Year-to-Date (PTYD) Sales.
*   **Average Price Analysis:** Evaluating YTD Average Price, MTD Average Price, YOY Growth in Average Price, and the net variance against PTYD Average Price.
*   **Cars Sold Metrics:** Monitoring YTD Quantities Sold, MTD Quantities Sold, YOY Volume Growth, and unit discrepancies vs. PTYD metrics.

### 3. Visual & Analytical Framework
*   **Trend Exploration:** Weekly progression profiling of YTD sales using multi-axis line visualizations.
*   **Categorical Segments:** Market share distribution breakdown by *Body Style* and *Colorway* leveraging high-impact distribution plots.
*   **Geographical Intelligence:** Interactive map overlays clustering unit sales across distinct dealer territories.
*   **Granular Performance Tables:** Structured matrices isolating company production metrics alongside granular atomic transactional log sheets.

---

## 🛠️ Tech Stack & Architecture
*   **BI Tool:** Microsoft Power BI Desktop
*   **Data Modeling:** Relational Star-Schema architecture featuring automated Calendar/Date Dimension tables.
*   **Query Engine:** Power Query (M Language) for ETL, structural normalization, and null management.
*   **Analytical Engine:** Advanced DAX (Data Analysis Expressions) for complex dynamic Time-Intelligence variables.

---

## 📐 Advanced DAX Metric Catalog

The data model utilizes highly responsive DAX measures to calculate temporal shifts dynamically:

```dax
// 1. Year-To-Date (YTD) Total Sales Amount
YTD Sales = TOTALYTD(SUM('Car Sales Data'[Price]), 'Calendar Date'[Date])

// 2. Previous Year-To-Date (PTYD) Sales Amount
PTYD Sales = CALCULATE([YTD Sales], SAMEPERIODLASTYEAR('Calendar Date'[Date]))

// 3. Sales Volume Variance (Difference between Current and Past Year-to-Date)
Diff YTD Sales = [YTD Sales] - [PTYD Sales]

// 4. Year-over-Year (YOY) Total Revenue Growth Rate
YOY Growth Sales = DIVIDE([Diff YTD Sales], [PTYD Sales], 0)

// 5. Year-To-Date (YTD) Average Selling Price
YTD Avg Price = DIVIDE(TOTALYTD(SUM('Car Sales Data'[Price]), 'Calendar Date'[Date]), TOTALYTD(COUNT('Car Sales Data'[Car_id]), 'Calendar Date'[Date]), 0)

// 6. Year-To-Date (YTD) Units Sold Volume
YTD Cars Sold = TOTALYTD(COUNT('Car Sales Data'[Car_id]), 'Calendar Date'[Date])
```

---

## 📊 Dashboard Interface & Interactive Layout

The solution is split into three functional layers to maintain clean user navigation:

### 🎛️ 1. Overview Canvas
Provides an immediate high-level summary of dealership health. Features stylized metric callout boxes displaying primary metrics ($371.19M YTD Sales, 54M MTD Sales, and 24% YOY Growth). It houses a weekly trend line chart, body style/color distribution pie charts, a Bing Maps regional plot, and custom hover tooltips showing deep-dive metric cards on demand.

### 📑 2. Details Ledger View
A high-density operational spreadsheet view cataloging transactional atomic-level history. Includes attributes like unique Car IDs, exact Purchase Dates, Customer Identities, Dealer Network Names, Vehicle Production Company, Color variants, and Model specifications alongside strict financial rows.

### 🧰 3. Dynamic Filtering Controls
A persistent global left-hand sidebar navigation panel containing localized multi-select slicers for:
*   **Dealer Name**
*   **Body Style**
*   **Engine Configuration**
*   **Transmission Type**

---

## 📈 Strategic Business Insights & Recommendations

1.  **Exploit Vehicle Style Dominance:** **SUV (26.91%)** and **Hardtop (approx. 22%)** categories generate nearly half of all global sales volume. Align upcoming procurement and floor plan financing to maintain healthy stock of these fast-turning body configurations.
2.  **Optimize Aesthetic Allocations:** **Pale White** is the dominant consumer choice, bringing in **$71.41M (19.24%)** in revenue. Dealerships should overweight default orders toward pale white options while maintaining regional buffers for secondary tones like Black and Red.
3.  **Address Average Price Shrinkage:** The model indicates a **-$0.02 YOY drop** in Average Vehicle Selling Price. While sales volumes remain strong, management must evaluate incentive packages or cross-sell high-margin extended warranties and custom dealer add-ons to lift unit margin rates back up.

---

## 🚀 How To Deploy & Replicate

1.  Clone this repository to your desktop machine: `git clone https://github.com/your-username/car-sales-powerbi-dashboard.git`
2.  Open the localized transactional spreadsheet asset within Microsoft Excel or host it inside your SQL environment.
3.  Launch the provided `.pbix` template inside **Power BI Desktop**.
4.  Navigate to *Transform Data* -> *Data Source Settings* to redirect file paths to your local data source.
5.  Select **Refresh** to let the Power Query ETL workflow update your visual environment.

---
*Developed as a portfolio project showcasing data storytelling, structural dimensional modeling, and time-intelligence mastery in corporate environments.*
