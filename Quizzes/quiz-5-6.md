# Quiz Review

## Question 1: Which situation is mainly handled by flow control?

**Answer:**
- A receiver buffer is limited

---

## Question 2: What can be caused by network congestion?

**Answer:**
- Long queueing delay
- Extra retransmissions
- Packet loss

---

## Question 3: If the receiver window is not limiting, what mainly controls TCP's sending rate?

**Answer:**
- cwnd (congestion window)

---

## Question 4 & 5

**Question:**
A receiver has a total buffer size RcvBuffer = 1000 bytes. The last byte received is 800, and the last byte read by the application is 500.

The sender has cwnd = 600 bytes, and the RTT is 100 ms.

What is the maximum amount of unacknowledged data allowed and what is the throughput?

**Solution:**

Receiver window:

```text
rwnd = RcvBuffer - (LastByteRcvd - LastByteRead)

rwnd = 1000 - (800 - 500)
rwnd = 1000 - 300
rwnd = 700 bytes
```

Maximum unacknowledged data:

```text
min(cwnd, rwnd)

min(600, 700)
= 600 bytes
```

Throughput:

```text
600 bytes = 4800 bits

RTT = 100 ms = 0.1 s

Throughput = 4800 / 0.1
           = 48,000 bps
```

**Answer:**
- Maximum unacknowledged data = 600 bytes
- Throughput = 48,000 bps

---

## Question 6

**Question:**
A TCP connection has cwnd = 18 KB and RTT = 90 ms. Ignoring loss, what is the approximate throughput?

**Solution:**

```text
90 ms = 0.09 s

Throughput = Window Size / RTT

Throughput = 18 KB / 0.09
           = 200 KB/s
```

**Answer:**
- 200 KB/s

---

## Question 7

**Question:**
TCP starts slow start with cwnd = 1 MSS. If no loss occurs and ssthresh is not reached, what is cwnd after 4 RTTs?

**Solution:**

Slow start doubles cwnd every RTT.

```text
Start: 1 MSS

After RTT 1: 2 MSS
After RTT 2: 4 MSS
After RTT 3: 8 MSS
After RTT 4: 16 MSS
```

**Answer:**
- 16 MSS

---

## Question 8

**Question:**
Suppose cwnd = 18 MSS when TCP Tahoe receives triple duplicate ACKs. What happens next?

**Solution:**

```text
ssthresh = cwnd / 2
         = 18 / 2
         = 9 MSS

Tahoe resets:

cwnd = 1 MSS
```

**Answer:**
- ssthresh = 9 MSS
- cwnd = 1 MSS

---

## Question 9

**Question:**
For TCP Reno, which event usually causes cwnd to reset to 1 MSS?

**Answer:**
- A timeout

---

## Question 10

**Question:**
For TCP Reno, suppose loss occurs when the congestion window reaches W = 20 MSS, and the RTT is 100 ms. What is the approximate average throughput?

**Solution:**

TCP Reno forms a sawtooth between:

```text
Maximum cwnd = 20 MSS
Minimum cwnd = 10 MSS
```

Average cwnd:

```text
(20 + 10) / 2
= 15 MSS
```

Throughput:

```text
RTT = 0.1 s

Throughput = 15 / 0.1
           = 150 MSS/s
```

**Answer:**
- 150 MSS/s

---

## Question 11

**Question:**
Which statements are true about end-to-end congestion control?

**Answer:**
- Congestion is usually inferred from endpoint observations
- TCP may lower its sending rate after detecting congestion
- Packet loss or duplicate ACKs can act as congestion signals

---

## Question 12

**Question:**
A university campus network supports:

- A live VR graduation ceremony
- A cloud-based AI homework assistant

Which switching approach best matches each application?

**Answer:**

### VR Ceremony → Circuit Switching

Reason:
- Dedicated resources
- Predictable delay
- Low jitter

### AI Homework Assistant → Packet Switching

Reason:
- Bursty traffic
- Shared resources
- Better utilization

---

## Question 13

**Question:**
Why is the Best-Effort service model considered successful despite its lack of guarantees?

**Answer:**
- Sufficient bandwidth often makes performance "good enough"
- Simplicity enabled widespread deployment
- Transport-layer protocols help manage loss

---

## Question 14

**Question:**
Which scheduling policies do not have fairness as part of their design?

**Answer:**
- Strict Priority
- FCFS (First Come First Served)

---

## Question 15

**Question:**
A WFQ scheduler manages three queues with weights:

```text
W1 = 2
W2 = 3
W3 = 5
```

Link rate = 20 Gbps

What bandwidth is allocated to Queue 2?

**Solution:**

```text
Total Weight = 2 + 3 + 5
             = 10

Queue 2 Share = 3 / 10

Bandwidth = (3 / 10) × 20
          = 6 Gbps
```

**Answer:**
- 6 Gbps

---

## Question 16

**Question:**
Compared to circuit switching, what are advantages of packet switching?

**Answer:**
- Better resource utilization
- No call setup required
- Efficient for bursty traffic

---

## Question 17

**Question:**
A 2 Gb/s link is shared among users who each need 200 Mb/s when active and are active 10% of the time.

With circuit switching, how many users can be supported?

**Solution:**

Circuit switching ignores activity percentage.

```text
2 Gb/s = 2000 Mb/s

Users = 2000 / 200
      = 10
```

**Answer:**
- 10 users

---

## Question 18

**Question:**
Why does the 10% activity not matter in the previous question?

**Answer:**

In circuit switching:

- Bandwidth is reserved
- Each user gets a dedicated circuit
- Activity percentage only matters in packet switching

---

## Question 19

**Question:**
A sender is transmitting data over TCP.

```text
cwnd = 120 KB
rwnd = 150 KB
One-way delay = 20 ms
ACK delay = 20 ms
```

Assuming no losses, what is the throughput?

**Solution:**

Effective window:

```text
min(cwnd, rwnd)

min(120 KB, 150 KB)
= 120 KB
```

RTT:

```text
20 ms + 20 ms
= 40 ms
= 0.04 s
```

Convert to bits:

```text
120 KB = 120 × 1024
       = 122,880 bytes

Bits = 122,880 × 8
     = 983,040 bits
```

Throughput:

```text
983,040 / 0.04
= 24,576,000 bps

≈ 24 Mbps
```

**Answer:**
- 24 Mbps

---

## Question 20

**Question:**
What are consequences of queueing at an output port?

**Answer:**
- Increased end-to-end delay
- Potential packet loss due to full buffers
- Variable wait times depending on arrival rate
- Jitter

## Question 21

**Question**
In a generic router architecture, what components belong to the control plane (routing plane)? 

The routing processor that runs routing protocols
creating the routing table


