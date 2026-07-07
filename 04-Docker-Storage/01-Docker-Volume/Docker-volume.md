# Docker Volume

## What is a Docker Volume?

A Docker Volume is a Docker-managed storage location used to persist data even after a container is removed.

Volumes are stored outside the container filesystem and are managed by Docker.

---

# Why Do We Need Volumes?

Without a Volume:

```
Container
│
├── index.html
└── data

↓

Container Removed

↓

All Data Lost ❌
```

With a Volume:

```
Container
      │
      ▼
Docker Volume
      │
      ▼
Data Persists ✅
```

---

# Benefits

- Persistent Storage
- Data survives container deletion
- Can be shared between containers
- Recommended for databases
- Managed by Docker

---

# Create a Volume

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

Remove Volume

```bash
docker volume rm myvolume
```

---

# Example

Folder Structure

```
project/
│
├── Dockerfile
└── index.html
```

Dockerfile

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/

VOLUME /usr/share/nginx/html

EXPOSE 80
```

Build Image

```bash
docker build -t nginx-volume .
```

Run Container

```bash
docker run -d \
--name volume-demo \
-v myvolume:/usr/share/nginx/html \
-p 8080:80 nginx-volume
```

Open Browser

```
http://localhost:8080
```

---

# Explanation

```
Docker Volume

↓

/usr/share/nginx/html

↓

Stores website files
```

Even if the container is removed, the volume remains.

---

# Real-World Examples

- MySQL → /var/lib/mysql
- PostgreSQL → /var/lib/postgresql/data
- MongoDB → /data/db
- Nginx Static Website → /usr/share/nginx/html

---

# Interview Question

Q. What is a Docker Volume?

Answer:

A Docker Volume is Docker-managed persistent storage used to store data outside the container lifecycle.

---

# Key Points

✔ Docker Managed

✔ Persistent Storage

✔ Can be Shared

✔ Survives Container Removal

✔ Best for Databases