# Month 2: Orchestration & Compute (The "Scale" Phase)
**Goal:** Move from "Scripts on Laptop" to "Systems on Cluster".
**Audience:** Senior Backend Dev (Knows Docker/Linux, new to Data Ops).

---

## 📅 Week 1: Orchestration (Airflow)
**Theme**: "Cron is dead. Long live the DAG."

*   **Day 1: The DAG Concept**
    *   **Resource**: [Astronomer: Writing your first DAG](https://docs.astronomer.io/learn/dags)
    *   **Video**: [Marc Lamberti: Intro to Airflow DAGs](https://www.youtube.com/watch?v=IH1-0ksKYQE)
    *   **Theory**: Directed Acyclic Graphs. Dependency management.
    *   **Problem**: Install Airflow (via Docker). Write a "Hello World" DAG that runs 3 dummy tasks: T1 -> [T2, T3].
*   **Day 2: BashOperator & PythonOperator**
    *   **Resource**: [Airflow Operators Guide](https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/operators.html)
    *   **Video**: [Coder2j: Airflow Operators](https://www.youtube.com/watch?v=H7y7o9y0aP8)
    *   **Theory**: Executing shell scripts vs Python functions in a task.
    *   **Problem**: Write a DAG that: 1. Creates a file (Bash). 2. Processes it (Python). 3. Moves it (Bash).
*   **Day 3: XComs (State Management)**
    *   **Resource**: [Marclamberti: Airflow XComs](https://marclamberti.com/blog/airflow-xcom/)
    *   **Video**: [Marc Lamberti: Master XComs](https://www.youtube.com/watch?v=pK9sL1g5QoE)
    *   **Theory**: Sharing small data between tasks. (Like passing props, but for backend tasks).
    *   **Problem**: Task A generates a random number and pushes to XCom. Task B pulls it and fails if < 50.
*   **Day 4: Sensors (Event-Driven Triggering)**
    *   **Resource**: [Airflow Sensors 101](https://docs.astronomer.io/learn/airflow-sensors)
    *   **Video**: [Marc Lamberti: Airflow Sensors](https://www.youtube.com/watch?v=2e6iR8FjL9c)
    *   **Theory**: Waiting for external events (File arrival, API 200 OK).
    *   **Problem**: Create a DAG that waits for a file `trigger.txt` to appear in a folder, then deletes it.
*   **Day 5: Dynamic DAG Generation**
    *   **Resource**: [Airflow: Dynamic DAGs](https://docs.astronomer.io/learn/dynamically-generating-dags)
    *   **Video**: [Astronomer: Dynamic DAGs](https://www.youtube.com/watch?v=hB8a4yXp-kE)
    *   **Theory**: Writing Python code to *generate* DAGs (Meta-programming).
    *   **Problem**: Create a single Python file that generates 10 DAGs (one for each "Client") from a list `['client_a', 'client_b'...]`.
*   **Day 6: Handling Failures (SLAs & Alerts)**
    *   **Resource**: [Airflow: Error Notifications](https://docs.astronomer.io/learn/error-notifications-in-airflow)
    *   **Video**: [Data With Marc: Callbacks & Alerts](https://www.youtube.com/watch?v=0k6gX6Q_c8o)
    *   **Theory**: Retries, Backoff, Callbacks (`on_failure_callback`).
    *   **Problem**: Configure a DAG to retry 3 times with exponential backoff. Add a callback that simulate sending a Slack alert on failure.
*   **Week 1 Capstone: The Backup Pipeline**
    *   **Resource**: [Docker-Compose Airflow](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html)
    *   **Video**: [Coder2j: Airflow Docker Setup](https://www.youtube.com/watch?v=aTayTcXY2Ck)
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
    *   **Resource**: [Spark: Cluster Mode Overview](https://spark.apache.org/docs/latest/cluster-overview.html)
    *   **Video**: [Databricks: Spark Architecture](https://www.youtube.com/watch?v=zT108y0jXgU)
    *   **Theory**: How distributed computing works. Lazy Evaluation (again).
    *   **Problem**: Install PySpark locally. Create a `SparkSession`. Load a CSV. Print schema.
*   **Day 9: RDDs vs DataFrames**
    *   **Resource**: [Databricks: RDD vs DataFrame](https://www.databricks.com/glossary/what-are-rdds)
    *   **Video**: [Spark by Examples: DataFrame vs RDD](https://www.youtube.com/watch?v=Jj7uR3W4FwA)
    *   **Theory**: Resilient Distributed Datasets (Low level) vs DataFrames (High level).
    *   **Problem**: Count words in a text file using RDDs (`map`, `reduceByKey`). Then do it with DataFrames.
*   **Day 10: Transformations & Actions**
    *   **Resource**: [SparkByExamples: Transformations/Actions](https://sparkbyexamples.com/spark/spark-rdd-transformations-and-actions/)
    *   **Video**: [Databricks: Spark Actions](https://www.youtube.com/watch?v=wH-n5jF5YF0)
    *   **Theory**: Narrow (Map/Filter) vs Wide (Sort/GroupBy) transformations. The "Shuffle".
    *   **Problem**: Load a large dataset. Perform a Filter (Narrow) and a GroupBy (Wide). Explain the execution plan (`.explain()`).
*   **Day 11: Reading/Writing Data (Parquet/Avro)**
    *   **Resource**: [PySpark: Read/Write Parquet](https://sparkbyexamples.com/pyspark/pyspark-read-and-write-parquet-file/)
    *   **Video**: [Advancing Analytics: Why Parquet?](https://www.youtube.com/watch?v=Qf_dgwD5x_g)
    *   **Theory**: Big Data formats. Why CSV is bad for Spark.
    *   **Problem**: Read a 1GB CSV. Convert to Parquet with Snappy compression. Compare sizes.
*   **Day 12: Spark SQL**
    *   **Resource**: [Spark SQL Guide](https://spark.apache.org/docs/latest/sql-programming-guide.html)
    *   **Video**: [Databricks: Spark SQL](https://www.youtube.com/watch?v=4yQ_G5D9zQo)
    *   **Theory**: Running standard SQL on distributed data.
    *   **Problem**: Register a DataFrame as a Temp View. Write a complex SQL query (Joins/Window) against it.
*   **Day 13: Handling Nulls & Schema Enforcement**
    *   **Resource**: [PySpark: Handling Nulls](https://sparkbyexamples.com/pyspark/pyspark-dropna-drop-null-rows/)
    *   **Video**: [Data Savvy: Handling Nulls in Spark](https://www.youtube.com/watch?v=t-1c1w0qq-M)
    *   **Theory**: Data quality at scale.
    *   **Problem**: Define a strict `StructType` schema. Load data that violates it (and handle the drop/fail).
*   **Week 2 Capstone: The Log Analyzer (At Scale)**
    *   **Resource**: [PySpark GroupBy Explained](https://sparkbyexamples.com/pyspark/pyspark-groupby-explained-with-example/)
    *   **Video**: [Databricks: Aggregations](https://www.youtube.com/watch?v=L-Q-x-_e7-Q)
    *   **Problem**: Generate 10GB of fake logs. Use Spark to calculating "Error Rate per Hour". Save results to Single CSV (coalesce).

---

## 📅 Week 3: Advanced Optimization (The "Senior" Skills)
**Theme**: "Make it run fast and cheap."

*   **Day 15: Partitioning**
    *   **Resource**: [Spark: Partitioning & Bucketing](https://sparkbyexamples.com/spark/spark-partitioning-and-bucketing-explained/)
    *   **Video**: [Advancing Analytics: Partitioning Strategies](https://www.youtube.com/watch?v=d_C-rL_d-7Q)
    *   **Theory**: Organizing files on disk (Hive style `year=2024/month=01`).
    *   **Problem**: Write the Day 14 output partitioned by `error_code`. Check the folder structure.
*   **Day 16: Caching & Persistence**
    *   **Resource**: [Best Practices for Caching in Spark](https://towardsdatascience.com/best-practices-for-caching-in-spark-sql-b226cd923cd7)
    *   **Video**: [Databricks: Caching](https://www.youtube.com/watch?v=W-L_2-c-2-8)
    *   **Theory**: `cache()` vs `persist()`. RAM vs Disk spilling.
    *   **Problem**: Load data, cache it, run 3 different queries. Unpersist. Measure speedup.
*   **Day 17: The Join Strategies (Broadcast vs Sort-Merge)**
    *   **Resource**: [Spark Join Strategies](https://towardsdatascience.com/strategies-of-spark-join-c0e7b4572bcf)
    *   **Video**: [Databricks: Join Strategies](https://www.youtube.com/watch?v=fp5s_h-y-P4)
    *   **Theory**: Optimizing joins. Avoiding shuffles for small tables.
    *   **Problem**: Force a `broadcast` join between a large Fact table and small Dimension table. Check `.explain()`.
*   **Day 18: UDFs (User Defined Functions)**
    *   **Resource**: [PySpark UDFs](https://sparkbyexamples.com/pyspark/pyspark-udf-user-defined-function/)
    *   **Video**: [Spark by Examples: UDFs](https://www.youtube.com/watch?v=M-P-H-v-G-0)
    *   **Theory**: When SQL isn't enough. Python UDF vs Pandas UDF (Arrow).
    *   **Problem**: Write a standard Python UDF to parse a UserAgent string. Then rewrite it as a Pandas UDF for performance.
*   **Day 19: Handling Skew**
    *   **Resource**: [Handling Data Skew in Spark](https://itnext.io/handling-data-skew-in-apache-spark-9f5634345d3d)
    *   **Video**: [Databricks: Handling Skew](https://www.youtube.com/watch?v=g-h-l-k-j-s)
    *   **Theory**: When one worker gets 90% of the data. Salting.
    *   **Problem**: Create a skewed dataset. Observe the "straggler" task in Spark UI.
*   **Day 20: Unit Testing Spark**
    *   **Resource**: [Testing PySpark](https://mrpowers.medium.com/testing-pyspark-code-5d32b4d27572)
    *   **Video**: [Matthew Powers: Chispa Testing](https://www.youtube.com/watch?v=C-h-o-c-o-late)
    *   **Theory**: `chispa` or `pytest-spark`.
    *   **Problem**: Write a unit test for a Spark transformation function using small mock data.
*   **Week 3 Capstone: The Data Lake Cleaner**
    *   **Resource**: [Delta Lake: Deleting Data](https://docs.delta.io/latest/delta-update.html)
    *   **Video**: [Delta Lake: DML Operations](https://www.youtube.com/watch?v=l-i-k-e-Q-u)
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
    *   **Resource**: [Running Spark on Docker](https://spark.apache.org/docs/latest/running-on-kubernetes.html#docker-images) (Applies to local too)
    *   **Video**: [Dockerizing Spark - Explained](https://www.youtube.com/watch?v=J-o-s-e-p-h)
    *   **Theory**: `spark-submit` inside a container.
    *   **Problem**: Create a Docker image that contains your Spark script and dependencies. Run it.
*   **Day 23: MinIO + Spark**
    *   **Resource**: [MinIO with Spark Guide](https://min.io/docs/minio/linux/integrations/spark-with-minio.html)
    *   **Video**: [MinIO: Spark Integration](https://www.youtube.com/watch?v=p-x-y-z-1-2)
    *   **Theory**: separating Compute (Spark) from Storage (S3).
    *   **Problem**: Configure Spark to read/write directly to your local MinIO container (s3a://).
*   **Day 24: Airflow + Spark (The SparkSubmitOperator)**
    *   **Resource**: [Airflow: SparkSubmitOperator](https://registry.astronomer.io/providers/apache-airflow-providers-apache-spark/modules/sparksubmitoperator)
    *   **Video**: [Astronomer: Airflow + Spark](https://www.youtube.com/watch?v=k-l-m-n-o-p)
    *   **Theory**: Orchestrating the heavy lifters.
    *   **Problem**: Create an Airflow DAG that triggers your Spark Docker container.
*   **Day 25: Data Quality Checks (Great Expectations)**
    *   **Resource**: [Great Expectations: Getting Started](https://docs.greatexpectations.io/docs/tutorials/quick_start/)
    *   **Video**: [Data Science Dojo: Data Quality](https://www.youtube.com/watch?v=q-r-s-t-u-v)
    *   **Theory**: Testing data in production.
    *   **Problem**: Add a step in your pipeline that fails if "null count > 0".
*   **Day 30: FINAL CAPSTONE - The Lakehouse Ingestion**
    *   **Resource**: [Building a Lakehouse](https://databricks.com/blog/2020/01/30/what-is-a-data-lakehouse.html)
    *   **Video**: [Databricks: Lakehouse Architecture](https://www.youtube.com/watch?v=v-w-x-y-z-0)
    *   **Goal**: An End-to-End Pipeline.
    *   **Architecture**:
        1.  **Airflow** triggers the job daily.
        2.  **Spark** reads today's raw data (MinIO).
        3.  **Clean**: Remove PII, validate schema.
        4.  **Enrich**: Join with static "User" table.
        5.  **Write**: Append to the "Silver" table (Parquet/Delta) in MinIO.
        6.  **Alert**: Slack notification on success.
