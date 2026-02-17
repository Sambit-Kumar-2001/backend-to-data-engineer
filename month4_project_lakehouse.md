# Month 4 Project: The Open Source Lakehouse
**Goal:** Build a "Medallion" Architecture (Bronze -> Silver -> Gold).
**Tech:** MinIO, Spark, dbt, Trino.

---

## 📅 Week 1: Infrastructure & Ingestion (The "Bronze" Layer)
*   **Day 1**: **Architectural Diagram**. Draw the flow. Define technologies for each step.
    *   **Resource**: [Databricks: Medallion Architecture](https://www.databricks.com/glossary/medallion-architecture)
    *   **Video**: [Databricks: Medallion Architecture Explained](https://www.youtube.com/watch?v=n-t-e-r-f-a-c-e)
*   **Day 2**: **Infrastructure Setup**. Write `docker-compose.yml` for MinIO, Spark Master/Worker, and Trino.
    *   **Resource**: [Docker Hub: MinIO](https://hub.docker.com/r/minio/minio)
*   **Day 3-5**: **Ingestion Script**.
    *   Pick a large dataset (e.g., NYC Taxi Data or GitHub Archive).
    *   Write a Python/Airflow job to download data daily and save as `Raw JSON` in MinIO (`s3://bronze/`).
    *   **Resource**: [NYC Taxi Dataset](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
*   **Day 6-7**: **Validation**. Ensure data is landing correctly partitioned by date (`/year=2024/month=01/`).
    *   **Resource**: [Hive Partitioning](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/FileSystemShell.html#ls)

## 📅 Week 2: Processing (The "Silver" Layer)
*   **Day 8-10**: **Cleaning with Spark**.
    *   Write a Spark Job to read Bronze.
    *   Deduplicate rows. Convert types. Remove corrupt data.
    *   Write to `s3://silver/` as **Parquet** (or Delta Lake table).
    *   **Resource**: [Delta Lake: Quickstart](https://docs.delta.io/latest/quick-start.html)
    *   **Video**: [Delta Lake: Features Explained](https://www.youtube.com/watch?v=c-h-a-n-g-e-s)
*   **Day 11-12**: **Schema Enforcement**.
    *   Implement checks that fail the job if the schema changes unexpectedly.
    *   **Resource**: [Delta Lake: Schema Enforcement](https://docs.delta.io/latest/delta-batch.html#schema-enforcement-and-evolution)
*   **Day 13-14**: **Backfill**.
    *   Run your script over 1 year of historical data to populate the Silver layer.

## 📅 Week 3: Transformation (The "Gold" Layer)
*   **Day 15-17**: **Modeling with dbt (or Spark SQL)**.
    *   Aggregate "Rides" into "Daily Revenue by Driver".
    *   Join with "Weather" data (dimension).
    *   Write to `s3://gold/`.
    *   **Resource**: [dbt with Spark](https://docs.getdbt.com/docs/core/connect-data-platform/spark-setup)
*   **Day 18-20**: **Optimization**.
    *   Z-Order or Partition the Gold tables for fast querying.
    *   Register these tables in the Hive Metastore (or Trino catalog).
    *   **Resource**: [Trino: Hive Connector](https://trino.io/docs/current/connector/hive.html)
    *   **Video**: [Trino: Architecture](https://www.youtube.com/watch?v=t-r-i-n-o)

## 📅 Week 4: Serving & Visualization
*   **Day 21-25**: **Trino Setup**.
    *   Configure Trino to query MinIO.
    *   Run SQL queries against your Gold layer.
*   **Day 26-29**: **Dashboard**.
    *   Connect **Superset** or **Streamlit** to Trino.
    *   Visualize "Revenue Trends".
*   **Day 30**: **Documentation & Demo**.
    *   Record a loom video explaining the architecture.
    *   Update your GitHub README.
