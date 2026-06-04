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

---

## 4. Stop-and-wait utilization

**Given:**
- Packet size = 8000 bits  
- Link rate = 1 Gbps = 1 × 10^9 bps  
- RTT = 20 ms = 0.02 s  

**Step 1: Transmission time**

```
Transmission time = packet size / link rate
                  = 8000 / (1 × 10^9)
                  = 8 × 10^-6 s
```

**Step 2: Utilization**

```
Utilization = Transmission time / (RTT + Transmission time)
```

```
= (8 × 10^-6) / (0.02 + 8 × 10^-6)
≈ 0.0004
≈ 0.04%
```

**Answer:**
- 0.04%

---

## 5. What fields are included in the UDP segment header?
- Source port  
- Destination port  
- Length  
- Checksum  

---

## 6. What is the main improvement of rdt3.0 over rdt2.0?
- It can recover from lost packets and lost ACKs using timeouts and retransmissions

---

## 7. TCP duplicate ACKs

**Question:**
A TCP sender receives three duplicate ACKs for the same byte. What does this usually suggest?

**Answer:**
- A segment after that ACK is likely missing (packet loss detected)

---

# 📌 Key Formulas / Equations

## Stop-and-Wait Utilization

```
Utilization = Transmission time / (RTT + Transmission time)
```

```
Transmission time = Packet size / Link rate
```

---

## RTT Conversion

```
1 ms = 0.001 s
20 ms = 0.02 s
40 ms = 0.04 s
```

---

## Throughput (TCP window-based)

```
Throughput = Window size / RTT
```

---

## Bandwidth conversion

```
1 Gbps = 10^9 bps
1 Mbps = 10^6 bps
1 kbps = 10^3 bps
```

---

## TCP ACK rule

```
ACK number = next byte expected
```

---

## Stop-and-wait key intuition

```
Sender utilization is low when RTT >> transmission time
```




	​






	​
