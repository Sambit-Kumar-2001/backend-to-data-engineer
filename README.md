# 🚀 Backend to Data & AI Engineer (The Transition)

> "Leveraging 3+ Years of Backend Experience to Master Data at Scale."

Welcome. I am a **Senior Backend Engineer** (Stack: .NET Core, NestJS, AWS, Docker) documenting my transition to **Data & AI Engineering**. 
Because I already know how to build systems (Linux, Git, Docker, Cloud), this roadmap skips the "basics" and focuses purely on **Data, Scale, and AI**.

---

## ⚡ The Strategy: "The Delta"
I am not starting from zero. I am focusing on the "Delta" between App Dev and Data Eng:

| I Know (Backend) | I Need to Master (Big Data) |
| :--- | :--- |
| **C# / TypeScript** | **Python** (Pandas, Polars, PySpark) |
| **PostgreSQL (OLTP)** | **Warehousing (OLAP)**, Partitioning, Columnar Storage |
| **RabbitMQ** | **Kafka** (Streaming, Log compaction) |
| **Docker / Linux** | **Kubernetes / Spark Clusters** |
| **AWS EC2** | **AWS EMR, Athena, Glue** |

---

## 🗺️ The Acceleration Roadmap

### Phase 1: The Data Stack (Months 1-3)
*   [ ] **Month 1: Python for Data & Advanced SQL**
    *   *Goal*: Stop writing "C# in Python". Master vectorization (Pandas/Polars) and complex SQL (Window functions, CTEs).
*   [ ] **Month 2: Orchestration & Distributed Compute**
    *   *Goal*: Move from "Crons" to **Airflow/Prefect**. Move from "Loops" to **Spark**.
*   [ ] **Month 3: The Modern Data Stack**
    *   *Goal*: dbt (Data Build Tool), Data Lakes (Iceberg/Delta), and Cloud Native Data (AWS).

### Phase 2: Building Systems (Months 4-6)
*   [ ] **Month 4**: The Lakehouse Project (End-to-End Batch)
*   [ ] **Month 5**: Real-Time Systems (Streaming)
*   [ ] **Month 6**: AI Engineering (RAG & LLMs)

---

## 📅 Daily Learning Log & Curriculum

Detailed Breakdown for each month:

### Phase 1: The Delta (Skills)
*   **Month 1**: [🐍 Python for Data Engineering (Mastery Guide)](./month1_python_mastery.md)
*   **Month 2**: [⚙️ Orchestration & Distributed Compute (Airflow/Spark)](./month2_orchestration_and_compute.md)
*   **Month 3**: [☁️ The Modern Data Stack (dbt, Cloud, Warehousing)](./month3_modern_data_stack.md)

### Phase 2: The Projects (Building)
*   **Month 4**: [🏗️ Project 1: The Open Source Lakehouse](./month4_project_lakehouse.md)
*   **Month 5**: [⚡ Project 2: Real-Time Fraud Detection](./month5_project_realtime.md)
*   **Month 6**: [🤖 Project 3: Enterprise RAG Pipeline](./month6_project_ai_rag.md)

---

### Month 1 Sample Log (See full guide above)
| Day | Topic | Old Habit (Backend) | New Habit (Data) | Code |
| :--- | :--- | :--- | :--- | :--- |
| **01** | Python Syntax | `const x = new List()` | `x = [1, 2, 3]` (List Comprehensions) | [Link](./day01) |
| **02** | Pandas/Polars | Looping through an array | Vectorized Operations (`df['col'] * 2`) | [Link](./day02) |
| **05** | Advanced SQL | Simple `SELECT` / ORM | Window Functions (`RANK() OVER...`) | [Link](./day05) |
| **10** | Data Modeling | 3NF (Normalization) | Star Schema (Denormalization for Reads) | [Notes](./day10) |

---

## 🏗️ Project Portfolio (Advanced)

### 1. **"The Open Source Lakehouse" (Architecture Focus)**
*   **The Challenge**: Experience with MinIO and Docker makes this perfect.
*   **Goal**: Build a multi-hop "Medallion" architecture.
*   **Tech Stack**: MinIO (Storage), Spark (Compute), dbt (Transformation), Trino (Serving).

### 2. **"Real-Time Fraud Detection Engine" (Velocity Focus)**
*   **The Challenge**: Replacing RabbitMQ with Kafka for high-throughput streaming.
*   **Goal**: Detect anomalies in millisecond latency.
*   **Tech Stack**: Kafka, Flink/Spark Streaming, Redis (Feature Store).

### 3. **"Enterprise RAG Pipeline" (AI Focus)**
*   **The Challenge**: Handling unstructured data (documents) instead of JSON.
*   **Goal**: A pipeline that creates a queryable "Brain" from internal docs.
*   **Tech Stack**: LangChain, Vector DB (Weaviate), Docker.

---

## 🛠️ My Tech Stack
*   **Languages**: Python (Learning), TypeScript, C#, SQL
*   **Infrastructure**: AWS (EC2, Lightsail), Docker, Linux
*   **Data Tools**: Spark, Airflow, Kafka, Postgres

---
*Documenting the journey from Backend to Big Data.*
