# 🛍️ Customer Segmentation — Retail Buyer Profiling
**By Ayush Rai**

A data science project that transforms a flat retail transaction database into actionable buyer profiles using **RFM Analysis** and **KMeans Clustering**, enabling the marketing team to move away from one-size-fits-all campaigns.

---

## 📌 Project Overview

This project analyzes an online retail dataset of **541,909 transactions** to segment customers into four distinct behavioral profiles. Each profile carries tailored marketing strategies to maximize revenue, retention, and engagement.

The core methodology combines:
- **RFM (Recency, Frequency, Monetary)** feature engineering
- **KMeans Clustering** for unsupervised grouping
- **Rule-based thresholds** for human-readable profile labeling

---

## 👥 Buyer Profiles

| Profile | Color | Description | Strategy |
|---|---|---|---|
| 🟢 **Champions** | Teal | High-frequency, high-spend, recently active | Loyalty perks, early access, personalised milestones |
| 🔵 **Regulars** | Indigo | Consistent buyers with untapped spend potential | Category upsells, personalised product journeys |
| 🔴 **Dormant** | Rose-Red | Lapsed buyers at risk of permanent churn | 3-stage re-engagement email flow |
| 🟠 **Newcomers** | Orange | First/second purchase buyers in the critical window | Post-purchase welcome journey (no discounts yet) |

---

## 📊 RFM Measurement Framework

| Metric | What It Measures | Why It Matters |
|--------|-----------------|----------------|
| **Recency** | Days elapsed since the last transaction | Signals current engagement level |
| **Frequency** | Count of distinct orders placed | Reflects purchase habit and brand loyalty |
| **Monetary** | Cumulative spend amount | Approximates customer lifetime value |

---

## 📁 Dataset

- **Source:** UCI Online Retail Dataset (`Online Retail.xlsx`)
- **Size:** 541,909 rows × 8 columns
- **Date Range:** December 2010 – December 2011
- **Primary Market:** United Kingdom

### Columns

| Column | Type | Description |
|--------|------|-------------|
| `InvoiceNo` | object | Unique invoice identifier |
| `StockCode` | object | Product code |
| `Description` | object | Product name |
| `Quantity` | int64 | Units purchased per line |
| `InvoiceDate` | datetime | Timestamp of transaction |
| `UnitPrice` | float64 | Price per unit (£) |
| `CustomerID` | float64 | Unique customer identifier |
| `Country` | object | Country of the customer |

> **Note:** 135,080 rows have missing `CustomerID` values and are excluded during RFM computation.

---

## 🔬 Project Workflow

The notebook follows a structured 17-step pipeline:

1. **Library Imports & Theme Setup** — Dark ocean visual theme configured
2. **Load Dataset** — Excel file ingested into a Pandas DataFrame
3. **Preliminary Data Inspection** — Schema review, null counts, descriptive stats
4. **Data Cleaning** — Remove cancellations, nulls, and negative values
5. **Feature Engineering** — Compute Revenue column (`Quantity × UnitPrice`)
6. **RFM Table Construction** — Aggregate per-customer Recency, Frequency, Monetary scores
7. **Outlier Treatment** — Cap extreme values to prevent cluster distortion
8. **Feature Scaling** — StandardScaler applied before clustering
9. **Optimal K Selection** — Elbow method + Silhouette score analysis
10. **KMeans Clustering** — Fit model on scaled RFM features
11. **Cluster Profiling** — Summarize cluster-level RFM statistics
12. **Segment Labeling** — Map clusters to Champion / Regular / Dormant / Newcomer
13. **Segment Distribution** — Count and proportion visualizations
14. **RFM Distribution Plots** — Per-segment box plots and histograms
15. **Recency vs Revenue Scatter** — Cross-segment revenue vs. engagement view
16. **Strategic Recommendations** — Actionable marketing strategies per profile
17. **Export Results** — Final RFM + segment data written to `buyer_profiles_output.xlsx`

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, and RFM aggregation |
| `numpy` | Numerical operations |
| `matplotlib` | Custom dark-themed visualizations |
| `seaborn` | Statistical plots |
| `scikit-learn` | StandardScaler, KMeans, Silhouette Score |
| `openpyxl` | Excel export |

---

## ⚙️ Setup & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/customer-segmentation.git
cd customer-segmentation
```

### 2. Install Dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```

### 3. Add the Dataset
Place `Online Retail.xlsx` in the project directory (or update the file path in **Step 2** of the notebook).

### 4. Run the Notebook
```bash
jupyter notebook Customer_Segmentation_By_Ayushrai.ipynb
```

---

## 📤 Outputs

| File | Description |
|------|-------------|
| `buyer_profiles_output.xlsx` | Full RFM table with segment labels + cluster summary sheet |
| `recency_revenue_scatter.png` | Scatter plot: Days since last purchase vs. total revenue |

---

## 💡 Key Insights

- **Champions** are a small but disproportionately valuable group — respond better to prestige than discounts.
- **Regulars** show genuine brand affinity; category-based upsell journeys can widen basket size.
- **Dormant** buyers should be targeted within 180 days of inactivity — win-back probability drops sharply after that.
- **Newcomers** are in a critical 30-day window; a post-purchase welcome journey (no discount codes) increases long-term conversion.

---

## 🔄 Maintenance Recommendation

Re-run the model **at least monthly**. Track **profile migration rates** (e.g., Dormant → Newcomer or Regular following a campaign) as a primary marketing KPI alongside acquisition and retention metrics.

---

## 👤 Author

**Ayush Rai**  
*Retail Buyer Profiling — Strategic Analytics Report*

---

## 📄 License

This project is for educational and analytical purposes. The dataset is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+Retail).
