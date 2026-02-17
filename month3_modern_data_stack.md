# Month 3: The Modern Data Stack (Cloud & Warehousing)
**Goal:** Master the tools that dominate the industry today.
**Audience:** Senior Backend Dev (Knows SQL, needs to learn "Analytics Engineering").

---

## 📅 Week 1: Advanced Warehousing (OLAP)
**Theme**: "It's not just a big Postgres."

*   **Day 1: OLTP vs OLAP Architecture**
    *   **Resource**: [AWS: OLTP vs OLAP](https://aws.amazon.com/compare/the-difference-between-olap-and-oltp/)
    *   **Video**: [Seattle Data Guy: OLTP vs OLAP](https://www.youtube.com/watch?v=XnyN1BsOqKs)
    *   **Theory**: Row-store vs Column-store. Compression. Zipf distribution.
    *   **Problem**: Benchmark a `SELECT SUM(col)` on a Postgres Row table vs a Parquet Columnar file (using DuckDB). Explain the 100x speedup.
*   **Day 2: Data Modeling (Star Schema)**
    *   **Resource**: [Kimball Group: Star Schema](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/star-schema-olap-cube/)
    *   **Video**: [Kahan Data Solutions: Star Schema](https://www.youtube.com/watch?v=J326L4r6YKE)
    *   **Theory**: Facts and Dimensions. Kimball Methodology.
    *   **Problem**: Design a Star Schema for an "Uber Rides" app. Create the DDL (Fact_Rides, Dim_Driver, Dim_Location).
*   **Day 3: Slowly Changing Dimensions (SCD)**
    *   **Resource**: [DataBricks: SCD Type 1, 2, 3](https://www.databricks.com/glossary/slowly-changing-dimension)
    *   **Video**: [Seattle Data Guy: SCDs Explained](https://www.youtube.com/watch?v=iX78D5u6_y8)
    *   **Theory**: Type 1 (Overwrite) vs Type 2 (History).
    *   **Problem**: Implement an SCD Type 2 merge logic using SQL `MERGE` or Python.
*   **Day 4: DuckDB (The SQLite for Analytics)**
    *   **Resource**: [DuckDB SQL Introduction](https://duckdb.org/docs/sql/introduction)
    *   **Video**: [MotherDuck: Intro to DuckDB](https://www.youtube.com/watch?v=bXOjJXh6t8c)
    *   **Theory**: Embedded OLAP.
    *   **Problem**: Query a 1GB CSV file directly using DuckDB CLI without loading it.
*   **Day 5: Partitioning & Clustering (Cloud Optimization)**
    *   **Resource**: [BigQuery: Partitioning vs Clustering](https://cloud.google.com/bigquery/docs/partitioned-tables)
    *   **Video**: [Google Cloud Tech: Partitioning](https://www.youtube.com/watch?v=DTsYd4n5WCo)
    *   **Theory**: Pruning. Micro-partitions (Snowflake concept).
    *   **Problem**: Simulate partitioning by saving data into `year=2024/month=01` folders and querying with a `WHERE year=...` filter.
*   **Week 1 Capstone: The Local Warehouse**
    *   **Resource**: [ClickHouse QuickStart](https://clickhouse.com/docs/en/getting-started/quick-start)
    *   **Video**: [ClickHouse: Architecture](https://www.youtube.com/watch?v=pZk-r3S-L4s)
    *   **Problem**: Spin up a **ClickHouse** or **Postgres** (tuned for analytics) container. Load 10M rows. optimize indexes for aggregation queries.

---

## 📅 Week 2: dbt (Data Build Tool)
**Theme**: "Software Engineering applied to SQL."

*   **Day 8: Setup & The Project Structure**
    *   **Resource**: [dbt Docs: Project Structure](https://docs.getdbt.com/docs/build/projects)
    *   **Video**: [dbt Labs: Fundamentals](https://www.youtube.com/watch?v=-55O5g4G_ds)
    *   **Theory**: `dbt init`. `dbt_project.yml`.
    *   **Problem**: Initialize a dbt project connecting to your local Postgres/DuckDB.
*   **Day 9: Models & Materializations**
    *   **Resource**: [dbt Docs: Materializations](https://docs.getdbt.com/docs/build/materializations)
    *   **Video**: [Kahan Data Solutions: dbt Models](https://www.youtube.com/watch?v=J326L4r6YKE)
    *   **Theory**: `view` vs `table` vs `incremental`.
    *   **Problem**: Create a `base` model (view) and a `mart` model (table). Run `dbt run`.
*   **Day 10: Testing data (Data Quality)**
    *   **Resource**: [dbt Docs: Tests](https://docs.getdbt.com/docs/build/tests)
    *   **Video**: [dbt Labs: Testing](https://www.youtube.com/watch?v=0k6gX6Q_c8o)
    *   **Theory**: `unique`, `not_null`, custom SQL tests.
    *   **Problem**: Add a test that ensures `order_total` is never negative. Run `dbt test`.
*   **Day 11: Documentation & Lineage**
    *   **Resource**: [dbt Docs: Documentation](https://docs.getdbt.com/docs/collaborate/documentation)
    *   **Video**: [Seattle Data Guy: dbt Docs](https://www.youtube.com/watch?v=XnyN1BsOqKs)
    *   **Theory**: The `manifest.json`. DAG visualization.
    *   **Problem**: Add descriptions to your `schema.yml`. Generate the doc site (`dbt docs generate`).
*   **Day 12: Jinja Templating (SQL + Code)**
    *   **Resource**: [Jinja for dbt](https://docs.getdbt.com/docs/build/jinja-macros)
    *   **Video**: [Kahan Data: Jinja Macros](https://www.youtube.com/watch?v=pK9sL1g5QoE)
    *   **Theory**: Macros. Loops in SQL.
    *   **Problem**: Write a Jinja macro `cents_to_dollars(col_name)` and use it in a model.
*   **Week 2 Capstone: The Analytics Engineer**
    *   **Resource**: [dbt Best Practices](https://docs.getdbt.com/best-practices)
    *   **Video**: [dbt Labs: Best Practices](https://www.youtube.com/watch?v=t1kQLkQd26A)
    *   **Problem**: Build a dbt pipeline that takes "Raw Orders" -> "Clean Orders" -> "Monthly Revenue Report". Include tests and docs.

---

## 📅 Week 3: Cloud Data Engineering (AWS)
**Theme**: "Serverless Data."

*   **Day 15: S3 as a Data Lake**
    *   **Resource**: [AWS: What is a Data Lake?](https://aws.amazon.com/big-data/datalakes-and-analytics/what-is-a-data-lake/)
    *   **Video**: [Be A Better Dev: Data Lake](https://www.youtube.com/watch?v=Jj7uR3W4FwA)
    *   **Theory**: Storage classes (Standard vs Glacier). Event notifications.
    *   **Problem**: Use `boto3` to upload a file and trigger a Lambda function (mocked or real) on upload.
*   **Day 16: AWS Glue (Serverless Spark)**
    *   **Resource**: [AWS Glue Concepts](https://docs.aws.amazon.com/glue/latest/dg/components-key-concepts.html)
    *   **Video**: [AWS: Glue Explained](https://www.youtube.com/watch?v=P4u8J_1-2-3)
    *   **Theory**: The Glue Crawler and Catalog.
    *   **Problem**: Write a Terraform script to define a Glue Database and Crawler.
*   **Day 17: AWS Athena (Presto as a Service)**
    *   **Resource**: [AWS Athena Querying](https://docs.aws.amazon.com/athena/latest/ug/querying-athena-tables.html)
    *   **Video**: [Be A Better Dev: Athena](https://www.youtube.com/watch?v=6-7-8-9-0)
    *   **Theory**: Querying S3 with SQL.
    *   **Problem**: Upload a CSV to S3. Define a schema definition. Query it using SQL.
*   **Day 18: IAM for Data Engineers**
    *   **Resource**: [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
    *   **Video**: [NetworkChuck: IAM Explained](https://www.youtube.com/watch?v=5iWhQWVXosU)
    *   **Theory**: Least Privilege. Role Assumption.
    *   **Problem**: defined a Policy that allows Read-Only access to a specific S3 bucket.
*   **Week 3 Capstone: The Serverless Pipeline**
    *   **Resource**: [Serverless Data Processing](https://aws.amazon.com/solutions/implementations/serverless-data-lake-framework/)
    *   **Video**: [AWS: Serverless Data Lake](https://www.youtube.com/watch?v=a-b-c-d-e)
    *   **Problem**: Architect (draw) a pipeline: API Gateway -> Lambda -> Kinesis -> S3 -> Athena. Implement the S3 -> Athena part.

---

## 📅 Week 4: CI/CD for Data
**Theme**: "Production-Grade Pipelines."

*   **Day 22: GitHub Actions for dbt**
    *   **Resource**: [dbt Continuous Integration](https://docs.getdbt.com/docs/deploy/continuous-integration)
    *   **Video**: [dbt Labs: CI/CD](https://www.youtube.com/watch?v=A-B-C-D-E)
    *   **Theory**: CI checks on PR.
    *   **Problem**: Create a workflow that runs `dbt parse` on every PR.
*   **Day 23: Dockerizing Everything**
    *   **Resource**: [Docker Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
    *   **Video**: [TechWorld with Nana: Docker Tutorial](https://www.youtube.com/watch?v=3-c-E-F-g-h)
    *   **Theory**: Reproducible environments.
    *   **Problem**: Create a `Dockerfile` that installs Python, dbt, and AWS CLI.
*   **Day 24: Infrastructure as Code (Terraform)**
    *   **Resource**: [Terraform: AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
    *   **Video**: [TechWorld with Nana: Terraform](https://www.youtube.com/watch?v=SLs3k8-i-j)
    *   **Theory**: Setup resources via code.
    *   **Problem**: Write a `.tf` file to provision an S3 bucket and an IAM user.
*   **Day 30: MONTH 3 CAPSTONE - The "Modern Stack"**
    *   **Resource**: [Modern Data Stack Guide](https://www.moderndatastack.xyz/stacks)
    *   **Video**: [Seattle Data Guy: Modern Data Stack](https://www.youtube.com/watch?v=k-l-m-n-o-p)
    *   **Goal**: Full ELT Pipeline.
    *   **Steps**:
        1.  **Extract**: Python script uploads data to S3 (MinIO).
        2.  **Load**: DuckDB reads from S3.
        3.  **Transform**: dbt transforms the data in DuckDB.
        4.  **Test**: dbt tests validate the data.
        5.  **Serve**: A Streamlit app reads the final dbt model and shows a chart.
