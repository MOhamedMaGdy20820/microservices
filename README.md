# 🚀 EazyBank Microservices Architecture

[![Java Version](https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=openjdk)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.1.3-green?style=for-the-badge&logo=springboot)](https://spring.io/projects/spring-boot)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue?style=for-the-badge&logo=docker)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-K8s-326ce5?style=for-the-badge&logo=kubernetes)](https://kubernetes.io/)

This repository contains my complete journey and project files for the **"Master Microservices with Spring Boot, Docker, Kubernetes"** course. It demonstrates how to create enterprise and production-ready Microservices using a modern cloud-native stack.

🎓 **[Click Here to View My Course Certificate](https://www.udemy.com/certificate/UC-518f9050-0b52-478b-accf-83588e37e33b/)**

🔗 **[Course Link on Udemy](https://www.udemy.com/share/104Pem3@D9Lkkp2RQs0aKlZY4RonnaHa45Pfk-7WwR0cacqF-C4IAl5XhTkbmtfZl_yZMjwgDg==/)**

---

## 📚 My Learning Journey (Course Sections)
This repository reflects my progression through the following advanced concepts:
* **Section 1-3:** Microservices Architecture basics, boundary identification, and building with Spring Boot.
* **Section 4-6:** Docker containerization, 15-Factor methodology, and centralized Configuration Management.
* **Section 7-9:** MySQL DB integration, Service Discovery (Eureka), and API Gateway routing.
* **Section 10-12:** Resilience strategies (Circuit Breakers), Full-stack Observability, and robust Security.
* **Section 13-14:** Event-Driven architectures using RabbitMQ, Apache Kafka, and Spring Cloud Stream.
* **Section 15-18:** Kubernetes Container Orchestration, Helm charts, and deploying to Cloud K8s clusters.
* **Section 19-20:** K8s Ingress, Istio Service Mesh, mTLS, and project completion.

---

## 🛠️ Tech Stack & Tools Cheatsheet
Below is a consolidated reference of the commands and tools I used and mastered throughout this project.

### 1. Maven Commands
| Command | Description |
|---------|-------------|
| `mvn clean install -Dmaven.test.skip=true` | Generate a jar inside the target folder |
| `mvn spring-boot:run` | Start a Spring Boot maven project |
| `mvn spring-boot:build-image` | Generate a Docker image using Buildpacks (No Dockerfile) |
| `mvn compile jib:dockerBuild` | Generate a Docker image using Google Jib (No Dockerfile) |

### 2. Docker Commands
| Command | Description |
|---------|-------------|
| `docker build . -t eazybytes/accounts:s4` | Generate a Docker image based on a Dockerfile |
| `docker run -p 8080:8080 eazybytes/accounts:s4` | Start a Docker container |
| `docker images` / `docker ps -a` | List all images / List all containers (running & stopped) |
| `docker push docker.io/eazybytes/accounts:s4` | Push an image to a registry |
| `docker compose up` / `docker compose down` | Start / Stop and remove containers based on Compose file |

### 3. Kubernetes (K8s) Commands
| Command | Description |
|---------|-------------|
| `kubectl apply -f filename` | Create deployment/service/configmap from YAML |
| `kubectl get all` | Get all components inside the cluster |
| `kubectl get pods` / `services` / `nodes` | Get details of pods, services, or nodes |
| `kubectl scale deployment accounts-deployment --replicas=1`| Set the number of replicas for a deployment |
| `kubectl rollout undo deployment gatewayserver-deployment --to-revision=1`| Rollback to a previous revision |

### 4. Helm Commands
| Command | Description |
|---------|-------------|
| `helm create [NAME]` | Create a default chart with the given name |
| `helm install [NAME] [CHART]` | Install the given helm chart into the K8s cluster |
| `helm upgrade [NAME] [CHART]` | Upgrades a specified release to a new version |
| `helm rollback [NAME] [REVISION]` | Roll back a release to a previous revision |

---

## 🔗 Useful References & Documentation
<details>
<summary>Click to expand the list of resources used in this project</summary>

* **Frameworks & Patterns:** [Spring Boot](https://start.spring.io) | [Spring Cloud](https://spring.io/projects/spring-cloud) | [DTO Pattern](https://martinfowler.com/eaaCatalog/dataTransferObject.html)
* **API & Mapping:** [Open API](https://www.openapis.org/) | [Spring Doc](https://springdoc.org/) | [Map Struct](https://mapstruct.org/)
* **Containerization & Cloud:** [Docker](https://www.docker.com) | [Google Jib](https://github.com/GoogleContainerTools/jib) | [Buildpacks](https://buildpacks.io)
* **Architecture:** [Twelve-Factor App](https://12factor.net) | [GCP SDK](https://cloud.google.com/sdk/docs/install)
* **Messaging & Data:** [RabbitMQ](https://www.rabbitmq.com) | [Apache Kafka](https://kafka.apache.org)
* **Resilience & Gateway:** [Resilience4j](https://resilience4j.readme.io) | [Stripe RateLimiter](https://stripe.com/blog/rate-limiters)
* **Observability:** [Grafana & Loki](https://grafana.com/docs/loki/latest/get-started/quick-start/) | [Prometheus](https://prometheus.io/) | [OpenTelemetry](https://opentelemetry.io/)
* **Security:** [Keycloak](https://www.keycloak.org/)
* **Kubernetes & Mesh:** [Helm](https://helm.sh) | [K8s Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) | [Istio (Service mesh)](https://istio.io)
</details>

---
👨‍💻 **Developed & Maintained by [Mohamed Magdy](https://github.com/MOhamedMaGdy20820)**