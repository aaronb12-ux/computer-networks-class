# Transport Layer

## Transport Services and Protocols

The transport layer provides **logical communication between applications (processes)** running on different hosts.

---

## Two Principal Internet Transport Protocols

### TCP (Transmission Control Protocol)

- Reliable
- Connection-oriented
- More detailed and higher overhead than UDP
- Uses:
  - Source IP
  - Source Port
  - Destination IP
  - Destination Port

---

### UDP (User Datagram Protocol)

- Connectionless
- Minimal overhead
- Less reliable than TCP
- Uses:
  - Destination Port
  - Destination IP

---

## Connection-Oriented Demultiplexing (TCP)

A TCP socket is identified by a **4-tuple**:

```text
(Source IP, Source Port, Destination IP, Destination Port)
```

### Demultiplexing

The receiver uses all four values of the 4-tuple to direct an incoming segment to the correct socket.

### Multiple TCP Connections

A server may support many simultaneous TCP connections:

- Each connection has its own 4-tuple
- Each socket is associated with a different client

---

## UDP: User Datagram Protocol

### Characteristics

- Connectionless
- No connection setup required
- Minimal protocol overhead

### Why Use UDP?

- Faster due to less overhead
- Useful for applications that prioritize speed over reliability
- Common in:
  - DNS
  - Streaming
  - Online gaming
  - VoIP

---

## UDP Segment Header

<img width="446" height="292" alt="UDP Segment Header" src="https://github.com/user-attachments/assets/5b7a0341-72a6-448b-8e7b-39e188ff301b" />

---

# Principles of Reliable Data Transfer

<img width="404" height="172" alt="Reliable Data Transfer Overview" src="https://github.com/user-attachments/assets/b507dd0f-0cfe-4ba4-9378-996447bb6da5" />

<img width="377" height="290" alt="Reliable Data Transfer Components" src="https://github.com/user-attachments/assets/141f1b1d-6a54-4d26-8a1e-50cc1fec29ab" />

Reliable data transfer protocols are concerned with:

- Reliability
- Throughput
- Delay
- Security

---

## Reliable Data Transfer Protocol (RDT): Interfaces

<img width="647" height="294" alt="RDT Interfaces" src="https://github.com/user-attachments/assets/f5fb31d5-830e-4882-bcfd-464cbf9d1450" />

---

## Reliable Data Transfer (RDT)

We will:

- Incrementally develop the sender and receiver sides of a reliable data transfer protocol
- Consider only **unidirectional data transfer**
  - Data flows in one direction
  - Control information flows in both directions
- Use **Finite State Machines (FSMs)** to specify sender and receiver behavior

<img width="562" height="167" alt="FSM Overview" src="https://github.com/user-attachments/assets/257e1cbf-1c63-4988-b4b8-1ae260808a24" />

---

# rdt1.0: Reliable Transfer Over a Reliable Channel

### Assumptions

A perfect-world scenario:

- No bit errors
- No packet loss
- No acknowledgments required
- No retransmissions required

<img width="666" height="82" alt="rdt1.0" src="https://github.com/user-attachments/assets/ebe59cb3-aba5-4c54-b2f0-17fa5f03b3e5" />

---

# rdt2.0: Channel with Bit Errors

rdt2.0 considers more realistic conditions.

### Problems Introduced

- Packet corruption due to bit errors

### Solutions

- ACK (Acknowledgment)
- NAK (Negative Acknowledgment)
- Checksums
- Retransmissions

---

## rdt2.0 Sender

### Functions

#### A. `rdt_send(data)`
Sends data from the upper layer.

#### B. `packet = make_pkt(data)`
Creates a packet and adds a checksum.

#### C. `udt_send(packet)`
Sends the packet into the channel.

#### `^`
Represents **no action**.

<img width="648" height="296" alt="rdt2.0 Sender FSM" src="https://github.com/user-attachments/assets/842bbad9-ebd9-4ece-9ac4-118e9c72f5a8" />

### Possible Outcomes

1. Receive correct ACK
2. Receive correct NAK
3. Receive corrupted ACK
4. Receive corrupted NAK

### Limitation

rdt2.0 cannot handle the ambiguity caused by corrupted ACKs or NAKs.

---

## rdt2.0 Receiver

### Functions

#### D. `rdt_rcv(packet)`
Receives a packet.

#### E. `extract(packet.data)`
Extracts data from the packet.

#### F. `deliver_data(data)`
Delivers data to the upper layer.

<img width="476" height="425" alt="rdt2.0 Receiver FSM" src="https://github.com/user-attachments/assets/01a324f4-6c92-4a0e-a9ab-761f8fef1b00" />

---

## rdt2.0: Sender and Receiver Behavior

rdt2.x is known as a **Stop-and-Wait Protocol**.

### Stop-and-Wait

The sender:

