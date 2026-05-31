# Transport Layer

## Two Principal Internet Transport Protocols

### TCP (Transmission Control Protocol)

- Connection-oriented
- Reliable data transfer
- Uses acknowledgments, retransmissions, flow control, and congestion control

### UDP (User Datagram Protocol)

- Connectionless
- Minimal overhead
- Best-effort delivery
- No built-in reliability

---

# Connection-Oriented Demultiplexing

A TCP socket is identified by a **4-tuple**:

```text
(Source IP Address, Source Port Number,
 Destination IP Address, Destination Port Number)
```

### Demultiplexing (Demux)

The receiver uses all four values in the 4-tuple to direct an incoming TCP segment to the correct socket.

### Multiple Simultaneous TCP Connections

A server may support many TCP connections simultaneously:

- Each socket is identified by its own 4-tuple
- Each socket is associated with a different client

---

## Connection-Oriented Demultiplexing Example

<img width="436" height="241" alt="Connection-Oriented Demultiplexing Example" src="https://github.com/user-attachments/assets/59a264a7-3fa2-4326-95e7-459260078ecb" />

### Key Observation

Three segments are all destined for:

```text
Destination IP = B
Destination Port = 80
```

Yet they are demultiplexed into different sockets because they have different:

- Source IP addresses
- Source port numbers

The complete 4-tuple uniquely identifies each TCP connection.

---

# Continuation of rdt3.0

## Performance of rdt3.0 (Stop-and-Wait)

### Sender Utilization

```text
Usender = Fraction of time the sender is busy transmitting
```

### Example

Given:

- Link rate = 1 Gbps
- Propagation delay = 15 ms
- Packet size = 8000 bits

### Transmission Delay

Transmission delay is:

:contentReference[oaicite:0]{index=0}

Substituting values:

```text
Dtrans = 8000 bits / 10^9 bits/sec
       = 8 × 10^-6 sec
       = 8 microseconds
```

**Note:**

```text
1 Gbps = 10^9 bits/sec
```

---

# rdt3.0: Stop-and-Wait Operation

## Operation

The sender:

1. Sends one packet
2. Waits for an ACK
3. Sends the next packet only after the ACK arrives

Reliability is achieved through:

- ACKs
- Timeouts
- Retransmissions

---

## Issues with Stop-and-Wait

At most:

```text
1 unacknowledged packet
```

can exist in the network at any time.

This means:

- Sender spends much of its time waiting
- Network resources are underutilized
- Throughput is limited

### Takeaway

Stop-and-Wait is:

✅ Reliable

❌ Inefficient on high-speed or high-latency links

---

## rdt3.0: Stop-and-Wait Operation (2 of 2)

### Transmission Delay

:contentReference[oaicite:1]{index=1}

### RTT

RTT stands for:

```text
Round-Trip Time
```

The time required for:

1. A packet to travel to the receiver
2. The ACK to return to the sender

<img width="735" height="438" alt="Stop-and-Wait Timing Diagram" src="https://github.com/user-attachments/assets/9ae7a174-853e-49b9-8821-90b4f2236d44" />

---

# Pipelining: Increased Utilization

## Motivation

Instead of waiting for an ACK after every packet:

- Send multiple packets before ACKs arrive
- Allow several packets to be "in flight" simultaneously

### Benefits

- Higher utilization
- Better throughput
- Better use of available bandwidth

---

## Data Pipelining Requirements

### Sequence Numbers

Must be expanded so multiple packets can be tracked simultaneously.

### Buffering

Required at:

- Sender
- Receiver
- Or both

<img width="716" height="435" alt="Pipelining" src="https://github.com/user-attachments/assets/a0bb69ad-bec2-4821-a7a4-b6ed385f3313" />

### Important

Pipelining leads to protocols such as:

- Go-Back-N (GBN)
- Selective Repeat (SR)

---

# Go-Back-N (GBN)

## Sender

The sender maintains a **window** of up to **N** transmitted but unacknowledged packets.

### Sequence Numbers

Packets contain a k-bit sequence number.

<img width="612" height="156" alt="GBN Sender Window" src="https://github.com/user-attachments/assets/120b3955-8073-4bf1-a2ad-24697ff074d5" />

### Important Variables

#### `base`

```text
Oldest unacknowledged packet
```

#### `nextseqnum`

```text
Sequence number of the next packet to send
```

