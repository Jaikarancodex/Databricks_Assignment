# 🚀 Databricks Assignment 

This project implements a full ETL pipeline using **Databricks Free Edition** with **Unity Catalog Volumes**.  
The pipeline includes reading raw CSV files, transforming them, and writing Delta tables across Bronze, Silver, and Gold layers.

---
# QUESTION 1
## 📂 1. Create 3 folders as source_to_bronze, bronze_to_silver, silver_to_gold. 
#### Folder Structure (Created in Workspace)
```python
source_to_bronze/
├── utils
└── employee_source_to_bronze

bronze_to_silver/
└── employee_bronze_to_silver

silver_to_gold/
└── employee_silver_to_gold
```


<img width="1888" src="https://github.com/user-attachments/assets/39457ad8-12e8-41e9-b5a1-4d6ceeb95b05" />

---

## 📘 2. Create 4 notebooks in this respective order. 
* 2 Notebooks named in source_to_bronze as utils (add all common functions in this notebook) and employee_source_to_bronze (driver notebook) 
* 1 Notebook in bronze to silver as employee_bronze_to_silver  
* 1 Notebook in silver to gold as employee_silver_to_gold 

## 🔹 Inside `source_to_bronze`
- `utils` (contains common functions + UDFs)
- `employee_source_to_bronze` (driver notebook)

<img width="1918" src="https://github.com/user-attachments/assets/d7793880-1751-42ba-a526-aa22ae6b9fb2" />

## 🔹 Inside `bronze_to_silver`
- `employee_bronze_to_silver`

<img width="1918" src="https://github.com/user-attachments/assets/230aa57f-34c5-433b-8057-5fed55dc3339" />

## 🔹 Inside `silver_to_gold`
- `employee_silver_to_gold`

<img width="1918" src="https://github.com/user-attachments/assets/35180a48-bdc1-4330-b480-d1c388f258d1" />

---

## 🥉 3. Read the 3 datasets as Dataframe in employee_source_to_bronze, call utils notebook in this notebook, and write to a location in DBFS, as /source_to_bronze/file_name.csv (employee, department_df, country_df) as CSV format. 

### ✔ Read the 3 CSV Files  
### ✔ Call utils notebook  
### ✔ Write the files to `/source_to_bronze/` as CSV

<img width="1918" src="https://github.com/user-attachments/assets/11909dd6-d65a-4fd6-9794-dca48c131966" />
<img width="1917" src="https://github.com/user-attachments/assets/0b522570-7e70-4982-b598-047d184999cd" />
<img width="1918" src="https://github.com/user-attachments/assets/3e404164-2bc4-4a60-8f11-a0e383b21054" />

---

## 🥈 4. In employee_bronze_to_silver, call utils notebook in this notebook.  Read the file located in DBFS location source_to_bronze with as data frame different read methods using custom schema. 

### ✔ Call utils notebook  
### ✔ Read data from `/source_to_bronze/`  
### ✔ Load using custom schema  
### ✔ Convert camelCase → snake_case using UDF

<img width="1918" src="https://github.com/user-attachments/assets/11b8b642-2211-47fe-8912-b0c187bfbed7" />
<img width="1917" src="https://github.com/user-attachments/assets/35fffa2a-b400-4355-a4ff-e3c65345a021" />

---

## 🐍 5. convert the Camel case of the columns to the snake case using UDF. 

<img width="1918" src="https://github.com/user-attachments/assets/ed0f98e8-1b93-48bb-b737-3e9b4be73c28" />
<img width="1707" src="https://github.com/user-attachments/assets/bb5a4617-dfa3-4526-9e6a-540e070f2e2c" />

---

## 📅 6. Add the load_date column with the current date. 
* The primary key is EmployeeID, the Database name is Employee_info, Table name is dim_employee. 
* write the DF as a delta table to the location /silver/db_name/table_name. 

### ✔ Add `load_date`  
<img width="1918" src="https://github.com/user-attachments/assets/c28b4e03-7762-4050-bdbe-28686e98d6c7" />

### ✔ PK = EmployeeID  
### ✔ DB = `assignment.Employee_info`  
### ✔ Table = `dim_employee`  
### ✔ Write Delta to `/silver/db_name/table_name`
### ✔ Silver Delta Write + Table Creation
<img width="1918" src="https://github.com/user-attachments/assets/70289f3d-8131-42e3-835c-5f8dc0a7ecf5" />
<img width="1918" src="https://github.com/user-attachments/assets/07b59ad3-72f1-421d-93cb-ca5e0955e993" />

---

## 🥇 7. In gold notebook employee_silver_to_gold, call utils notebook in this notebook  Read the table stored in a silver layer as DataFrame and select the columns based on the following requirements. 

### ✔ Call utils notebook  
### ✔ Read Silver table  
### ✔ Select columns required for analytics

<img width="1918" src="https://github.com/user-attachments/assets/58ccd2de-9ad2-4d5b-b310-08d36af104f0" />
<img width="1917" src="https://github.com/user-attachments/assets/56d32a57-7970-4e48-b9f1-55ae49664bc9" />

---

# ⭐ 8. Gold Layer Requirements

## 🔹 1. Salary of each department (descending)
<img width="1918" src="https://github.com/user-attachments/assets/d64284e6-4473-4e9e-aa05-2d7ff4838c8a" />

## 🔹 2. Employee count per department per country
<img width="1918" src="https://github.com/user-attachments/assets/90657188-fce3-4590-8fa7-9fdefdee0c9b" />

## 🔹 3. Map of departments ↔ countries
<img width="1918" src="https://github.com/user-attachments/assets/306c096e-86ca-4169-bc10-55824a387f94" />

## 🔹 4. Average age by department
<img width="1918" src="https://github.com/user-attachments/assets/a48a969e-c927-4722-b401-b9c62e1e5fb0" />

## 🔹 5. Add `at_load_date`
<img width="1918" src="https://github.com/user-attachments/assets/59eb6d7d-050d-4d27-b9ff-35a7fc55b1ea" />

## 🔹 6. Write GOLD table to Delta  
Location:  
`/gold/employee/fact_employee`  
Mode:  
`overwrite` + `replaceWhere(at_load_date)`

<img width="1918" src="https://github.com/user-attachments/assets/d4f0716a-479e-454a-8887-76ce87ca601b" />

---

# ✅ Summary

| Layer | Description |
|-------|-------------|
| **Bronze** | Raw CSV files written to volume |
| **Silver** | Cleaned, standardized employee table with snake_case + load_date |
| **Gold** | Analytical outputs + fact table with at_load_date |

---


