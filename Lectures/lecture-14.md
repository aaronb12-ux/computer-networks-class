## Link Layer

### Introduction:

**Nodes:** hosts, switches, routers

**Links:** Communication channels connecting adjacent nodes
- May be wired (Ethernet) or wireless (WiFi)

<img width="274" height="282" alt="Screenshot 2026-05-28 at 1 31 53 AM" src="https://github.com/user-attachments/assets/a9381aa7-de43-4174-8c52-28cd4690ae8d" />

**Link Layer is responsible for hop-by-hop delivery:**
- **Network Layer:** Decides where packet should go
- **Link Layer:** Determines how to move packets across each link

---

### Link Layer: Context

End-to-end communication may traverse multiple links.

Different links may use different link-layer technologies.

**Example:**
Laptop → WiFi → Access Point → Ethernet → PC

Some IP datagrams may be carried by different frame formats on different links.

Different link-layer protocols may provide different services.

---

### Link Layer: Services

**Framing:** Encapsulates datagram into frame

**Link Access:** Control access to a shared medium

**MAC Addressing:** Source and destination MAC addresses identify devices

**Reliable Delivery:** Optional retransmission between adjacent nodes
- Why Reliability at link layer: Avoid expensive retransmissions. Particularly useful for wireless links with higher error rates

<img width="258" height="297" alt="Screenshot 2026-05-28 at 1 45 44 AM" src="https://github.com/user-attachments/assets/7b6524da-a37b-48d1-bbec-cf47b3a219ee" />

---

### More Services:

**Flow Control:** Prevent sender from overwhelming receiver

**Error Detection:** Detect corrupted frames

**Error Correction:** Correct bit errors without retransmission

**Half Duplex:** Only one side transmits at a time

**Full Duplex:** Both sides may transmit simultaneously

---

### Host Link-Layer Implementation

Link Layer is implemented in the **Network Interface Card (NIC)**.

**NIC:** Typically implements both link and physical layer

**Functionality of NIC:**
- Framing
- MAC processing
- Error detection

Link layer can be implemented in hardware and software.

<img width="244" height="269" alt="Screenshot 2026-05-28 at 1 49 46 AM" src="https://github.com/user-attachments/assets/0d18d5c4-a664-4e04-9605-11ffc95e040c" />

---

### Interfaces Communicating:

<img width="518" height="174" alt="Screenshot 2026-05-28 at 1 50 25 AM" src="https://github.com/user-attachments/assets/1955c595-905e-42ec-8b0d-1a16662b1ba4" />

**Sender:**
- Data encapsulation
- Add error-checking info
- May perform flow control and reliability functions

**Receiver:**
- Checks for errors
- Performs reliability functions
- Extracts datagram from frame and passes to network layer

---

### Error Detection

**EDC:** Error detection and correction bits (e.g., redundancy)

**D:** Data protected by error checking, may include header fields

<img width="399" height="211" alt="Screenshot 2026-05-28 at 1 54 28 AM" src="https://github.com/user-attachments/assets/f7db40a6-fb8e-448c-a5a2-7da67d24d177" />

**Process:**
- Receiver recomputes EDC and compares results
- If mismatch: Error detected
- Error detection is not perfect
- Larger EDC fields generally provide stronger protection

---

### Key Points:

- Link layer operates between adjacent nodes
- Different links may use different technologies
- MAC addresses identify devices at link layer (vs. IP addresses at network layer)
- Error detection adds redundancy but cannot guarantee detection of all errors


