# blockBOX
Your one stop shop to deploy Blockchain ETL Data Infrastructure.

## Table of Contents
1. [Motivation](#Motivation)
2. [Project Structure](#Project-Structure)
3. [Usage](#Usage)
    - [Project Infrastructure](#Project-Infrastructure)
    - [Airflow Orchestration](#Airflow-Orchestration)
    - [Monitoring](#Monitoring)
    

## Motivation
Blockchain databases are rich in information but querying them can be very expensive. This is because the data in blockchain lives in a decentralized network of nodes that are constantly replicating records among themselves. This project will allow you to to deploy a robust infrastructure for blockchain ETL, creating an environment for data transfer and to preform analytics on the queried data. The data pipeline is orchestrated with Airflow allowing scheduling of multiple tasks that might have dependencies on one another. This project is leveraging AWS cloud infrastructure and Terraform for easy deployment. It is also using Prometheus and Grafana to monitor the data pipeline and infrastructure.

## Project Structure
There are three main components of this project:

1. Project Infrastructure
2. Airflow Orchestration
3. Monitoring

## Usage

### Project Infrastructure

The infrastructure needed for this project can be found at:
[terragrunt-icon-analytics](https://github.com/kaavya1698/terragrunt-icon-analytics) which is a fork from the original repo. A second S3 bucket was added to allow for the transfer of data from Amazon RDS to Amazon Redshift.  

Prerequisites:
* Terraform v0.12.29
* Terragrunt v0.23.40
* Ansible
  
Many of the infrastructure components are dependent on previous components. In order to deploy the infrastructure:  
  
``` git clone https://github.com/kaavya1698/terragrunt-icon-analytics```.   
  
Navigate to icon-analytics/aws. Here you will see the infrastructure components needed to be deployed. Deploy the infrastructure in the following order by running ```terragrunt apply``` after navigating the the respective folder:

1. network
2. rds
3. postgres
4. airflow
5. s3
6. s3-redshift

```redshift-db``` and ```superset``` can be deployed at anytime after if desired to use.

### Airflow Orchestration

The dags written for the ETL deployment can be found at [icon-etl-airflow](https://github.com/kaavya1698/icon-etl-airflow) which is a fork of the original repo.  
Please view [deployment instructions](https://github.com/insight-icon/icon-etl-airflow/blob/master/README.md) to see how to get started with deploying the dags.  
  
The ```load_rds_to_s3``` dag load schema ready data from RDS to a second s3 bucket. In order for this function to work please set manditory variables in the Airflow console:
Variable     | Suggested Default | Description 
------------ | ----------------- |------------
rds_s3_start_date | | first date to export from RDS to second S3 bucket
s3_redshift_bucket | icon-redshift-dump-dev | name of S3 bucket to hold RDS data

The ```load_rds_to_redshift``` dag loads data from S3 bucket holding RDS data to Redshift when desired. In order for this function to work please set manditory variables in the Airflow console:

*complete when finished*

Variable     | Suggested Default | Description 
------------ | ----------------- |------------

### Monitoring
