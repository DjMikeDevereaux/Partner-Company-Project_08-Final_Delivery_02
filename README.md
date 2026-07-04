# Partner-Company-Project_08-Final_Delivery_02

Overview
This repository contains the second final deliverable for the Partner Company Project (Proyecto Empresa Aliada). In this stage, the focus is on preparing and structuring the sales dataset to enable robust time‑series modeling in future deliverables. The notebook includes data cleaning, date reconstruction, weekly aggregation, and initial exploratory analysis.

The notebook 58M.01.ProyectoEmpresaAliada_EntregaFinal_02.ipynb documents the full workflow using Python, Pandas, and Statsmodels.

## Objectives
- Convert the raw weekly sales dataset into a clean, time‑indexed structure.
- Reconstruct real calendar dates from WEEK codes.
- Aggregate sales at weekly level to build a consistent time series.
- Prepare the dataset for forecasting models such as SARIMAX.

## Repository Structure
Code
├── 58M.01.ProyectoEmpresaAliada_EntregaFinal_02.ipynb  
├── data/
│   └── FACT_SALES.csv                                   
├── outputs/                                             
└── README.md

## Methodology
1. Data Loading
The dataset FACT_SALES.csv is imported and inspected.
Columns include:

WEEK
ITEM_CODE
TOTAL_UNIT_SALES
TOTAL_VALUE_SALES
TOTAL_UNIT_AVG_WEEKLY_SALES

REGION

2. Date Reconstruction
The WEEK field (e.g., "01-22") is split into:

WEEK_NUM → week number

YEAR → converted from two‑digit format to full year (e.g., "22" → 2022)

A real calendar date is created using ISO week format:

Code
FECHA = pd.to_datetime(YEAR + WEEK_NUM + '1', format='%G%V%u')
This sets the date to the Monday of each ISO week.

The dataset is then sorted and indexed by FECHA.

3. Weekly Aggregation
Weekly total unit sales are computed:

Code
df_weekly = df.groupby(df.index)['TOTAL_UNIT_SALES'].sum().to_frame('VENTAS')
Sample output:

2022‑01‑03 → 5661.824

2022‑01‑10 → 5686.147

2022‑01‑17 → 4844.874

This produces a clean weekly time series ready for forecasting.

4. Exploratory Analysis
The notebook includes:

Descriptive statistics

Weekly trends

Initial visualization of sales behavior

Identification of fluctuations and seasonal patterns

These insights guide the modeling strategy for Deliverable 03.

📈 Key Insights
Based on the visible notebook content:

The dataset spans multiple items and regions but is aggregated into a unified weekly sales series.

Weekly sales show noticeable fluctuations, suggesting potential seasonality.

The reconstructed date index ensures compatibility with SARIMAX and other time‑series models.

The transformation pipeline significantly improves data consistency.

🛠️ Technologies Used
Python 3.x

Pandas, NumPy

Matplotlib

Statsmodels (SARIMAX)

Scikit‑learn (metrics)

Jupyter Notebook
