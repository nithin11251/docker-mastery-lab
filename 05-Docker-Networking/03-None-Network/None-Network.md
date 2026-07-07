# Docker None Network

## What is None Network?

The None network completely disables networking inside the container.

```
Container

No Internet

No IP

No Network
```

---

# Run

```bash
docker run --network none ubuntu
```

---

# Check

```bash
docker inspect container_name
```

You'll notice there is no network interface except loopback (`lo`).

---

# Advantages

- Maximum Isolation
- Increased Security

---

# Disadvantages

- No Internet
- No Communication
- No External Access

---

# Use Cases

- Security Testing
- Offline Processing
- Sensitive Workloads

---

# Interview Question

Q. What happens when a container uses the None network?

The container has no network connectivity except its internal loopback interface.