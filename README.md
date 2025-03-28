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
Additional datasets: sanction Lists, Student Lists, and Case Lists.
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
Tools and Technologies:

AWS S3
AWS Glue DataBrew
PowerShell
draw.io
Amazon S3 Lifecycle Management
Architecture Overview:
The system integrates EC2 (for ingestion), S3 (for storage), and Glue DataBrew (for profiling and cleaning).

PowerShell Upload Command Used: Write-S3Object -Bucket academics-raw-anita -File "C:\Users\Administrator\Documents\academics-user-log.txt" -Key "/academic misconduct/academics-user-log/Ingestion/year=2025/quarter=1/month=1/day=25/server=ASVS-anita/academics-user-log.txt"
Deliverables:

DataBrew profile reports and cleaning job outputs
Cleaned and validated log datasets
Lifecycle-enabled data lake structure
Timeline:

Completed in under 2 weeks: profiling, cleaning, and lifecycle setup
Outcome:
This project ensures continuous data quality and archival integrity of academic logs at UCW, supporting compliance and analytics.
# Project 3 ERD Diagram
Data Wrangling for Academic Admissions Entity-Relationship Modeling

Project Title: Designing and Structuring Academic Admissions Data Using ER Diagrams

Objective:
The objective of this project is to model and structure data related to academic admissions processes using Entity-Relationship Diagrams (ERDs). The goal is to establish a clean relational schema to support database design, ensuring proper linkage between applicants, programs, applications, and interviews.

Background:
Academic institutions manage various components in the admissions workflow—from applicant submissions to program mapping and interviews. To optimize this process and support robust data handling, a normalized and well-structured ER model was designed using draw.io. This forms the basis for database implementation and analytical reporting in future stages.

Dataset:
The data model is abstract and applies to academic admissions data. It includes entities for applicants, applications, programs, and interviews. Fields include IDs, names, submission dates, and foreign key relationships between entities.

Methodology:

Data Collection:
Identified key entities involved in the admissions process based on institutional needs.
Reviewed existing data fields typically used in admissions and interview tracking systems.

Data Assessment:
Validated relationships between entities such as one-to-many (Applicants to Applications) and one-to-one (Applicants to Interviews).
Ensured no redundant or improperly linked attributes.

Data Cleaning (Conceptual Level):
Normalized entity attributes to avoid duplication.
Assigned unique identifiers (primary keys) for each entity and mapped foreign key relationships.

Data Transformation:
Constructed an ER diagram using draw.io.
Defined the following entities and relationships:

Applicants (Applicant ID, Applicant Name)
Programs (Program ID, Program Name)
Applications (Application ID, Applicant ID, Program ID, Submission Date)
Interview (Interview ID, Applicant ID)
Data Consolidation:
Ensured referential integrity among relationships by applying appropriate foreign key constraints.
Reviewed cardinality (one-to-many and one-to-one) across entity links.

Documentation and Validation:
ERD was documented visually and reviewed for accuracy and normalization.
![Screenshot 2025-03-27 150036](https://github.com/user-attachments/assets/0e5ef980-91a7-40a8-89c4-f6304c172658)

Ready for use in SQL database schema creation and relational queries.

Tools and Technologies:

draw.io for ERD creation
SQL (planned use for schema and query development)
Deliverables:

Normalized ER diagram for academic admissions
Visual mapping of relationships and attributes
Logical foundation for implementing relational databases
Timeline:
Completed within 1–2 days including review, diagramming, and documentation

Outcome:
The final ER diagram provides a scalable, normalized structure for managing admissions-related data. It serves as a reference for database creation and supports future extensions such as data analytics, reporting, and student lifecycle tracking.

# Project 4 Data Analytics and Security Platform

Cloud-Based  Analytics and Security Platform

Project Title: Design and Implementation of a Secure Cloud-Based Data Analytics Platform

Objective:
To design and implement a secure and scalable cloud-based data analytics solution for the City of Vancouver's information using AWS services. The platform focuses on storing, analyzing, and protecting sensitive  data while ensuring governance, availability, and system observability.

Background:
The City of Vancouver’s growing demand for efficient  data analysis and integrity led to the development of a cloud-native analytics platform. The goal was to extract insights into workforce compensation patterns using Amazon Athena while ensuring security and governance through AWS Glue, CloudTrail, and KMS. The project also prioritized backup and recovery using S3 versioning and replication, and real-time monitoring through CloudWatch.

Dataset:
The dataset contained Cultural space-related records such as State,website,Phone,Address,years, and workforce distribution across categories. Although specific details remain confidential, data analysis was performed on anonymized records stored in Amazon S3.

Methodology:

Architecture Design:

Outlined high-level architecture leveraging AWS S3, Athena, Glue Studio, KMS, CloudTrail, and CloudWatch.
Defined the interaction between data storage, analysis, encryption, monitoring, and logging.

Data Security Measures:

Created a customer-managed KMS key for encryption.
![Screenshot 2025-03-23 022005](https://github.com/user-attachments/assets/cbd527a5-e7e3-4dcd-ab2a-4c92b5bc7299)

Enabled S3 default encryption, versioning, and replication to backup buckets.
![Screenshot 2025-03-23 022053](https://github.com/user-attachments/assets/0026859b-0e1b-4290-ae79-d4d20d96d4dd)
![Screenshot 2025-03-23 022122](https://github.com/user-attachments/assets/5d5362b6-660a-44c3-a546-c97b403dfd34)
![Screenshot 2025-03-23 022148](https://github.com/user-attachments/assets/06baf8ef-1728-443c-82cf-64956b1d5851)

Monitoring and Logging:

Configured CloudWatch dashboards and alarms for tracking bucket usage and anomalies.
![Screenshot 2025-03-23 124451](https://github.com/user-attachments/assets/e060ea01-a348-4e10-8942-27351aa4e6dc)
Enabled AWS CloudTrail to log all user/API activity for compliance and traceability.

Tools and Technologies:

Amazon S3
Amazon Athena
AWS Glue Studio
AWS CloudTrail
AWS CloudWatch
AWS KMS
IAM Role Policies
SQL (Athena Queries)
ETL Design (Visual with Governance Rules)
Deliverables:

End-to-end AWS analytics pipeline with monitoring, security, and governance
Executed SQL queries on salary trends, workforce structure, and classification comparison
CloudWatch dashboard and alert system
Glue ETL workflow with rule-based data quality filtering
CloudTrail audit trail and encrypted replicated S3 buckets
Visuals, configurations, and code captured in supporting documentation
Timeline:
Project completed in 2 weeks, from initial design and setup through data querying, security implementation, monitoring configuration, and final documentation.

Outcome:
The cloud-based platform successfully processed sensitive payroll data while upholding high standards for security and governance. The system delivered meaningful insights into salary distribution, operational workforce structures, and data quality. Security measures such as encryption, replication, and audit logging were fully integrated, ensuring compliance and disaster recovery readiness for future operational use.








