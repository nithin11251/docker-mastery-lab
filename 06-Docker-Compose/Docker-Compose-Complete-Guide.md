# 🐳 Docker Compose Commands Cheat Sheet

## 📖 Overview

Docker Compose is a tool used to define, manage, and run multi-container Docker applications using a single **docker-compose.yml** file. Instead of executing multiple `docker run` commands, Docker Compose allows you to start all services with a single command.

Docker Compose automatically creates containers, networks, and volumes based on the configuration provided in the Compose file.

---
Note:
 This guide uses docker compose (Docker Compose V2), which is the current and recommended command. If you are using an older Docker installation that supports only Docker Compose V1, replace docker compose with docker-compose in all examples.

# 📌 Basic Syntax

```bash
docker compose [COMMAND]
```

To use a specific compose file:

```bash
docker compose -f docker-compose.yml [COMMAND]
```

---

# 🚀 Start Services

## Start all services

```bash
docker compose up
```

Starts all services and displays logs.

---

## Start services in detached mode

```bash
docker compose up -d
```

Runs containers in the background.

---

## Build images before starting

```bash
docker compose up --build
```

Rebuilds images before starting containers.

---

## Build and run in detached mode

```bash
docker compose up -d --build
```

---

## Start a specific service

```bash
docker compose up nginx
```

Example

```bash
docker compose up amazon_app
```

---

# 🛑 Stop Services

## Stop running containers

```bash
docker compose stop
```

Containers remain available.

---

## Stop a specific service

```bash
docker compose stop amazon_app
```

---

## Restart stopped services

```bash
docker compose start
```

---

## Restart a specific service

```bash
docker compose restart amazon_app
```

---

## Restart all services

```bash
docker compose restart
```

---

# ❌ Remove Services

## Stop and remove containers

```bash
docker compose down
```

Removes:

- Containers
- Networks

Volumes remain.

---

## Remove containers and volumes

```bash
docker compose down -v
```

Removes:

- Containers
- Networks
- Named Volumes

---

## Remove images also

```bash
docker compose down --rmi all
```

---

## Remove local images only

```bash
docker compose down --rmi local
```

---

# 🏗 Build Images

## Build all images

```bash
docker compose build
```

---

## Build without cache

```bash
docker compose build --no-cache
```

---

## Build a single service

```bash
docker compose build amazon_app
```

---

# 📦 Pull Images

## Pull all images

```bash
docker compose pull
```

---

## Pull a specific image

```bash
docker compose pull amazon_app
```

---

# 📤 Push Images

## Push all images

```bash
docker compose push
```

---

## Push a specific image

```bash
docker compose push amazon_app
```

---

# 📋 View Running Services

## Show running containers

```bash
docker compose ps
```

---

## Show all containers

```bash
docker ps -a
```

---

# 📜 Logs

## View logs

```bash
docker compose logs
```

---

## Follow logs

```bash
docker compose logs -f
```

---

## View logs of a service

```bash
docker compose logs amazon_app
```

---

## Tail last 100 log lines

```bash
docker compose logs --tail=100
```

---

# 🖥 Execute Commands

## Open Bash shell

```bash
docker compose exec amazon_app bash
```

---

## Open Sh shell

```bash
docker compose exec amazon_app sh
```

---

## Run a command

```bash
docker compose exec amazon_app ls
```

---

## Display current directory

```bash
docker compose exec amazon_app pwd
```

---

# ▶ Run One-Time Commands

## Run temporary container

```bash
docker compose run amazon_app bash
```

---

## Execute Maven command

```bash
docker compose run maven-app mvn clean package
```

---

## Execute Nginx command

```bash
docker compose run nginx nginx -v
```

---

# 🔍 View Configuration

## Validate compose file

```bash
docker compose config
```

---

## Show resolved configuration

```bash
docker compose config --services
```

---

## Display service names

```bash
docker compose config --services
```

---

## Display volumes

```bash
docker compose config --volumes
```

---

## Display networks

```bash
docker compose config --networks
```

---

# 📊 Resource Usage

## Display resource usage

```bash
docker stats
```

---

## Display compose containers

```bash
docker compose ps
```

---

# 🌐 Networks

## List Docker networks

```bash
docker network ls
```

---

## Inspect network

```bash
docker network inspect my_network
```

---

# 💾 Volumes

## List volumes

```bash
docker volume ls
```

---

## Inspect volume

```bash
docker volume inspect amazon_volume
```

---

## Remove unused volumes

```bash
docker volume prune
```

---

# 🧹 Cleanup

## Remove stopped containers

```bash
docker container prune
```

---

## Remove unused images

```bash
docker image prune
```

---

## Remove unused networks

```bash
docker network prune
```

---

## Remove everything unused

```bash
docker system prune
```

---

## Remove everything including volumes

```bash
docker system prune -a --volumes
```

---

# 📂 Multiple Compose Files

Run with another compose file

```bash
docker compose -f docker-compose.dev.yml up
```

---

Run multiple compose files

```bash
docker compose -f docker-compose.yml -f docker-compose.override.yml up
```

---

# 🔄 Scaling Services

Run multiple container instances

```bash
docker compose up --scale amazon_app=3
```

---

# 🛠 Useful Docker Compose Workflow

## Build project

```bash
docker compose build
```

---

## Start project

```bash
docker compose up -d
```

---

## Check containers

```bash
docker compose ps
```

---

## View logs

```bash
docker compose logs -f
```

---

## Execute into container

```bash
docker compose exec amazon_app bash
```

---

## Restart services

```bash
docker compose restart
```

---

## Stop services

```bash
docker compose stop
```

---

## Remove everything

```bash
docker compose down -v
```

---

# 💡 Tips

- Always keep your `docker-compose.yml` file in the project root.
- Use `docker compose config` to validate your configuration before running it.
- Prefer `docker compose up -d` for background execution.
- Use bind mounts for development and named volumes for persistent data.
- Use `docker compose logs -f` to monitor applications in real time.
- Use `docker compose down -v` when you need a clean environment.

---

# 📌 Key Commands Summary

| Command | Description |
|----------|-------------|
| `docker compose up` | Start all services |
| `docker compose up -d` | Start services in background |
| `docker compose up --build` | Build images and start |
| `docker compose build` | Build images |
| `docker compose pull` | Pull images |
| `docker compose push` | Push images |
| `docker compose ps` | Show running services |
| `docker compose logs` | View logs |
| `docker compose exec` | Execute commands in a running container |
| `docker compose run` | Run one-time command |
| `docker compose stop` | Stop services |
| `docker compose restart` | Restart services |
| `docker compose down` | Stop and remove containers |
| `docker compose down -v` | Remove containers and volumes |
| `docker compose config` | Validate compose file |
| `docker compose config --services` | List services |
| `docker compose config --volumes` | List volumes |
| `docker compose config --networks` | List networks |
| `docker compose up --scale service=3` | Scale service |
| `docker system prune` | Remove unused Docker resources |

---

# ✅ Conclusion

Docker Compose simplifies the deployment and management of multi-container applications. With a single `docker-compose.yml` file, you can build images, create containers, manage networks, mount volumes, view logs, execute commands, scale services, and clean up resources efficiently. Understanding these commands helps streamline development, testing, and deployment workflows while ensuring consistency across different environments.