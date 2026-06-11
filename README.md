# ☸️ EazyBank Microservices: Kubernetes Basics 

[![Kubernetes](https://img.shields.io/badge/Kubernetes-K8s-326ce5?style=for-the-badge&logo=kubernetes)](https://kubernetes.io/)
[![YAML](https://img.shields.io/badge/YAML-Manifests-red?style=for-the-badge&logo=yaml)](https://yaml.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.1.3-green?style=for-the-badge&logo=springboot)](https://spring.io/projects/spring-boot)

This repository branch represents **Section 15: Container Orchestration using Kubernetes**. It marks the critical transition from local Docker Compose environments to a declarative, distributed **Kubernetes (K8s)** cluster using standard YAML manifests (`Deployments`, `Services`, `ConfigMaps`).

---

## 🏗️ Deployment Strategy & Order

To ensure high availability and prevent startup failures due to missing dependencies, the Kubernetes manifests in this repository are strictly numbered. They must be applied to the cluster in the exact sequential order:

1. **`1_configmaps.yaml`**: Establishes cluster-wide environment variables and configuration properties required by the services.
2. **`2_keycloak.yml`**: Deploys the Identity and Access Management (IAM) server to handle OAuth2/OIDC authentication.
3. **`3_configserver.yml`**: Deploys the Spring Cloud Config Server (depends on Keycloak & ConfigMaps).
4. **`4_eurekaserver.yml`**: Deploys the Netflix Eureka Service Discovery Registry.
5. **`5_accounts.yml`**, **`6_loans.yml`**, **`7_cards.yml`**: The core business microservices (depend on Config Server, Eureka, and underlying databases).
6. **`8_gateway.yml`**: Deploys the Spring Cloud API Gateway as the unified edge router (depends on all backend services being up and registered).

---

## 🛠️ Kubernetes Commands Cheatsheet

Below are the essential `kubectl` commands used to deploy and manage this raw manifest architecture:

### Applying & Deploying
| Command | Description |
|---------|-------------|
| `kubectl apply -f kubernetes/` | Apply all YAML files in the directory at once |
| `kubectl apply -f kubernetes/1_configmaps.yaml` | Apply a specific YAML manifest |

### Monitoring & Inspecting
| Command | Description |
|---------|-------------|
| `kubectl get all` | Get all components (Pods, Services, Deployments, ReplicaSets) |
| `kubectl get pods` | List all running pods in the current namespace |
| `kubectl get services` | List all services and their exposed IP/Ports |
| `kubectl describe pod <pod-id>` | Get detailed lifecycle and event information for a specific pod |
| `kubectl logs -f <pod-id>` | Tail the live logs of a running pod for debugging |

### Scaling & Management
| Command | Description |
|---------|-------------|
| `kubectl scale deployment accounts-deployment --replicas=3`| Scale a specific microservice to handle more traffic |
| `kubectl delete -f kubernetes/` | Tear down the entire architecture based on the YAML definitions |

---

## 🚀 Evolution to Helm (Next Steps)
While raw YAML manifests are excellent for understanding Kubernetes primitives, they can lead to massive code duplication across environments.

**Next Step (Section 16):** Evolving this exact architecture into dynamic, reusable **Helm Charts** to apply the DRY (Don't Repeat Yourself) principle and manage environment-specific configurations (`dev`, `qa`, `prod`) effortlessly.

---
👨‍💻 **Developed & Maintained by [Mohamed Magdy](https://github.com/MOhamedMaGdy20820)**