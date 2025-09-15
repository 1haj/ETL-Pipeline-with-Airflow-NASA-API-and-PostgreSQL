Project Overview: NASA APOD ETL Pipeline with Airflow and PostgreSQL

This project demonstrates a full ETL (Extract, Transform, Load) pipeline built using Apache Airflow. The pipeline automatically fetches data from an external source—the NASA Astronomy Picture of the Day (APOD) API—processes it, and stores it in a PostgreSQL database for further analysis or reporting.

The project uses Docker to run both Airflow and PostgreSQL, ensuring a reproducible and isolated environment. Airflow’s operators and hooks manage the workflow efficiently, handling API requests, data transformations, and database operations.

Key Components

1. Apache Airflow:

Orchestrates and schedules the ETL workflow.

Defines a DAG (Directed Acyclic Graph) for sequential task execution.

Handles task dependencies and ensures reliability of the pipeline.

2. PostgreSQL Database:

Stores the extracted and transformed APOD data.

Runs inside a Docker container for easy setup and persistent storage.

Interacted with via Airflow’s PostgresHook, allowing automated table creation and data insertion.

3. NASA APOD API:

Provides daily astronomy data including image title, description, URL, and date.

Accessed through Airflow’s SimpleHttpOperator to extract JSON data automatically.

Project Objectives

Extract Data:

Fetch daily APOD data from NASA’s API.

Transform Data:

Process the JSON response to extract relevant fields.

Ensure the data is formatted correctly for database storage.

Load Data:

Insert the transformed data into a PostgreSQL table.

Automatically create the table if it doesn’t exist.

Workflow Architecture

The ETL process follows a classic Extract → Transform → Load structure:

Extract:

Make HTTP requests to the NASA APOD API.

Receive JSON responses containing title, explanation, URL, and date.

Transform:

Use Airflow’s TaskFlow API to process the data.

Extract only the necessary fields and prepare them for insertion.

Load:

Insert the processed data into a PostgreSQL table using PostgresHook.

Maintain data persistence and allow easy access for analysis.