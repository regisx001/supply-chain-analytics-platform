# SupplyChain Analytics Platform

Event-Driven Supply Chain Monitoring, Data Processing & Operational Intelligence

## 1. Project Overview

SupplyChain Analytics Platform is an event-driven platform designed to monitor, analyze and optimize supply chain operations through real-time data processing and operational analytics.

The platform focuses on shipment management, warehouse operations, inventory movements and delivery performance. It collects operational data from different stages of the supply chain, processes business events asynchronously and transforms them into meaningful analytical information.

The objective is to provide logistics managers with better visibility into their operations, allowing them to identify delivery delays, monitor warehouse performance, detect inventory shortages and understand operational trends.

The platform combines backend engineering, distributed messaging, data engineering and container orchestration in a single business-oriented system.

## 2. Business Context

A logistics company manages shipments across multiple warehouses, transportation routes and delivery destinations.

Each operational activity generates information: shipments are created, goods are picked up, inventory is reserved, products arrive at warehouses and deliveries are completed.

When these operations are handled by disconnected systems, obtaining a consistent overview of the supply chain becomes difficult.

The SupplyChain Analytics Platform addresses this problem by introducing an event-driven architecture in which operational services publish business events that other components can consume independently.

This enables the platform to process operational information continuously and provide analytical insights without tightly coupling business services.

## 3. Core Business Capabilities

The platform focuses on three main operational domains.

Shipment Management

Manage shipment creation, assignment, tracking and lifecycle transitions. Monitor shipment statuses, expected delivery dates, actual delivery times and transportation progress.

Warehouse & Inventory Management

Manage warehouse information, product availability, inventory reservations and stock movements. Maintain inventory records and track incoming and outgoing goods.

Supply Chain Analytics

Analyze operational performance through shipment volume, delivery duration, delay rates, warehouse throughput, inventory turnover and transportation performance.

The analytical layer provides historical reports as well as near-real-time operational indicators.

## 4. System Architecture

The platform uses independent services with clearly defined responsibilities.

| Component                | Responsibility                           | Technology   |
| ------------------------ | ---------------------------------------- | ------------ |
| Shipment Service         | Shipment lifecycle and tracking          | FastAPI      |
| Inventory Service        | Warehouse inventory and stock movements  | FastAPI      |
| Analytics Service        | Analytical data and reporting APIs       | FastAPI      |
| Event Processing         | Business event validation and enrichment | Python       |
| Data Processing Pipeline | Streaming and batch analytics            | PySpark      |
| Message Broker           | Asynchronous event communication         | Apache Kafka |
| Persistence              | Operational and analytical data          | SQLite       |

Each backend service owns its own database. Services communicate through REST APIs where synchronous interactions are required and Kafka where asynchronous communication is more appropriate.

PySpark operates independently from the backend services and consumes event streams to perform data transformations and analytical aggregations.

## 5. Data Engineering Pipeline

The platform uses historical supply chain datasets as its initial source of business information.

Historical records provide information about orders, products, shipments, customers and delivery performance.

A dedicated event simulator transforms suitable historical records into simulated operational events, creating a continuous stream of shipment and inventory activities.

These events are published to Kafka and consumed by the data processing pipeline.

PySpark Structured Streaming processes the incoming data, performs transformations, calculates time-window aggregations and produces analytical results.

The platform also supports batch processing of historical datasets to identify long-term trends and operational patterns.

This creates two complementary analytical capabilities:

- Batch processing for historical analysis and reporting.
- Stream processing for continuous operational monitoring.

## 6. Technology Stack

| Domain              | Technologies               |
| ------------------- | -------------------------- |
| Backend Development | Python, FastAPI, Pydantic  |
| Database Access     | SQLAlchemy, SQLite         |
| Database Migrations | Alembic                    |
| Messaging           | Apache Kafka               |
| Data Engineering    | Apache Spark, PySpark      |
| Streaming           | Spark Structured Streaming |
| Containerization    | Docker, Docker Compose     |
| Orchestration       | Kubernetes, k3d            |
| CI/CD               | GitHub Actions             |
| Testing             | Pytest                     |

## 7. Infrastructure and Deployment

The platform is initially developed and tested using Docker Compose.

Once the individual services and event-processing pipelines are functional, the deployment environment is progressively migrated to Kubernetes using k3d.

The Kubernetes deployment covers application workloads, service discovery, internal networking, persistent storage, configuration management, health checks, scaling and application recovery.

GitHub Actions provides automated testing, Docker image building, image publishing and deployment workflows.

The deployment process is designed to be reproducible, version-controlled and easy to operate locally.

## 8. Engineering Objectives

The project is intended to demonstrate practical experience in several engineering disciplines.

Backend engineering involves designing independent services, implementing business rules, handling transactions, validating data and exposing reliable APIs.

Distributed systems engineering involves asynchronous communication, Kafka producers and consumers, message ordering, idempotency, retries and failure recovery.

Data engineering involves historical data ingestion, stream processing, event-time aggregation, data transformation and analytical pipelines.

Infrastructure engineering involves containerization, Kubernetes orchestration, persistent storage, deployment automation and application observability.

The emphasis is on understanding the entire system, implementing its components independently and making deliberate architectural decisions.

## 9. Expected Outcome

The final result will be a functional Supply Chain Analytics Platform capable of managing simulated logistics operations, processing operational events in real time and providing analytical insights into supply chain performance.

It will serve as an end-to-end demonstration of backend development, distributed systems, data engineering and Kubernetes deployment, supported by a realistic business use case and measurable technical requirements.
