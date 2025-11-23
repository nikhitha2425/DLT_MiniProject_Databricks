 **Databricks DLT Taxi Pipeline — Mini Assignment**
This repository contains the implementation of a Delta Live Tables (DLT) pipeline for the Taxi Trip Analytics mini-project.
The entire Bronze → Silver → Gold flow is implemented using a single SQL DLT notebook, with a separate validation script and results folder.
This project demonstrates ingestion, data cleaning, quality expectations, weekly aggregations, and creation of a materialized gold table.
📁**Repository Structure**

dlt\_taxi\_assignment/
│
├── dlt\_pipeline/
│   ├── dlt\_pipeline.sql              # Single SQL file with all DLT tables (Bronze, Silver, Gold)
│   └── pipeline\_overview.png         # DLT lineage / pipeline graph
│
├── validation\_queries/
│   └── validation\_queries.sql        # Queries to validate all pipeline outputs
├── results/
│   ├── bronze\_preview.png
│   ├── silver\_clean\_preview.png
│   ├── silver\_weekly\_agg\_preview.png
│   ├── gold\_top3\_fares\_preview.png
│   └── validation\_checks.png
│
└── README.md

 **Pipeline Overview**

The pipeline is written entirely in one SQL notebook (dlt\_pipeline.sql), containing four DLT tables:

**1. Bronze Layer**

Ingests raw taxi data
Table: bronze\_taxi
Enforces data quality using an expectation:
EXPECT trip\_distance > 0 ON VIOLATION DROP;

**2. Silver Layer (Clean Table)**

Creates: silver\_taxi\_clean
Removes invalid data
Standardizes schema

**3. Silver Layer (Weekly Aggregation)**

Creates: silver\_weekly\_agg
Produces: weekly total trips, avg fare, sum distance
Groups by year \& week

**4. Gold Layer**

Creates: gold\_top3\_fares (materialized view)
Displays top-3 rides with highest fare
Includes passenger and distance information

 **🧪Validation Notebook**

The validation\_queries.sql file contains SQL commands that verify:
Bronze table ingestion
Quality checks applied (trip\_distance > 0)
Cleaned Silver table results
Weekly aggregates correctness
Top 3 fare rides
Schema validation using DESCRIBE
Join validation between layers
These queries were executed against the same catalog/schema configured in the DLT pipeline.

 **🖼️ Results**

The results folder includes:
Bronze table preview
Cleaned Silver table output
Weekly aggregate sample
Final Gold table output
Validation outputs
Each screenshot confirms correctness of the pipeline execution.

▶️ How to Run the Pipeline
Go to Workflows → Delta Live Tables
Select the pipeline for this project
Attach the SQL notebook: dlt\_pipeline.sql
Configure target catalog/schema
Click Run Pipeline
Once green, open and run validation\_queries.sql

###### **📦 Submission Contents**
✔ DLT SQL pipeline file
✔ Validation queries file
✔ Pipeline lineage screenshot
✔ Complete results from validation
✔ README documentation

