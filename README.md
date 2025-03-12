# End-to-End Data Engineering Pipeline

## Introduction
This project demonstrates a complete **End-to-End Data Engineering Pipeline** for real-time data processing. It integrates multiple technologies including **Apache Kafka, Apache Spark, Apache Airflow, PostgreSQL, Cassandra, and Docker** to handle data ingestion, transformation, and storage.

## Architecture Overview
The system is composed of several components that work together:

1. **Data Source** – Uses the `randomuser.me` API to fetch and simulate user data.
2. **Apache Airflow** – Orchestrates data ingestion and transformation.
3. **Apache Kafka & Zookeeper** – Facilitates real-time data streaming.
4. **Apache Spark** – Processes streamed data and loads it into the database.
5. **PostgreSQL** – Stores raw ingested data.
6. **Apache Cassandra** – Stores processed data for scalable analytics.
7. **Docker** – Containerizes all components for easy deployment.

![Data engineering architecture](https://github.com/user-attachments/assets/f3d4b867-8206-42c3-9f87-3a37d37fcbf9)

## Technology Stack
- **Apache Kafka** – Message broker for real-time streaming.
- **Apache Spark** – Streaming and batch data processing.
- **Apache Cassandra** – Scalable NoSQL database for processed data.
- **PostgreSQL** – SQL database for raw data storage.
- **Apache Airflow** – Workflow orchestration and task scheduling.
- **Docker & Docker Compose** – Containerization for easy deployment.

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/mohamedmostafam0/End-to-end-DE-pipeline.git
cd End-to-end-DE-pipeline
```
### 2. Set Up Environment Variables
Create a .env file in the root directory and define the required environment variables:
```bash
POSTGRES_USER=airflow
POSTGRES_PASSWORD=airflow
POSTGRES_DB=airflow

KAFKA_BROKER=broker:29092
KAFKA_TOPIC=users_created

CASSANDRA_USERNAME=cassandra
CASSANDRA_PASSWORD=cassandra
```
### 3. Run the Pipeline
Ensure Docker is running, then start the pipeline:
```bash
docker compose up -d
```
### 4. Check Running Containers
Verify that all services are up and running:
```bash
docker ps
```

## Project Structure
```
End-to-end-DE-pipeline/
│── dags/                     # Apache Airflow DAGs for orchestrating workflows
│── script/                   # Entry point scripts for Airflow containers
│── spark_stream.py           # Apache Spark streaming job
│── docker-compose.yml        # Docker configuration for all services
│── requirements.txt          # Python dependencies
│── README.md                 # Project documentation
```


## How It Works
1. **Airflow DAGs** extract data from the API and insert it into PostgreSQL.
2. **Kafka Producer** picks up new records and streams them to Kafka topics.
3. **Kafka Consumer (Spark Streaming Job)** reads the real-time data.
4. **Spark processes** the data and stores it in Cassandra.
5. **Cassandra stores processed records** for scalable analytics.

## Monitoring
- **Kafka UI**: [http://localhost:9021](http://localhost:9021)
- **Airflow UI**: [http://localhost:8080](http://localhost:8080)
- **Spark Master UI**: [http://localhost:9090](http://localhost:9090)
- **Schema Registry**: [http://localhost:8081](http://localhost:8081)

## Next Step(s)
- Deploy to **Kubernetes** for production-scale execution.




