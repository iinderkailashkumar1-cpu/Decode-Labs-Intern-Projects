# Decode Labs Data Analytics Internship - Project 1
## Project 1: Data Cleaning & Formatting Log (Excel Dataset Standardization)

---

### 📊 Project Overview
This repository documents the systematic data cleaning and standardization process executed on a raw e-commerce dataset consisting of **1,201 sales records**. 

In alignment with **Decode Labs** guidelines, the core objective of this project was to resolve structural discrepancies, eliminate formatting errors, handle missing values, and establish an immutable audit trail—all using standard **Microsoft Excel formulas**[cite: 4].

To guarantee **data integrity** and facilitate easy verification, **the raw columns were not deleted or overwritten**[cite: 4]. Instead, all cleaning and transformation workflows were isolated to newly created columns with the prefix `Cleaned_`, preserving the original data for audit purposes[cite: 4].

---

### 📋 Dataset Metadata
*   **Dataset Size:** 1,201 Rows[cite: 4]
*   **Status:** 100% Cleaned & Verified ✅[cite: 4]
*   **Prepared By:** Data Analyst Team[cite: 4]
*   **Target Deliverables:** Zero duplicate IDs, standardized text casing, filled missing coupon codes, and uniform dates[cite: 4].

---

### 🛠️ Step-by-Step Modification Log

Below is the detailed log of checked issues, actions taken, and the precise Excel formulas implemented:

| ID | Data Check / Feature | Action Taken & Excel Formulas | Status |
| :--- | :--- | :--- | :---: |
| **CR001** | **Duplicate Records** | Scanned all 1,200 rows for duplicate entries. No identical rows were found; all data points are unique[cite: 4]. | **Done** |
| **CR002** | **Text Columns Casing & Spaces** | Removed accidental double spaces and fixed text casing (e.g., converting `"monitor"` or `"MONITOR"` to `"Monitor"`).<br><br>👉 **Formula:**<br>`=PROPER(TRIM(Cell))`[cite: 4] | **Done** |
| **CR003** | **Missing Coupon Codes** | Found blank cells in the coupon column. Instead of deleting records, empty cells were populated with the most frequently used coupon code (`"Freeship"`) using a robust nested array index-match lookup formula[cite: 4].<br><br>👉 **Formula:**<br>`=IF(ISBLANK(T2), PROPER(TRIM(INDEX(T$2:T$1201, MATCH(MAX(COUNTIF(T$2:T$1201, T$2:T$1201)), COUNTIF(T$2:T$1201, T$2:T$1201), 0)))), PROPER(TRIM(T2)))`[cite: 4] | **Done** |
| **CR004** | **Date Format Consistency** | Standardized all date occurrences across the 1,200 rows to strictly follow the uniform `YYYY-MM-DD` standard, regardless of whether they were stored as Excel serial numbers or text strings[cite: 4].<br><br>👉 **Formula:**<br>`=TEXT(IF(ISNUMBER(C2), C2, DATEVALUE(C2)), "yyyy-mm-dd")`[cite: 4] | **Done** |
| **CR005** | **Number Formatting** | Formatted the unit economics metrics (`UnitPrice` and `TotalPrice`) to standard currency with exactly **two decimal places**[cite: 4]. Set `Quantity` and `ItemsInCart` explicitly as clean whole numbers[cite: 4]. | **Done** |

---

### 📈 Summary Notes & Quality Control

*   **🛡️ Impeccable Audit Trail:** The raw data columns were kept completely intact[cite: 4]. New columns prefixed with `Cleaned_` were generated alongside the original variables to make it easy for anyone to audit the logical progression of the formulas[cite: 4].
*   **📐 Data Type Integrity Check:** Conducted a structural verification of values. Text-based fields are aligned to the left, and numerical/financial fields are aligned to the right[cite: 4]. This structural formatting guarantees that Excel Pivot Tables, SQL imports, or BI tool dashboards can group, aggregate, and slice the dataset with **zero calculation errors**[cite: 4].

---