# 🚀 Docker Compose for Maven Application

## 📖 Overview

This project demonstrates how to use **Docker Compose** to build and run a Maven-based Java application inside a Docker container. Instead of manually creating and running containers using multiple `docker run` commands, Docker Compose allows you to define the entire application configuration in a single YAML file.

Docker Compose simplifies container management by describing services, images, volumes, networks, and startup commands in one place.

---

# 📂 Project Structure

```text
01-Sample-MVN-Project
│
├── docker-compose.yml
├── pom.xml
├── Dockerfile (Optional)
├── src/
├── target/
└── .mvn/
```

---

# 📄 docker-compose.yml

```yaml
services:
  maven-app:
    image: maven:3.8.7-eclipse-temurin-17
    container_name: maven_project1
    working_dir: /app
    volumes:
      - .:/app
      - ~/.m2:/root/.m2
    command: /bin/bash -c "mvn clean package && tail -f /dev/null"
```

---

# 🎯 Purpose

This Compose file creates a container with Maven and Java 17 already installed. The project directory from the host machine is mounted inside the container, allowing Maven to build the application without installing Java or Maven on the local machine.

This approach provides a consistent development environment across different systems.

---

# 🔍 Service Explanation

## Service Name

```yaml
services:
  maven-app:
```

The **services** section defines the containers managed by Docker Compose.

Here, **maven-app** is the service name.

---

## Image

```yaml
image: maven:3.8.7-eclipse-temurin-17
```

This specifies the official Maven Docker image.

It already includes:

- Apache Maven 3.8.7
- Eclipse Temurin OpenJDK 17
- Linux operating system
- Maven command-line tools

Using an official image eliminates the need to install Maven manually.

---

## Container Name

```yaml
container_name: maven_project1
```

Assigns a custom name to the container.

Without this option, Docker Compose automatically generates names such as:

```
sample-mvn-project_maven-app_1
```

Using a custom name makes container management easier.

---

## Working Directory

```yaml
working_dir: /app
```

Sets the default working directory inside the container.

Every command executes from:

```
/app
```

This avoids repeatedly changing directories.

---

## Volumes

### Project Volume

```yaml
- .:/app
```

Mounts the current project directory from the host machine into the container.

Host:

```
Current Project Folder
```

↓

Container:

```
/app
```

Benefits:

- Live synchronization of source code
- No need to rebuild the image after every code change
- Easy development workflow

---

### Maven Repository Cache

```yaml
- ~/.m2:/root/.m2
```

Mounts the local Maven repository into the container.

Host:

```
~/.m2
```

↓

Container:

```
/root/.m2
```

Benefits:

- Dependencies are downloaded only once
- Faster Maven builds
- Reduced internet usage
- Improved build performance

---

## Command

```yaml
command: /bin/bash -c "mvn clean package && tail -f /dev/null"
```

This command performs two tasks.

### Step 1

```bash
mvn clean package
```

- Cleans previous build files
- Downloads dependencies if required
- Compiles Java source code
- Executes unit tests
- Creates the application package (JAR)

---

### Step 2

```bash
tail -f /dev/null
```

Normally, after Maven finishes, the container exits.

The command:

```bash
tail -f /dev/null
```

keeps the container running continuously.

This is useful because you can:

- Enter the container using `docker exec`
- Inspect build files
- Execute additional Maven commands
- Debug the application

---

# ⚙️ Docker Compose Workflow

```
docker-compose.yml
        │
        ▼
docker compose up
        │
        ▼
Pull Maven Image
        │
        ▼
Create Container
        │
        ▼
Mount Project Files
        │
        ▼
Execute Maven Build
        │
        ▼
Generate JAR File
        │
        ▼
Keep Container Running
```

---

# ▶️ Running the Project

Start the service:

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

Access the container:

```bash
docker exec -it maven_project1 bash
```

Stop the service:

```bash
docker compose down
```

---

# 📦 Build Output

After execution, Maven generates build artifacts inside the `target/` directory.

Example:

```text
target/
├── classes/
├── test-classes/
├── maven-status/
├── surefire-reports/
└── *.jar
```

These files are available both inside the container and on the host because the project directory is mounted as a volume.

---

# 💡 Advantages of Using Docker Compose

- Single configuration file for the application
- Consistent build environment across different machines
- No local Maven installation required
- Simplifies container management
- Supports reusable project configuration
- Easy integration with CI/CD pipelines
- Faster builds using Maven dependency caching
- Simplifies development and testing

---

# 📌 Key Concepts Covered

- Docker Compose
- Services
- Official Docker Images
- Container Naming
- Working Directory
- Bind Mounts
- Volume Mapping
- Maven Dependency Cache
- Maven Build Lifecycle
- Build Artifacts
- Docker Compose Commands

---

# ✅ Conclusion

This Docker Compose configuration provides a simple and efficient way to build a Maven-based Java application inside a container. By using the official Maven image, mounting the project directory, and caching Maven dependencies, developers can build applications consistently without installing Java or Maven locally. Docker Compose also simplifies project management by keeping all container configuration in a single, easy-to-maintain YAML file.