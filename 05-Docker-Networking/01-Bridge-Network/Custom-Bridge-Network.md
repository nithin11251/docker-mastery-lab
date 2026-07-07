# Custom Bridge Network

## Create Network

```bash
docker network create mynetwork
```

---

## List Networks

```bash
docker network ls
```

---

## Run Containers

```bash
docker run -d --name app1 --network mynetwork nginx
```

```bash
docker run -d --name app2 --network mynetwork ubuntu sleep infinity
```

---

## Connect Existing Container

```bash
docker network connect mynetwork app1
```

---

## Disconnect Container

```bash
docker network disconnect mynetwork app1
```

---

## Remove Network

```bash
docker network rm mynetwork
```

---

## Remove Unused Networks

```bash
docker network prune
```

---

## Inspect

```bash
docker network inspect mynetwork
```

---

## Verify DNS

Inside app2

```bash
ping app1
```

Docker resolves the container name automatically.

---

# Why Custom Bridge?

- Better Security
- Automatic DNS
- Better Isolation
- Production Ready
- Recommended for Microservices