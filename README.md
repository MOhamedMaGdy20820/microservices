# 🏦 EazyBank:Microservices Architecture (Phase 1)

[![Java Version](https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=openjdk)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.1.3-green?style=for-the-badge&logo=springboot)](https://spring.io/projects/spring-boot)
[![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-Event_Driven-black?style=for-the-badge&logo=apachekafka)](https://kafka.apache.org/)
[![Docker Compose](https://img.shields.io/badge/Docker-Compose_Ready-blue?style=for-the-badge&logo=docker)](https://www.docker.com/)

This repository represents **Phase 1** of the EazyBank ecosystem. It showcases a fully functional, event-driven microservices architecture containerized and orchestrated locally using **Docker Compose**, prior to the Kubernetes migration.

---

## 🏛️ System Architecture (Dockerized Environment)

In this phase, the ecosystem relies on **Spring Cloud Netflix Eureka** for service discovery and **Apache Kafka** for asynchronous messaging.

* **`configserver`**: Centralized configuration management.
* **`eurekaserver`**: Client-side service discovery and registry.
* **`gatewayserver`**: Edge server handling routing, rate limiting, and JWT validation.
* **`accounts`, `cards`, `loans`**: Core business domain services.
* **`message`**: Event-driven worker consuming async payloads from Kafka.

---

## 🛠️ Tech Stack & Key Implementations

### 1. Backend & Routing
* **Java 17 & Spring Boot 3.x**: Core development framework.
* **Spring Cloud Gateway & OpenFeign**: API Edge routing and declarative synchronous REST calls.
* **Resilience4j**: Circuit breaker and retry mechanisms ensuring fault tolerance.

### 2. Event-Driven Messaging
* **Apache Kafka & RabbitMQ**: High-performance message brokers.
* **Spring Cloud Stream**: Abstracted reactive event streaming bridging the `accounts` and `message` microservices.

### 3. Security & IAM
* **Keycloak**: OpenID Connect (OIDC) provider issuing JWTs.
* **Spring Security OAuth2**: Protecting downstream APIs and the Gateway.

### 4. Full-Stack Observability
* **Metrics**: Micrometer + Prometheus.
* **Tracing**: OpenTelemetry Java Agent + Grafana Tempo.
* **Logging**: Grafana Loki + Promtail.
* **Visualization**: Grafana Dashboards.

### 5. Local Orchestration
* **Jib Maven Plugin**: Dockerless container image building.
* **Docker Compose**: Multi-environment orchestration blueprints (`dev`, `qa`, `prod`).

---

## 🚀 How to Run Locally

1.  **Build the Images:**
    ```bash
    ./mvnw clean install jib:dockerBuild
    ```
2.  **Spin Up the Infrastructure (Kafka, Keycloak, DBs):**
    ```bash
    cd docker-compose/default
    docker-compose up -d
    ```
3.  **Spin Up Observability Stack:**
    ```bash
    cd docker-compose/observability
    docker-compose up -d
    ```

---
👨‍💻 **Developed by [Mohamed Magdy](https://github.com/MOhamedMaGdy20820)**