# JCBOUNCE · Employee Analytics Dashboard

A fully self-contained HTML dashboard for employee performance analytics, powered by Excel data.

## Files

| File | Description |
|------|-------------|
| `Employee_Dashboard_v2.html` | Main dashboard (data embedded or loaded from `data.js`) |
| `EMPLOYEE_DATA_ONLINE.xlsx` | Source data (update this file to refresh metrics) |
| `build_data.py` | Script to convert Excel → `data.js` for external loading |
| `README.md` | This file |

## Quick Start (GitHub Pages)

1. Clone or download this repository.
2. Open `Employee_Dashboard_v2.html` directly in a browser — the data is already embedded.
3. *(Optional)* To use an external data file, see **Updating Data** below.

## Updating Data

When the Excel file changes:

```bash
# Install dependencies (once)
pip install pandas openpyxl

# Re-generate data.js from the updated Excel
python build_data.py EMPLOYEE_DATA_ONLINE.xlsx

# Then open Employee_Dashboard_v2.html — it reads data.js automatically
# if you include: <script src="data.js"></script> before the dashboard script
```

## Excel Format

The Excel file (`EMPLOYEE_DATA_ONLINE.xlsx`) must contain these columns:

| Column | Description |
|--------|-------------|
| `Salon` | Salon/location name |
| `Designation` | Employee designation |
| `Category` | Department (e.g. HAIR, BEAUTY) |
| `Tenure` | Years of service |
| `EmployeeCode` | Unique employee identifier |
| `EmployeeName` | Full name |
| `Category.1` | Metric name (SERVICE SALES, PRODUCT SALES, etc.) |
| `YearNum` | Year (2025, 2026, …) |
| `JAN`–`DEC` | Monthly values for the metric |
| `Brand` | Brand code (e.g. JCB) — used for the Brand filter |

## Dashboard Features

- **Filters**: Year, Department, Designation, Salon, **Brand**, Month
- **Employee Table** with 5 view matrices: Service Sales, Product Sales, Clients, Performance, All Columns
- **Monthly Trends** page with per-employee or aggregate charts
- **Year vs Year** comparison
- **Light / Dark** theme toggle (Light by default)

## Metrics

| Metric | Calculation |
|--------|-------------|
| Monthly Avg (Sales) | Total ÷ number of months with data > 0 |
| Prod Penetration % | (Total Clients Product ÷ Total Clients Services) × 100 |
| Retention % | Average of non-zero monthly retention % values |
| Repeat % | 3-Month Repeat Clients ÷ Total Clients × 100 |

