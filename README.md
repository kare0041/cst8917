
# Azure Functions with Storage Queue and Azure SQL Output Bindings

This project demonstrates the use of Azure Functions with Storage Queue and Azure SQL output bindings using Python and Visual Studio Code.

## Overview

This project includes:
1. A function that adds messages to an Azure Storage Queue.
2. A function that inserts records into an Azure SQL Database.

Both functions were created and tested locally before being deployed to Azure.

## Prerequisites

- Python 3.10+
- Azure Functions Core Tools
- Visual Studio Code with Azure Functions and Python extensions
- Azure CLI
- An active Azure subscription

## Setup Instructions

### Storage Queue Function

1. Create a Storage Account on Azure.
2. Set up a Queue named `outqueue`.
3. Update `local.settings.json` with your storage connection string:
   ```json
   {
     "Values": {
       "AzureWebJobsStorage": "<Your_Storage_Connection_String>"
     }
   }
   ```
4. Run the function locally or deploy to Azure.

### Azure SQL Function

1. Create an Azure SQL Database and SQL Server.
2. Create a table using the following schema:
   ```sql
   CREATE TABLE dbo.ToDo (
    [Id] UNIQUEIDENTIFIER PRIMARY KEY,
    [order] INT NULL,
    [title] NVARCHAR(200) NOT NULL,
    [url] NVARCHAR(200) NOT NULL,
    [completed] BIT NOT NULL
   );
   ```

3. Update `local.settings.json` with your SQL connection string:
   ```json
   {
     "Values": {
       "SqlConnectionString": "<Your_SQL_Connection_String>"
     }
   }
   ```

## Running Locally

1. Navigate to the project root through VS code:
   -
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Start the function app locally:
   ```bash
   func start
   ```

## Testing

- Trigger the Storage Queue function via an HTTP request 
- Verify that a message is added to the storage queue.
- Trigger the Azure SQL function similarly and confirm a new record is inserted into the database.

## Important

The function_app.py code has been updated from Storage Queue output binding to Azure SQL Database output binding. In order to access the function code that performs output binding to Azure Storage queue, please refer to the first commit named "adding an HTTP trigger function app files with Storage Queue output binding"

## Youtube Video

https://www.youtube.com/watch?v=prJ4XeSSjrM
