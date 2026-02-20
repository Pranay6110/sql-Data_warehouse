**Sql-Data_Warehouse**

A centralized SQL Server-based data warehousing solutions by integrating ERP and CRM sources, enabling high-fidelity BI reporting on sales trends and customer behavior.

**Data engineering part: Data warehousing:**

Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

Specifications:
Data Sources: Import data from two source systems (ERP and CRM) provided as CSV files.
Data Quality: Cleanse and resolve data quality issues prior to analysis.
Integration: Combine both sources into a single, user-friendly data model designed for analytical queries.
Scope: Focus on the latest dataset only; historization of data is not required.
Documentation: Provide clear documentation of the data model to support both business stakeholders and analytics teams.


**BI: Analytics & Reporting (Data Analysis)**

Objective: Develop SQL-based analytics to deliver detailed insights into:
**Customer Behavior**
**Product Performance**
**Sales Trends**

These insights empower stakeholders with key business metrics, enabling strategic decision-making.
Reference: For more details, refer to docs/requirements.md.


**Designing the Data Architecture:**

Data lake building: can store semi-structure and unstructured data (logs, images, different DBs) + ML +reporting
Data lakehouse: Mix of Data warehouse and data lake
Data Mesh: use decentralized approach, free from bottle neck problem.
Data Warehouse building: when you want to built solid foundation for reporting and visualization.



i) Inmon approach
a. Staging: where the row data is landing
b. Enterprise data warehouse: transform the data into 3NF
c. Data mars: take small sebsets from data warehouse +connect with the BI tool

ii) Kimball approach
a. Staging +Data mars = results in saving time, to again and again transform the data in DW

iii) Data vault
a. Staging + Enterprise DW (Raw Vault +Business Vault) + Data Mars + BI reporting

iv) Medallion Architecture (Basically - Ingest + Cleaning + Business)
a. Bronze layer: Row, unprocessed data as it is from the source (Tracebility and Debugging)  - Tables - Full load (Truncate and insert)
b. Silver Layer : Clean and standarised data - Tables - Full load (Truncate and insert) = cleaning+normalization+enrichment
c. gold layer: Business ready data + Reporting - Views - None - Integration+aggregation+busiesslogic


**Naming Convention:**
Set of Rules and guidelines of:
Database, Schema, tables, Store Procedure

Bronze Layer: Camel case, pascal case, snake case, etc.
   Example: crm_customer_info
2. Silver layer: Same rules has to be followed in this layer also
3. Gold Layer: Meaningful and business aligned

4. Column naming convention:
  a. Surrogate keys: all primary keys will have suffix as _key
  b. technical Columns: all technical keys will have prefix as dwh_
  c. Stored Procedure: naming pattern = load_bronze, load_silver
