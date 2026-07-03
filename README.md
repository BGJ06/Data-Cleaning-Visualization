# E-Commerce Data Cleaning & Interactive Dashboard Pipeline 📊

A robust, modular data pipeline that generates a raw messy e-commerce dataset, processes it using a multi-stage cleaning workflow, performs exploratory data analysis (EDA), and serves insights through an interactive **Streamlit** dashboard.

## 🎯 Project Overview
This project simulates real-world data engineering and analytics tasks. It demonstrates how to clean inconsistent customer transaction records (addressing missing values, typos, duplicates, and statistical outliers) and compile business insights (such as revenue metrics, sales trends, and customer satisfaction profiles) into a sleek corporate web application.

---

## ⚙️ Core Pipeline Components
1. **Messy Data Generator** (`src/generator.py`): Generates a synthetic dataset of 1,200+ records with intentional flaws (e.g., negative prices/quantities, extreme ages, conflicting duplicates, and missing dates).
2. **Data Cleaner** (`src/cleaner.py`): Imputes missing numeric values using medians, standardizes categorical representations (e.g., normalising gender inputs and payment methods like `GPay`), recalculates erroneous spend totals, and filters records.
3. **Exploratory Data Analysis** (`src/analyzer.py`): Creates publication-quality static Seaborn charts to visualize customer demographics and sales performance.
4. **Interactive Streamlit Web Dashboard** (`app.py`): A premium dark-mode dashboard displaying KPI cards, filters, interactive distributions, and data narratives.

---

## 🔧 Data Issues Handled & Cleaned
* **Duplicate Records**: Dropped exact duplicate rows and resolved conflicting entries sharing the same `Transaction_ID`.
* **Broken Formats & Missing Dates**: Standardized multiple input formats (e.g., YYYY-MM-DD, DD/MM/YYYY, and long text dates) and filled unparseable fields.
* **Customer Demographics**: Cleaned gender variations (`M`, `male`, `Mlae` ➔ `Male`) and imputed missing ages while capping extreme age outliers.
* **Numerical Imputation & Outlier Capping**: Imputed missing/zero unit prices based on category-specific medians and capped quantity anomalies.
* **Recalculated Expenditures**: Validated and recalculated incorrect `Total_Spent` values (`Quantity * Unit_Price`).
* **Customer Satisfaction Rating**: Standardized ratings to a $1$ to $5$ scale and filled missing inputs.

---

## 📊 Visualizations Included (`/plots`)
* **Monthly Sales Trend** (`sales_trend.png`): Line chart tracking sales revenue fluctuations.
* **Customer Age Distribution** (`age_distribution.png`): Demographic frequency histogram with KDE curve.
* **Revenue by Product Category** (`revenue_by_category.png`): Rank-ordered bar chart of categorical revenue in Indian Rupees (INR ₹).
* **Spend vs Satisfaction** (`satisfaction_vs_spend.png`): Bar chart evaluating how average order value correlates with ratings.

---

## 📂 Project Structure
```
d:\Internship project\
├── data/                      # Data storage
│   ├── raw_sales_data.csv     # Messy dataset
│   └── cleaned_sales_data.csv # Cleaned dataset
├── plots/                     # Static EDA visualizations
├── src/                       # Source files
│   ├── __init__.py
│   ├── generator.py           # Synthetic dataset generator
│   ├── cleaner.py             # Normalization and cleaning
│   └── analyzer.py            # Static plot builder
├── app.py                     # Streamlit application
├── requirements.txt           # Project dependencies
└── README.md                  # Project documentation
```

---

## 🚀 Quickstart Guide

### 1. Prerequisites
Ensure you have Python 3.10+ installed.

### 2. Setup Virtual Environment & Install Dependencies
```bash
# Create virtual environment
python -m venv .venv

# Activate virtual environment (Windows PowerShell)
.venv\Scripts\Activate.ps1

# Activate virtual environment (Mac/Linux)
source .venv/bin/activate

# Install required libraries
pip install -r requirements.txt
```

### 3. Run Pipeline Scripts
You can run each stage of the pipeline independently from the command line:
```bash
# Generate messy data
python src/generator.py

# Run cleaning script
python src/cleaner.py

# Generate static charts
python src/analyzer.py
```

### 4. Start the Interactive Dashboard
Launch the web interface locally:
```bash
streamlit run app.py
```
Open **`http://localhost:8501`** in your browser to view the interactive dashboard.

---

## 🛠️ Built With
* **Python** — Core language
* **Pandas** — Data manipulation and structuring
* **NumPy** — Mathematical operations
* **Matplotlib & Seaborn** — Data visualization
* **Streamlit** — Web application framework
