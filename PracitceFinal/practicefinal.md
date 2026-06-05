# Networking Quiz (Clean Version)

---

## 1. A home laptop runs a browser and contacts a web server. Where does the browser application run?
- On end systems (hosts)

---

## 2. Which statement best distinguishes hosts and packet switches in the Internet?
- Hosts run network applications; packet switches forward packets

---

## 3. A web browser sends a request to a web server and receives a web page. Which protocol is most directly involved at the application layer?
- HTTP

---

## 4. A user enters a hostname such as www.example.com. Which system is used to obtain the corresponding IP address?
- DNS

---

## 5. What are services provided by TCP?
- Reliable delivery  
- In-order delivery  
- Flow control  
- Congestion control  

---

## 6. An application wants low overhead and can tolerate some loss. Which protocol satisfies this requirement?
- UDP

---

## 7. For TCP demultiplexing, what information is used to identify the correct socket?
- Source IP  
- Source port  
- Destination IP  
- Destination port  

---

## 8. A TCP receiver has received bytes through byte 100. What should its ACK number represent?
- The next byte expected

---

## 9. In rdt3.0, a packet or ACK may be lost. What mechanism allows the sender to recover from this loss?
- Timeout timer and retransmission

---

## 10. Why is stop-and-wait data transfer inefficient on long-delay links?
- The sender stays idle while waiting for ACKs

---

## 11. What is related to TCP flow control?
- Receiver advertises available buffer space  
- Sender limits unacknowledged data based on rwnd  
- Prevents sender from overwhelming receiver  

---

## 12. What can happen when a network is congested?
- Queueing delay increases  
- Router buffers may overflow  
- Packets may be dropped  

---

## 13. A router receives a packet and chooses the output port. This is:
- Forwarding  

---

## 14. Routers exchange information to compute paths from source to destination. This is:
- Routing  

---

## 15. In distance-vector routing, what information does a router mainly use?
- Direct neighbor costs and neighbor-advertised distances  

---

## 16. What are advantages or effects of NAT?
- Multiple local devices share one public IPv4 address  
- Internal IPs can change without notifying external networks  
- Internal devices are not directly reachable from the Internet  

---

## 17. In a router output queue, the buffer becomes full. What can happen to an arriving packet?
- It may be dropped  

---

## 18. ALOHA allows nodes to transmit immediately. CSMA improves this by:
- Listening before transmitting  

---

## 19. Collisions can still happen in CSMA mainly because:
- Propagation delay exists  

---

## 20. In CSMA/CD, what can happen after a collision is detected?
- The sender aborts transmission  
- The sender waits before retransmitting  
- Binary exponential backoff may be used  

---

## 21. Binary exponential backoff makes a node more conservative because after more collisions:
- The range of possible backoff times increases  

---

## 22. Why is SIFS shorter than DIFS in WiFi CSMA/CA?
- ACKs get priority over new transmissions  
- Allows immediate ACK after data  
- Reduces chance of collisions for ACKs  

---

## 23. In WiFi, a station that wants to begin a new transmission generally waits for:
- DIFS  

---

## 24. In an infrastructure WiFi network, a Basic Service Set consists of:
- An access point and associated wireless stations  

---

## 25. As received wireless signal power decreases, which may happen?
- Reduced coverage  
- More retransmissions  
- Less reliable communication  

---

## 26. Why does link-layer reliability exist?
- To recover errors locally on unreliable physical links  

---

## 27. Which TCP value limits sending based on receiver buffer space?
- Receiver advertised window (rwnd)  

---

## 28. In distance-vector routing, what two values are added?
- Link cost + neighbor’s advertised distance  

---

## 29. In NAT, what distinguishes connections sharing one public IP?
- Port numbers (specifically NAT-assigned source ports)

---

## 30. What metric describes variability in packet delay?
- Jitter  

---

## 31. What does Pure ALOHA do differently compared to Slotted ALOHA?
- Pure ALOHA allows transmissions at any time, while Slotted ALOHA restricts transmissions to fixed time slots  

---

## 32. A station is counting down to transmit data. It senses the channel is busy and enters freeze period. What happens next if it senses idle again?
- The station resumes its countdown from where it left off  

---

## 33. Which IEEE 802.11 structure contains an AP and stations?
- Basic Service Set (BSS)
```



