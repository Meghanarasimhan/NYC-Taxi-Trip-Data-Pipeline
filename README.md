# CSC 555 / DSC 333 Final Project - Spring 2025

## Project Title: Scalable Taxi Fare Prediction Using Spark and AWS Analytics Pipeline

### Author: Meghashree BL 
### Submission Date: June 10, 2025  

---

## 📌 Project Overview

This project implements a full end-to-end big data pipeline using AWS and Apache Spark. The pipeline handles data ingestion, transformation, storage, analysis, machine learning modeling, and reporting. The aim is to explore the power of distributed computing and cloud-native tools to process large-scale datasets efficiently.

---

## Dataset

- **Source**: ```https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page```
- **Size**: >1M rows
- **Description**: I selected this dataset because it offers real-world, large-scale data with over 1 million rows, making it ideal for demonstrating the capabilities of distributed computing using Spark. The dataset contains diverse variables (e.g., timestamps, locations, numeric amounts) that allow for meaningful transformations, feature engineering, and machine learning.

Additionally, the dataset aligns well with cloud-based analytics tools like Athena and S3 due to its structured format. It also enables practical insights—such as trip patterns, fare predictions, or customer behavior—which makes the machine learning component more relevant and interpretable. The scale and variety of the data provided the right balance of complexity and clarity for building an end-to-end pipeline.

---

##  Architecture

- **Data Staging**: Raw data stored in Amazon S3
- **Data Processing**: Apache Spark (PySpark) on EMR for data cleaning and transformation
- **Data Querying**: Transformed data stored in Athena tables
- **Machine Learning**: Spark MLlib used for building and evaluating a [classification/regression/clustering] model
- **Visualization**: Charts and summary metrics presented using [Matplotlib/Seaborn/other tools]
- **Diagrams**: Included two diagrams:
  - Core Architecture (Data Flow)
  - Full Pipeline Architecture (with orchestration tools)

---

##  Methodology

1. **Data Cleaning & Transformation**
   - Handled missing values, formatted timestamps, removed outliers
   - Applied feature engineering and aggregation

2. **Querying with Athena**
   - Created external tables for transformed data
   - Used SQL to explore data and prepare features for ML

3. **Modeling**
   - Applied [ML model name] using Spark MLlib
   - Evaluation using metrics like [Accuracy, RMSE, F1-score, etc.]

---

##  Results & Insights


##  Project Structure
```
├── data/ # Dataset files 
├── notebooks/ # Jupyter notebooks or Python scripts
├── report/ # Final report in .pdf or .docx format
├── README.md # This file
```
## Requirements

- Apache Spark
- AWS S3
- AWS Athena
- PySpark
- Spark MLlib

## Challenges Faced

- AWS EMR Configuration and Resource Constraints
Setting up EMR clusters within the institution’s lab environment was limiting, as only one cluster was allowed per user. This constraint required careful planning of pipeline steps to avoid repeated cluster setups, especially during Spark MLlib training and transformation phases.
- S3 and Athena Integration Issues
Mapping transformed data from EMR back to S3 and querying it in Athena involved schema mismatches and partitioning problems. Understanding proper Parquet formatting and table definitions in Athena was critical to resolve these.
- Data Volume Handling with Spark
The dataset, being over 1 million rows, initially led to slow transformations and out-of-memory errors. This was addressed by tuning Spark configurations (spark.sql.shuffle.partitions, using .persist(), etc.) and filtering unnecessary columns early in the pipeline.
- Model Performance Tuning in Spark MLlib
Choosing the right algorithm and tuning hyperparameters was difficult within Spark MLlib’s limited API compared to scikit-learn. Repeatedly evaluating models using TrainValidationSplit and CrossValidator under Spark's distributed setup required trial-and-error with long run times.
- Creating Effective Architecture Diagrams
Translating the real pipeline into clear, informative architecture diagrams that meet both functional (core) and full (orchestrated) views required iterations. Ensuring AWS icons were used correctly and that data flow was intuitive took effort with tools like diagrams.net.
- Cost Awareness and Lab Timeout
Since the AWS student lab environment shuts down automatically or may suspend accounts for misuse, keeping the session alive and ensuring the process completes within that time was a recurring operational challenge.

