 I’m happy to announce that I have successfully completed another Data Engineering project using Azure Data Factory (ADF) and Azure Databricks.

📌 Project Overview
 Our NGTV router team performed weekly health checks, and the router generated raw .txt log files.
 Manually identifying port-level errors from these logs was time-consuming and prone to human error.

💡 With this end-to-end data engineering solution, we achieved:
 ✔ 50% reduction in manual effort
 ✔ 30% faster reporting for Monday client calls

🔷 Modern Data Lakehouse Architecture Followed
Landing → Bronze → Silver → Gold

🔷 Azure Data Factory (ADF)

Implemented data ingestion from on-premise servers to ADLS (Bronze layer) using Self-Hosted Integration Runtime (SSIS)
Configured linked services and managed datasets
Designed and optimized the Self-Hosted IR for seamless connectivity

🔷 Azure Data Lake Storage Gen2

The NGTV router produced 3 different log files for 2 ports, including:
Error_disable_logs_1_49.log
Error_disable_logs_1_50.log
Erroring_links_logs_1_49.log
Erroring_links_logs_1_50.log
Metric_logs_script.log
All files were stored in the Landing layer before processing.

🔷 Azure Databricks

Bronze Layer

Authenticated Databricks with ADLS
Read the raw log files from the Landing layer
Applied regexp_extract() to extract key parameters
Converted the parsed data into structured DataFrames
Saved the output to the Bronze layer as Delta tables

Silver Layer

Loaded Bronze data into Silver notebooks
Applied deduplication, schema enforcement, and cleanup transformations
Wrote transformed data to ADLS Silver layer in Delta format

Gold Layer

Read curated data from Silver
Applied business rules for final insights
Loaded the final dataset into Azure Synapse Analytics for reporting and analytics

🎯 Impact
 This project significantly improved operational efficiency and automated a previously manual, error-prone process. It also strengthened our data pipeline for real-time monitoring and reporting.

## Architecture

Following is the architecture of the project.

<p align='center'>
  <img src='https://github.com/waqarg2001/earthquake-etl-pipeline/blob/main/Resources/architecture.png' height=385 width=1100>
</p> 

 
