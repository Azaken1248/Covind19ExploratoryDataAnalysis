# Covid-19 Data Analytics Pipeline

## Project Overview
This project implements an end-to-end data analytics pipeline using PySpark to analyze global COVID-19 trends. It ingests, cleans, and transforms multiple real-world datasets containing daily confirmed cases, deaths, recoveries, active cases, population details, and geographic information. The final objective is a scalable workflow that converts raw pandemic data into meaningful, exportable insights for reporting and visualization.

## Business Problem Statement
During the COVID-19 pandemic, reliable insights were required to determine which countries were most affected, when global cases peaked, and how population size impacted infection rates. Because this data is spread across multiple datasets with varying formats and granularity, a robust data pipeline is necessary to clean, join, and analyze this information efficiently. This project simulates how an analytics team processes pandemic data for decision-making.

## Tech Stack
* **Data Processing:** PySpark (DataFrames, Spark SQL, Window Functions)
* **Data Manipulation:** Pandas
* **Visualization:** Matplotlib
* **Output Storage:** CSV

## Datasets
The project utilizes the following datasets (Source: [Kaggle - Corona Virus Report](https://www.kaggle.com/datasets/imdevskp/corona-virus-report)):
* `full_grouped.csv`: Daily country-level COVID trends
* `covid_19_clean_complete.csv`: Location-level historical data
* `country_wise_latest.csv`: Latest country statistics
* `day_wise.csv`: Global day-wise trends
* `usa_county_wise.csv`: US county-level data
* `worldometer_data.csv`: Population and global COVID statistics

## Pipeline Architecture
The pipeline is divided into 10 core modules:

1. **Data Loading & Schema Handling:** Ingesting multiple CSV files, inferring schemas, and validating row counts.
2. **Data Cleaning:** Handling null values and standardizing inconsistent country names across disparate datasets using regular expressions.
3. **Aggregations:** Generating KPIs such as top countries by total cases, death rates, and WHO region summaries.
4. **Time-Series Analysis:** Tracking daily global case trends, calculating daily death growth percentages using lag functions, and extracting monthly growth metrics.
5. **Window Functions:** Ranking the most affected countries per region and computing country-wise daily case increases.
6. **Join Operations:** Comparing datasets for discrepancies and calculating population-adjusted infection rates.
7. **Geographic Analysis:** Analyzing state-wise reporting distributions and mapping latitude/longitude case clusters.
8. **Advanced Analytics:** Evaluating recovery rates, identifying active case burdens, and pinpointing global pandemic peaks.
9. **Feature Engineering:** Categorizing countries into severity levels based on total confirmed cases.
10. **Final Pipeline Export:** An automated extraction and transformation step that exports aggregated metrics as clean CSV files for external visualization dashboards.

## Setup and Execution

### Prerequisites
Ensure Python is installed along with the following packages:
```bash
pip install pyspark numpy pandas matplotlib
```

### Directory Structure
Ensure the raw datasets are placed in a `dataset` folder in the root directory:
```text
project_root/
│
├── dataset/
│   ├── full_grouped.csv
│   ├── covid_19_clean_complete.csv
│   ├── country_wise_latest.csv
│   ├── day_wise.csv
│   ├── usa_county_wise.csv
│   └── worldometer_data.csv
│
└── covid_analysis.ipynb
```

### Running the Pipeline
Execute the provided Jupyter Notebook (`covid_analysis.ipynb`) sequentially. 

### Outputs
Upon successful execution of the final module, the pipeline generates a `pipeline_output` directory containing the following analytical tables in CSV format:
* `top_10_countries.csv`
* `region_summary.csv`
* `mortality_report.csv`
* `daily_trends.csv`