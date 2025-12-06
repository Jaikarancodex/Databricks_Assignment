# Databricks_Assignment
<img width="1888" height="677" alt="image" src="https://github.com/user-attachments/assets/39457ad8-12e8-41e9-b5a1-4d6ceeb95b05" />
1.Create 3 folders as source_to_bronze, bronze_to_silver, silver_to_gold. 
2. Create 4 notebooks in this respective order. 
* 2 Notebooks named in source_to_bronze as utils (add all common functions in this notebook) and employee_source_to_bronze (driver notebook)
  <img width="1918" height="425" alt="image" src="https://github.com/user-attachments/assets/d7793880-1751-42ba-a526-aa22ae6b9fb2" />

* 1 Notebook in bronze to silver as employee_bronze_to_silver  
* 1 Notebook in silver to gold as employee_silver_to_gold 
3.Read the 3 datasets as Dataframe in employee_source_to_bronze, call utils notebook in this notebook, and write to a location in DBFS, 
as /source_to_bronze/file_name.csv (employee, department_df, country_df) as CSV format. 

4.In employee_bronze_to_silver, call utils notebook in this notebook.  
Read the file located in DBFS location source_to_bronze with as data frame different read methods using custom schema. 

5.convert the Camel case of the columns to the snake case using UDF. 

6.Add the load_date column with the current date. 
* The primary key is EmployeeID, the Database name is Employee_info, Table name is dim_employee. 
* write the DF as a delta table to the location /silver/db_name/table_name. 

7. In gold notebook employee_silver_to_gold, call utils notebook in this notebook 
 Read the table stored in a silver layer as DataFrame and select the columns based on the following requirements. 
