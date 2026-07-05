# Docker Basics

## What is Docker?

Docker is an open-source containerization platform used to package an application along with all its dependencies into a lightweight unit called a **container**. It ensures that the application runs the same way on any machine.

---

# Why Docker?

Without Docker:

Developer Machine
↓
Works on my laptop
↓
Fails on another machine

With Docker:

Application
+
Dependencies
+
Runtime
↓
Docker Image
↓
Runs the same everywhere

---

# What is an Image?

A Docker Image is a **read-only blueprint** used to create containers.

Think of it as a class in Java.

Example:

Ubuntu Image

↓

Can create multiple Ubuntu Containers.

List Images

```bash
docker images
```

---

# What is a Container?

A Container is a **running instance of an image**.

Think of it as an object in Java.

Example

Image

↓

Container 1

Container 2

Container 3

List Running Containers

```bash
docker ps
```

List All Containers

```bash
docker ps -a
```

---

# Image vs Container

| Image | Container |
|--------|-----------|
| Blueprint | Running Instance |
| Read-only | Read & Write |
| Cannot Execute | Executes Applications |
| Can create many containers | Created from an image |

---

# Docker Architecture

```
Developer
     │
Docker CLI
     │
Docker Engine
     │
Images
     │
Containers
```

---

# Docker Commands

## Check Docker Version

```bash
docker --version
```

---

## Docker Information

```bash
docker info
```

---

## Download an Image

```bash
docker pull nginx
```

Downloads an image from Docker Hub.

---

## List Images

```bash
docker images
```

---

## Remove an Image

```bash
docker rmi IMAGE_ID
```

Example

```bash
docker rmi nginx
```

---

# Container Commands

## Create and Start Container

```bash
docker run nginx
```

---

## Run Container in Background

```bash
docker run -d nginx
```

---

## Give Container Name

```bash
docker run -d --name my-nginx nginx
```

---

## List Running Containers

```bash
docker ps
```

---

## List All Containers

```bash
docker ps -a
```

---

## Stop Container

```bash
docker stop CONTAINER_ID
```

Example

```bash
docker stop my-nginx
```

---

## Start Container

```bash
docker start CONTAINER_ID
```

---

## Restart Container

```bash
docker restart CONTAINER_ID
```

---

## Pause Container

```bash
docker pause CONTAINER_ID
```

---

## Resume Container

```bash
docker unpause CONTAINER_ID
```

---

## Kill Container

```bash
docker kill CONTAINER_ID
```

Immediately stops the container.

---

## Remove Container

```bash
docker rm CONTAINER_ID
```

---

## Remove Running Container

```bash
docker rm -f CONTAINER_ID
```

---

# Execute Commands Inside Container

```bash
docker exec -it CONTAINER_ID bash
```

or

```bash
docker exec -it CONTAINER_ID sh
```

---

# View Logs

```bash
docker logs CONTAINER_ID
```

Follow logs continuously

```bash
docker logs -f CONTAINER_ID
```

---

# Inspect Container

```bash
docker inspect CONTAINER_ID
```

---

# Build Docker Image

```bash
docker build -t myimage .
```

Explanation

```
-t
Tag (Image Name)

myimage
Image Name

.
Current Directory
```

---

# Run Built Image

```bash
docker run myimage
```

---

# Run with Port Mapping

```bash
docker run -p 8080:80 nginx
```

Meaning

```
Host Port
8080

↓

Container Port
80
```

---

# Run with Name

```bash
docker run --name mycontainer nginx
```

---

# Run in Interactive Mode

```bash
docker run -it ubuntu bash
```

---

# Remove All Stopped Containers

```bash
docker container prune
```

---

# Remove Unused Images

```bash
docker image prune
```

---

# Remove Everything Unused

```bash
docker system prune
```

---

# Docker Workflow

Write Dockerfile

↓

Build Image

```bash
docker build -t myapp .
```

↓

Run Container

```bash
docker run myapp
```

↓

Stop Container

```bash
docker stop myapp
```

↓

Restart Container

```bash
docker restart myapp
```

↓

Remove Container

```bash
docker rm myapp
```

---

# Summary

Image = Blueprint

Container = Running Instance

Build = Create Image

Run = Create Container

Stop = Stop Container

Start = Start Existing Container

Restart = Restart Container

Remove = Delete Container

Dockerfile = Recipe to Build Image