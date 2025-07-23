Chronic Disease Analytics System: OLTP to OLAP
Project Overview
This project presents a comprehensive database solution designed to track, analyze, and respond to chronic disease trends, particularly within urban populations. It demonstrates the full lifecycle of data management, from transactional data capture (OLTP) to analytical insights (OLAP), enabling healthcare providers, researchers, and policymakers to make data-driven decisions.

Business Problem
Chronic diseases like diabetes, hypertension, asthma, and heart disease are increasingly prevalent, especially in urban areas, influenced by lifestyle, environmental factors, and healthcare disparities. Health organizations require a robust system to monitor diagnosis rates, treatment plans, hospital visits, medication usage, and patient outcomes to improve public health, optimize resource allocation, and implement targeted interventions.

Solution
This project addresses the business problem by developing a dual-layered database system:

Online Transaction Processing (OLTP) Database: For efficient day-to-day operations, recording granular patient data, diagnoses, treatments, and locations.

Online Analytical Processing (OLAP) Data Warehouse: A dimensional model built for analytical queries, enabling fast and flexible reporting on chronic disease trends and treatment effectiveness.

An Extract, Load, Transform (ELT) process is implemented using SQL to move and reshape data from the OLTP schema into the dimensional data warehouse.

Architecture & Data Flow
The system is built using PostgreSQL, demonstrating a robust relational database foundation for both transactional and analytical workloads.

OLTP Schema:

Designed with normalized tables (e.g., person, disease, location, medicine, indication, diseased_patient, race, disease_type, race_disease_propensity).

Focuses on data integrity and transactional efficiency.

See Disease Project (1).sql for schema creation and data population.

Dimensional Model (OLAP Schema - warehouse):

Features a central fact_disease_diagnosis table at the grain of a single patient diagnosis event.

Supported by various dimension tables: dim_date, dim_disease, dim_person, dim_location, dim_medicine, dim_race.

Optimized for analytical querying and reporting.

ETL Process:

SQL scripts within Disease Project (1).sql handle the transformation of data from the public (OLTP) schema to the warehouse (OLAP) schema.

This includes data cleaning, joining, aggregation, and loading into the dimensional structure.

Analytical Layer:

Direct SQL queries on the dimensional model provide quick insights.

The data is structured for easy integration with Business Intelligence (BI) tools like Tableau for dashboarding and visualization. (Refer to the presentation for visualization examples).

Key Features & Capabilities
Comprehensive Data Model: Captures essential information about patients, diseases, treatments, locations, and demographics.

Data Population: Includes sample data to demonstrate functionality.

Integrity Constraints: Ensures data quality and relationships are maintained.

Analytical Queries: Provides examples of complex queries to extract insights, such as:

Most common diseases by race.

Medicine effectiveness by disease type.

Cities with the highest average disease severity.

Disease propensity by race.

Dimensional Modeling: Transforms transactional data into a star schema for optimized analytical performance.

Business Intelligence Integration: Data ready for visualization tools to create interactive dashboards.

Technologies Used
Database: PostgreSQL

Query Language: SQL

Data Modeling: OLTP (Normalized), OLAP (Dimensional Model/Star Schema)

ETL: SQL-based transformations

Presentation/Documentation: Microsoft PowerPoint

How to Use (SQL Script)
To run the SQL scripts:

Install PostgreSQL: Ensure you have a PostgreSQL database server set up.

Connect to a Database: Use a SQL client (like pgAdmin, DBeaver, or psql) to connect to your PostgreSQL instance.

Execute Disease Project (1).sql: Run the script sequentially. It will:

Create the OLTP tables.

Populate the OLTP tables with sample data.

Create the warehouse schema and its dimensional tables.

Perform the ETL process to load data into the dimensional model.

Execute various analytical queries.

Insights & Business Value
The analytical capabilities of this system provide significant business value by enabling:

Targeted Interventions: Identifying high-risk populations or geographic hotspots.

Resource Optimization: Efficient allocation of healthcare resources based on disease prevalence and severity.

Treatment Effectiveness Analysis: Informing evidence-based decisions on therapies and medications.

Policy Making: Supporting policymakers with data-driven intelligence for public health initiatives.

Disclaimer
The entire dataset used in this project is synthetic (artificially generated). It was created solely for the purpose of demonstrating the analytical capabilities of the system. The values presented in queries, dashboards, and visualizations are mock data designed to simulate realistic patterns and showcase the database and analytical tools' functionality. This project does not use real-world clinical data.

Project Files
Disease Project (1).sql: Contains all SQL scripts for OLTP schema creation, data population, OLAP schema creation, ETL, and analytical queries.

sdm final project .pptx: The project presentation slides, including ER diagrams, dimensional models, and analytical visualizations.
