# Business Request
In this project, a company has identified a gap in understanding its customer demographics, specifically, the gender distribution within the customer base and how it might influence product purchases.

A significant amount of customer data is stored in an on-premise SQL database, and key shareholders have requested a comprehensive dashboard.

This dashboard should provide insights into sales by gender and product category, showing total products sold, total sales revenue and a clear gender split among customers. Additionally, they need the ability to filter this data by products category and gender, with a user-friendly interface for date-based queries.

# Solution
Build a pipeline to extract the data from the SQL on-premise data
Loads the data into Azure
Performs the necessary transformations that make the data more query-friendly
Pipeline should be scheduled to run automatically every day.

### Project Overview:
![Project Architecture](https://github.com/user-attachments/assets/b955ce86-8694-4704-98e3-4ae73fa48bc2)

 In this project, data is taken from the on-premises SQL database and uploading the data to the Azure Data Factory. The data is ingested into a Azure Data Lake, here the data undergoes three levels of transformations: 
 - Bronze: Unstructured Data; no transformations
 - Silver: Identifying the Data/ Time columns
 - Gold: Changing column names, making the data more readable.

The transformed data is then **Loaded** into Azure Synapse Analytics, here the data is in a structured, cleaned format which can we can use to query the data. 

### Sexurity & Governance 

AAD and Key Vaults are used in conjunction to allow access to the SQL database that connects to the Data Factory. Instead of hard-coding the user name and password we store the information in **Key Vaults**.  ****To assign the Data Factory to SQL Database, we use **Microsoft Intra ID** (formerly known as Azure Active Directory). This is done by assigning a managed identity to the Data Factory and then giving it Key Vault access, so that the Data Factory can access the username and password to access the SQL database.


   










 ### **Definition Of Terms**

 - Data Factory: A Data Factory is a cloud-based service for automating a data pipeline, such as movement or transformation of data. it is different to a standard cloud based database where data is only stored and managed.
 - Data Lake: A Data Lake is a method of storing large unstrucutred data in its native format. 
