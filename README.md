# Analyze & get benefit from iPhone health data for daily life style and better health
The actual purpose of this repo is to fulfil an acadamic task. 
Below are that high level tasks being done here, i.e:

Parsing apple native health data, performing data processing, analysis, gaps, feature engineering, forecasting and finally improving health statistics and life style 

## Background


# applehealthdata
Extract Data from Apple Health App's XML Export



  * v1.0: http://www.tdda.info/in-defence-of-xml-exporting-and-analysing-apple-health-data

-----------------------------------------



# Analyze your Apple Health data

## Setup

* export your Apple Health via iPhone or iPad app
* extract the zip file to "apple_health_export/export.xml"

## Features

* converts Apple Health export XML data to CSV and Excel format (based on code from [here](https://towardsdatascience.com/analyse-your-health-with-python-and-apple-health-11c12894aae2))
* provides a starting point for your own data analytics
* some simple statistics on the data sources

*
*
*   --------------------------



## Description
This project involves an **ETL** (Extract, Transform, Load) process to analyze sleep data exported from Apple Health to iCloud in XML format. 

The data is then processed and transformed using **AWS** services, queried through Amazon Athena, and visualized using a **Streamlit** dashboard.

## Project Overview

+ Export Health Data from iPhone to iCloud in **XML** format.
+ Load the data into an **Amazon S3** bucket.
+ Set up an **AWS Lambda** function to process the **XML** data into a **CSV** file and store it in the S3 bucket.
+ Set up another AWS Lambda function to further transform the data using **DuckDB** and **Pandas**. 
+ The data is then redirected to a Lambda Function, which saves the data as **Parquet** files in an S3 Bucket, partitioned by year. 
+ Set up **AWS Glue** Crawlers to crawl the Parquet files stored in the S3 bucket and store the data in the **AWS Glue Data Catalog** table, partitioned by year.
+ Finally, A **Streamlit** dashboard is set up on an **Amazon EC2** instance to display sleep analytics over the years.

## Tech Stack
+ AWS Services : S3, Lambda, Glue, Athena, SNS, EC2
+ Python Libraries : boto3, lxml, s3fs, awswrangler, pandas, duckdb, streamlit
+ Data Processing : DuckDB
+ Analytics and Visualization : Athena, Streamlit

## Prerequisites
The above tech stack and an iCloud Account with Apple Health Data synced regularly from Apple Watch are required. If you don't have an account, you can download my [Health Dataset](https://github.com/vinamrgrover/ETL-Apple-Health/files/11360011/apple_health_export.zip)

## Workflow
1. The Data is Exported from Apple Health to iCloud (Download [here](https://github.com/vinamrgrover/ETL-Apple-Health/files/11360011/apple_health_export.zip))

2. The Data is then transfered locally to an S3 Bucket using AWS CLI. 

<img width="1111" alt="Screenshot 2023-04-30 at 2 11 27 AM" src="https://user-images.githubusercontent.com/100070155/235323410-9d9fa9ec-050d-45a6-9cc4-4f512bd83bce.png">

3. An AWS Lambda Function (*Process_XML*) is set up to Transform the Raw Data (XML) and save it as CSV Files in an S3 Bucket. If the Function's execution fails, its response is redirected to an AWS SNS Topic. 

<img width="857" alt="Screenshot 2023-04-30 at 2 14 19 AM" src="https://user-images.githubusercontent.com/100070155/235323511-6e28d998-7918-42fb-b064-e3fea64d41bd.png">

Processed CSV Files: 




-----------------



# Apple Health XML Export Parser
Parse apple health XML export file for useful summaries. To export the data, in your iOS Health app, tap on your avatar and choose `Export All Health Data`. 

![export xml](pic/export.png)

Extract the `.zip` file and call the script, passing the year and the `export.xml` as a parameter:

```
python3 ./parse-apple-health-sax.py 2023 ~/Downloads/apple_health_export/export.xml
```


-----------------







