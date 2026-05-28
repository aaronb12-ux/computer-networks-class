## Link Layer: Quiz Study Guide

---

## Key Concepts

**Nodes:** Hosts, switches, routers

**Links:** Communication channels connecting adjacent nodes
- Wired (Ethernet) or wireless (WiFi)

**Link Layer Responsibility:** Hop-by-hop delivery
- **Network Layer:** Decides where packet should go
- **Link Layer:** Determines how to move packets across each link

---

## Link Layer Context

**Multi-link communication:**
- End-to-end communication may traverse multiple links
- Different links may use different technologies
- Different protocols may provide different services
- Example: Laptop → WiFi → Access Point → Ethernet → PC

---

## Link Layer Services

### Core Services:
**Framing:** Encapsulates datagram into frame

**Link Access:** Control access to shared medium

**MAC Addressing:** Source and destination MAC addresses identify devices

**Reliable Delivery:** Optional retransmission between adjacent nodes
- Avoids expensive end-to-end retransmissions
- Particularly useful for wireless links (higher error rates)

### Additional Services:
**Flow Control:** Prevent sender from overwhelming receiver

**Error Detection:** Detect corrupted frames

**Error Correction:** Correct bit errors without retransmission

**Half Duplex:** Only one side transmits at a time

**Full Duplex:** Both sides transmit simultaneously

---

## Link Layer Implementation

**Network Interface Card (NIC):**
- Implements both link and physical layer
- Can be hardware or software
- Functionality: Framing, MAC processing, error detection

---

## Frame Communication

**Sender:**
- Data encapsulation
- Add error-checking info
- Perform flow control and reliability functions

**Receiver:**
- Check for errors
- Perform reliability functions
- Extract datagram from frame and pass to network layer

---

## Error Detection

**EDC:** Error detection and correction bits (redundancy)

**D:** Data protected by error checking (may include header fields)

**Process:**
- Receiver recomputes EDC and compares results
- Mismatch = Error detected
- Error detection is not perfect
- Larger EDC fields provide stronger protection

---

## Key Distinctions

| Layer | Addressing | Scope |
|-------|-----------|-------|
| Link Layer | MAC addresses | Between adjacent nodes (hop-by-hop) |
| Network Layer | IP addresses | End-to-end |

---

## Quiz Reminders

1. Link layer operates **between adjacent nodes** only
2. Different links may use **different technologies**
3. **MAC addresses** ≠ **IP addresses**
4. Error detection uses **redundancy** but cannot guarantee detection
5. Link layer has **multiple services** (framing, access control, error detection, flow control, etc.)
6. **NIC** implements link AND physical layer
7. Reliable delivery at link layer is **optional**
