# Docker Bridge Network

## What is Bridge Network?

Bridge is the default Docker network driver.

If you don't specify a network while creating a container, Docker automatically connects it to the default bridge network.

```
Container A
       │
       │
   Bridge Network
       │
       │
Container B
```

Containers connected to the same bridge network can communicate using their IP addresses.

---

# Types of Bridge Network

## 1. Default Bridge Network

Created automatically by Docker.

Check:

```bash
docker network ls
```

Output

```
bridge
host
none
```

Run

```bash
docker run -d --name nginx nginx
```

Docker automatically connects the container to the default bridge network.

Inspect

```bash
docker inspect nginx
```

---

## 2. User Defined Bridge Network

Create

```bash
docker network create mynetwork
```

Run Container

```bash
docker run -d --name web --network mynetwork nginx
```

```bash
docker run -d --name app --network mynetwork ubuntu sleep infinity
```

Now both containers can communicate using their container names.

Example

```
ping web
```

---

# Docker Network Commands

List Networks

```bash
docker network ls
```

Inspect Network

```bash
docker network inspect bridge
```

Create Network

```bash
docker network create mynetwork
```

Remove Network

```bash
docker network rm mynetwork
```

---

# Connect Container to Network

```bash
docker network connect mynetwork nginx
```

---

# Disconnect Container

```bash
docker network disconnect mynetwork nginx
```

---

# Verify Connection

```bash
docker inspect nginx
```

or

```bash
docker network inspect mynetwork
```

---

# Advantages

- Default Docker Network
- Container-to-Container Communication
- Easy to Create
- Supports DNS in Custom Bridge Networks

---

# Interview Questions

Q. What is the difference between Default Bridge and Custom Bridge?

Default Bridge

- Created automatically
- Limited DNS support

Custom Bridge

- Created manually
- Better DNS
- Better isolation
- Recommended for applications