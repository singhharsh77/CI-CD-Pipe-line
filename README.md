# CI/CD Pipe Line 🚀

This project demonstrates a **production-style containerized architecture**
using **Docker, Nginx, CI/CD**, and **high availability design principles**.

---
### 🧠 High-Level System Design (Before Code)
                           ┌───────────────────────┐
                           │        Users          │
                           └───────────┬───────────┘
                                       │
                                       ▼
                           ┌───────────────────────┐
                           │        NGINX          │
                           │ Reverse Proxy & LB    │
                           └───────────┬───────────┘
                 ┌─────────────────────┴─────────────────────┐
                 ▼                                           ▼
       ┌───────────────────────┐                 ┌───────────────────────┐
       │       Frontend        │                 │        Backend         │
       │   (React / Vue App)   │                 │   (Node / Java API)    │
       │   Stateless Service   │                 │   Stateless Service    │
       └───────────┬───────────┘                 └───────────┬───────────┘
                   │                                           │
                   │                                   ┌───────▼────────┐
                   │                                   │   Redis Cache   │
                   │                                   │ (In-Memory KV)  │
                   │                                   └───────┬────────┘
                   │                                           │
                   │                                   ┌───────▼────────┐
                   │                                   │   PostgreSQL    │
                   │                                   │    Database     │
                   │                                   │  (Persistent)  │
                   │                                   └────────────────┘
---
### 📁 Repository Structure

CI/CD Pipe-Line/
│<br>
├── docker-compose.yml<br>
├── nginx/<br>
│   └── nginx.conf<br>
│<br>
├── backend/<br>
│   └── Dockerfile<br>
│<br>
├── frontend/<br>
│   └── Dockerfile<br>
│<br>
├── ci-cd/<br>
│   ├── Jenkinsfile<br>
│   └── .drone.yml<br>
│<br>
└── README.md

---
## 🧠 Architecture Overview

User<br>
↓<br>
Nginx (Reverse Proxy)<br>
↓<br>
Frontend (UI)<br>
↓<br>
Backend (API)<br>
↓<br>
PostgreSQL (Database)


---

## 🧱 Components

| Component | Description |
|---------|------------|
| Frontend | UI Layer (React / Next.js) |
| Backend | API Layer (Node / Python / Java) |
| Database | PostgreSQL with persistent volume |
| Nginx | Reverse Proxy + Load Balancer |
| CI/CD | Jenkins / Drone |

---

## ⚙️ How to Run Locally

```bash
docker-compose up -d
```

### Access:

Frontend → http://localhost

Backend API → http://localhost/api

Database → http://localhost:5432

### 🏗️ System Design Principles Used
1️⃣ Separation of Concerns

UI, API, DB are isolated

Easy to scale & maintain

2️⃣ High Availability Ready

Stateless frontend & backend

Nginx supports load balancing

Easy horizontal scaling:

docker-compose up --scale backend=3

3️⃣ Reverse Proxy Pattern

Single entry point

Hides internal services

Improves security

4️⃣ Persistence

Database uses Docker volumes

Data survives container restarts

5️⃣ CI/CD Automation

Jenkins & Drone pipelines included

Zero manual deployment

### ☸️ Kubernetes (Future Scope)

This setup can be migrated to Kubernetes:

Docker containers → Pods

docker-compose → Helm / Manifests

Nginx → Ingress Controller

> **Made by Harsh Singh**