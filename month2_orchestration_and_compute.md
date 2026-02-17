# Month 2: Orchestration & Compute (The "Scale" Phase)
**Goal:** Move from "Scripts on Laptop" to "Systems on Cluster".
**Audience:** Senior Backend Dev (Knows Docker/Linux, new to Data Ops).

---

## 📅 Week 1: Orchestration (Airflow)
**Theme**: "Cron is dead. Long live the DAG."

*   **Day 1: The DAG Concept**
    *   **Theory**: Directed Acyclic Graphs. Dependency management.
    *   **Problem**: Install Airflow (via Docker). Write a "Hello World" DAG that runs 3 dummy tasks: T1 -> [T2, T3].
*   **Day 2: BashOperator & PythonOperator**
    *   **Theory**: Executing shell scripts vs Python functions in a task.
    *   **Problem**: Write a DAG that: 1. Creates a file (Bash). 2. Processes it (Python). 3. Moves it (Bash).
*   **Day 3: XComs (State Management)**
    *   **Theory**: Sharing small data between tasks. (Like passing props, but for backend tasks).
    *   **Problem**: Task A generates a random number and pushes to XCom. Task B pulls it and fails if < 50.
*   **Day 4: Sensors (Event-Driven Triggering)**
    *   **Theory**: Waiting for external events (File arrival, API 200 OK).
    *   **Problem**: Create a DAG that waits for a file `trigger.txt` to appear in a folder, then deletes it.
*   **Day 5: Dynamic DAG Generation**
    *   **Theory**: Writing Python code to *generate* DAGs (Meta-programming).
    *   **Problem**: Create a single Python file that generates 10 DAGs (one for each "Client") from a list `['client_a', 'client_b'...]`.
*   **Day 6: Handling Failures (SLAs & Alerts)**
    *   **Theory**: Retries, Backoff, Callbacks (`on_failure_callback`).
    *   **Problem**: Configure a DAG to retry 3 times with exponential backoff. Add a callback that simulate sending a Slack alert on failure.
*   **Week 1 Capstone: The Backup Pipeline**
    *   **Problem**: A DAG that:
        1.  Dumps your local Postgres DB to a `.sql` file.
        2.  Compresses it (`gzip`).
        3.  Uploads to MinIO.
        4.  Deletes local files.
        5.  Sends a "Success" log.

---

## 📅 Week 2: Distributed Compute (PySpark Basics)
**Theme**: "Pandas doesn't scale. Spark does."

*   **Day 8: The Spark Architecture (Driver/Worker)**
    *   **Theory**: How distributed computing works. Lazy Evaluation (again).
    *   **Problem**: Install PySpark locally. Create a `SparkSession`. Load a CSV. Print schema.
*   **Day 9: RDDs vs DataFrames**
    *   **Theory**: Resilient Distributed Datasets (Low level) vs DataFrames (High level).
    *   **Problem**: Count words in a text file using RDDs (`map`, `reduceByKey`). Then do it with DataFrames.
*   **Day 10: Transformations & Actions**
    *   **Theory**: Narrow (Map/Filter) vs Wide (Sort/GroupBy) transformations. The "Shuffle".
    *   **Problem**: Load a large dataset. Perform a Filter (Narrow) and a GroupBy (Wide). Explain the execution plan (`.explain()`).
*   **Day 11: Reading/Writing Data (Parquet/Avro)**
    *   **Theory**: Big Data formats. Why CSV is bad for Spark.
    *   **Problem**: Read a 1GB CSV. Convert to Parquet with Snappy compression. Compare sizes.
*   **Day 12: Spark SQL**
    *   **Theory**: Running standard SQL on distributed data.
    *   **Problem**: Register a DataFrame as a Temp View. Write a complex SQL query (Joins/Window) against it.
*   **Day 13: Handling Nulls & Schema Enforcement**
    *   **Theory**: Data quality at scale.
    *   **Problem**: Define a strict `StructType` schema. Load data that violates it (and handle the drop/fail).
*   **Week 2 Capstone: The Log Analyzer (At Scale)**
    *   **Problem**: Generate 10GB of fake logs. Use Spark to calculating "Error Rate per Hour". Save results to Single CSV (coalesce).

---

## 📅 Week 3: Advanced Optimization (The "Senior" Skills)
**Theme**: "Make it run fast and cheap."

*   **Day 15: Partitioning**
    *   **Theory**: Organizing files on disk (Hive style `year=2024/month=01`).
    *   **Problem**: Write the Day 14 output partitioned by `error_code`. Check the folder structure.
*   **Day 16: Caching & Persistence**
    *   **Theory**: `cache()` vs `persist()`. RAM vs Disk spilling.
    *   **Problem**: Load data, cache it, run 3 different queries. Unpersist. Measure speedup.
*   **Day 17: The Join Strategies (Broadcast vs Sort-Merge)**
    *   **Theory**: Optimizing joins. Avoiding shuffles for small tables.
    *   **Problem**: Force a `broadcast` join between a large Fact table and small Dimension table. Check `.explain()`.
*   **Day 18: UDFs (User Defined Functions)**
    *   **Theory**: When SQL isn't enough. Python UDF vs Pandas UDF (Arrow).
    *   **Problem**: Write a standard Python UDF to parse a UserAgent string. Then rewrite it as a Pandas UDF for performance.
*   **Day 19: Handling Skew**
    *   **Theory**: When one worker gets 90% of the data. Salting.
    *   **Problem**: Create a skewed dataset. Observe the "straggler" task in Spark UI.
*   **Day 20: Unit Testing Spark**
    *   **Theory**: `chispa` or `pytest-spark`.
    *   **Problem**: Write a unit test for a Spark transformation function using small mock data.
*   **Week 3 Capstone: The Data Lake Cleaner**
    *   **Problem**:
        1.  Read nested JSON data (complex schema).
        2.  Flatten it.
        3.  Deduplicate rows.
        4.  Partition by Date.
        5.  Write to Parquet.

---

## 📅 Week 4: Integration (The Platform)
**Theme**: "Putting it all together."

*   **Day 22: Dockerizing Spark Jobs**
    *   **Theory**: `spark-submit` inside a container.
    *   **Problem**: Create a Docker image that contains your Spark script and dependencies. Run it.
*   **Day 23: MinIO + Spark**
    *   **Theory**: separating Compute (Spark) from Storage (S3).
    *   **Problem**: Configure Spark to read/write directly to your local MinIO container (s3a://).
*   **Day 24: Airflow + Spark (The SparkSubmitOperator)**
    *   **Theory**: Orchestrating the heavy lifters.
    *   **Problem**: Create an Airflow DAG that triggers your Spark Docker container.
*   **Day 25: Data Quality Checks (Great Expectations)**
    *   **Theory**: Testing data in production.
    *   **Problem**: Add a step in your pipeline that fails if "null count > 0".
*   **Day 30: FINAL CAPSTONE - The Lakehouse Ingestion**
    *   **Goal**: An End-to-End Pipeline.
    *   **Architecture**:
        1.  **Airflow** triggers the job daily.
        2.  **Spark** reads today's raw data (MinIO).
        3.  **Clean**: Remove PII, validate schema.
        4.  **Enrich**: Join with static "User" table.
        5.  **Write**: Append to the "Silver" table (Parquet/Delta) in MinIO.
        6.  **Alert**: Slack notification on success.
