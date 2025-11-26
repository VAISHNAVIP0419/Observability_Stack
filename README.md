
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


## Setup Monitoring Stack

The monitoring stack consists of Prometheus, cAdvisor, Grafana, Loki, and Promtail, which work together to collect container metrics and logs and visualize them in real time.

### Prometheus Setup (Metrics Collection)

Prometheus is used to scrape and store metrics from various data sources such as cAdvisor and Docker Engine. In our setup, Prometheus reads configuration from the prometheus.yml file and scrapes metrics every 5 seconds.

#### Access Prometheus UI

Open the URL in a browser:

```bash
http://localhost:9090
```

Screenshot to capture:
Description	Screenshot
Prometheus home page	Take screenshot of Prometheus UI
Prometheus Targets page	Go to Status → Targets showing cadvisor and prometheus as UP

#### Path: Prometheus → Status → Targets

(Insert Screenshot Example Placeholder in Document)
Screenshot: Prometheus Targets page showing cadvisor and prometheus UP

#### cAdvisor Setup (Container Metrics Provider)

cAdvisor provides real-time metrics for CPU, memory, network, and disk of each Docker container. Prometheus scrapes metrics from cAdvisor and sends them to Grafana for visualization.

Access cAdvisor web UI : 
```bash 
http://localhost:8080/containers/
```

Screenshot to capture:
Description
cAdvisor container metrics UI page
View showing running containers list

### Grafana Setup (Visualization Layer)

Grafana is used to visualize both metrics (Prometheus) and logs (Loki) by configuring them as data sources.

Access Grafana :
```bash
http://localhost:3001/
```


Default credentials:
```bash
username: admin
password: admin
```

#### Add Prometheus Datasource in Grafana

Go to Settings → Data Sources

Click Add data source

Select Prometheus

Set URL:
```bash
http://prometheus:9090
```

Click Save & Test → should show "Data source is working"

Screenshot to capture:
Description
List of Data Sources showing Prometheus added
Prometheus datasource configuration page

#### Add Loki Datasource in Grafana (Log Storage)

Go to Settings → Data Sources

Click Add data source

Select Loki

Set URL:
```bash
http://loki:3100
```

Click Save & Test

Screenshot to capture:
Description
List of Data Sources showing Loki added
Loki datasource configuration page
### Create Dashboards for Real-Time Monitoring

We will import a pre-built dashboard to visualize container CPU, memory, and network usage.

#### Steps to import dashboard

Go to Grafana → Dashboards → Import

Enter Dashboard ID:
```bash
893  (Docker & system metrics)
```

or
```bash
193  (cAdvisor exporter container metrics)
```

Choose Prometheus datasource

Click Import

Screenshots to capture:
Description
Screenshot of Import Dashboard screen
Dashboard visible with CPU, Memory, Network panels

### Logging Visualization with Loki & Promtail

Promtail collects container logs and pushes them to Loki. Logs are viewed inside Grafana using the Explore tab.

Steps to View Logs

Go to Grafana → Explore

Select Loki datasource

Run query:
```bash 
{container=~".*"}
```

To filter specific container logs:
```bash
{container="observability_backend"}
```
Enable Live Log Streaming:

Click Live → it will show real-time logs

Screenshots to capture:
Description
Grafana Explore tab with Loki selected
All container logs streaming live
Filtered backend logs example
Frontend / backend / mongo log view

## Final Observability Dashboard

Create dashboard with both metrics & logs panels together for real-time monitoring.

Screenshot to capture:
Description
Complete dashboard full-screen view
Metrics + Logs combined real-time dashboard

### Troubleshooting

Common checks:

### Conclusion

This project demonstrates a complete DevOps observability stack that enables real-time performance monitoring and centralized log aggregation for containerized applications. Using Prometheus, Grafana, cAdvisor, Loki, and Promtail, we successfully visualized CPU, memory, network usage, and live application logs, ensuring simplified debugging, improved reliability, and enhanced observability.

## completed!