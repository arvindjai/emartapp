# emart-app

# 🛒 EmartApp – E-Commerce Project

EmartApp is a **sample e-commerce web application** built for learning real-world **DevOps workflows**, including:

✅ CI/CD automation (Jenkins)  
✅ Containerization (Docker, Docker Compose)  
✅ Reverse proxy & routing (NGINX)  
✅ Polyglot microservices (Node.js API + Java API)  
✅ Deterministic dependency management (npm, package-lock)  
✅ Graceful lifecycle handling (npm script hooks, Node request flow)

---

## 🧩 Architecture Overview

Client (Browser)
↓ (HTTP/HTTPS)
NGINX (Reverse Proxy/API Gateway)
↓──────────────↓
Node.js API Java API
↓──────────────↓
Data Layer (DB / Cache / Message Queue - can be extended)


---

## 📁 Repository Structure

| Component | Path | Description |
|----------|------|-------------|
| Frontend UI | `client/` | User-facing interface (HTML/CSS/TS/JS) |
| API Service 1 | `nodeapi/` | Backend API built in Node.js |
| API Service 2 | `javaapi/` | Backend API built in Java (Spring Boot likely) |
| Reverse Proxy | `nginx/` | Config for routing UI and API traffic |
| Module/Feature | `kkartchart/` | Auxiliary component (cart/analytics/charting module) |
| Container Build | `Dockerfile` | Image build instructions for services |
| Local Orchestration | `docker-compose.yaml` | Multi-container app definition |
| CI/CD | `Jenkinsfile` | Jenkins pipeline for build/test/deploy |
| Node Dependency Lock | `package-lock.json` | Ensures deterministic npm builds |

---

## 🚀 How It Works Internally

### 🔹 Node.js API Request Handling (Runtime)
1. OS handles **DNS + TCP handshake**
2. Request reaches Node → **libuv detects socket event**
3. Event loop queues request handler
4. NGINX forwards to route → Node (JS handler executes)
5. Heavy operations are offloaded to **libuv thread pool** or **worker threads**
6. Response written to socket → OS sends back to client

### 🔹 npm Script Lifecycle Hooks
npm executes scripts in the sequence:

pre<command> → <command> → post<command>


Example for install & publish:

npm install:
preinstall → install → postinstall → prepare

npm publish:
prepare → prepublishOnly → prepack → pack → postpack → publish → postpublish



---

## 🐳 Running Locally (Docker Compose)

### 1️⃣ Clone repository

git clone https://github.com/arvindjai/emartapp.git

cd emartapp

### 2️⃣ Build and run all services
docker compose up --build -d

### 3️⃣ Access application
- UI → `http://localhost`
- Node API → `http://localhost/api/...`
- Java API → `http://localhost/java/...` (depends on nginx routing)

### 4️⃣ View logs
docker compose logs -f


### 5️⃣ Stop app
docker compose down


---

## 🧰 CI/CD Pipeline (Jenkins)

Typical pipeline flow defined in `Jenkinsfile`:



Checkout Code
↓
Build Frontend + Backend Services
↓
Run Unit Tests
↓
Build Docker Images
↓
Push to Registry (can be added)
↓
Deploy Containers
↓
Post-Deployment Tests (can be extended)



---

## ⚙️ Best Practices Demonstrated

| Practice | Benefit |
|---------|---------|
| No thread per request | Low memory footprint, high concurrency |
| Async I/O for API | Handles 1000s of requests efficiently |
| Libuv thread pool | Offloads crypto, FS, compression jobs |
| Docker Compose | Reproducible local environments |
| Jenkinsfile IAC | Automated delivery pipeline |
| npm lifecycle hooks | Automates build/setup/publish events |

---

## ❗Limitations (Since This is a Learning Repo)

This project is designed to learn, so you may extend with:

🔸 Database persistence (Postgres/MySQL/Mongo)  
🔸 Caching layer (Redis/Memcache)  
�� Message queue (RabbitMQ/Kafka)  
🔸 Monitoring (Prometheus, Grafana, ELK, PM2, APM tools)  
🔸 Secrets management (AWS SSM, Vault, GitHub Secrets)

---

## 📌 Useful Extensions for DevOps Practice

You can use this repo to practice:

- Docker image builds
- Reverse proxy routing
- Multi-service deployments
- CI/CD pipelines
- Load testing (`wrk`, `autocannon`)
- Deploy to cloud (AWS EC2, ECS, EKS, ELB, etc.)
- Microservice resiliency & observability

---

## 🤝 Contributing

Feel free to fork and enhance the project for additional DevOps learning!

---

## 📄 License

This is a demo/learning project intended for DevOps practice.

