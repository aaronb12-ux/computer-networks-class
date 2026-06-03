# DNS + HTTP + TCP Quiz (Clean Version)

---

## 1. What is a primary drawback of relying entirely on recursive queries at the upper levels of the DNS hierarchy?
- It causes extremely high processing and traffic load at root and TLD servers

---

## 2. Persistent HTTP response time (RTT = 40 ms)

**Question:**
A web page contains:
- 1 base HTML file
- 5 small images from the same server  
Assume transmission time is negligible and RTT = 40 ms. With persistent HTTP, after TCP connection is established, all objects use the same connection.

What is the minimum response time?

**Solution:**

Persistent HTTP steps:

```
TCP connection setup = 1 RTT = 40 ms
Request + receive HTML = 1 RTT = 40 ms
Request + receive all images = 1 RTT = 40 ms
```

Total:

```
40 + 40 + 40 = 120 ms
```

**Answer:**
- 120 ms

---

## 3. What is the primary purpose of the Receive Window (rwnd) field in TCP?

- To implement flow control by preventing the sender from overwhelming the receiver’s buffer
```
	​
