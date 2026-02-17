# Month 5 Project: Real-Time Fraud Detection
**Goal:** Process data in motion (< 500ms latency).
**Tech:** Kafka (Redpanda), Flink (or Faust), Redis.

---

## 📅 Week 1: The Event Bus (Kafka/Redpanda)
*   **Day 1**: **Setup**. Spin up Redpanda (simpler Kafka) and Redpanda Console via Docker.
*   **Day 2-4**: **The Producer**.
    *   Write a Python script that simulates Credit Card transactions.
    *   Inject artificial anomalies (e.g., massive amount, 2 transactions in different countries instantly).
    *   Push to topic `transactions`.
*   **Day 5-7**: **The Consumer**.
    *   Write a simple consumer to read messages and print them. Verify throughput.

## 📅 Week 2: State & Enrichment (Redis)
*   **Day 8-10**: **The Feature Store**.
    *   Populate Redis with "User Profiles" (e.g., `user_123_avg_spend: 50.00`).
*   **Day 11-14**: **Enrichment Service**.
    *   Modify your consumer to lookup User History from Redis for every transaction.
    *   Calculate: `deviation = current_amount / avg_spend`.

## 📅 Week 3: Stream Processing (The logic)
*   **Day 15-20**: **The Processor (Flink/Faust)**.
    *   Implement Windowing (e.g., "Count transactions in last 5 minutes").
    *   Rules Engine:
        *   IF `amount > 5 * avg_spend` -> FRAUD.
        *   IF `location` != `last_location` AND `time_diff < 1 hour` -> FRAUD.
    *   Push results to two topics: `transactions_approved` and `transactions_fraud`.

## 📅 Week 4: Action & Monitoring
*   **Day 21-25**: **The Alerting System**.
    *   Consumer on `transactions_fraud` that sends a message to Slack/Discord webhook.
*   **Day 26-29**: **Real-Time Dashboard**.
    *   Use Grafana with a Kafka datasource to plot "Fraud Rate" in real-time.
*   **Day 30**: **Stress Test**.
    *   Ramp up the producer to 1000 events/sec. Measure latency. Tune the system.
