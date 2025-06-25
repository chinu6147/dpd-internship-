# Microservices Reverse Proxy with Nginx and Docker Compose

## 📦 Overview

This project demonstrates a microservices architecture containing:
- **Nginx** (as a reverse proxy)
- **Service 1:** Go application
- **Service 2:** Python Flask application

All services run in Docker containers, orchestrated with Docker Compose.  
Nginx routes requests to the appropriate backend service based on the URL path.

---

## 🚀 Setup Instructions

1. **Clone the repository:**
    ```bash
    git clone <your-repo-url>
    cd <repo-folder>
    ```

2. **Build and start all services with:**
    ```bash
    docker-compose up --build
    ```

3. **Access the services in your browser or with curl:**

    - Go Service (Service 1):  
      - [http://localhost:8080/service1/hello](http://localhost:8080/service1/hello)  
      - [http://localhost:8080/service1/ping](http://localhost:8080/service1/ping)

    - Python Service (Service 2):  
      - [http://localhost:8080/service2/hello](http://localhost:8080/service2/hello)  
      - [http://localhost:8080/service2/ping](http://localhost:8080/service2/ping)

4. **To stop and remove all containers:**
    ```bash
    docker-compose down
    ```

---

## 🔀 How Routing Works

- **Nginx** listens on port `8080` and acts as a reverse proxy.
- Requests to `/service1/*` are routed to the Go application (`service_1`) running on port 8001 in its container.
- Requests to `/service2/*` are routed to the Python Flask app (`service_2`) running on port 8002 in its container.
- All routing logic is defined in [`nginx/nginx.conf`](nginx/nginx.conf).

---

## ✨ Bonus Features

- **Clear Nginx Access Logs:**  
  Each request is logged with timestamp and path for easy auditing and debugging.
- **Service Isolation:**  
  Service containers are only accessible to Nginx, not to the public host directly (unless you add `ports:`).
- **Minimal & Modular Dockerfiles:**  
  Each service uses best-practice multi-stage Dockerfiles for clear and secure builds.

---

## 🗄️ Project Structure
.
├── docker-compose.yml
├── nginx
│ ├── nginx.conf
│ └── Dockerfile
├── service_1
│ ├── main.go
│ └── Dockerfile
├── service_2
│ ├── app.py
│ ├── pyproject.toml
│ └── Dockerfile
└── README.md


---

## 🛟 Troubleshooting

- If you change any configuration, re-run:
    ```bash
    docker-compose down
    docker-compose up --build
    ```
- View logs for Nginx or other services:
    ```bash
    docker-compose logs nginx
    ```
- Make sure ports `8080`, `8001`, and `8002` are not being used elsewhere on your machine.

---

**Enjoy your microservices playground!**

---
