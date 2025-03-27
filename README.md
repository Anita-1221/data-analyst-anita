# project 1
Data Wrangling for Academic Misconduct Record Ingestion at UCW

Project Title: Data Wrangling for Cloud-Based Ingestion of Academic Integrity Records at UCW

Objective: The primary goal of this project is to perform structured data wrangling and cloud-based ingestion for academic misconduct records at University Canada West (UCW). By organizing, transforming, and uploading data to AWS S3, the project aims to create a secure, traceable, and analysis-ready dataset.

Background: UCW collects academic misconduct reports that require centralized, compliant storage and integration with backend systems. This project implements a repeatable ingestion process using AWS CLI and PowerShell for uploading structured CSV files to Amazon S3 with folder logic based on timestamped hierarchy.

Dataset:

RecordForm-List.csv: CSV file containing academic misconduct records including student ID, case ID, and sanction form details.
Entity relationships: StudentList, CaseList, and AcademicIntegrityReportFormList.
Methodology:

Data Collection:
Academic misconduct data is collected and formatted into structured CSV files.
![Screenshot 2025-03-27 121136](https://github.com/user-attachments/assets/902f12ca-8189-4dca-a851-4fc3a7536f56)
Files are reviewed for formatting consistency and correct field mapping.

Data Assessment:
Verified the integrity of field types, presence of required values, and filename standardization.
Reviewed alignment with database schema.
Data Cleaning:
Ensured no missing or duplicate values for key fields (StudentID, CaseID).
Standardized column headers and value formats.
Data Transformation:
Constructed a dynamic S3 folder structure by year, quarter, month, and day using PowerShell.
![Screenshot 2025-03-27 113000](https://github.com/user-attachments/assets/8a1a15dd-e6ac-407b-a3c2-4dbf6423f5b7)
Example S3 Key: /Academic misconduct/sanction-List/year=2025/quarter=1/month=1/day=20/server=AGVS-anita/RecordForm-List

Upload command: Write-S3Object -Bucket academics-raw-anita -File "C:\Users\Administrator\Documents\sanction-List.csv" -Key "/Academic misconduct/sanction-List/year=2025/quarter=1/month=1/day=20/server=AGVS-anita/sanction-List"

Data Consolidation:
Uploaded files are linked to backend architecture on EC2 with a relational schema:
StudentList (StudentID, StudentName)
CaseList (CaseID, CaseDescription)
AcademicIntegrityReportFormList (CaseID, StudentID)
Documentation and Validation:
Infrastructure architecture created in draw.io.
Upload process and S3 confirmation documented through screenshots.
Tools and Technologies:

PowerShell and AWS CLI for data upload
Amazon S3 and EC2 for cloud infrastructure
draw.io for architecture diagram
CSV format for raw and uploaded records
Deliverables:

Ingested dataset: sanction-List.csv stored in a structured S3 path
System architecture diagram showing ingestion flow and backend mapping
Upload script (PowerShell)
Screenshots confirming the upload and data structure
Timeline: Completion of the project: 1 week including ingestion logic design, upload validation, and documentation.

Outcome: This data wrangling project enables UCW to maintain a centralized, cloud-based repository of academic misconduct records, supporting future reporting, auditing, and analytics with high data integrity and structure

# Project 2 Data Profiling and Cleaning
Data Quality Control for Academic User Logs – UCW Project
Project Title: Implementation of Data Quality Control Measures for Academic Logs at UCW
Objective:
To establish a robust data quality control framework for managing academic user log data stored in Amazon S3. The focus is on ensuring accuracy, completeness, consistency, and long-term integrity through profiling, cleaning, validation, and lifecycle rules using AWS Glue DataBrew and S3.

Background:
Academic systems at University Canada West collect detailed logs and records, which were previously unmanaged. This project implements a scalable solution to ingest, profile, clean, and monitor these logs in AWS, ensuring regulatory compliance and data readiness for analytics.

Dataset:

academics-user-log.txt: A structured log file with 50 rows and multiple attributes.
Additional datasets: Academic sanction, Student Lists, and Case Lists.
Methodology:

Current State Assessment
Analyzed user logs and academic data in AWS S3.
Identified data issues: inconsistent column structures and lack of validation checks.
Data Profiling (using AWS Glue DataBrew)
Identified column types, missing values, and duplicate rows.
Profiled datasets:
academic-Sanction-list-ds-anita
academic-Case-list-ds-anita
academic-student-list-ds-anita
![Dataprofile overview](https://github.com/user-attachments/assets/68a36fd6-7abc-4112-9e88-1f907093dbef)
Data Cleansing
Created DataBrew recipes and ran successful jobs to clean each dataset.
Standardized column formats and removed invalid rows.
![Screenshot 2025-03-27 112659](https://github.com/user-attachments/assets/c8ffb874-0039-4543-8226-c73b6f730a78)
![Screenshot 2025-03-27 112747](https://github.com/user-attachments/assets/0a73f148-0d81-45e0-b8e4-601c90bacdc2)




