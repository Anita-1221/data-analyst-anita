# project 1
Data Wrangling for Academic Misconduct Record Ingestion at UCW

Project Title: Data Wrangling for Cloud-Based Ingestion of Academic Integrity Records at UCW

Objective: The primary goal of this project is to perform structured data wrangling and cloud-based ingestion for academic misconduct records at University Canada West (UCW). By organizing, transforming, and uploading data to AWS S3, the project aims to create a secure, traceable, and analysis-ready dataset.

Background: UCW collects academic misconduct reports that require centralized, compliant storage and integration with backend systems. This project implements a repeatable ingestion process using AWS CLI and PowerShell for uploading structured CSV files to Amazon S3 with folder logic based on timestamped hierarchy.

Dataset:

RecordForm-List.csv: CSV file containing academic misconduct records including student ID, case ID, and report form details.
Entity relationships: StudentList, CaseList, and AcademicIntegrityReportFormList.
Methodology:

Data Collection:
Academic misconduct data is collected and formatted into structured CSV files.
