![photo](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/blob/operations/photos/ETL_1.png)

# INFO OF THIS PROJECT

The aim of this project is to explore the possibilities of ETL pipeline.

The data came from [NYC taxi trip](https://github.com/DataTalksClub/nyc-tlc-data/releases).
The technologies used are :
- Terraform
- Cloud GCP
- Kestra
- Docker
- Bigquery
- DBT

In this project, i used the vm instance of GCP cloud to simulate the pipeline ETL. With the help of terraform, i configured the VM instance, the dataset and google storage([file](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/blob/operations/terraform)). 

In the VM, i deployed Kestra with docker to do the workflows of extraction data and load them into bigquery([file](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/tree/operations/installations)).

After that, we could use DBT([file](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/tree/operations/dbt)) to transform data and get the purified data that we want. Then, we could use the visual tools like lookerstudio to display them. 