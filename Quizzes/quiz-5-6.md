# TCP + Networking Practice Quiz (Clean Version)

---

## 1. Which situation is mainly handled by flow control?
- A receiver buffer is limited

---

## 2. What can be caused by network congestion?
- Long queueing delay  
- Extra retransmissions  
- Packet loss  

---

## 3. If the receiver window is not limiting, what mainly controls TCP's sending rate?
- cwnd (congestion window)

---

## 4. Receiver window calculation

```
RcvBuffer = 1000
LastByteRcvd = 800
LastByteRead = 500

rwnd = 1000 - (800 - 500)
rwnd = 1000 - 300
rwnd = 700 bytes
```

---

## 5. Max unacknowledged data + throughput

```
cwnd = 600 bytes
rwnd = 700 bytes

Max unacknowledged data = min(600, 700) = 600 bytes

RTT = 100 ms = 0.1 s

600 bytes = 600 * 8 = 4800 bits

Throughput = 4800 / 0.1 = 48,000 bps
```

✔ Answer: 600 bytes; 48,000 bps

---

## 6. TCP throughput (18 KB, RTT = 90 ms)

```
RTT = 0.09 s

Throughput = 18 KB / 0.09
= 200 KB/s
```

---

## 7. Slow start cwnd after 4 RTTs

```
Start cwnd = 1 MSS

RTT 1: 2 MSS
RTT 2: 4 MSS
RTT 3: 8 MSS
RTT 4: 16 MSS
```

✔ Answer: 16 MSS

---

## 8. TCP Tahoe (cwnd = 18 MSS, triple duplicate ACKs)

```
ssthresh = 18 / 2 = 9 MSS
cwnd = 1 MSS
```

✔ Answer: ssthresh = 9 MSS, cwnd = 1 MSS

---

## 9. TCP Reno: event that resets cwnd to 1 MSS
- Timeout

---

## 10. TCP Reno average throughput

```
W = 20 MSS
min = 10 MSS
max = 20 MSS

Average cwnd = (20 + 10) / 2 = 15 MSS

RTT = 0.1 s

Throughput = 15 / 0.1 = 150 MSS/s
```

---

## 11. True statements about congestion control
- Congestion is inferred from endpoints  
- TCP reduces sending rate when congestion is detected  
- Loss or duplicate ACKs signal congestion  

---

## 12. Application vs switching type

VR Ceremony → Circuit Switching  
AI Assistant → Packet Switching  

---

## 13. Why best-effort works
- Enough bandwidth makes performance acceptable  
- Simple design enables scalability  
- Transport layer handles reliability  

---

## 14. Scheduling policies without fairness
- Strict Priority  
- FCFS  

---

## 15. WFQ bandwidth allocation

```
Weights: 2, 3, 5
Total = 10

Queue 2 share = (3 / 10) * 20 = 6 Gbps
```

---

## 16. Advantages of packet switching
- Better resource utilization  
- No setup delay  
- Efficient for bursty traffic  

---

## 17. Circuit switching capacity

```
Link = 2 Gb/s = 2000 Mb/s
Each user = 200 Mb/s

2000 / 200 = 10 users
```

---

## 18. Circuit switching note
- Ignore 10% activity (only relevant for packet switching)

---

## 19. TCP throughput (window-limited)

```
cwnd = 120 KB
rwnd = 150 KB

Effective window = 120 KB

RTT = 20 ms + 20 ms = 40 ms = 0.04 s

120 KB = 120 * 1024 = 122,880 bytes
Bits = 122,880 * 8 = 983,040 bits

Throughput = 983,040 / 0.04
= 24,576,000 bps ≈ 24 Mbps
```

---

## 20. Consequences of queueing at output port
- Increased delay  
- Packet loss when buffer fills  
- Jitter (variable delay)
  
