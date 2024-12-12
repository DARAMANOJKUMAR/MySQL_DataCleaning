Project: Data Cleaning
1.Data Backup and Staging:
Created a staging table layoffs_staging as a working copy of the original layoffs table to avoid affecting raw data.
Inserted all data from the original table into the staging table.

2.Duplicate Detection and Removal:
Identified duplicates using ROW_NUMBER() with PARTITION BY on key columns.
Marked rows with a row_num > 1 as duplicates and removed them.
Added a new row_num column for easier tracking of duplicate rows.

3.Standardizing Data:
Standardized industry values (e.g., unified "Crypto Currency" and "CryptoCurrency" into "Crypto").
Cleaned country values (e.g., removed trailing periods from "United States.") using the TRIM() function.
Reformatted date columns using STR_TO_DATE() to ensure uniform date formatting.

4.Null Value Handling:
Addressed null and empty values by setting blank strings in industry to NULL.
Used a self-join query to populate missing industry values where other rows for the same company had the information.

5.Column and Row Cleanup:
Removed unnecessary columns and rows where data was unusable (e.g., rows with both total_laid_off and percentage_laid_off as NULL).
Dropped the row_num column after cleaning.
