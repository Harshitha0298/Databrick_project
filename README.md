# Databricks Lakehouse Project

## Overview
This project implements a modern data lakehouse architecture on Databricks,
following the medallion architecture pattern to process and transform data from multiple source systems (CRM and ERP)
into analytics-ready datasets.
## Architecture

The project follows a three-tier medallion architecture:

### 🥉 Bronze Layer (`my_lakehouse/Bronze/`)
Raw data ingestion layer that captures data from source systems in its original format. This layer provides:
- Historical data archival
- Data lineage tracking
- Ability to reprocess data from source

### 🥈 Silver Layer (`my_lakehouse/Silver/`)
Cleaned and validated data layer that applies business rules and data quality checks. Key transformations include:
- **CRM Data Processing**
  - Customer information cleansing and standardization
  - Product catalog enrichment
  - Sales transaction validation
- **ERP Data Integration**
  - Customer master data (az12)
  - Location reference data (a101)
  - Product category hierarchies (px_cat_g1v2)

### 🥇 Gold Layer (`my_lakehouse/Gold/`)
Business-level aggregated datasets optimized for analytics and reporting:
- **Dimension Tables**
  - `dim_customers`: Customer master dimension
  - `dim_products`: Product master dimension
- **Fact Tables**
  - `fact_sales`: Sales transactions with business metrics

## Technologies Used
- **Databricks**: Unified data analytics platform
- **Delta Lake**: ACID-compliant storage layer
- **Apache Spark**: Distributed data processing
- **Python**: Primary programming language for transformations
