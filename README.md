# Azure-incremental_data_pipeline

## 📌 Project Overview

This project implements an end-to-end data engineering pipeline using Microsoft Azure services. The pipeline extracts data from Azure SQL, ingests and orchestrates the data using Azure Data Factory, stores data in Azure Data Lake Storage Gen2, and performs scalable transformations using Azure Databricks, PySpark, and Delta Lake.

The project follows the Medallion Architecture with Bronze, Silver, and Gold layers and implements incremental data processing for efficient data ingestion.

## 🛠️ Technologies Used

* Azure Data Factory (ADF)
* Azure Data Lake Storage Gen2 (ADLS Gen2)
* Azure Databricks
* Apache Spark
* PySpark
* Delta Lake
* Azure SQL Database
* Unity Catalog
* Databricks Metastore
* Azure Databricks Access Connector
* Git
* GitHub

## 🔄 Data Pipeline

The overall data flow is:

**Azure SQL → Azure Data Factory → ADLS Gen2 → Bronze → Silver → Gold**

### Source

Azure SQL Database is used as the source system containing the data to be processed.

### Ingestion

Azure Data Factory is used to extract data from Azure SQL and load it into Azure Data Lake Storage Gen2.

ADF pipelines handle data ingestion, parameterization, incremental extraction, and pipeline orchestration.

### Bronze Layer

The Bronze layer stores the ingested source data with minimal transformation, providing a reliable foundation for downstream processing.

### Silver Layer

Azure Databricks and PySpark are used to clean, validate, and transform the Bronze data.

Transformations include data cleansing, data type handling, null handling, duplicate handling, and standardization.

### Gold Layer

The Gold layer contains refined and business-ready datasets generated from the Silver layer for downstream consumption.

## 📈 Incremental Data Loading

The pipeline implements incremental data loading to avoid processing the complete source dataset during every execution.

A watermark-based approach is used to identify and process newly available records.

**Last Load Value → Current Load Value → Extract New Records → Transform → Load**

This approach reduces unnecessary data processing and improves pipeline efficiency.

## ⚙️ Databricks Workflows

Databricks Workflows are used to orchestrate multiple notebook tasks and execute them according to their dependencies.

The workflow coordinates different stages of data processing, such as:

**Ingestion → Bronze to Silver → Silver to Gold**

Task execution and status can be monitored through Databricks Workflows.

## 🗂️ Unity Catalog & Data Governance

Unity Catalog is used to provide centralized governance and organization of data and data assets within Azure Databricks.

The Databricks Metastore provides the central metadata management layer for Unity Catalog.

The project uses the Unity Catalog hierarchy:

**Metastore → Catalog → Schema → Tables**

Access to Azure Data Lake Storage is configured through an **Azure Databricks Access Connector**, managed identity, storage credentials, and external locations.

This enables Databricks to securely access cloud storage without embedding storage access keys directly in notebooks.

## 🔐 Security

Azure Databricks Access Connector and managed identity-based authentication are used to provide secure access to Azure Data Lake Storage.

Unity Catalog is used to manage data access and governance within Databricks.

## 📂 Repository Structure

```text
Azure-incremental_data_pipeline/
│
├── adf/
│   └── ADF pipeline artifacts
│
├── databricks/
│   └── notebooks/
│       ├── silver_notebook
│       ├── gold_dim_model
│       ├── gold_dim_date
│       |── gold_dim_dealer
│       |__ gold_dim_branch
|       |__ fact_table
├── architecture/
│   └── architecture diagram
│
└── README.md
```

## 🚀 Key Features

* End-to-end Azure data engineering pipeline
* Azure SQL as the source system
* Azure Data Factory orchestration
* Azure Data Lake Storage Gen2
* Medallion Architecture
* Bronze, Silver, and Gold layers
* Incremental data loading
* PySpark transformations
* Delta Lake
* Databricks Workflows
* Unity Catalog
* Databricks Metastore
* Access Connector with managed identity
* Data quality validation
* Git and GitHub version control

## 📚 Project Outcomes

This project provides hands-on experience in designing and implementing a complete cloud-based data engineering workflow using Azure services.

It demonstrates the integration of data ingestion, cloud storage, distributed data processing, incremental loading, orchestration, data governance, secure cloud storage access, data quality, and version control into a single end-to-end data engineering solution.
