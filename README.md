# MySQL Data Cleaning Project

This project focuses on cleaning and preparing a real-world dataset using MySQL. The dataset used (`world_layoffs.layoffs`) contains global layoff data and required multiple stages of cleaning to ensure quality and usability for future analysis.

## Cleaning Steps Overview

The data cleaning process followed four key steps:

1. **Remove Duplicates**  
   - Identified duplicate rows using `ROW_NUMBER()` and `PARTITION BY`.
   - Verified false positives (e.g. multiple entries for companies like *Oda* were legitimate).
   - Deleted true duplicates using a `DELETE` with `ROW_NUMBER()` via CTE logic.
   - Created a new table (`layoffs_staging2`) for cleaner control and tracking row numbers.

2. **Standardise the Data and Fix Errors**  
   - Replaced blank fields in the `industry` column with `NULL`.
   - Updated `NULL` industry values using matching rows from the same company.
   - Standardised inconsistent labels (e.g. *"Crypto Currency"* → *"Crypto"*).
   - Trimmed extra characters from `country` values (e.g. removed trailing periods).
   - Converted the `date` column to `DATE` format using `STR_TO_DATE()` and modified the column type.

3. **Handle Null or Blank Values**  
   - Chose to leave valid `NULL` values in fields like `total_laid_off`, `percentage_laid_off`, and `funds_raised_millions` for analytical flexibility.
   - Deleted rows where both `total_laid_off` and `percentage_laid_off` were missing, as they added no value.

4. **Remove Unnecessary Columns and Rows**  
   - Dropped helper columns like `row_num` after cleaning.
   - Removed records without essential data to ensure analytical quality.
