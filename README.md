# 🚀 Fullstack Chat App – DevOps Deployment

[![GitHub Repo](https://img.shields.io/badge/GitHub-JyotirajM-blue?logo=github)](https://github.com/JyotirajM/Fullstack-ChatApp)

## 💡 Overview

This is a **production-ready fullstack chat application** deployed using modern DevOps tools. It features real-time messaging and includes containerization, orchestration, monitoring, and CI/CD pipelines.

> Built & deployed by **Jyotiraj Aditinandan Mahanta**

---

## 🛠 Tech Stack

- **Frontend:** React, TailwindCSS, DaisyUI
- **Backend:** Node.js, Express, Socket.io
- **Database:** MongoDB
- **State Management:** Zustand

---

## ⚙️ DevOps & Cloud Tooling

| Purpose              | Tool/Tech             |
|----------------------|-----------------------|
| Containerization     | Docker                |
| Orchestration        | Kubernetes            |
| Monitoring           | Prometheus + Node Exporter |
| Web Server           | Nginx                 |
| CI/CD Pipeline       | Jenkins, GitHub Actions |
| Version Control      | Git, GitHub           |

---

## 📦 Project Structure

```bash
Fullstack-ChatApp/
├── backend/
│   └── Dockerfile
├── frontend/
│   └── Dockerfile
├── k8s/
│   └── all K8s manifests (deployment, service, ingress)
├── prometheus/
│   └── prometheus.yml (scrape configs)
└── docker-compose.yml
```
## 🚀 Local Setup

🐳 Docker Compose (Quick Local Launch)
```bash
git clone https://github.com/JyotirajM/Fullstack-ChatApp.git
cd Fullstack-ChatApp
docker-compose up -d --build
```
- Frontend: http://localhost:5173

- Backend API: http://localhost:5001

- MongoDB: localhost:27017

## ☸️ Kubernetes Setup
```bash
kubectl apply -f k8s/
```
Includes:

- `Deployment` & `Service` for frontend and backend

- `ConfigMap` and `Secrets` (if needed)

- Ingress support (Nginx)

- Prometheus metrics endpoint

## 📊 Prometheus Monitoring
- Prometheus is configured to scrape backend `metrics` exposed via /metrics endpoint (using `prom-client` Node.js lib).

- Node Exporter used for infrastructure metrics.

To access Prometheus:

```bash
kubectl port-forward svc/prometheus 9090:9090
```
Then visit: http://localhost:9090

## 🔁 CI/CD Pipelines
### ✅ GitHub Actions
- Auto-build Docker images

- Push to DockerHub

- Lint, test, and deploy on `main` push

### ✅ Jenkins (Self-hosted)
Declarative Jenkins pipeline with steps:

- Checkout repo

- Docker build & push

- Deploy via `kubectl` or `helm`

Pipelines are configured in `.github/workflows`/ and `Jenkinsfile`

## 🧪 Future Enhancements
 - Group Chat Support

 - Media Upload

 - Redis for Caching

 - Helm Charts for Production

 - Grafana Dashboards
## 🙌 Connect
Created & maintained by Jyotiraj Aditinandan Mahanta

📫 GitHub
