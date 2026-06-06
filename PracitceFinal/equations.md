# Networking Conversions & Key Formulas

---

## 📌 Unit Conversions

```
1 Gbps = 1 × 10^9 bps
1 Mbps = 1 × 10^6 bps
1 Kbps = 1 × 10^3 bps
```

```
1 ms = 0.001 s
```

---

## 📌 Transmission Delay

```
dtrans = L / R
```

Where:
- L = packet/frame length (bits)
- R = transmission rate (bps)

---

## 📌 Propagation Delay

```
dprop = D / S
```

Where:
- D = distance (meters)
- S = propagation speed (m/s)

---

## 📌 Total Link Delay

```
Total delay = transmission delay
            + propagation delay
            + queueing delay
            + processing delay
```

---

## 📌 Stop-and-Wait Utilization

```
U = dtrans / (RTT + dtrans)
```

Where:
- RTT = round-trip time
- dtrans = transmission time

---

## 📌 CSMA/CD Efficiency

### Step 1: Compute ratio

```
a = dprop / dtrans
```

Example:
```
a = 10 µs / 120 µs
  = 0.0833
```

### Step 2: Efficiency formula

```
Efficiency ≈ 1 / (1 + 5a)
```

---

## 📌 TCP Congestion Control

### Slow Start
- Begin with `cwnd = 1 MSS`
- Double cwnd each RTT until `cwnd >= ssthresh`

### Congestion Avoidance
- Once `cwnd >= ssthresh`, increase by 1 MSS per RTT

### On Loss (3 duplicate ACKs)
```
ssthresh = cwnd / 2
```

- **Tahoe:** cwnd → 1 MSS, restart slow start
- **Reno:** cwnd → ssthresh + 3, enter congestion avoidance

### On Timeout
```
ssthresh = cwnd / 2
cwnd → 1 MSS  (both Tahoe and Reno)
```

---

## 📌 TCP Flow Control

```
Sender's allowed window = min(cwnd, rwnd)
```

Where:
- cwnd = congestion window (sender-side)
- rwnd = receiver advertised window (receiver buffer space)

---

## 📌 Distance-Vector Routing (Bellman-Ford)

```
D(x, y) = min over v { c(x, v) + D(v, y) }
```

Where:
- c(x, v) = cost of link from x to neighbor v
- D(v, y) = neighbor v's advertised distance to destination y

---

## 📌 Weighted Fair Queueing (WFQ)

```
Rate(i) = W(i) / sum(W) × Link Rate
```

Where:
- W(i) = weight of queue i
- sum(W) = sum of weights of all **active** (backlogged) queues

Example (120 Mbps link, weights 1:2:3, all active):
```
sum(W) = 6
Q1 = (1/6) × 120 = 20 Mbps
Q2 = (2/6) × 120 = 40 Mbps
Q3 = (3/6) × 120 = 60 Mbps
```

---

## 📌 Key Intuition

- Higher propagation delay → worse CSMA/CD efficiency
- Higher transmission time (larger frames) → better CSMA/CD efficiency
- Efficiency depends heavily on `a = dprop / dtrans`
- TCP slow start is exponential; congestion avoidance is linear
- WFQ only counts **active** queues when dividing bandwidth



