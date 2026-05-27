```markdown
# 🛒 Amazon Global Sales Dashboard — Tableau

> An end-to-end data analytics project analyzing Amazon's global sales performance across regions, product categories, and sales channels using Tableau.

---

## 📌 Project Overview

This project involves cleaning a real-world Amazon sales dataset, engineering key metrics, and building a multi-page interactive Tableau dashboard styled to look like the Amazon.in interface.

The dashboard provides business insights across **1,717 orders** spanning **2010–2017**, covering **7 global regions** and **12 product categories**.

---

## 🔗 Live Dashboard

> **[View on Tableau Public →](https://public.tableau.com/app/profile/sumit.bhandari4239/viz/amazon_17798766652680/ItemAnalysis?publish=yes)**

---

## 📊 Dashboard Pages

| Page | Description |
|------|-------------|
| **Homepage** | KPI cards (Total Profit, Revenue, Avg Shipment Days, Units Sold) + Region-wise profit bar chart + Country-wise profit world map |
| **Executives Page** | Sales Channel pie chart, Orders over time, Priority-wise order count, Total Cost per year |
| **Revenue Analysis** | Year-wise revenue trend vs shipment volume dual-axis chart with insight annotation |
| **Item Analysis** | Revenue vs Item, Units Sold vs Item, Cost vs Item, Profit vs Item — all broken down by product category |

---

## 📸 Dashboard Preview

![Homepage](assets/homepage.png)
![Executives](assets/executives.png)
![Revenue Analysis](assets/revenue_analysis.png)
![Item Analysis](assets/item_analysis.png)

> **Note:** The `assets/` folder also contains UI images (buttons, backgrounds) used inside the Tableau workbook. Keep them in the same relative path for the dashboard to render correctly.

---

## 📁 Repository Structure

```
amazon-sales-tableau/
│
├── data/
│   └── Amazon_Sales_data.csv          # Cleaned dataset (1,717 rows, 11 columns)
│
├── dashboard/
│   └── amazon.twb                     # Tableau workbook file
│
├── docs/
│   └── data_dictionary.md             # Field definitions and calculated fields
│
├── assets/
│   ├── homepage.png                   # Dashboard screenshot — Homepage
│   ├── executives.png                 # Dashboard screenshot — Executives Page
│   ├── revenue_analysis.png           # Dashboard screenshot — Revenue Analysis
│   ├── item_analysis.png              # Dashboard screenshot — Item Analysis
│   ├── Back button.png                # Tableau UI — back navigation button
│   ├── Button.png                     # Tableau UI — next navigation button
│   ├── behind kpi.png                 # Tableau UI — KPI card background
│   └── next .png                      # Tableau UI — next page button
│
└── README.md
```

---

## 🗂️ Dataset

**File:** `data/Amazon_Sales_data.csv`  
**Rows:** 1,717 | **Columns:** 11

| Column | Type | Description |
|--------|------|-------------|
| Country | String | Country of the order |
| Item Type | String | Product category (12 types) |
| Order Date | Date | Date order was placed |
| Order ID | Integer | Unique order identifier |
| Order Priority | String | H / M / L / C |
| Region | String | Geographic region (7 regions) |
| Sales Channel | String | Online / Offline |
| Ship Date | Date | Date order was shipped |
| Total Cost | Float | Total cost of the order |
| Total Revenue | Float | Total revenue from the order |
| Units Sold | Integer | Number of units in the order |

**Regions covered:**
- Asia · Europe · North America · Australia and Oceania
- Central America and the Caribbean · Middle East and North Africa · Sub-Saharan Africa

---

## 🧮 Calculated Fields (Tableau)

| Field Name | Formula | Purpose |
|------------|---------|---------|
| Profit | `[Total Revenue] - [Total Cost]` | Net profit per order |
| Shipment Days | `[Ship Date] - [Order Date]` | Days taken to ship |
| Highlight (LOD) | `IF SUM(Profit) = WINDOW_MAX(SUM(Profit)) THEN 'color' ELSE 'no color' END` | Highlights top-performing bar |

---

## 🔍 Key Insights

- **Total Revenue:** $2,510M across all years
- **Total Profit:** $1,074M — ~42.8% profit margin
- **Average Shipment Days:** 20.01 days
- **Top Region by Profit:** Europe (~$150M+)
- **Top Product by Revenue:** Household ($528M)
- **Top Product by Profit:** Household ($330M)
- **Sales Channel Split:** Online ($1,265M) vs Offline ($1,245M) — nearly equal
- **Peak Order Year:** 2017 (239 orders) with a sharp drop in 2018 (only 8 — partial year data)

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Python (pandas) | Data cleaning and dataset generation |
| Tableau Desktop 2026.1 | Dashboard design and visualisation |
| Tableau Public | Publishing and sharing |
| GitHub | Version control and project documentation |

---

## 🚀 How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/bruce-01/amazon-sales-tableau.git
   ```

2. Open `dashboard/amazon.twb` in **Tableau Desktop**

3. When prompted for the data source, point it to:
   ```
   data/Amazon_Sales_data.csv
   ```

4. The dashboard will load with all 4 pages and interactive filters

---

## 👤 Author

**Sumit Bhandari**  
B.Tech Civil Engineering, Delhi Technological University  
Aspiring Data Analyst | Tableau · Python · SQL  

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/sumitbhandari01)

---

## 📄 License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
```
# amazon-sales-tableau
