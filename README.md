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

# Question 2: 

1. Api: https://reqres.in/api/users?page=2 
2.drop "page”, "per_page", "total", "total_pages" and complete block of support. 

3.Fetch the data from the given API by passing the parameter as a page and retrieving the data till the data is empty. 

4.Read the data frame with a custom schema 
<img width="1918" height="685" alt="image" src="https://github.com/user-attachments/assets/7f9a1cf2-c62d-4831-a55e-f49644452742" />

5.Flatten the dataframe 
<img width="1917" height="658" alt="image" src="https://github.com/user-attachments/assets/d8f1568e-0a96-49ba-a393-c9fec33e0cd4" />

6.Derive a new column from email as site_address with values(reqres.in) 
<img width="1917" height="567" alt="image" src="https://github.com/user-attachments/assets/2551fb13-0446-44f8-8055-85f03a02efd5" />

7.Add load_date with the current date 
<img width="1918" height="601" alt="image" src="https://github.com/user-attachments/assets/f88f9aa9-9a9c-4d6c-9570-05abc0488f94" />

8.Write the data frame to location in DBFS as /db_name /table_name with  
<img width="1918" height="432" alt="image" src="https://github.com/user-attachments/assets/6fa8c720-6d0c-4dd7-a2fc-0ed0aecb06a6" />

9.Db_name as site_info and table_name as person_info with delta format and overwrite mode. 
<img width="1918" height="642" alt="image" src="https://github.com/user-attachments/assets/c167854b-b867-49f2-9c4a-a0ca43d30c35" />

# Question 2 — API Ingestion, Transformation & Delta Load (Databricks)

This task implements ingesting API data from **reqres.in**, flattening JSON, transforming fields, and writing the output as a Delta table inside **Unity Catalog / Volumes**.

---

# 🔄 Part A — Free Edition Workaround (Before Q4 Logic)

Databricks Free Edition blocks external API calls.  
To simulate API ingestion, we generate and store the JSON response manually.

---

## ✅ Step 1 — Create JSON API Response
<img width="1916" height="787" alt="image" src="https://github.com/user-attachments/assets/2ff6729b-ec58-400c-a0c6-c04cce6cc39b" />

---

## ✅ Step 2 — Save JSON to Volume
<img width="1918" height="322" alt="image" src="https://github.com/user-attachments/assets/f1a2e9ee-3f19-4e08-b8a1-726c940dbc71" />

---

## ✅ Step 3 — Read JSON With Multiline Support
<img width="1918" height="621" alt="image" src="https://github.com/user-attachments/assets/d04e2e68-abdd-4949-bf2d-c32dc0076a36" />

---

# ⭐ Part B — Required Assignment Logic (Q4 onward)

---

## 📌 1. API URL

```
https://reqres.in/api/users?page=2
```

---

## 📌 2. Drop Columns

Drop:
- page
- per_page
- total
- total_pages
- support (entire block)

<img width="1918" height="555" alt="image" src="https://github.com/user-attachments/assets/36e181a1-333c-4b70-a927-8368d6f0c4e9" />

---

## 📌 3. Fetch Pages Until Empty
### Databricks FREE EDITION (NO INTERNET)
#### You CANNOT do the loop.

## ✅You MUST:

* Download the JSON manually
* Save it into /Volumes/.../api/users_page1.json
* Read it with multiline JSON
* Then flatten it
* No loop needed
* No pagination logic needed
* Correct code:
<img width="1918" height="640" alt="image" src="https://github.com/user-attachments/assets/a4fb5342-e969-4921-ac5d-6cde04f1289e" />

### Then:

<img width="1918" height="611" alt="image" src="https://github.com/user-attachments/assets/8c286743-dfc8-41d0-b36e-f22b3cc658f7" />


---

## 📌 4. Read Into DataFrame Using Custom Schema
<img width="1918" height="611" alt="image" src="https://github.com/user-attachments/assets/d4c14dd3-3dd1-4ada-83e6-c6b32ad206b4" />


---

## 📌 5. Flatten the DataFrame
<img width="1918" height="636" alt="image" src="https://github.com/user-attachments/assets/fe4d9ee8-5d2f-471f-8ce9-4ace9740d366" />

---

## 📌 6. Derive Column `site_address`
<img width="1917" height="536" alt="image" src="https://github.com/user-attachments/assets/51db6a00-4d60-41cf-8afd-95068c678c7b" />

---

## 📌 7. Add `load_date`
<img width="1918" height="556" alt="image" src="https://github.com/user-attachments/assets/bcc05a0f-3f4e-4300-9146-05f1e21b5539" />


---

## 📌 8. Write DataFrame to DBFS as Delta
<img width="1918" height="300" alt="image" src="https://github.com/user-attachments/assets/d2823729-db43-4ad4-a57e-e00e4419fefd" />

---

## 📌 9. Register Table in Unity Catalog
<img width="1918" height="660" alt="image" src="https://github.com/user-attachments/assets/bbcab0c1-2410-4800-b424-c54a8b4413ca" />

---

### 🎉 Final Output

A fully transformed Delta table registered in Unity Catalog:



 
