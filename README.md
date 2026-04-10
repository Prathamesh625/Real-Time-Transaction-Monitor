# Real‑Time Transaction Monitor

A Java‑based backend that ingests transactions and applies rule‑based checks to flag suspicious activity in near real time.

## Tech Used
- Java / Spring Boot (REST API)
- PostgreSQL / MySQL (transactions + alerts)
- Kafka (optional, for streaming events)

## Features
- `POST /api/transactions` – ingest transaction (user ID, amount, currency, timestamp, category).
- Rule‑based detection:
  - High‑value transactions (e.g., > 10,000 INR),
  - Multiple large transactions in a short window.
- `GET /api/alerts` – list all flagged transactions.
- `GET /api/stats` – basic stats (e.g., today’s flagged count).

## How to Run
1. Clone:
   ```bash
   git clone https://github.com/your-username/transaction-monitor.git
   cd transaction-monitor
   ```
2. Create DB and update `application.yml`.
3. Run:
   ```bash
   ./mvnw spring-boot:run
   ```
4. Test:
   ```bash
   curl -X POST http://localhost:8080/api/transactions \
     -H "Content-Type: application/json" \
     -d '{"userId":"user1","amount":12000,"currency":"INR","timestamp":"2026-04-10T07:00:00","category":"transfer"}'
   ```
