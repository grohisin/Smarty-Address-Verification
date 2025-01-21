# Smarty-Address-Verification

# Overview
The Smarty Address Verification Project is a comprehensive data pipeline designed to validate and standardize address data using the Smarty API. This project integrates Snowflake, Azure Data Factory (ADF), and Smarty to ensure address accuracy, minimize errors, and improve data quality for downstream applications.

# Features
Automated Address Validation: Validates and standardizes addresses using the Smarty API.
Batch Processing: Processes large datasets in batches for efficient validation.
Azure Data Factory Integration: Uses ADF pipelines for seamless data movement and API interactions.
Dynamic Data Updates: Handles both initial and incremental address validation.
Error Handling: Ensures robust handling of missing or invalid data fields.
Architecture
# The project workflow involves:

Data Extraction: Address data is pulled from Snowflake.
Data Transformation: Tabular data is converted into JSON format.
API Integration: JSON data is sent to the Smarty API via ADF pipelines for validation.
Validated Data Storage: Validated addresses are stored back in Snowflake and/or Azure Blob Storage.
Comparison & Reporting: Pre-validation and post-validation tables are compared to calculate the percentage of corrected addresses.
# Tools & Technologies
Snowflake: For data storage and transformation.
Azure Data Factory (ADF): To create pipelines for data movement and API calls.
Smarty API: For address verification and standardization.
Azure Blob Storage: To temporarily store JSON files during the validation process.
Key Components
Snowflake Stored Procedures:

Handles JSON parsing and data insertion into staging and validation tables.
Ensures duplicate addresses are not reprocessed.
ADF Pipelines:

Includes activities like Copy Data, Set Variable, and Web Activity for API interactions.
ForEach loop processes address batches efficiently.
Validation Logic:

Unverified records are sent for validation.
Updates fields like IS_VALIDATED and LAST_UPDATED_DATE post-validation.
Comparison View:

Compares pre-validation and post-validation data.
Calculates mismatched fields and generates a report.
How to Use
Setup:

Configure Snowflake database, tables, and stored procedures.
Set up Azure Data Factory pipelines and linked services (Snowflake, Blob Storage, Smarty API).
Run Pipeline:

Execute the ADF pipeline for address validation.
Monitor pipeline activities for successful API calls and data updates.
Generate Report:

Use the comparison view or stored procedure to calculate validation improvements.
Export the final report as an Excel file or store it in Blob Storage.
