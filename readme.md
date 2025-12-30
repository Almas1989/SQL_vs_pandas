# SQL vs Pandas — Salary Analytics Practice

## Project Overview

This repository contains interactive Jupyter notebooks for practicing SQL analytics using DuckDB and exploring salary data. The notebooks demonstrate common SQL patterns, window functions, grouping/rollups, pivoting, time-series operations, and comparisons across categories and grades.

## Notebooks

- [EDA(SQL,pandas).ipynb](EDA(SQL,pandas).ipynb) — exploratory data analysis mixing SQL and pandas.
- [SQL_pract_1.ipynb](SQL_pract_1.ipynb) — first set of SQL practice examples.
- [SQL_pract_2.ipynb](SQL_pract_2.ipynb) — extended SQL practice focused on window functions, QUALIFY, named windows, pivots, and advanced aggregations.

## Dataset

- Main file: `salaries_clean.csv` (cleaned salary listings). Another related file present: `itkz_salaries.csv`.
- The data is loaded into an in-memory DuckDB table called `salaries` using `read_csv_auto`.

### Key columns (typical)

- `Profession` — job title or role.
- `Grade` — seniority level (e.g., Trainee, Junior, Middle, Senior, Lead).
- `Salary` — numeric salary value.
- `City` — location/city of the listing.
- `Skill` — skills tag(s) associated with the listing.
- `Industry` — sector (e.g., IT product, Bank, Startup).
- `Created` — timestamp/datetime when the record was created.
- `Year`, `Quarter`, `Localization`, `Gender`, `Age` — derived or original attributes used for grouping/time analysis.

## Libraries & Tools

- Python: `duckdb`, `pandas`, `numpy`.
- Visualization: `matplotlib`, `seaborn`.
- SQL engine: DuckDB (in-memory tables via a Jupyter kernel).

## SQL Functions & Techniques Used

- Data loading: `read_csv_auto` → `CREATE TABLE salaries` (DuckDB in-memory).
- Filtering & subqueries: `WHERE`, `EXISTS`, `IN`, `BETWEEN`, `ANY`, `ALL`.
- Aggregations: `AVG`, `SUM`, `COUNT`, `MIN`, `MAX`, `MEDIAN`, `ROUND`, `CAST`.
- Arrays: `ARRAY_AGG`, `ARRAY_LENGTH`.
- Window functions: `OVER (PARTITION BY ...)` for non-aggregated group computations.
- Ranking & percentiles: `ROW_NUMBER`, `RANK`, `DENSE_RANK`, `PERCENT_RANK`.
- Row comparison: `LAG`, `LEAD`.
- Running/accumulation and extremes: `SUM() OVER`, `FIRST_VALUE`, `LAST_VALUE`.
- Named windows: `WINDOW` clause for re-usable window definitions.
- Window filtering: `QUALIFY` to filter on window-function results.
- Hierarchical/multi grouping: `ROLLUP`, `CUBE`, `GROUPING SETS`.
- Pivoting: `PIVOT` and manual `CASE`-based pivots for year/grade comparisons.
- Common Table Expressions: `WITH` (CTEs) for clearer query structure.
- Date/time functions: `EXTRACT`, `DATE_TRUNC`, `STRFTIME`, `DATE`, `CURRENT_DATE`, `INTERVAL` for period-based analysis.
- Window ranges: `RANGE BETWEEN INTERVAL ... PRECEDING AND CURRENT ROW` (e.g., 90-day moving averages).
- Formatting: `printf` for human-friendly numeric formatting.

## Typical Analyses Demonstrated

- Top-N salaries per city or profession using `ROW_NUMBER`/`DENSE_RANK` + `QUALIFY`.
- Average salary comparisons across `Grade` levels and pivot tables by year.
- Percentile and ranking-based insights within partitions (e.g., city-level percentiles).
- Rolling averages for professions over the last 90 days using window RANGE frames.
- Time-based aggregations: counts by day/month/year/quarter, and period-over-period percent change using `LAG`.
- Hierarchical summaries using `ROLLUP` / `CUBE` / `GROUPING SETS` for multi-level totals.
- Filtering records relative to groups via `ANY`/`ALL` subqueries (e.g., salaries above any Junior salary).
