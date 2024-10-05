## City Vehicle Data Pipeline

The City Vehicle Data Pipeline is designed to process and migrate JSON data from IoT devices (such as vehicle telemetry data) stored in an AWS S3 bucket to an Azure SQL Database. This data pipeline ensures smooth data ingestion, validation, transformation, and loading into the Azure environment for further analysis and reporting.

This repository contains the architecture and detailed explanation of the pipeline implementation.

### Architecture
![diagram](https://github.com/aadhil96/Azure_City_Vehicle_Data_Pipeline/blob/e00e71e3151aab8208c667949b3040311b3b6710/Azure_Data_Eng.jpg)


## Key Components

### 1. AWS S3 Bucket
- IoT devices send daily **JSON data** (vehicle data) to the **AWS S3 bucket**.

### 2. Azure Data Factory (ADF)
- **ADF** orchestrates the entire data flow from AWS S3 to Azure SQL DB.
- **ADF** extracts JSON data from **S3** and processes it through different stages:
  - Data ingestion from S3.
  - Validation, transformation, and loading processes.

### 3. Azure Function
- Performs **data validation** by applying rules to check the integrity and structure of incoming JSON data.
- **Invalid data** is routed to the **Rejected Folder**, while **valid data** proceeds to the **Staging Folder** for further processing.

### 4. Landing Folder (Blob Storage)
- Temporary storage for incoming JSON files before they are processed by the **Azure Function**.

### 5. Rejected Folder (Blob Storage)
- **Invalid or corrupted JSON data** is stored here for further inspection and manual review.

### 6. Staging Folder (Blob Storage)
- Validated JSON data is temporarily stored in the **Staging Folder** before being loaded into the SQL database.

### 7. Azure SQL Database
- The final destination for **processed and validated JSON data**.
- **ADF** loads the validated data into this **Azure SQL Database** for structured storage and analysis.
