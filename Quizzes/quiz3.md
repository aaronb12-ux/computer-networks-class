# Practice Problems: Networking Fundamentals

### 1. Queuing Delay of the Second Packet

**Question:** If *n* packets of length *L* arrive at a router simultaneously, and the transmission rate is *R*, what is the queuing delay of the second packet?

**Answer:** **L / R**

**Explanation:** The first packet begins transmission immediately at time 0. It takes **L / R** seconds to fully transmit. The second packet must wait for the first packet to finish before it can begin transmission.

So the queuing delay of the second packet is **L / R**.

---

### 2. File Transfer Time Calculation

**Question:** If a file is **4 × 10⁶ bits** and the throughput is **500 kbps**, what is the transfer time?

**Conversions:**
- 500 kbps = 500 × 10³ bits/s

**Formula:** Transfer Time = L / R

**Solution:**

```
4 × 10⁶ / (500 × 10³)
= 8
```

**Answer:** **8 seconds**

---

### 3. Functions of Nodal Processing Delay

**Functions of processing delay include:**
- ✓ Determining the output link
- ✓ Checking bit errors
- ✓ Checking packet headers

**NOT a function of processing delay:**
- ❌ Time waiting at the output link for transmission

**Explanation:** Waiting for transmission is part of **queueing delay**, not processing delay.

---

### 4. Go-Back-N and Out-of-Order Packets

**Question:** What does a destination do when an out-of-order packet arrives in the Go-Back-N protocol?

**Answer:**
- ✓ Drops the packet
- ✓ Sends an acknowledgement for the last correctly received packet

**Explanation:** Go-Back-N receivers do not buffer out-of-order packets.

---

### 5. Socket Type for Maximum Performance

**Question:** Which socket type is used when performance is the most important factor and a few lost packets can be ignored?

**Answer:** **SOCK_DGRAM (UDP)**

**Explanation:** UDP provides low overhead and does not guarantee delivery, making it suitable for applications such as streaming, gaming, and voice communication.

---

### 6. Client-Side Socket Functions

**Question:** What are client-side functions in a client-server architecture socket program?

**Answer:**
- ✓ send()
- ✓ receive()
- ✓ connect()

---

### 7. When Packet Arrival Rate Exceeds Service Rate

**Question:** Assume that *A* is the packet arrival rate, the transmission rate is *R*, and all packets have length *L*. What happens when:

```
L/R < A
```

**Answer:**
- ✓ Buffer fills up
- ✓ Queueing delay becomes large
- ✓ Packets may be dropped

**Explanation:** Packets are arriving faster than they can be transmitted, causing congestion.

---

### 8. Huge File Transfer Across Multiple Links

**Question:** A source wants to transfer a huge file of size **8 × 10⁶ bits** to a destination. Assuming there is no other traffic in the network, how long will the transfer take if the slowest link is **2 Mbps**?

**Given Rates:**
- 200 Mbps = 200 × 10⁶ bits/s
- 2 Mbps = 2 × 10⁶ bits/s
- 8000 kbps = 8000 × 10³ bits/s

**Formula:**

```
dTrans = L / R
```

where **R** is the transmission rate of the slowest link.

**Solution:**

```
8 × 10⁶ / 2 × 10⁶
= 4
```

**Answer:** **4 seconds**

---

### 9. Characteristics of Selective Repeat

**Question:** What are characteristics of the Selective Repeat Protocol?

**Answer:**
- ✓ The sender can have up to **N** unacknowledged packets
- ✓ The receiver buffers out-of-order packets

**Explanation:** Unlike Go-Back-N, Selective Repeat stores correctly received out-of-order packets and only retransmits missing packets.

---

### 10. What is Network Jitter?

**Question:** What is "jitter" in a network environment?

**Answer:** The variability or inconsistency in packet latency.

**Explanation:** Jitter occurs when packets experience different delays while traveling through the network, causing uneven arrival times.

---

### 11. Delays at a Network Node

**Question:** Which delays contribute to the time a packet spends at a node?

**Answer:**
- ✓ Transmission delay
- ✓ Queueing delay
- ✓ Processing delay

**Note:** Propagation delay occurs on the link itself, not at the node.

---

### 12. Propagation Delay Equals Transmission Delay

**Question:** A sender transmits a packet of length **L = 1250 bytes** over a link with transmission rate **R = 10 Mbps**. The propagation speed is **s = 2.5 × 10⁸ m/s**. At what distance **d** would the propagation delay equal the transmission delay?

**Conversions:**
- 1250 bytes = 10,000 bits
- 10 Mbps = 10 × 10⁶ bits/s

**Formulas:**

```
dProp = d / s

dTrans = L / R
```

Set them equal:

```
d / (2.5 × 10⁸)
=
10000 / (10 × 10⁶)
```

Solving for **d**:

```
d = 250,000 m
```

**Answer:** **250 km**

---

# Key Equations

### Transmission Delay

```
dTrans = L / R
```

where:
- **L** = packet length (bits)
- **R** = transmission rate (bps)

---

### Propagation Delay

```
dProp = d / s
```

where:
- **d** = distance
- **s** = propagation speed

---

### Transfer Time

```
Transfer Time = L / R
```

---

### Condition for Congestion

```
L/R < A
```

which leads to:
- Growing queues
- Larger queueing delays
- Possible packet loss
            



