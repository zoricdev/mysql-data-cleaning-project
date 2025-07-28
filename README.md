# MySQL Data Cleaning Project

This project focuses on cleaning and preparing a dataset of global company layoffs using MySQL. The original data contained duplicates, inconsistent values, null fields, and irrelevant rows/columns. Through a series of SQL queries and best practices, the dataset was transformed into a clean, structured version ready for analysis.

## Dataset

The dataset comes from the `world_layoffs.layoffs` table and includes information such as company names, industries, layoff numbers, dates, funding, and more.

## Cleaning Steps

The project was broken into four key stages:

### 1. Remove Duplicates
- Used `ROW_NUMBER()` to identify exact duplicate records.
- Validated that similar entries (e.g. "Oda") were not removed if they were legitimate.
- Removed true duplicates using a CTE or temporary row number column.
- Ensured only the first instance of each duplicate remained.

### 2. Standardise the Data and Fix Errors
- Converted blank strings to `NULL` for consistency.
- Populated missing `industry` fields using values from other matching rows.
- Standardised variations (e.g. "Crypto Currency" → "Crypto").
- Trimmed trailing characters from `country` names (e.g. "United States.").
- Converted the `date` column to a proper `DATE` format using `STR_TO_DATE()`.

### 3. Handle Null or Blank Values
- Reviewed `NULL` values in key fields like `total_laid_off`, `percentage_laid_off`, and `funds_raised_millions`.
- Left these as-is when appropriate to support accurate analysis (especially in EDA).

### 4. Remove Unnecessary Columns and Rows
- Removed rows where both `total_laid_off` and `percentage_laid_off` were `NULL`.
- Dropped helper columns such as `row_num` used temporarily for deletion.

## 💻 Technologies Used
- MySQL
- MySQL Workbench

## Key SQL Concepts Applied
- Common Table Expressions (CTEs)
- `ROW_NUMBER()` window function
- Conditional updates and joins
- String manipulation and formatting
- Data type conversion
- Data validation and integrity checks

## ✅ Outcome

A clean and consistent version of the layoffs dataset (`layoffs_staging2`) was created. This dataset is now ready for further analysis, visualisation, or use in an EDA (Exploratory Data Analysis) pipeline.

---

> This project showcases strong SQL data cleaning practices and is a great foundation for any data analysis or business intelligence workflow.
