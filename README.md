# Cloud ETL Pipeline with Azure Data Factory & Medallion Architecture

This project implements a scalable cloud ETL pipeline using Azure Data Factory (ADF) to ingest raw data from a SQL Server and the GitHub API into Azure Data Lake Storage Gen2, following the Medallion architecture (Bronze layer).

# Architecture & Design Choices

*   *Ingestion Tool:* Azure Data Factory (Serverless, orchestration)
*   *Source Systems:* 
       SQL Server: On-premises or Azure SQL DB (using ADF Integration Runtime)
       GitHub API: REST API connector in ADF
*   Storage Layer: Azure Data Lake Storage Gen2 (Scalable, cost-effective data lake)
*   Data Architecture: Medallion Architecture
       Bronze Layer: Raw landed data in ADLS Gen2, preserving the source's exact format. Data is partitioned by ingestion time for efficient auditing and reprocessing.

# Technical Implementation

 ## Data Factory Pipelines
The ADF pipelines are designed for incremental loads and fault tolerance.
   **pipeline_bronze_sql:** Copies data from SQL Server tables to ADLS Gen2 (incremental extraction).
*   **pipeline_bronze_github:** Makes a REST API call to GitHub, handles pagination, and lands the JSON response into the data lake.

### Key Techniques Demonstrated:
*   Parameterized pipelines and datasets in ADF.
*   Incremental data extraction strategy.
*   Handling REST API pagination.
*   Partitioning data on the data lake.
*   Using efficient file formats (Parquet/JSON) for storage.
