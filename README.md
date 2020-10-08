# blockBOX
Your one stop shop to deploy Blockchain ETL Data Infrastructure.

## Motivation
Blockchain databases are rich in information but querying them can be very expensive. This is because the data in blockchain lives in a decentralized network of nodes that are constantly replicating records among themselves. This project will allow you to to deploy a robust infrastructure for blockchain ETL, creating an environment for data transfer and to preform analytics on the queried data. The data pipeline is orchestrated with Airflow allowing scheduling of multiple tasks that might have dependencies on one another. This project is also leveraging AWS cloud infrastructure and Terraform for easy deployment.

## Project Structure
There are three main components of this project:

1. Project Infrastructure
2. Airflow Orchestration
3. Monitoring

## Usage

### Project Infrastructure

The infrastructure needed for this project can be found at:
[terragrunt-icon-analytics](https://github.com/kaavya1698/terragrunt-icon-analytics) which is a fork from the original repo. A second S3 bucket was added to allow for the transfer of data from Amazon RDS to Amazon Redshift.  
Many deployments of infrastructure is dependent on previous components. In order to 
