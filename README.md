End-to-End Data Engineering Pipeline using Databricks
Overview

This project demonstrates an end-to-end data engineering pipeline built using Databricks, PySpark, SQL, and Delta Lake following the Medallion Architecture (Bronze–Silver–Gold).

The pipeline ingests raw JSON data from AWS S3, performs data cleaning and transformations using PySpark, models the data into a star schema, implements Slowly Changing Dimension (SCD Type 2) for historical tracking, and generates analytical datasets for reporting.

The workflow is orchestrated using Databricks Jobs, enabling automated pipeline execution.

Medallion Architecture
Bronze Layer

Raw data is ingested from AWS S3 into Databricks.

Data Files

customers.json

orders.json

products.json

payments.json

Raw data is stored in the Bronze layer inside Databricks Volumes.

Silver Layer

Data is cleaned and standardized using PySpark transformations.

Transformations Performed

Removed duplicate records

Handled null values

Converted data types

Standardized date formats

Filtered invalid records

Rounded numerical values

Cleaned datasets are stored in Parquet format.

Gold Layer

The Gold layer contains analytics-ready datasets.

Star Schema Model
Fact Table

order_fact

Dimension Tables

customer_dim

product_dim

payment_dim

Slowly Changing Dimension (SCD Type 2)

SCD Type 2 was implemented on the Customer Dimension to track historical changes in customer attributes.

Fields Added for Tracking

effective_from

effective_to

is_current

Workflow Orchestration

The pipeline is automated using Databricks Jobs.

The workflow consists of four notebooks executed sequentially:

Data Ingestion & Transformation

Data Modeling (Star Schema Creation)

SCD Type 2 Implementation

SCD Validation & Reporting

The workflow is scheduled to run once per day, ensuring the pipeline processes new data and keeps analytical datasets updated.

Reporting

SQL queries are used to generate analytical reports such as:

Daily sales report

Weekly sales report

Monthly sales report

Revenue by product category

Orders by city

Tech Stack
Data Processing

PySpark

SQL

Platform

Databricks

Storage

AWS S3

Databricks Volumes

Data Format

JSON

Parquet

Delta Lake

Workflow Orchestration

Databricks Jobs

Data Modeling

Star Schema

Slowly Changing Dimension (SCD Type 2)

Future Improvements

Implement Auto Loader for incremental ingestion

Integrate Power BI dashboards for visualization

Add Delta Live Tables

Implement Data Quality Checks

Integrate AWS Glue Catalog

Project Outcome

This project demonstrates practical implementation of modern data engineering concepts, including data ingestion, transformation, modeling, historical tracking, and workflow orchestration using Databricks and PySpark.
