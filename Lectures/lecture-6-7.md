# Transport Layer

The transport layer connects **processes** running on different hosts.

Applications write data into the **TCP send buffer**, and TCP is responsible for:

- Breaking data into segments
- Sending segments across the network
- Reassembling data at the receiver

---

## TCP Data Flow Overview

<img width="651" height="305" alt="TCP data flow" src="https://github.com/user-attachments/assets/f5634017-32ff-473e-b23f-d7849212c1e6" />

---

## TCP Properties

### Full-Duplex Communication

TCP is **full duplex**, meaning:

- Both endpoints can send and receive simultaneously
- Supports bidirectional data transfer

---

## TCP Header

- Minimum size: **20 bytes**
- Can grow larger due to optional fields

<img width="697" height="514" alt="TCP header" src="https://github.com/user-attachments/assets/63c515d9-fa26-47b5-991b-24426423f64e" />

---

## TCP Segment Structure

<img width="797" height="622" alt="TCP segment structure" src="https://github.com/user-attachments/assets/0dbb8b15-c02e-44f3-a4b2-6f274dbbf2be" />

---

# TCP Sequence Numbers and ACKs

## TCP Sequence Numbers (1 of 2)

<img width="703" height="332" alt="TCP sequence numbers 1" src="https://github.com/user-attachments/assets/c58a6ac3-685d-465b-b829-47d0828d74dc" />

---

## TCP Sequence Numbers (2 of 2)

TCP operates at the **byte level**, not the packet level.

Key properties:

- Uses **cumulative ACKs**
- **Selective ACKs (SACK)** are used when necessary

---

## Key Relationship

```text
Sequence number of sender segment
= ACK number expected from receiver side
```

---

## Receiver Behavior

- TCP buffers **out-of-order segments**
- Combines behavior of:
  - Go-Back-N (cumulative ACKs)
  - Selective Repeat (buffering out-of-order data)

---

# TCP Round Trip Time (RTT) and Timeout

## Question

How should TCP set its timeout value?

---

## Timeout Mechanism

- Timer is set for the **oldest unacknowledged segment**

### If timeout is:

#### Too short:
- Causes unnecessary retransmissions

#### Too long:
- Slow recovery from packet loss
- Poor utilization of bandwidth

---

## Key Idea

Timeout should be based on RTT and adapt dynamically:

```text
Timeout ≈ Estimated RTT + safety margin
```

TCP continuously adjusts this based on observed network conditions.

---

## Important Insight

- RTT is not constant
- TCP must continuously estimate it
- Timeout must adapt to avoid:
  - Overreacting (too many retransmissions)
  - Underreacting (slow recovery)

---
  
