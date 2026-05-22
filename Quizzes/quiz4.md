## Practice Problems: TCP and Networking

### 1. What are NOT functions of pipelining?
   - ❌ Eliminating the need for acknowledgements
   - ❌ Ensuring that segments are always received in order
   
   **What pipelining DOES do:**
   - ✓ Reduces the impact of long Round Trip Times (RTT) on throughput
   - ✓ Allows the sender to have multiple 'in-flight' segments

---

### 2. Maximum Segment Size (MSS) Calculation

**Question:** If the Maximum Transmission Unit (MTU) of the Link-Layer is 1,680 bytes, and the standard TCP and IP headers are 20 bytes each, what is the maximum segment size (MSS)?

**Formula:** MSS = MTU − IP header − TCP header

**Solution:** MSS = 1,680 − 20 − 20 = **1,640 bytes**

---

### 3. What are characteristics of the TCP protocol?
   - ✓ It is full-duplex, allowing simultaneous data transfer in both directions
   - ✓ It connects processes via sockets

---

### 4. Receive Window (rwnd) Calculation

**Question:** A receiver has a total buffer size (RcvBuffer) of 1,000 bytes. The last byte received is 800, and the last byte read by the application is 300. What value is advertised in the rwnd field?

**Formula:** rwnd = RcvBuffer − (LastByteRcvd − LastByteRead)

**Solution:** rwnd = 1,000 − (800 − 300) = 1,000 − 500 = **500 bytes**

---

### 5. TCP Flow Control Ensures that:
   - ✓ Data is only sent when in-flight data is less than rwnd
   - ✓ The sender does not overwhelm the receiver's buffer

---

### 6. Total Number of Ports

**Question:** What is the total number of ports that can be used by a process?

**Answer:** 2¹⁶ = **65,536 ports** (numbered 0 to 65,535)

---

### 7. ACK Number Interpretation

**Question:** If a TCP sender receives an ACK with the number 120, what is the first byte of data it will send in the next segment?

**Answer:** **120**

**Explanation:** An ACK number means: "I have successfully received all bytes up to ACK−1, and I am expecting byte ACK next."

So when we receive an ACK of 120, bytes 0-119 were received successfully. The next byte the receiver wants is byte 120.

---

### 8. Go-Back-N Maximum Window Size

**Question:** If the total number of sequence numbers that can be used is 10, what is the maximum window size of Go-Back-N?

**Formula:** For Go-Back-N, the maximum sender window size is: N − 1

**Solution:** Max window size = 10 − 1 = **9**

---

### 9. What problems can occur if the TCP timeout value is set incorrectly?
   - **If too short:** leads to unnecessary retransmissions and bandwidth waste
   - **If too long:** results in slow recovery after a packet loss

---

### 10. What are the benefits of using 'Fast Retransmit' over 'Timeout-Based Retransmit'?
   - ✓ Reduces the delay caused by waiting for a timer to expire
   - ✓ Improves overall throughput

---

### 11. In the process of closing a TCP connection using the FIN flag, which of the following statements are true?
   - ✓ Both the client and the server can independently initiate a connection teardown by sending a segment with the FIN bit set to 1
   - ✓ TCP connection teardown ensures that all 'in-flight' data is accounted for before the connection variables and buffers are released
   - ✓ A FIN segment must be acknowledged (ACK) by the receiver to confirm that the request to close that direction of byte stream was received

---

## Key Equations

### Maximum Segment Size (MSS):
**MSS = MTU − IP header − TCP header**

### Receive Window (rwnd):
**rwnd = RcvBuffer − (LastByteRcvd − LastByteRead)**

### Go-Back-N Maximum Window Size:
**Max window size = N − 1**
