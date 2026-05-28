# Lecture 15

---

## Key Concepts

**Link Types:**
- **Point-to-Point:** Exactly 2 devices share the link
- **Broadcast/Shared Medium:** Multiple devices share same channel

**Collision:** Occurs when two or more nodes transmit simultaneously

**MAC (Medium Access Control):** Determines who can transmit and when
- Distributed (no central controller)
- Nodes make independent decisions
- Coordination uses same channel

---

## Ideal Multiple Access Protocol Requirements

1. Single transmitting node should use full channel rate **R**
2. If **m** nodes transmit, each gets average rate **R/m**
3. Decentralized (no special coordinator, minimum synchronization)
4. Simple to implement

---

## MAC Protocol Categories

### 1. Channel Partitioning
Divide channel resources among users

### 2. Random Access
Nodes contend for channel
Collisions may occur
Protocols specify how to detect and handle collisions

### 3. Taking Turns
Nodes take turns transmitting

---

## Channel Partitioning Protocols

### TDMA (Time Division Multiple Access)
- **How:** Time divided into repeating slots
- **Allocation:** Each node assigned fixed slot in every round
- **Throughput per node:** R/N (where N = number of nodes)
- **Advantage:** No collisions
- **Disadvantage:** Unused slots waste bandwidth

### FDMA (Frequency Division Multiple Access)
- **How:** Channel bandwidth divided into frequency bands
- **Allocation:** Each node gets dedicated band
- **Ownership:** Nodes continuously own assigned band
- **Throughput per node:** R/N
- **Advantage:** No collisions
- **Disadvantage:** Unused bands waste bandwidth

---

## Random Access Protocols

**Characteristics:**
- Nodes transmit whenever they have data
- No prior coordination among nodes
- Collisions are possible
- Protocol specifies collision detection and handling

**Examples:** Aloha, CSMA, CSMA/CD

---

## Aloha Protocol

### Pure Aloha:
- Nodes transmit immediately when frame arrives
- No listening before transmitting
- Collision recovery: retransmit after random delay

### Slotted Aloha:
- Time divided into equal slots
- Nodes transmit only at slot boundaries
- Improves efficiency

### Key Aloha Equations:

**Maximum Throughput (Pure Aloha):**
- S = G × e^(-2G)
- Where S = throughput, G = offered load
- **Maximum efficiency ≈ 18.4%** (at G = 0.5)

**Maximum Throughput (Slotted Aloha):**
- S = G × e^(-G)
- **Maximum efficiency ≈ 36.8%** (at G = 1)

### Aloha Advantages:
- Simple to implement
- Decentralized
- No synchronization needed

### Aloha Disadvantages:
- Low throughput efficiency
- High collision rate
- Wasted bandwidth

---

## Quick Comparison Table

| Protocol | Collision | Throughput | Efficiency | Synchronization |
|----------|-----------|-----------|-----------|-----------------|
| TDMA | No | R/N | Good | Required |
| FDMA | No | R/N | Good | Required |
| Pure Aloha | Yes | Low | ~18% | None |
| Slotted Aloha | Yes | Medium | ~37% | Required |

---

## Key Takeaways for Quiz

1. **Channel Partitioning** = guaranteed access, no collisions, but bandwidth waste
2. **Random Access** = efficient use of channel, but collisions possible
3. **Aloha** = simplest random access, but low efficiency
4. **Slotted Aloha** = 2× better efficiency than Pure Aloha
5. Single node always gets full rate R; N nodes share R equally (R/N each)
