# Data_Analyst_Project_1
# Enterprise Data Reconciliation & Analytics Dashboard

A data analytics project that transforms raw server logs, customer records, and daily foreign exchange rates into reconciled transaction data and finance-ready insights using **Python, SQL, pandas, SQLite, and Power BI**.

## Project Overview

Enterprise transaction data often contains errors, missing exchange rates, and inconsistent customer records. This project implements a data reconciliation pipeline to clean, process, validate, and analyze transaction data.

The workflow extracts active customer records, parses transaction details from server logs, fills missing exchange rates, reconciles transactions, calculates revenue in USD, and generates datasets for business intelligence reporting.

## Key Results

| Metric | Result |
|---|---:|
| Raw server log records | 100,000 |
| Error records removed | 5,098 |
| Valid transactions parsed | 94,902 |
| Missing exchange rates filled | 104 |
| Latest active users identified | 14,183 |
| Final reconciled transactions | 53,899 |
| Total reconciled revenue | $148,274,622.91 |

*These figures are recorded outputs from the included notebook and may change if the input data or processing logic changes.*

## Project Workflow

1. **SQL Data Extraction:** Use SQLite and SQL window functions to identify the latest customer record and filter active users.
2. **Log Parsing:** Use Python regular expressions to extract transaction dates, user IDs, product IDs, and euro amounts from server logs.
3. **Data Cleaning:** Remove error log entries and prepare transaction records for analysis.
4. **Exchange Rate Processing:** Fill missing daily EUR-to-USD exchange rates using forward filling.
5. **Data Reconciliation:** Join transactions with exchange rates and active customer records.
6. **Revenue Calculation:** Calculate USD revenue from euro transaction values and exchange rates.
7. **Business Intelligence:** Generate monthly revenue and top-customer datasets for Power BI dashboards.

## Technologies Used

- **Python** — Data processing and automation
- **pandas** — Data cleaning, transformation, joins, and aggregation
- **SQL / SQLite** — Customer data extraction and filtering
- **Regular Expressions** — Transaction parsing from server logs
- **Jupyter Notebook** — Analysis and workflow documentation
- **Power BI** — Interactive business intelligence dashboards
- **CSV** — Data exchange and analytical outputs

## Repository Structure

```text
.
├── README.md
├── Enterprise_Reconciliation.pbip
├── Enterprise_Reconciliation.Report/
├── Enterprise_Reconciliation.SemanticModel/
└── Enterprise_Data_Reconciliation/
    ├── data/
    │   ├── daily_exchange_rates.csv
    │   ├── exchange_rates_filled.csv
    │   ├── enterprise_database.db
    │   ├── latest_active_users.csv
    │   ├── monthly_revenue.csv
    │   ├── reconciled_transactions.csv
    │   ├── server_logs.txt
    │   └── top5_customers.csv
    ├── powerbi/
    ├── powerbi_backup_20261008_144612/
    ├── screenshots/
    └── source/
        └── Enterprise_Reconciliation_Completed.ipynb
```

## Getting Started

### Prerequisites

Install the following software:

- Python 3.10 or later
- Jupyter Notebook or JupyterLab
- Power BI Desktop (for dashboard visualization)

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd Data_Analyst_Project_1
```

Replace `<YOUR_GITHUB_REPOSITORY_URL>` with your actual GitHub repository URL.

### 2. Install Dependencies

```bash
python -m pip install pandas jupyter
```

The notebook also uses Python's built-in `sqlite3`, `re`, and `pathlib` modules.

### 3. Run the Jupyter Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the following file:

```text
Enterprise_Data_Reconciliation/source/Enterprise_Reconciliation_Completed.ipynb
```

**Important:** Update the Windows-specific `PROJECT_DIR` path in the notebook to match your local project directory before running the cells. Ensure the required input files are available in the expected `data/` directory.

Execute the notebook cells in order to reproduce the data-processing workflow and review the generated results.

### 4. Open the Power BI Dashboard

1. Install and launch Power BI Desktop.
2. Open `Enterprise_Reconciliation.pbip` from the repository root.
3. Reconnect data sources if Power BI reports missing file paths.
4. Refresh the data and inspect the report visuals.

The repository contains Power BI project files rather than a compiled `.pbix` file.

## Data Outputs

| File | Description |
|---|---|
| `reconciled_transactions.csv` | Reconciled transaction-level dataset |
| `latest_active_users.csv` | Latest records for active customers |
| `exchange_rates_filled.csv` | Exchange rates after filling missing values |
| `monthly_revenue.csv` | Aggregated monthly revenue in USD |
| `top5_customers.csv` | Five highest-revenue customers |
| `daily_exchange_rates.csv` | Original daily exchange-rate data |
| `server_logs.txt` | Raw server log input |
| `enterprise_database.db` | SQLite database used for customer extraction |

## Business Value

This project demonstrates how data analytics can help organizations:

- Improve the consistency of transaction records.
- Identify and remove invalid log entries.
- Convert international transactions into a common reporting currency.
- Analyze revenue trends over time.
- Identify high-value customers.
- Prepare structured datasets for financial and executive reporting.

## Limitations and Considerations

- The reconciliation process uses an inner join with active customer records, so transactions without a matching active customer may be excluded.
- Forward filling assumes the last available exchange rate is appropriate for subsequent missing dates.
- Local file paths may need to be updated when running the project on another computer.
- Revenue figures are calculated from the supplied data and exchange rates and are not independently audited financial statements.
- Review datasets and logs for confidential or personal information before making the repository public.

## Future Improvements

- Replace hardcoded file paths with configurable project settings.
- Add automated data-quality checks and unit tests.
- Track unmatched transactions in a separate exception report.
- Add a `requirements.txt` file for reproducible installation.
- Automate scheduled data processing and Power BI refreshes.

## Author

**Enterprise Data Reconciliation & Analytics Dashboard**

*Built to demonstrate practical skills in data engineering, data analysis, SQL, Python, and business intelligence.*

---

If you find this project useful, consider giving the repository a ⭐ on GitHub.