1. Sends one packet
2. Waits for a response (ACK/NAK)
3. Sends the next packet only after receiving a response

<img width="772" height="230" alt="rdt2.0 Stop-and-Wait" src="https://github.com/user-attachments/assets/0f688c7b-2c27-4093-8bd2-e4b300513146" />

---

## Problems with rdt2.0

### ACK/NAK Corruption

ACKs and NAKs themselves can become corrupted.

### Duplicate Packets

If ACK/NAK corruption occurs:

- Sender may retransmit the current packet
- Receiver may receive duplicates

### Solution

Add:

- Sequence numbers
- Duplicate detection at the receiver

The receiver can then discard duplicate packets.

---

# rdt2.1: Handling Corrupted ACKs and NAKs

rdt2.1 improves upon rdt2.0 by removing ambiguity.

### Key Addition

- Sequence numbers

This allows the receiver to distinguish between:

- New packets
- Retransmitted packets

<img width="797" height="617" alt="rdt2.1 Sender" src="https://github.com/user-attachments/assets/154e5330-e5cb-4205-8750-7e0a0baeb847" />

<img width="793" height="618" alt="rdt2.1 Receiver" src="https://github.com/user-attachments/assets/84013557-b36a-49a5-ba9d-cc186f071a83" />

---

# rdt2.2: A NAK-Free Protocol

rdt2.2 provides the same functionality as rdt2.1 but eliminates NAKs.

### Main Idea

Instead of sending a NAK:

- The receiver sends an ACK for the last correctly received packet.

The ACK implicitly contains the sequence number being acknowledged.

### Duplicate ACKs

A duplicate ACK has the same effect as a NAK:

```text
Duplicate ACK → Retransmit Current Packet
```

---

## rdt2.2 Sender

<img width="797" height="624" alt="rdt2.2 Sender FSM" src="https://github.com/user-attachments/assets/44bd6a2d-42f7-4c94-adec-5b40d1eea844" />

---

## rdt2.2 Receiver

<img width="792" height="616" alt="rdt2.2 Receiver FSM" src="https://github.com/user-attachments/assets/66982faf-9358-4628-ba3c-73c784c9c861" />

---

# rdt3.0: Channels with Errors and Loss

rdt3.0 extends reliable communication to handle packet loss.

### New Problem

Packets or ACKs may be lost entirely.

### Solution

Add a **timer**.

---

## Core Idea

### Silence Means Possible Loss

If the sender does not receive an ACK:

```text
No Response
    ↓
Packet Lost OR ACK Lost
```

### Timer-Based Retransmission

The sender:

1. Sends packet
2. Starts timer
3. Waits for ACK
4. Retransmits if timeout occurs

---

## rdt3.0 Approach

The sender waits a "reasonable" amount of time for an ACK.

### If ACK Arrives

- Stop timer
- Continue normally

### If ACK Does Not Arrive

- Timeout occurs
- Retransmit packet

### Delayed Packets

If a packet or ACK is merely delayed:

- Retransmission creates a duplicate
- Sequence numbers already handle duplicates

### Requirements

- Receiver must indicate the sequence number being acknowledged
- Sender uses a countdown timer

---

## rdt3.0 Sender (1 of 2)

<img width="559" height="377" alt="rdt3.0 Sender FSM Part 1" src="https://github.com/user-attachments/assets/b9561f4c-e261-4fce-9087-0a957c49c3ca" />

---

## rdt3.0 Sender (2 of 2)

<img width="569" height="362" alt="rdt3.0 Sender FSM Part 2" src="https://github.com/user-attachments/assets/953c50f3-c21d-4360-8d77-e628d61be4ae" />

---

## rdt3.0 in Action (1 of 2)

<img width="613" height="371" alt="rdt3.0 Example 1" src="https://github.com/user-attachments/assets/dfc8c715-f950-4d7c-a2e8-f27d3ef5e2bc" />

---

## rdt3.0 in Action (2 of 2)

<img width="594" height="358" alt="rdt3.0 Example 2" src="https://github.com/user-attachments/assets/57fabdea-a159-4d66-af20-2f1b4e95b75e" />

---

# Evolution of Reliable Data Transfer

| Protocol | Handles Errors? | Handles ACK Corruption? | Handles Packet Loss? |
|-----------|----------------|------------------------|---------------------|
| rdt1.0 | No need (perfect channel) | No need | No need |
| rdt2.0 | Yes | No | No |
| rdt2.1 | Yes | Yes | No |
| rdt2.2 | Yes | Yes (ACK-only design) | No |
| rdt3.0 | Yes | Yes | Yes |

### Progression

```text
rdt1.0
   ↓
rdt2.0
   ↓
rdt2.1
   ↓
rdt2.2
   ↓
rdt3.0
```

Each version incrementally addresses a new problem:

1. Bit errors
2. ACK/NAK corruption
3. Duplicate packets
4. Packet loss
