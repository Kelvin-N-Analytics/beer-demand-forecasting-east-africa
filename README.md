#  🍺 Beer Demand Forecasting & Inventory Optimization  East Africa FMCG

> **A end-to-end supply chain analytics project simulating real-world demand planning and inventory optimization for a beverage company operating across Kenya.**

---

## 📌 Project Overview

FMCG companies in East Africa face a common challenge: **too much stock of the wrong product, in the wrong place, at the wrong time.** This results in high holding costs, stockouts during peak seasons, and reactive supply chain decisions.

This project simulates 3 years of beer and spirits sales data across 4 Kenyan regions and 6 SKUs, then applies demand forecasting and inventory optimization techniques to quantify how much better analytical decisions can save a business.

**Target companies this analysis mirrors:** East African Breweries Limited (EABL) and Kenya Wine Agencies Limited (KWAL).

---

## 🎯 Business Questions Answered

1. What does demand look like across regions and products  and when does it spike?
2. How much does running a promotion actually lift sales?
3. Can we forecast demand more accurately than a simple moving average?
4. What is the optimal safety stock and reorder point for each SKU?
5. How much money does better forecasting save in holding costs?
6. Which suppliers and regions have the most lead time risk?

---

## 📊 Dataset

| Parameter | Detail |
|---|---|
| Records | 864 rows |
| Products | 6 SKUs (Tusker Lager, Senator Keg, Tusker Malt, Johnnie Walker Black, Smirnoff Vodka, Baileys Original) |
| Regions | Nairobi, Mombasa, Kisumu, Nakuru |
| Time Period | January 2022 – December 2024 (36 months) |
| Features | Demand, Opening/Closing Stock, Lead Time, Promotions, Unit Price, Revenue |

> **Note:** Data is simulated using realistic FMCG assumptions including seasonality, regional demand multipliers, promotional uplifts, and random variation. It is designed to mirror the data environment at EABL/KWAL.

---

## 🔍 Key Findings

### 1. Seasonality & Demand Patterns
- **December** is the peak demand month (+45% above baseline) driven by festive season consumption
- **February** is the slowest month (-20% below baseline)
- **April** shows a secondary spike (+20%) corresponding to the Easter period
- **Nairobi** accounts for the largest share of demand (1.5× the national average)

### 2. Promotion Impact
- Promotions drive a **+26.6% average uplift in demand** across all SKUs
- Tusker Lager benefits most due to its high base volume
- Insight: promotional planning should account for supply chain readiness  a demand spike without pre-positioned stock creates stockouts

### 3. Demand Forecasting: MA3 vs Exponential Smoothing

| Model | MAPE | Interpretation |
|---|---|---|
| 3-Month Moving Average (Baseline) | 15.63% | Off by ~16 cases per 100 forecasted |
| Exponential Smoothing with Trend & Seasonality | **8.17%** | Off by ~8 cases per 100 forecasted |
| **Improvement** | **47% more accurate** | ETS captures seasonal peaks the MA3 misses |

The Exponential Smoothing model captures December and Easter spikes that the Moving Average consistently underestimates  the exact failure mode that leads to festive season stockouts.

### 4. Inventory Optimization (Nairobi — 95% Service Level)

| Product | Avg Monthly Demand | Safety Stock | Reorder Point |
|---|---|---|---|
| Tusker Lager | 1,918 cases | 382 cases | 1,229 cases |
| Senator Keg | 1,428 cases | 272 cases | 965 cases |
| Tusker Malt | 959 cases | 158 cases | 607 cases |
| Smirnoff Vodka | 715 cases | 149 cases | 460 cases |
| Johnnie Walker Black | 473 cases | 87 cases | 303 cases |
| Baileys Original | 317 cases | 57 cases | 201 cases |

### 5. Annual Holding Cost Savings from Better Forecasting

| Product | Annual Saving (KES) |
|---|---|
| Johnnie Walker Black | 245,004 |
| Tusker Lager | 135,852 |
| Smirnoff Vodka | 114,744 |
| Baileys Original | 108,000 |
| Tusker Malt | 75,600 |
| Senator Keg | 39,744 |
| **Total (Nairobi)** | **KES 718,944** |
| **Projected (4 Regions)** | **KES ~2,400,000** |

> Johnnie Walker Black delivers the highest saving despite lower volume  because its high unit price (KES 28,000/case) means even small stock reductions have outsized financial impact. **Premium SKUs drive disproportionate holding costs.**

### 6. Supplier Performance

| Product | Avg Lead Time | Reliability |
|---|---|---|
| Tusker Malt | 13.1 days | ⚠️ Variable |
| Smirnoff Vodka | 13.3 days | ⚠️ Variable |
| Tusker Lager | 13.4 days | ⚠️ Variable |
| Baileys Original | 13.4 days | ✅ Reliable |
| Johnnie Walker Black | 13.6 days | ✅ Reliable |
| Senator Keg | 13.8 days | ✅ Reliable |

- All suppliers are within the 14-day benchmark on average
- **Nairobi has the lowest on-time delivery rate (58.8%)** - the highest-volume region carries the most supplier risk
- **Kisumu has the best on-time rate (67.6%)** despite lower volumes

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|---|---|
| Python | Data simulation, analysis, and forecasting |
| Pandas | Data wrangling and aggregation |
| NumPy | Statistical calculations |
| Statsmodels | Exponential Smoothing (Holt-Winters) model |
| Matplotlib | Data visualisation |
| Jupyter Notebook | Development environment |
| Power BI | Dashboard (see `/dashboard` folder) |

---

## 📁 Project Structure

```
beer-demand-forecasting/
│
├── Beer Demand Forecasting & Inventory Optimization.ipynb  # Main notebook
├── eabl_kwal_supply_chain_data.csv                         # Generated dataset
├── README.md                                               # This file
└── dashboard/                                              # Power BI files (coming soon)
```

---

## 🚀 How to Run This Project

1. Clone this repository
```bash
git clone https://github.com/YOUR_USERNAME/beer-demand-forecasting.git
```

2. Install required libraries
```bash
pip install pandas numpy matplotlib statsmodels
```

3. Open the notebook
```bash
jupyter notebook "Beer Demand Forecasting & Inventory Optimization.ipynb"
```

4. Run all cells from top to bottom (Cell → Run All)

---

## 💡 Business Recommendations

Based on the analysis, a beverage company like EABL or KWAL should:

1. **Replace moving average forecasting with Exponential Smoothing**: the 47% accuracy improvement directly reduces both stockouts and excess inventory
2. **Pre-position stock 3–4 weeks before December and Easter**: lead times average 14 days, so orders need to go out before the demand spike hits
3. **Prioritise inventory accuracy for premium SKUs**: Johnnie Walker Black generates the highest holding cost savings per case reduced
4. **Investigate Nairobi supplier reliability**: the largest market has the lowest on-time delivery rate (58.8%), creating unnecessary supply risk
5. **Build promotional stock buffers**: with a +26.6% average uplift, promotions without pre-positioning stock risk turning sales opportunities into stockouts

---

## 👤 Author

**Kelvin Njoroge**
Supply Chain & Operations Analyst | Excel · Power BI · SQL · Python · SAP ERP

- 📧 kelvin.njoroge156@gmail.com
- 💼 [LinkedIn](https://www.linkedin.com/in/kelvinnjoroge-2b4k)
- 🌍 Nairobi, Kenya

---

*This project is part of a portfolio demonstrating supply chain analytics skills for FMCG roles in East Africa.*
