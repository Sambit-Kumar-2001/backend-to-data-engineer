# Month 3: The Modern Data Stack (Cloud & Warehousing)
**Goal:** Master the tools that dominate the industry today.
**Audience:** Senior Backend Dev (Knows SQL, needs to learn "Analytics Engineering").

---

## 📅 Week 1: Advanced Warehousing (OLAP)
**Theme**: "It's not just a big Postgres."

*   **Day 1: OLTP vs OLAP Architecture**
    *   **Theory**: Row-store vs Column-store. Compression. Zipf distribution.
    *   **Problem**: Benchmark a `SELECT SUM(col)` on a Postgres Row table vs a Parquet Columnar file (using DuckDB). Explain the 100x speedup.
*   **Day 2: Data Modeling (Star Schema)**
    *   **Theory**: Facts and Dimensions. Kimball Methodology.
    *   **Problem**: Design a Star Schema for an "Uber Rides" app. Create the DDL (Fact_Rides, Dim_Driver, Dim_Location).
*   **Day 3: Slowly Changing Dimensions (SCD)**
    *   **Theory**: Type 1 (Overwrite) vs Type 2 (History).
    *   **Problem**: Implement an SCD Type 2 merge logic using SQL `MERGE` or Python.
*   **Day 4: DuckDB (The SQLite for Analytics)**
    *   **Theory**: Embedded OLAP.
    *   **Problem**: Query a 1GB CSV file directly using DuckDB CLI without loading it.
*   **Day 5: Partitioning & Clustering (Cloud Optimization)**
    *   **Theory**: Pruning. Micro-partitions (Snowflake concept).
    *   **Problem**: Simulate partitioning by saving data into `year=2024/month=01` folders and querying with a `WHERE year=...` filter.
*   **Week 1 Capstone: The Local Warehouse**
    *   **Problem**: Spin up a **ClickHouse** or **Postgres** (tuned for analytics) container. Load 10M rows. optimize indexes for aggregation queries.

---

## 📅 Week 2: dbt (Data Build Tool)
**Theme**: "Software Engineering applied to SQL."

*   **Day 8: Setup & The Project Structure**
    *   **Theory**: `dbt init`. `dbt_project.yml`.
    *   **Problem**: Initialize a dbt project connecting to your local Postgres/DuckDB.
*   **Day 9: Models & Materializations**
    *   **Theory**: `view` vs `table` vs `incremental`.
    *   **Problem**: Create a `base` model (view) and a `mart` model (table). Run `dbt run`.
*   **Day 10: Testing data (Data Quality)**
    *   **Theory**: `unique`, `not_null`, custom SQL tests.
    *   **Problem**: Add a test that ensures `order_total` is never negative. Run `dbt test`.
*   **Day 11: Documentation & Lineage**
    *   **Theory**: The `manifest.json`. DAG visualization.
    *   **Problem**: Add descriptions to your `schema.yml`. Generate the doc site (`dbt docs generate`).
*   **Day 12: Jinja Templating (SQL + Code)**
    *   **Theory**: Macros. Loops in SQL.
    *   **Problem**: Write a Jinja macro `cents_to_dollars(col_name)` and use it in a model.
*   **Week 2 Capstone: The Analytics Engineer**
    *   **Problem**: Build a dbt pipeline that takes "Raw Orders" -> "Clean Orders" -> "Monthly Revenue Report". Include tests and docs.

---

## 📅 Week 3: Cloud Data Engineering (AWS)
**Theme**: "Serverless Data."

*   **Day 15: S3 as a Data Lake**
    *   **Theory**: Storage classes (Standard vs Glacier). Event notifications.
    *   **Problem**: Use `boto3` to upload a file and trigger a Lambda function (mocked or real) on upload.
*   **Day 16: AWS Glue (Serverless Spark)**
    *   **Theory**: The Glue Crawler and Catalog.
    *   **Problem**: Write a Terraform script to define a Glue Database and Crawler.
*   **Day 17: AWS Athena (Presto as a Service)**
    *   **Theory**: Querying S3 with SQL.
    *   **Problem**: Upload a CSV to S3. Define a schema definition. Query it using SQL.
*   **Day 18: IAM for Data Engineers**
    *   **Theory**: Least Privilege. Role Assumption.
    *   **Problem**: defined a Policy that allows Read-Only access to a specific S3 bucket.
*   **Week 3 Capstone: The Serverless Pipeline**
    *   **Problem**: Architect (draw) a pipeline: API Gateway -> Lambda -> Kinesis -> S3 -> Athena. Implement the S3 -> Athena part.

---

## 📅 Week 4: CI/CD for Data
**Theme**: "Production-Grade Pipelines."

*   **Day 22: GitHub Actions for dbt**
    *   **Theory**: CI checks on PR.
    *   **Problem**: Create a workflow that runs `dbt parse` on every PR.
*   **Day 23: Dockerizing Everything**
    *   **Theory**: Reproducible environments.
    *   **Problem**: Create a `Dockerfile` that installs Python, dbt, and AWS CLI.
*   **Day 24: Infrastructure as Code (Terraform)**
    *   **Theory**: Setup resources via code.
    *   **Problem**: Write a `.tf` file to provision an S3 bucket and an IAM user.
*   **Day 30: MONTH 3 CAPSTONE - The "Modern Stack"**
    *   **Goal**: Full ELT Pipeline.
    *   **Steps**:
        1.  **Extract**: Python script uploads data to S3 (MinIO).
        2.  **Load**: DuckDB reads from S3.
        3.  **Transform**: dbt transforms the data in DuckDB.
        4.  **Test**: dbt tests validate the data.
        5.  **Serve**: A Streamlit app reads the final dbt model and shows a chart.
