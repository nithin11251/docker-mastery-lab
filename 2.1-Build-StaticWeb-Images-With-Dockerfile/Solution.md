# 🐳 2.1 - Build Static Web Images With Dockerfile

## 📖 Overview

This directory contains sample projects that demonstrate how to create Docker images using Dockerfiles. Each project focuses on a different application type, helping understand how Docker packages applications into portable images.

---

# 📂 Project Structure

```text
2.1-Build-StaticWeb-Images-With-Dockerfile
│
├── CalculatorApp/
├── Sample-MVN-Project/
└── StaicWeb3_2158_forge_reality/
```

---

# 📁 Project 1: CalculatorApp

## Description

This project is a simple calculator application used to demonstrate how an application can be containerized using Docker.

The Dockerfile builds the application and packages all required files into a Docker image.

### Contents

```text
CalculatorApp/
├── Dockerfile
├── (Application Source Files)
```

### Purpose

- Learn how Docker builds application images.
- Understand Dockerfile execution.
- Package a simple application into a container.

---

# 📁 Project 2: Sample-MVN-Project

## Description

This is a Maven-based Java project that demonstrates how Docker can build Java applications using the official Maven image.

The project contains Java source code, Maven configuration, and a Dockerfile.

### Folder Structure

```text
Sample-MVN-Project
│
├── .mvn/
├── src/
├── target/
├── pom.xml
└── Dockerfile
```

### File Explanation

### `.mvn/`

Contains Maven Wrapper configuration files that help build the project using the bundled Maven wrapper.

---

### `src/`

Contains the Java source code of the Maven application.

Typical structure:

```text
src
├── main
└── test
```

- **main** – Application source code.
- **test** – Unit test classes.

---

### `target/`

Contains generated build files after executing Maven build commands.

Examples include:

- Compiled classes
- JAR files
- Temporary build files

This folder is automatically generated during the build process.

---

### `pom.xml`

Project Object Model (POM) file.

It contains:

- Project metadata
- Dependencies
- Plugins
- Build configuration
- Java version

Maven reads this file while building the application.

---

### `Dockerfile`

Used to build the Docker image.

Example:

```dockerfile
FROM maven:3.6.3-openjdk-17

WORKDIR /mvn-app

COPY . .

RUN mvn clean

CMD ["mvn","package"]
```

#### Explanation

**FROM**

Uses the official Maven image with OpenJDK 17.

**WORKDIR**

Creates and switches to `/mvn-app`.

**COPY**

Copies the complete Maven project into the container.

**RUN**

Executes:

```bash
mvn clean
```

which removes previous build artifacts.

**CMD**

Runs

```bash
mvn package
```

to build the application when the container starts.

---

# 📁 Project 3: StaicWeb3_2158_forge_reality

## Description

This project demonstrates how to package a static website into a Docker image.

Since the website contains only static files, no application server is required other than a lightweight web server like Nginx.

### Folder Structure

```text
StaicWeb3_2158_forge_reality
│
├── Dockerfile
├── index.html
├── templates.html
└── images/
```

---

### `index.html`

Main homepage of the website.

It is the default page displayed when the container starts.

---

### `templates.html`

Contains additional webpage content or template page used for navigation within the website.

---

### `images/`

Stores image assets used by the HTML pages.

Examples:

- Background images
- Icons
- Logos
- Other static resources

---

### `Dockerfile`

Packages the website into a Docker image.

Example:

```dockerfile
FROM nginx:latest

COPY . /usr/share/nginx/html
```

#### Explanation

**FROM**

Uses the official Nginx image.

**COPY**

Copies all HTML files and images into Nginx's default web directory.

When the container starts, Nginx serves these files automatically.

---

# 🚀 Learning Outcomes

After completing these projects, you will understand how to:

- Build Docker images using Dockerfiles.
- Package static websites into containers.
- Package Java Maven projects into Docker images.
- Organize project files for Docker builds.
- Use official base images such as Nginx and Maven.
- Copy project files into Docker images.
- Execute build commands during image creation.
- Create reusable and portable application images.

---

# 📌 Summary

This module includes three different Docker-based projects:

| Project | Purpose |
|----------|---------|
| CalculatorApp | Demonstrates Dockerizing a simple application |
| Sample-MVN-Project | Demonstrates building Java Maven applications inside Docker |
| StaicWeb3_2158_forge_reality | Demonstrates serving a static website using Docker and Nginx |

These examples provide practical experience with Docker image creation for different types of applications and form the foundation for building more complex containerized projects.