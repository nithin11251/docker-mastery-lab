# 🚀 Docker Compose for Multi-Container Static Web Applications

## 📖 Overview

This project demonstrates how to use **Docker Compose** to deploy multiple static web applications using **Nginx** containers. Each application runs in its own container while sharing a common Docker network. The project also uses **Bind Mounts** for live source code synchronization and **Docker Volumes** for persistent Nginx log storage.

Docker Compose simplifies the deployment and management of multiple containers by defining all services, networks, and volumes in a single configuration file.

---

# 📂 Project Structure

```text
Multi-Container-App
│
├── docker-compose.yml
│
├── zomato-web-app
│   ├── Dockerfile
│   ├── index.html
│   ├── css/
│   ├── js/
│   └── images/
│
└── Amazon-Clone
    ├── Dockerfile
    ├── index.html
    ├── css/
    ├── js/
    └── images/
```

---

# 📄 docker-compose.yml

```yaml
services:
  zomato_app:
    build: ./zomato-web-app
    image: zomato-image
    container_name: zomato-cont
    ports:
      - "8081:80"
    volumes:
      - ./zomato-web-app:/usr/share/nginx/html
      - zomato_volume:/var/log/nginx
    networks:
      - my_network

  amazon_app:
    build: ./Amazon-Clone
    image: amazon-image
    container_name: amazon-cont
    ports:
      - "8082:80"
    volumes:
      - ./Amazon-Clone:/usr/share/nginx/html
      - amazon_volume:/var/log/nginx
    networks:
      - my_network

networks:
  my_network:
    driver: bridge

volumes:
  zomato_volume:
  amazon_volume:
```

---

# 🎯 Purpose

This Compose file demonstrates how Docker Compose can manage multiple web applications simultaneously.

Each application:

- Builds its own Docker image
- Runs inside a separate container
- Uses its own persistent log storage
- Shares a common Docker network
- Can be accessed independently using different ports

---

# 🔍 Service Explanation

## Services

```yaml
services:
```

The **services** section defines all containers that Docker Compose will create and manage.

In this project there are two services:

- zomato_app
- amazon_app

Each service runs independently.

---

# 🍽 Zomato Application

## Build

```yaml
build: ./zomato-web-app
```

Docker builds an image using the Dockerfile inside:

```
zomato-web-app/
```

---

## Image

```yaml
image: zomato-image
```

The generated Docker image is named:

```
zomato-image
```

---

## Container Name

```yaml
container_name: zomato-cont
```

Creates the container with the name:

```
zomato-cont
```

instead of an automatically generated name.

---

## Port Mapping

```yaml
ports:
  - "8081:80"
```

Maps

Host:

```
localhost:8081
```

↓

Container:

```
Port 80
```

The application can be accessed through:

```
http://localhost:8081
```

---

## Bind Mount

```yaml
- ./zomato-web-app:/usr/share/nginx/html
```

Maps the application source code into the container.

Host

```
./zomato-web-app
```

↓

Container

```
/usr/share/nginx/html
```

Benefits

- Live code synchronization
- No image rebuild required after HTML/CSS/JS changes
- Faster development

---

## Docker Volume

```yaml
- zomato_volume:/var/log/nginx
```

Creates a Docker-managed volume for storing Nginx logs.

Container

```
/var/log/nginx
```

↓

Docker Volume

```
zomato_volume
```

Advantages

- Persistent logs
- Data survives container removal
- Easy debugging

---

# 🛒 Amazon Application

## Build

```yaml
build: ./Amazon-Clone
```

Builds the Docker image using the Dockerfile inside:

```
Amazon-Clone/
```

---

## Image

```yaml
image: amazon-image
```

Names the generated image:

```
amazon-image
```

---

## Container Name

```yaml
container_name: amazon-cont
```

Creates the container:

```
amazon-cont
```

---

## Port Mapping

```yaml
ports:
  - "8082:80"
```

Maps

Host

```
localhost:8082
```

↓

Container

```
Port 80
```

Application URL:

```
http://localhost:8082
```

---

## Bind Mount

```yaml
- ./Amazon-Clone:/usr/share/nginx/html
```

Synchronizes application files between host and container.

Benefits

- Instant code updates
- No rebuilding required
- Easy testing

---

## Docker Volume

```yaml
- amazon_volume:/var/log/nginx
```

Stores Nginx log files in a Docker-managed volume.

Benefits

- Persistent storage
- Easy maintenance
- Log retention after container recreation

---

# 🌐 Docker Network

```yaml
networks:
  my_network:
    driver: bridge
```

Creates a custom bridge network.

Both containers join this network automatically.

Advantages

- Container-to-container communication
- Network isolation
- Secure communication
- Easy service discovery

---

# 💾 Docker Volumes

```yaml
volumes:
  zomato_volume:
  amazon_volume:
```

Creates two named Docker volumes.

Purpose

- Store Nginx log files
- Preserve logs after container deletion
- Separate logs for each application

---

# ⚙️ Docker Compose Workflow

```
docker-compose.yml
        │
        ▼
docker compose up
        │
        ▼
Build Docker Images
        │
        ▼
Create Network
        │
        ▼
Create Volumes
        │
        ▼
Start Containers
        │
        ▼
Mount Application Files
        │
        ▼
Applications Available
```

---

# ▶️ Running the Project

Start all services:

```bash
docker compose up
```

Run in detached mode:

```bash
docker compose up -d
```

View running containers:

```bash
docker ps
```

View logs:

```bash
docker compose logs
```

List Docker volumes:

```bash
docker volume ls
```

List Docker networks:

```bash
docker network ls
```

Stop all services:

```bash
docker compose down
```

Stop and remove volumes:

```bash
docker compose down -v
```

---

# 🌍 Accessing the Applications

| Application | URL |
|-------------|-----------------------|
| Zomato Clone | http://localhost:8081 |
| Amazon Clone | http://localhost:8082 |

---

# 💡 Advantages of This Configuration

- Multiple applications managed using one Compose file
- Separate containers for each application
- Automatic image building
- Automatic network creation
- Persistent log storage using Docker volumes
- Live code updates using bind mounts
- Easy deployment with a single command
- Simplified container management

---

# 📌 Key Concepts Covered

- Docker Compose
- Multi-Container Applications
- Services
- Docker Images
- Docker Build
- Port Mapping
- Bind Mounts
- Named Volumes
- Docker Networks
- Bridge Network
- Persistent Storage
- Nginx Containers
- Static Website Deployment

---

# ✅ Conclusion

This project demonstrates how Docker Compose simplifies the deployment of multiple static web applications. Each application runs in its own Nginx container with dedicated bind mounts for source code synchronization, named volumes for persistent log storage, and a shared bridge network for communication. By defining services, networks, and volumes in a single `docker-compose.yml` file, the entire application stack can be started, managed, and stopped using a few simple Docker Compose commands.