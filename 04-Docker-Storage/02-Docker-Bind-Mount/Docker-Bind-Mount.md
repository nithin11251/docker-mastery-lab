# Docker Bind Mount

## What is a Bind Mount?

A Bind Mount maps a folder or file from the Host Machine directly into the Container.

Unlike Docker Volumes, Docker does not manage the storage.

The host directory is used directly.

---

# Why Use Bind Mount?

Perfect for development.

Whenever you edit files on your computer, the changes are immediately visible inside the container.

No image rebuild is required.

---

# Volume vs Bind Mount

| Docker Volume | Bind Mount |
|--------------|------------|
| Managed by Docker | Managed by Host OS |
| Stored inside Docker | Stored on Host Machine |
| Better for Production | Better for Development |

---

# Folder Structure

```
project/

├── index.html
```

index.html

```html
<h1>Hello Docker Bind Mount</h1>
```

---

# Run Nginx

```bash
docker run -d \
--name nginx-bind \
-p 8080:80 \
-v ${PWD}:/usr/share/nginx/html \
nginx
```

Linux / macOS

```bash
-v $(pwd):/usr/share/nginx/html
```

Windows PowerShell

```powershell
-v ${PWD}:/usr/share/nginx/html
```

---

# Explanation

```
Host Folder

project/

↓

Mapped To

↓

Container

/usr/share/nginx/html
```

Whenever you edit

```
index.html
```

The browser updates after refresh.

No need to rebuild the image.

---

# Practical Example

Before

```
<h1>Hello</h1>
```

Browser

```
Hello
```

Edit

```
<h1>Welcome to Docker</h1>
```

Save

Refresh Browser

```
Welcome to Docker
```

No Docker build required.

---

# Advantages

- Instant File Synchronization
- Great for Development
- No Rebuild Required
- Easy Debugging

---

# Real-World Usage

- React
- Angular
- Vue
- Node.js
- Spring Boot
- Python Flask
- Django

Developers use Bind Mounts daily.

---

# Interview Question

Q. What is the difference between a Docker Volume and a Bind Mount?

Volume

- Docker manages storage.
- Best for Production.
- Used for databases.

Bind Mount

- Host manages storage.
- Best for Development.
- Used for source code.

---

# Key Points

✔ Host Directory

✔ Live Synchronization

✔ Development Friendly

✔ No Image Rebuild

✔ Faster Development