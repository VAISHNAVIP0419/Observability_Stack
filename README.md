
# Docker Observability Stack – Monitoring & Logging with Prometheus, Grafana, and Loki.




## Introduction

This assessment focuses on implementing a complete monitoring and logging solution for containerized microservices using modern DevOps tools. The goal is to deploy a sample three-tier application using Docker Compose and then integrate Prometheus, Grafana, cAdvisor, Loki, and Promtail to collect metrics, monitor container performance in real time, and visualize application logs. By the end of this assignment, we will have a fully functional observability stack that provides real-time insights into CPU, memory, network usage, and centralized log management—all displayed through Grafana dashboards.


##  Environment Setup

To run the sample microservices and observability stack locally, ensure the following prerequisites are installed and configured on the system:

###  System Requirements (Local Machine)
- Minimum 2 Core CPU
- Minimum 4 GB RAM (Recommended 8 GB)
- 10–20 GB free disk space
- Operating System: Ubuntu 20.04 / 22.04 / 24.04 or Windows / macOS with Docker support

###  AWS EC2 (Optional Deployment)
- Instance Type: t3.medium (Recommended: t3.large)
- CPU: 2 vCPU
- RAM: 4–8 GB
- Storage: 20–30 GB EBS (gp3)
- Operating System: Ubuntu 20.04 / 22.04 LTS
- Security Groups: Allow ports 22, 3000, 9090, 3100, 8080, and any application ports

###  Required Tools
- Docker (latest version)
- Docker Compose (v3.8 or above)
- Git (for cloning project repository)
- Web browser (Chrome / Firefox for Grafana visualization & UI access)
- Optional: MongoDB Compass or VS Code extensions for database inspection

## 🚀 Deploy Sample Application (Microservices)

This project includes three microservices running via Docker Compose:
- **Frontend Service** (React / UI)
- **Backend Service** (Node.js API)
- **Database Service** (MongoDB)

To start the services, run:
```bash
docker compose up -d
```
<img width="921" height="74" alt="Screenshot 2025-11-25 231109" src="https://github.com/user-attachments/assets/6216ddc5-097e-4842-9c8c-c34531ade63e" />

Verify running containers using:
```bash
docker ps
```
<img width="984" height="226" alt="Screenshot 2025-11-26 001105" src="https://github.com/user-attachments/assets/437849c5-89aa-44f3-8c71-9385c247d867" />

### Access Services:

Frontend: http://localhost:3000

<img width="1365" height="679" alt="Screenshot 2025-11-25 233737" src="https://github.com/user-attachments/assets/49ff006e-403f-4798-8bd3-60fb23ef1dcf" />

Backend API: http://localhost:5000

<img width="1365" height="226" alt="Screenshot 2025-11-25 233754" src="https://github.com/user-attachments/assets/f6e903be-3c55-4e0c-a313-59a0e8068b3d" />

