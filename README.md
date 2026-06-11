# 🚀 EazyBank Microservices: Kubernetes & Helm Orchestration

[![Kubernetes](https://img.shields.io/badge/Kubernetes-K8s-326ce5?style=for-the-badge&logo=kubernetes)](https://kubernetes.io/)
[![Helm](https://img.shields.io/badge/Helm-v3-0f1689?style=for-the-badge&logo=helm)](https://helm.sh/)
[![Observability](https://img.shields.io/badge/Kube_Prometheus-Stack-purple?style=for-the-badge&logo=prometheus)](https://prometheus.io/)
[![DevOps](https://img.shields.io/badge/DevOps-Infrastructure_as_Code-black?style=for-the-badge)]()

This repository represents of the EazyBank Microservices project (focusing on Section 16: Deep Dive on Helm). It demonstrates the transition from local Docker Compose environments to a robust, production-ready **Kubernetes** cluster using **Helm** as the package manager.

---

## 🏗️ Helm Infrastructure & Chart Architecture

To avoid massive duplication of Kubernetes manifests (YAML files) and apply the **DRY (Don't Repeat Yourself)** principle, this project utilizes advanced Helm chart features:

### 1. `eazybank-common` (The Umbrella/Library Chart)
A centralized base chart containing generic K8s templates (`Deployment`, `Service`, `ConfigMap`). All individual microservices inherit their core structure from this common chart, drastically reducing boilerplate code and simplifying cluster-wide updates.

### 2. `eazybank-services`
Contains individual, lightweight charts for each microservice (`accounts`, `cards`, `loans`, `gatewayserver`, `eurekaserver`, `configserver`, `message`). These charts primarily supply specific `values.yaml` to override the `eazybank-common` templates.

### 3. `environments` (Environment-Specific Deployments)
Manages dynamic values for different deployment lifecycle stages:
* `dev-env`: Fast-iteration configurations.
* `qa-env`: Testing and integration configurations.
* `prod-env`: High-availability, production-grade configurations.

### 4. Third-Party Infrastructure Charts
Instead of reinventing the wheel, this project integrates industry-standard Bitnami and Grafana Helm charts for infrastructure:
* **Kafka**: Distributed event streaming.
* **Keycloak**: IAM and OAuth2 provider.
* **Kube-Prometheus / Grafana Stack**: Complete Kubernetes-native observability (Metrics, Logs via Loki, Traces via Tempo).

---

## 🛠️ Helm Commands Cheatsheet

Below are the core commands utilized to manage the cluster lifecycle in this repository:

| Command | Description |
|---------|-------------|
| `helm create [NAME]` | Create a default chart with the given name |
| `helm template [NAME] [CHART]` | Render chart templates locally along with the values to verify YAML structure |
| `helm dependencies build` | Recompile and update the chart dependencies |
| `helm install [NAME] [CHART]` | Install the given helm chart into the K8s cluster |
| `helm upgrade [NAME] [CHART]` | Upgrades a specified release to a new version of a chart |
| `helm history [NAME]` | Display historical revisions for a given release |
| `helm rollback [NAME] [REVISION]` | Roll back a release to a previous revision |
| `helm list` | Lists all of the helm releases inside a K8s cluster |
| `helm uninstall [NAME]` | Uninstall all resources associated with a given release |

---
👨‍💻 **Developed & Maintained by [Mohamed Magdy](https://github.com/MOhamedMaGdy20820)**