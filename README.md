# Cloud Data Engineering Pipeline for Real-Time Global Economic Indicator Analysis

## Overview

This project implements a **cloud-native ETL pipeline using AWS services** to ingest, process, transform, and visualize global economic indicators from the **World Bank API**.

The pipeline processes macroeconomic data across **200+ economies**, stores raw and processed datasets in Amazon S3, performs ETL operations using AWS Glue, and makes the processed data available for querying through Amazon Athena and visualization through Power BI.

The project covers the complete data engineering workflow from **API ingestion to data storage, transformation, modelling, querying, and visualization**.

---

## Architecture

```text
World Bank API
      |
      v
AWS Lambda
      |
      v
Amazon S3
Raw Data
      |
      v
AWS Glue
ETL / Transformation
      |
      v
Amazon S3
Processed Data
      |
      v
Amazon Athena
SQL Querying
      |
      v
Power BI
Interactive Dashboard
```

**Data Flow:**
`World Bank API → Lambda → S3 → Glue ETL → Processed Data → Athena → Power BI`

---

## Technologies Used

| Technology         | Purpose                            |
| ------------------ | ---------------------------------- |
| **Python**         | Data ingestion and processing      |
| **World Bank API** | Source of global economic data     |
| **AWS Lambda**     | Serverless data ingestion          |
| **Amazon S3**      | Raw and processed data storage     |
| **AWS Glue**       | ETL processing and transformation  |
| **Amazon Athena**  | SQL-based analytical querying      |
| **IAM**            | AWS access control and permissions |
| **SQL**            | Data modelling and analysis        |
| **Power BI**       | Data visualization and dashboards  |

---

## Key Features

* Automated ingestion of economic indicators from the **World Bank API**
* Processing of data across **200+ countries and economies**
* Cloud-based storage using **Amazon S3**
* Serverless ingestion using **AWS Lambda**
* ETL processing using **AWS Glue**
* SQL-based querying using **Amazon Athena**
* **Star Schema** data modelling for analytical workloads
* Interactive **Power BI dashboards**
* IAM-based access control between AWS services
* End-to-end cloud data engineering pipeline

---

## Data Pipeline

### 1. Data Ingestion

The **World Bank API** is used as the primary source for global macroeconomic indicators.

AWS Lambda retrieves the required data programmatically and initiates the data pipeline without requiring dedicated servers.

### 2. Raw Data Storage

The data retrieved from the API is stored in **Amazon S3** as the raw data layer.

Keeping raw and processed data separately allows the original data to be preserved while transformations are performed downstream.

### 3. ETL and Transformation

**AWS Glue** processes the raw datasets and performs the required cleaning, transformation, and enrichment operations.

The resulting datasets are stored back in Amazon S3 in a processed format suitable for analytical workloads.

### 4. Data Modelling

The processed data is structured using a **Star Schema** to simplify analytical queries and improve the organisation of economic metrics.

The model separates measurable economic data from descriptive dimensions such as countries, indicators, and time periods.

### 5. Analytical Querying

**Amazon Athena** is used to query the processed data directly using SQL.

This provides a serverless analytical layer without requiring a dedicated database server.

### 6. Visualization

The processed data is connected to **Power BI** to create interactive dashboards for comparing economic indicators across countries and time periods.

---

## Economic Indicators

The pipeline works with macroeconomic indicators including:

* **GDP**
* **Inflation**
* **Trade**
* Country-level economic metrics
* Economic trends over time

The data can be analysed across different countries, regions, indicators, and years.

---

## Data Model

The project uses a **Star Schema** for analytical data modelling.

```text
                 Country Dimension
                        |
                        |
                        v
Time Dimension ---> Economic Fact <--- Indicator Dimension
                        |
                        |
                        v
                 Economic Metrics
```

The model allows economic data to be analysed across:

* Countries
* Regions
* Economic indicators
* Years
* Macroeconomic metrics

---

## Power BI Dashboard

The Power BI dashboard provides interactive visualizations for exploring the processed economic data.

The dashboard enables:

* GDP comparison across countries
* Inflation trend analysis
* Trade comparison
* Economic trend analysis over time
* Country and region-level filtering
* Indicator and year-based filtering
* Comparative analysis of economic performance

### Dashboard Preview

Add screenshots of the Power BI dashboard here.

```text
screenshots/
├── dashboard-overview.png
├── country-comparison.png
└── economic-trends.png
```

---

## AWS Architecture

```text
                  World Bank API
                        |
                        v
                  AWS Lambda
                 Data Ingestion
                        |
                        v
                   Amazon S3
                  Raw Data Layer
                        |
                        v
                   AWS Glue
               ETL / Transformation
                        |
                        v
                   Amazon S3
              Processed Data Layer
                        |
                        v
                 Amazon Athena
                SQL Analytics
                        |
                        v
                    Power BI
              Interactive Dashboard
```

---

## Security

**AWS IAM roles and permissions** are used to control access between the different AWS services involved in the pipeline.

Access is configured based on the requirements of each service and pipeline stage.

---

## Project Structure

```text
Data-Engineering-Pipeline-for-Real-Time-Global-Economic-Indicator-Analysis/
│
├── README.md
│
├── lambda/
│   └── ingestion.py
│
├── glue/
│   └── etl_pipeline.py
│
├── sql/
│   ├── schema.sql
│   └── analytical_queries.sql
│
├── data/
│   └── sample_data.csv
│
├── powerbi/
│   └── economic-indicators-dashboard.pbix
│
├── screenshots/
│   ├── dashboard-overview.png
│   └── country-analysis.png
│
└── architecture/
    └── architecture-diagram.png
```

---

## Setup

### Prerequisites

* AWS Account
* Python 3.x
* AWS CLI
* Power BI Desktop
* World Bank API access

### Steps

1. Configure the required **AWS IAM roles and permissions**.
2. Create S3 buckets for raw and processed data.
3. Deploy the Lambda ingestion function.
4. Configure the World Bank API data ingestion.
5. Configure AWS Glue for ETL processing.
6. Store transformed datasets in the processed S3 layer.
7. Create Athena tables and run analytical SQL queries.
8. Connect the processed data to Power BI.
9. Open the `.pbix` file in Power BI Desktop to explore the dashboard.

---

## Future Improvements

* Add **AWS Step Functions** for workflow orchestration
* Implement **CloudWatch monitoring and logging**
* Add automated data quality checks
* Implement incremental data loading
* Add pipeline failure notifications
* Expand the number of World Bank indicators
* Automate Power BI dataset refreshes
* Add additional analytical dashboards
