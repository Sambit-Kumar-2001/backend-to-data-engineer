# Month 4 Project: The Open Source Lakehouse
**Goal:** Build a "Medallion" Architecture (Bronze -> Silver -> Gold).
**Tech:** MinIO, Spark, dbt, Trino.

---

## 📅 Week 1: Infrastructure & Ingestion (The "Bronze" Layer)
*   **Day 1**: **Architectural Diagram**. Draw the flow. Define technologies for each step.
*   **Day 2**: **Infrastructure Setup**. Write `docker-compose.yml` for MinIO, Spark Master/Worker, and Trino.
*   **Day 3-5**: **Ingestion Script**.
    *   Pick a large dataset (e.g., NYC Taxi Data or GitHub Archive).
    *   Write a Python/Airflow job to download data daily and save as `Raw JSON` in MinIO (`s3://bronze/`).
*   **Day 6-7**: **Validation**. Ensure data is landing correctly partitioned by date (`/year=2024/month=01/`).

## 📅 Week 2: Processing (The "Silver" Layer)
*   **Day 8-10**: **Cleaning with Spark**.
    *   Write a Spark Job to read Bronze.
    *   Deduplicate rows. Convert types. Remove corrupt data.
    *   Write to `s3://silver/` as **Parquet** (or Delta Lake table).
*   **Day 11-12**: **Schema Enforcement**.
    *   Implement checks that fail the job if the schema changes unexpectedly.
*   **Day 13-14**: **Backfill**.
    *   Run your script over 1 year of historical data to populate the Silver layer.

## 📅 Week 3: Transformation (The "Gold" Layer)
*   **Day 15-17**: **Modeling with dbt (or Spark SQL)**.
    *   Aggregate "Rides" into "Daily Revenue by Driver".
    *   Join with "Weather" data (dimension).
    *   Write to `s3://gold/`.
*   **Day 18-20**: **Optimization**.
    *   Z-Order or Partition the Gold tables for fast querying.
    *   Register these tables in the Hive Metastore (or Trino catalog).

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
