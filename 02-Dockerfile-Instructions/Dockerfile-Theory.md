# Dockerfile Instructions Quick Notes

## 1. FROM

Purpose:
Selects the base image.

Example:

```dockerfile
FROM ubuntu:24.04
```

---

## 2. RUN

Purpose:
Executes commands during image build.

Example:

```dockerfile
RUN apt-get update
RUN apt-get install -y nginx
```

---

## 3. WORKDIR

Purpose:
Sets the current working directory.

Example:

```dockerfile
WORKDIR /app
```

---

## 4. COPY

Purpose:
Copies files from local machine to image.

Example:

```dockerfile
COPY sample.py /app
```

---

## 5. ADD

Purpose:
Copies files and can extract archives automatically.

Example:

```dockerfile
ADD app.tar.gz /app
```

---

## 6. ENV

Purpose:
Creates runtime environment variables.

Example:

```dockerfile
ENV PORT=8080
```

Access:

```bash
echo $PORT
```

---

## 7. ARG

Purpose:
Creates build-time variables.

Example:

```dockerfile
ARG VERSION=1.0
```

Build:

```bash
docker build --build-arg VERSION=2.0 .
```

---

## 8. EXPOSE

Purpose:
Documents which port the application uses.

Example:

```dockerfile
EXPOSE 8080
```

Important:

EXPOSE does not publish ports.

Use:

```bash
docker run -p 8080:8080 image
```

---

## 9. LABEL

Purpose:
Stores image metadata.

Example:

```dockerfile
LABEL author="Nithin"
LABEL version="1.0"
```

---

## 10. USER

Purpose:
Runs container as a specific user.

Example:

```dockerfile
RUN useradd appuser

USER appuser
```

---

## 11. VOLUME

Purpose:
Persists data outside the container.

Example:

```dockerfile
VOLUME /data
```

Useful for:

- MySQL
- PostgreSQL
- MongoDB

---

## 12. CMD

Purpose:
Default command executed when container starts.

Example:

```dockerfile
CMD ["python","app.py"]
```

Can be overridden:

```bash
docker run image ls
```

---

## 13. ENTRYPOINT

Purpose:
Makes container behave like an executable.

Example:

```dockerfile
ENTRYPOINT ["python"]
CMD ["app.py"]
```

Result:

```bash
python app.py
```

---

# CMD vs ENTRYPOINT

CMD:
Default command.
Can be overridden.

ENTRYPOINT:
Fixed command.
Cannot be easily overridden.

Example:

```dockerfile
ENTRYPOINT ["python"]
CMD ["app.py"]
```

docker run image

Runs:

```bash
python app.py
```

docker run image test.py

Runs:

```bash
python test.py
```

---

# Build Command

```bash
docker build -t myimage .
```

# Run Command

```bash
docker run myimage
```

# Port Mapping

```bash
docker run -p 8080:80 image
```

Host Port:

```text
8080
```

Container Port:

```text
80
```