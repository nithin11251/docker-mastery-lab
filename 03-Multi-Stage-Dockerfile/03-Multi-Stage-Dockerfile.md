# Multi-Stage Dockerfile

## What is a Multi-Stage Dockerfile?

A Multi-Stage Dockerfile is a Dockerfile that uses **multiple `FROM` instructions** to separate the build environment from the runtime environment.

It helps create **smaller, faster, and more secure Docker images** by copying only the required files from one stage to another.

---

# Why Do We Need Multi-Stage Builds?

Consider a Java Spring Boot application.

To build the application, we need:

- JDK
- Maven
- Source Code

However, to run the application, we only need:

- JRE
- Generated JAR File

If we use a normal Dockerfile, the final image contains:

- JDK
- Maven
- Source Code
- Build Cache
- JAR File

This makes the image unnecessarily large.

---

# Solution

Multi-stage builds separate:

```
Build Stage
        │
        ▼
Compile Application
        │
Copy Only Required Files
        │
        ▼
Runtime Stage
```

Only the application is copied into the final image.

---

# Benefits

- Smaller Docker Images
- Faster Deployment
- Improved Security
- Reduced Storage Usage
- Faster Image Pulls
- Production Ready

---

# Syntax

```dockerfile
FROM image AS build-stage

# Build application

FROM runtime-image

# Copy files from build stage
COPY --from=build-stage source destination
```

---

# Example 1 - Java Spring Boot

```dockerfile
# Stage 1 - Build

FROM maven:3.9.6-eclipse-temurin-21 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

# Stage 2 - Runtime

FROM eclipse-temurin:21-jre

WORKDIR /app

COPY --from=builder /app/target/app.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
```

---

# How It Works

Step 1

```
Builder Image

Maven
JDK
Source Code
```

↓

Compiles

↓

Creates

```
app.jar
```

---

Step 2

Runtime Image

```
Only

JRE

app.jar
```

No Maven

No Source Code

No Build Files

---

# Example 2 - Node.js Application

```dockerfile
# Build Stage

FROM node:20 AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Runtime Stage

FROM nginx:latest

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80
```

---

# Example 3 - React Application

```dockerfile
FROM node:20 AS builder

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

FROM nginx:alpine

COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80
```

---

# COPY --from

This is the most important instruction in a multi-stage Dockerfile.

Syntax

```dockerfile
COPY --from=<stage-name> <source> <destination>
```

Example

```dockerfile
COPY --from=builder /app/target/app.jar app.jar
```

Explanation

```
builder
↓

Take app.jar

↓

Copy into final image
```

---

# Naming Stages

Instead of writing:

```dockerfile
FROM maven
```

Use

```dockerfile
FROM maven AS builder
```

Now Docker knows this stage is called:

```
builder
```

Later:

```dockerfile
COPY --from=builder
```

---

# Build Command

```bash
docker build -t spring-app .
```

---

# Run Command

```bash
docker run -d -p 8080:8080 spring-app
```

---

# Single Stage vs Multi-Stage

| Single Stage | Multi-Stage |
|--------------|-------------|
| Large Image | Small Image |
| Includes Build Tools | Build Tools Removed |
| Slower | Faster |
| Less Secure | More Secure |
| Higher Storage Usage | Lower Storage Usage |

---

# Real-World Workflow

```
Source Code

↓

Builder Stage

↓

Compile Application

↓

Generate JAR

↓

Runtime Stage

↓

Copy JAR

↓

Run Application
```

---

# Interview Questions

## What is a Multi-Stage Dockerfile?

A Multi-Stage Dockerfile uses multiple `FROM` instructions to separate the build environment from the runtime environment, producing smaller and more secure images.

---

## Why use Multi-Stage Builds?

- Reduce image size
- Improve security
- Remove unnecessary build tools
- Faster deployments
- Better production images

---

## Which instruction copies files between stages?

```dockerfile
COPY --from=builder
```

---

## Can a Dockerfile have multiple FROM instructions?

Yes.

Each `FROM` starts a new build stage.

---

# Key Takeaways

✅ Multiple `FROM` instructions

✅ Separate Build and Runtime environments

✅ Uses `COPY --from`

✅ Smaller Images

✅ Production Best Practice

✅ Widely used in DevOps and CI/CD pipelines