### Sender Window

The sender may transmit packets in:

```text
[base, base + N - 1]
```

This enables packet pipelining.

---

# Go-Back-N Receiver

The receiver focuses on **in-order delivery**.

### Behavior

- Accepts packets that arrive in order
- Delivers them to the upper layer
- Does not buffer out-of-order packets

### Out-of-Order Packets

Any out-of-order packet is:

```text
Discarded
```

<img width="640" height="131" alt="GBN Receiver" src="https://github.com/user-attachments/assets/b893b751-45d9-4069-8aa7-e0b857dec14f" />

### ACK Behavior

If an out-of-order packet arrives:

```text
Send ACK(last correctly received packet)
```

Equivalent to:

```text
ACK(x - 1)
```

where `x` is the expected sequence number.

---

# Go-Back-N in Action

### Sender Behavior

If ACK `y` (the base packet) is not received before timeout:

```text
Retransmit packet y
Retransmit all packets after y
```

that were sent but not yet acknowledged.

**Note:** `x` and `y` represent sequence numbers.

<img width="506" height="284" alt="GBN Example" src="https://github.com/user-attachments/assets/bb566615-1993-42b8-a418-d125cbe16738" />

### Receiver Behavior

If packet `x` is expected but packet `x + n` arrives (`n > 0`):

1. Discard packet `x + n`
2. Send:

```text
ACK(x - 1)
```

### Main Drawback

If one packet is lost:

```text
Many packets may need retransmission
```

even if only one packet was actually lost.

---

# Selective Repeat (SR)

## Motivation

Selective Repeat improves efficiency by retransmitting only lost packets.

### Key Idea

Instead of retransmitting an entire window:

```text
Retransmit only the missing packet
```

---

## Characteristics

### Sender

- Maintains a separate timer for each packet
- Tracks acknowledgments individually

### Receiver

- Accepts out-of-order packets
- Buffers them
- Sends ACKs individually

### Takeaway

Selective Repeat is:

✅ More efficient

❌ More complex

because it requires:

- Buffering
- Individual timers
- Additional bookkeeping

---

# Selective Repeat: Sender and Receiver Windows

<img width="530" height="182" alt="Selective Repeat Windows" src="https://github.com/user-attachments/assets/f6bba887-92e8-4073-a583-a5f4a9cc9a0c" />

### Difference from Go-Back-N

Selective Repeat includes a **receiver window**.

The receiver can accept packets within its window even if they arrive out of order.

---

# Selective Repeat: Sender and Receiver

## Sender

- Sends packets whose sequence numbers fall within the sender window
- Maintains a timer for every packet
- Retransmits only timed-out packets
- Slides the window when the lowest outstanding packet is acknowledged
- Ignores duplicate ACKs

---

## Receiver

Maintains a receiver window:

```text
[rcvbase, rcvbase + N - 1]
```

### Receiver Behavior

- Sends an ACK for every correctly received packet within the window
- Buffers out-of-order packets
- Delivers packets in order when missing packets arrive
- If duplicate packets arrive:
  - ACK them
  - Discard the duplicates

---

# Selective Repeat in Action

<img width="803" height="619" alt="Selective Repeat Example" src="https://github.com/user-attachments/assets/1a597adb-909e-4709-b16c-7adb6166b055" />

---

# Go-Back-N vs Selective Repeat

<img width="608" height="354" alt="GBN vs Selective Repeat" src="https://github.com/user-attachments/assets/bbb374be-577c-4e97-94bf-3202fb00d03e" />

| Feature | Go-Back-N | Selective Repeat |
|----------|------------|------------------|
| Receiver buffers out-of-order packets | No | Yes |
| Retransmission strategy | Retransmit many packets | Retransmit only lost packets |
| Receiver window | No | Yes |
| Timer usage | One timer (oldest unACKed packet) | One timer per packet |
| Complexity | Lower | Higher |
| Efficiency | Lower | Higher |

---

# Summary

### Stop-and-Wait

- One packet in flight at a time
- Reliable but inefficient

### Pipelining

- Multiple packets in flight simultaneously
- Improves utilization and throughput

### Go-Back-N

- Sender window only
- Discards out-of-order packets
- Retransmits multiple packets after a timeout

### Selective Repeat

- Sender and receiver windows
- Buffers out-of-order packets
- Retransmits only lost packets
- More efficient but more complex

