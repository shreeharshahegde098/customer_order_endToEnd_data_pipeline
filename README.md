# End-to-End Data Engineering Pipeline using Databricks

## 📌 Overview
This project demonstrates an end-to-end **Data Engineering pipeline** built using **Databricks, PySpark, SQL, and Delta Lake**, following the **Medallion Architecture (Bronze → Silver → Gold)**.

The pipeline performs the following tasks:
- Ingests raw JSON data from AWS S3
- Cleans and transforms data using PySpark
- Models the data into a Star Schema
- Implements Slowly Changing Dimension (SCD Type 2) for historical tracking
- Generates analytical datasets using SQL
- Automates the workflow using Databricks Jobs

---


## 🏗 Architecture Diagram

flowchart TD
    A[S3 (Raw JSON Data)] --> B[Bronze Layer <br/> (Databricks Volumes / S3)]
    B --> C[Silver Layer <br/> (PySpark Transformations)]
    C --> D[Gold Layer <br/> (Star Schema + Delta Tables)]
    D --> E[SQL Analytics / Reports]

## 🧱 Medallion Architecture

### Bronze Layer – Raw Data Ingestion
- Raw data ingested from **AWS S3** into **Databricks Volumes**.
- **Data Files:**
  - `customers.json`
  - `orders.json`
  - `products.json`
  - `payments.json`
- Stores raw unprocessed data exactly as received from the source system.

---

### Silver Layer – Data Cleaning & Transformation
- Data cleaning and standardization using **PySpark transformations**.
- **Transformations Performed:**
  - Remove duplicate records
  - Handle null values
  - Convert data types
  - Standardize date formats
  - Filter invalid records
  - Round numerical values
- **Output Format:** Cleaned datasets stored in **Parquet** format for efficient querying.

---

### Gold Layer – Data Modeling
- Analytics-ready datasets designed using a **Star Schema**.
- **Fact Table:**
  - `order_fact`
- **Dimension Tables:**
  - `customer_dim`
  - `product_dim`
  - `payment_dim`
- Stored in **Delta Lake** format to support ACID transactions and optimized analytical queries.

---

## 🔄 Slowly Changing Dimension (SCD Type 2)
Implemented on the **Customer Dimension** to maintain historical changes in customer attributes.

- **Fields Added for Tracking:**
  - `effective_from`
  - `effective_to`
  - `is_current`

This enables tracking of historical customer attribute changes while preserving previous records.

---

## ⚙️ Workflow Orchestration
Automated using **Databricks Jobs**.

**Workflow Execution Steps:**
1. Data Ingestion & Transformation  
2. Data Modeling (Star Schema Creation)  
3. SCD Type 2 Implementation  
4. SCD Validation & Reporting  

Scheduled to run **daily**, ensuring new data is processed and analytical datasets remain updated.

---

## 📊 Reporting & Analytics
SQL queries generate analytical reports such as:
- Daily Sales Report
- Weekly Sales Report
- Monthly Sales Report
- Revenue by Product Category
- Orders by City

Datasets can be connected to **BI tools (e.g., Power BI)** for visualization.

---

## 🛠 Tech Stack
- **Data Processing:** PySpark, SQL  
- **Platform:** Databricks  
- **Storage:** AWS S3, Databricks Volumes  
- **Data Formats:** JSON, Parquet, Delta Lake  
- **Workflow Orchestration:** Databricks Jobs  
- **Data Modeling:** Star Schema, SCD Type 2  

---

## 🚀 Future Improvements
- Implement **Auto Loader** for incremental data ingestion  
- Integrate **Power BI dashboards** for visualization  
- Add **Delta Live Tables (DLT)** for managed pipelines  
- Implement **Data Quality Checks**  
- Integrate **AWS Glue Data Catalog**  

---

## ✅ Project Outcome
This project demonstrates practical implementation of modern **Data Engineering concepts**, including:
- Data ingestion  
- Data transformation  
- Data modeling  
- Historical data tracking (SCD Type 2)  
- Workflow orchestration  

The pipeline showcases how **Databricks and PySpark** can be used to build scalable data pipelines for analytics and reporting.
