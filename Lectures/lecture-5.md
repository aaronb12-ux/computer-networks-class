# Network Performance Measurement

Network performance is commonly measured using:

- Delay (Latency)
- Packet Loss
- Throughput
- Bandwidth-Delay Product (BDP)
- TCP Window Size
- Jitter

---

# Delays

A packet experiences several different types of delay as it travels through a network.

## Types of Delay

### Processing Delay

The time required for a router or host to:

- Examine the packet header
- Check for bit errors
- Determine where to forward the packet

---

### Queueing Delay

The time a packet spends waiting in a queue before it can be transmitted.

Queueing delay depends on:

- Current network traffic
- Queue length
- Link utilization

---

### Transmission Delay

The time required to place all packet bits onto the link.

Transmission delay depends on:

- Packet size
- Link transmission rate

Formula:

:contentReference[oaicite:0]{index=0}

Where:

- \(L\) = packet length (bits)
- \(R\) = transmission rate (bits/sec)

---

### Propagation Delay

The time required for the signal to physically travel across the link.

Depends on:

- Distance between nodes
- Propagation speed of the medium

Formula:

:contentReference[oaicite:1]{index=1}

Where:

- \(d\) = distance
- \(s\) = propagation speed

---

# Packet Delay: Four Sources

<img width="594" height="348" alt="Packet Delay Sources" src="https://github.com/user-attachments/assets/b9f53d3d-57f2-43f0-92d5-dceb34f86f10" />

<img width="676" height="350" alt="Packet Delay Example" src="https://github.com/user-attachments/assets/20ef8378-1ee7-49f9-94d5-cd72fb23a6da" />

### Total Nodal Delay

A packet's total delay at a router is:

```text
Processing Delay
+ Queueing Delay
+ Transmission Delay
+ Propagation Delay
```

Or:

```text
dnodal = dproc + dqueue + dtrans + dprop
```

---

# Packet Loss

Packet loss occurs when packets arrive at a full queue (buffer).

Since buffers have finite capacity:

```text
Queue Full
    ↓
Packet Dropped
```

---

## Packet Loss Scenario

<img width="469" height="180" alt="Packet Loss" src="https://github.com/user-attachments/assets/d3ae1af7-1024-4050-8a64-e3f71a828e57" />

### Variables

- **A** = Average arrival rate
- **R** = Transmission rate
- **L** = Packet length

---

## Ideal Case

Packets leave faster than they arrive.

```text
A < R/L
```

Result:

- Little or no queueing
- No packet loss

---

## Congested Case

Packets arrive faster than they can be transmitted.

```text
A > R/L
```

Result:

- Growing queues
- Increased delay
- Possible packet loss

### Key Idea

When incoming traffic exceeds outgoing capacity:

```text
Arrival Rate > Service Rate
```

queue lengths continue to grow until packets are dropped.

---

# Throughput

## Definition

Throughput is the rate at which data is successfully delivered from sender to receiver.

Usually measured in:

- bits/sec (bps)
- Kbps
- Mbps
- Gbps

---

## Network Scenario

<img width="767" height="354" alt="Throughput Example" src="https://github.com/user-attachments/assets/6925572e-55e0-49f5-8ba0-18d0fdd8ad54" />

### Key Concept

The slowest link determines the end-to-end throughput.

Example:

```text
Sender ---- 100 Mbps ---- Router ---- 10 Mbps ---- Receiver
```

Effective throughput:

```text
10 Mbps
```

This is often called the **bottleneck link**.

---

# Bandwidth-Delay Product (BDP)

## Definition

The Bandwidth-Delay Product (BDP) is the maximum amount of data that can be "in flight" on a network path at any given time.

"In flight" means:

- Sent by the sender
- Not yet acknowledged

---

## Formula

:contentReference[oaicite:2]{index=2}

Where:

- **Bandwidth** = link capacity
- **RTT** = Round-Trip Time

---

## Why It Matters

BDP tells us:

```text
How much data the sender should keep in transit
```

to fully utilize the network.

Large bandwidth + large RTT:

```text
Large BDP
```

which means more data must be in flight to achieve maximum throughput.

---

## Visualization

<img width="775" height="269" alt="Bandwidth Delay Product" src="https://github.com/user-attachments/assets/b072a7b9-10ea-4812-8b82-3c8a1cd1e805" />

---

# TCP Sliding Window

TCP uses a **sliding window** mechanism to keep multiple packets in flight simultaneously.

---

## Core Idea

TCP maintains a window called:

```text
cwnd (Congestion Window)
```

Data inside the window may be transmitted.

---

## Operation

1. Sender transmits packets within the current window
2. Sender waits for ACKs
3. ACK for the earliest packet arrives
4. Window slides forward
5. New packets enter the window
6. Sender transmits additional packets

---

## Dynamic Window Growth

TCP dynamically adjusts the window size:

### No Congestion

```text
Window grows
```

Result:

- More packets in flight
- Higher throughput

### Congestion Detected

```text
Window shrinks
```

Result:

- Reduced traffic load
- Helps avoid network collapse

---

## Visualization

<img width="456" height="450" alt="TCP Sliding Window" src="https://github.com/user-attachments/assets/71fced19-ca59-4aa9-902c-d13e58829019" />

---

# Jitter

## Definition

Jitter is the variation in packet delay over time.

While latency measures:

```text
How long packets take to arrive
```

jitter measures:

```text
How much that delay changes
```

between packets.

---

## Example

Suppose packet delays are:

```text
20 ms
21 ms
19 ms
22 ms
```

Low jitter.

Now suppose delays are:

```text
20 ms
60 ms
15 ms
80 ms
```

High jitter.

---

## Effects of High Jitter

High jitter can cause problems for real-time applications:

### Voice Calls (VoIP)

- Choppy audio
- Robotic voices

### Video Conferencing

- Frozen video
- Audio/video desynchronization

### Online Gaming

- Lag spikes
- Inconsistent gameplay

---

# Summary

| Metric | Description |
|----------|------------|
| Processing Delay | Time to process packet headers |
| Queueing Delay | Time spent waiting in a queue |
| Transmission Delay | Time required to place bits on the link |
| Propagation Delay | Time required for signals to travel through the medium |
| Packet Loss | Packets dropped due to full buffers |
| Throughput | Rate of successful data delivery |
| BDP | Maximum amount of data that can be in flight |
| TCP Sliding Window | Mechanism for pipelined transmission |
| Jitter | Variation in packet delay |

---

## Key Formulas

### Transmission Delay

```text
Dtrans = L / R
```

Where:

- `L` = Packet Length (bits)
- `R` = Transmission Rate (bits/sec)

---

### Propagation Delay

```text
Dprop = d / s
```

Where:

- `d` = Distance between nodes
- `s` = Propagation speed of the medium

---

### Total Nodal Delay

```text
dnodal = dproc + dqueue + dtrans + dprop
```

Where:

- `dproc` = Processing Delay
- `dqueue` = Queueing Delay
- `dtrans` = Transmission Delay
- `dprop` = Propagation Delay

---

### Bandwidth-Delay Product (BDP)

```text
BDP = Bandwidth × RTT
```

Where:

- `Bandwidth` = Link capacity
- `RTT` = Round-Trip Time
  
