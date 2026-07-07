# Docker Host Network

## What is Host Network?

Host networking removes network isolation between the container and the host.

The container shares the host's network stack.

```
Host Machine

Port 80

▲

Container

Port 80
```

There is no separate container IP.

---

# Run

```bash
docker run --network host nginx
```

No port mapping is required.

```
docker run --network host nginx
```

instead of

```
docker run -p 80:80 nginx
```

---

# Check Networks

```bash
docker network ls
```

---

# Inspect

```bash
docker network inspect host
```

---

# Advantages

- Highest Performance
- No NAT
- Low Latency

---

# Disadvantages

- Less Isolation
- Port Conflicts
- Linux only (true host networking is primarily supported on Linux)

---

# Interview Question

Q. When should Host Networking be used?

High-performance applications that require direct access to the host network.