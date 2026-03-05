End-to-End Data Engineering Pipeline using Databricks
Overview

This project demonstrates an end-to-end Data Engineering pipeline built using Databricks, PySpark, SQL, and Delta Lake, following the Medallion Architecture (Bronze → Silver → Gold).

The pipeline performs the following:

Ingests raw JSON data from AWS S3

Cleans and transforms data using PySpark

Models the data into a Star Schema

Implements Slowly Changing Dimension (SCD Type 2) for historical tracking

Generates analytical datasets using SQL

Automates the workflow using Databricks Jobs

🧱 Medallion Architecture
Bronze Layer (Raw Data Ingestion)

Raw data is ingested from AWS S3 into Databricks Volumes.

Data Files

customers.json

orders.json

products.json

payments.json

The Bronze layer stores the raw unprocessed data exactly as received from the source.

Silver Layer (Data Cleaning & Transformation)

The Silver layer performs data cleaning and standardization using PySpark transformations.

Transformations Performed

Removed duplicate records

Handled null values

Converted data types

Standardized date formats

Filtered invalid records

Rounded numerical values

Output Format

Cleaned datasets are stored in Parquet format for efficient querying.

Gold Layer (Data Modeling)

The Gold layer contains analytics-ready datasets designed using a Star Schema.

Star Schema Model
Fact Table

order_fact

Dimension Tables

customer_dim

product_dim

payment_dim

These tables are stored in Delta Lake format to support ACID transactions and efficient analytics.

Slowly Changing Dimension (SCD Type 2)

SCD Type 2 was implemented on the Customer Dimension to maintain historical changes in customer attributes.

Fields Added for Historical Tracking

effective_from

effective_to

is_current

This enables tracking customer attribute changes over time while preserving historical records.

Workflow Orchestration

The pipeline is automated using Databricks Jobs.

Workflow Execution Steps

Data Ingestion & Transformation

Data Modeling (Star Schema Creation)

SCD Type 2 Implementation

SCD Validation & Reporting

The workflow is scheduled to run daily, ensuring the pipeline processes new data and keeps analytical datasets updated.

Reporting & Analytics

SQL queries are used to generate analytical reports such as:

Daily Sales Report

Weekly Sales Report

Monthly Sales Report

Revenue by Product Category

Orders by City

These datasets can be connected to BI tools such as Power BI for visualization.

Tech Stack
Data Processing

PySpark

SQL

Platform

Databricks

Storage

AWS S3

Databricks Volumes

Data Formats

JSON

Parquet

Delta Lake

Workflow Orchestration

Databricks Jobs

Data Modeling

Star Schema

Slowly Changing Dimension (SCD Type 2)

Future Improvements

Implement Auto Loader for incremental data ingestion

Integrate Power BI dashboards for visualization

Add Delta Live Tables (DLT) for managed pipelines

Implement Data Quality Checks

Integrate AWS Glue Data Catalog

Project Outcome

This project demonstrates practical implementation of modern Data Engineering concepts, including:

Data ingestion

Data transformation

Data modeling

Historical data tracking (SCD Type 2)

Workflow orchestration

The pipeline showcases how Databricks and PySpark can be used to build scalable data pipelines for analytics and reporting.
