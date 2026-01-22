# Spotify-End-To-End-Azure-Data-Engineering-Project
In this project I created a Azure SQL database to store the spotify data and act as a source and migrated the data using Azure Data Factory to the Data Lake that is ADLS GEN 2. Then used Databricks to transform the data to be used for analysis.

### Tech stack
 - ADLS Gen 2
 - Azure Data Factory
 - Azure SQL Database
 - Spark
 - CI/CD
 - Github
 - Azure Databricks
 - Unity catalog
   (project architecture pic)

### Concepts tackled
1. Incremental processing
2. stream processing
3. Git CI/CD standards
4. Dynamic code
5. Metadata driven code
6. Star schema

## Resource group creation
I created a resource group together with the resources in it

<img width="1364" height="768" alt="Screenshot (96)" src="https://github.com/user-attachments/assets/42176ae9-3a0e-44ed-b418-ee33944ace3b" />

Also created containers for the medallion architecture in the storage account that is ADLS GEN 2 for gold, silver and bronze

<img width="1368" height="768" alt="Screenshot (88)" src="https://github.com/user-attachments/assets/ca1f561b-6c15-42c5-904f-dffe215706a3" />

## Azure Data Factory + Github
I integrated Git with ADF to help in CI/CD.
I created a repository in my github account(private)
In ADF > go to manage > source control > git
After these created a branch from the main to help us in development and later merge.

<img width="1368" height="768" alt="Screenshot (87)" src="https://github.com/user-attachments/assets/0b8d5b7d-b859-416a-9e45-5e2749d02ded" />

## Azure SQL 
Copied data from my github and run the query in the SQL DB to create the spotify tables in the database.

<img width="1377" height="768" alt="Screenshot (89)" src="https://github.com/user-attachments/assets/118a89b3-bb30-4089-8aba-06e2c22fb447" />

## Azure Data Factory
Created linked connection with Azure SQL DB and ADLS Gen 2.
- Authentication type in linked service is Account key because they(ADLS GEN 2 and ADF) are in the same resource group but when in different groups from ADF use system managed identity.
- Used copy activity to migrate the data from the SQL DB to the data lake. In the source; because I wanted to migrate the whole tables, no specific table was selected.
- Also created a json file to store a key value pair with time much earlier like 'col':1900-01-10'. This was to help in incremental data loading. Also an empty json file was created to be updated anytime the data was loaded.
- Both these files were stored in the bronze layer.


















   
