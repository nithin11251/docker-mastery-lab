# 🐳 Docker Mastery Lab

A comprehensive hands-on Docker learning repository covering Docker fundamentals, Dockerfile creation, multi-stage builds, storage, networking, and real-world containerization examples. This repository is designed for beginners and aspiring DevOps engineers who want to master Docker through practical examples.

---

## 📌 Repository Overview

This repository contains structured Docker examples organized by topics. Each module includes practical demonstrations, sample applications, Dockerfiles, and best practices to help understand Docker concepts from beginner to advanced level.

---

## 📂 Repository Structure

```text
docker-mastery-lab/
│
├── 01-Docker-Basics/
├── 02-Dockerfile/
├── 03-Multi-Stage-Dockerfile/
├── 04-Docker-Storage/
├── 05-Docker-Networking/
└── README.md
```

---

# 📚 Modules Covered

## 01 - Docker Basics

Topics Covered

- What is Docker?
- Why Docker?
- Virtual Machines vs Containers
- Docker Architecture
- Docker Installation
- Docker Images
- Docker Containers
- Docker Hub
- Docker CLI Commands

Examples

- Pull Images
- Run Containers
- Stop Containers
- Remove Containers
- List Images
- Container Lifecycle

---

## 02 - Dockerfile

Topics Covered

- Dockerfile Introduction
- Dockerfile Instructions
- FROM
- RUN
- COPY
- ADD
- WORKDIR
- CMD
- ENTRYPOINT
- ENV
- EXPOSE
- LABEL
- USER

Examples

- Java Application
- Static Website
- Spring Boot Application

---

## 03 - Multi-Stage Dockerfile

Topics Covered

- Multi-stage Builds
- Build Optimization
- Smaller Image Size
- Builder Pattern
- Production Images
- Security Best Practices

Examples

- Java Application
- Spring Boot
- Maven Build
- Runtime Image

---

## 04 - Docker Storage

Topics Covered

- Docker Volumes
- Bind Mounts
- Named Volumes
- Anonymous Volumes
- Volume Lifecycle
- Persistent Storage

Examples

- MySQL Data Persistence
- PostgreSQL Volumes
- Static Website Bind Mount
- Data Backup

---

## 05 - Docker Networking

Topics Covered

- Docker Network Basics
- Bridge Network
- Host Network
- None Network
- Custom Bridge Network
- Container Communication
- DNS Resolution

Examples

- Multi-container Communication
- Custom Network Creation
- Web and Database Containers
- Network Inspection

---

# 🚀 Getting Started

## Clone Repository

```bash
git clone https://github.com/your-username/docker-mastery-lab.git
```

```bash
cd docker-mastery-lab
```

---

## Verify Docker Installation

```bash
docker --version
```

```bash
docker info
```

---

# 🐳 Frequently Used Docker Commands

## Images

```bash
docker images
```

```bash
docker pull nginx
```

```bash
docker rmi image_name
```

---

## Containers

```bash
docker ps
```

```bash
docker ps -a
```

```bash
docker run -d nginx
```

```bash
docker stop container_id
```

```bash
docker start container_id
```

```bash
docker restart container_id
```

```bash
docker rm container_id
```

---

## Dockerfile

Build Image

```bash
docker build -t myapp .
```

Run Container

```bash
docker run -d -p 8080:80 myapp
```

---

## Docker Volumes

Create Volume

```bash
docker volume create myvolume
```

List Volumes

```bash
docker volume ls
```

Inspect Volume

```bash
docker volume inspect myvolume
```

---

## Docker Networks

List Networks

```bash
docker network ls
```

Create Network

```bash
docker network create mynetwork
```

Inspect Network

```bash
docker network inspect mynetwork
```

---

# 📖 Learning Roadmap

- ✅ Docker Fundamentals
- ✅ Docker CLI
- ✅ Docker Images
- ✅ Docker Containers
- ✅ Dockerfile
- ✅ Multi-stage Dockerfile
- ✅ Docker Storage
- ✅ Docker Networking
- ⏳ Docker Compose
- ⏳ Docker Swarm
- ⏳ Docker Security
- ⏳ Docker Logging
- ⏳ Docker Monitoring
- ⏳ Docker Best Practices
- ⏳ Kubernetes Basics

---

# 💡 Prerequisites

- Basic Linux Commands
- Git & GitHub
- Command Line Basics
- Basic Programming Knowledge

---

# 🛠️ Technologies Used

- Docker
- Docker Hub
- Docker CLI
- Linux
- Git
- GitHub
- Java
- Maven
- Spring Boot
- HTML
- CSS
- JavaScript

---

# 🎯 Repository Goals

- Learn Docker from scratch
- Practice Docker commands
- Build Docker images
- Understand Dockerfile instructions
- Create optimized multi-stage builds
- Work with Docker storage
- Configure Docker networking
- Build real-world containerized applications

---

# 📈 Future Enhancements

- Docker Compose
- Docker Swarm
- Kubernetes Integration
- CI/CD with Docker
- Jenkins Integration
- GitHub Actions
- Docker Security
- Docker Monitoring
- Container Orchestration
- Production Deployment Examples

---




# ⭐ Support

If you found this repository helpful:

⭐ Star this repository

🍴 Fork this repository

📢 Share it with others learning Docker

---

# 📜 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**R. Nithin Kumar Reddy**


Aspiring Software Engineer | Java Full Stack | DevOps Enthusiast

GitHub: https://github.com/nithin11251

---

## ⭐ Happy Learning & Happy Containerizing! 🐳