# 🛒 BlinkIT Grocery Sales & Outlet Performance Analytics

A data analytics project on **BlinkIT**, a quick-commerce grocery platform. Using **Excel** and **Power BI**, I cleaned the raw sales data, explored it, and built an interactive dashboard that shows which outlets, locations and product categories drive sales.

![Executive Summary](images/executive_summary.png)

---

## 🎯 Business Problem

The VP of Merchandising needs evidence to plan assortment and outlet-expansion budgets. The dashboard answers four questions:

1. Which **outlet formats and locations** drive the most sales?
2. Which **item categories** are over- or under-performing relative to shelf visibility?
3. Do **item ratings** actually predict sales?
4. How does **outlet age** affect performance?

## 📊 Dataset

One row per item-outlet combination: **8,523 rows × 12 columns**, covering **1,559 unique items**, **16 categories** and **10 outlets** (established 2011–2022).

| Column | Description |
|--------|-------------|
| Item Identifier / Item Type | Unique item code and its category |
| Item Fat Content | Low Fat or Regular |
| Item Weight | Product weight (kg) |
| Item Visibility | Share of shelf space the item occupies at that outlet (0–1) |
| Outlet Identifier | Which of the 10 outlets |
| Outlet Establishment Year | Year the outlet opened |
| Outlet Location Type | Tier 1 / Tier 2 / Tier 3 city |
| Outlet Size | Small / Medium / High |
| Outlet Type | Grocery Store or Supermarket Type1 / 2 / 3 |
| Sales | Sales value of the item at that outlet |
| Rating | Item rating (1–5) |

## 🧹 Data Cleaning (Excel)

| Issue in raw data | Fix |
|-------------------|-----|
| Item Fat Content had 5 labels for 2 categories (`Low Fat`, `LF`, `low fat`, `Regular`, `reg`) | Standardised into exactly **Low Fat** and **Regular** |
| Item Weight missing on 1,463 rows (17%) | Filled in, so the cleaned file has **no missing weights** |
| Column names with spaces and mixed case | Renamed to `snake_case` (e.g. `item_fat_content`) |

The raw file is kept in `data/` so the cleaning can be checked against the original.

## 📈 Dashboard (Power BI)

The report has **3 pages**:

| Page | What it shows |
|------|---------------|
| **Executive Summary** | Total sales, average rating, items and outlets; sales by outlet type, location tier, item type and establishment year; rating vs. sales |
| **Outlet Performance** | Average sales per outlet, sales by outlet, average rating by outlet type, sales trend by establishment year, outlet × item type table |
| **Product & Outlet Analysis** | Sales by outlet size and fat content, top item types, average visibility and weight, visibility vs. sales scatter |

Every page has slicers for outlet type, size, location tier, establishment year and fat content.

**DAX measures:** `Total_Sales`, `Avg_Sales_per_Outlet`, `Total_Outlets`, `Total_Items`, `Total_Categories`, `Avg_Rating`, `Avg_Visibility`, `Avg_Weight`

### Screenshots

![Outlet Performance](images/outlet_performance.png)
![Product and Outlet Analysis](images/product_outlet_analysis.png)

## 💡 Key Insights

*Calculated from `Blinkit_Cleaned.xlsx`.*

- **Total sales are about 1.20M** across 10 outlets, with an average sale value of about 141 per item-outlet row.
- **Supermarket Type1 brings in 65.5% of all sales**, but mostly because it has 6 of the 10 outlets. Per outlet, Type1, Type2 and Type3 all sell about **131K**.
- **The two Grocery Store outlets sell far less**, about 76K each, roughly 42% below a supermarket outlet.
- **Tier 3 cities have the highest sales share (39.3%)**, followed by Tier 2 (32.7%) and Tier 1 (28.0%).
- **Fruits and Vegetables and Snack Foods are the top categories**, followed by Household, Frozen Foods and Dairy.
- **Ratings and visibility barely predict sales.** The correlation of both with sales is close to zero (about 0.01 and -0.00), so higher-rated or more visible items do not sell noticeably more in this data.

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Excel | Data cleaning and exploration |
| Power BI | Data model, DAX measures and interactive dashboard |

## 📁 Repository Structure

```
├── data/
│   ├── BlinkIT-Grocery-Data_Raw.csv    # Original raw data
│   └── Blinkit_Cleaned.xlsx            # Cleaned data
├── dashboard/
│   └── Blinkit_report.pbix             # Power BI report
├── docs/
│   ├── BlinkIT_Grocery_Case_Study.pdf  # Case study brief
│   └── BlinkitQuestions.txt            # Business questions
├── images/                             # Dashboard screenshots
└── README.md
```

## 🚀 How to Open the Dashboard

1. Download or clone this repository.
2. Open `dashboard/Blinkit_report.pbix` in **[Power BI Desktop](https://powerbi.microsoft.com/desktop/)** (Windows).
3. If the data doesn't load, go to **Transform data → Data source settings** and point the source to the file in the `data/` folder.

## 🔮 Possible Next Steps

- Treat the 526 rows with zero item visibility as missing values
- Add an `Outlet_Age` column with a stated reference year
- Add a one-page summary with recommendations for the VP
- Publish the dashboard to Power BI Service

## 👨‍💻 Author

Made by **<Your Name>**
GitHub: [@<your-username>](https://github.com/<your-username>)

---

⭐ If you found this project useful, give it a star!
