# Application Layer

## Overview

Topics covered:

- How applications communicate
- Web and HTTP
- The Domain Name System (DNS)

---

## Creating a Network Application

### Client
- Initiates requests

### Server
- Provides responses

---

## Client-Server Paradigm

### Servers
- Always active
- Have a permanent IP address
- Typically hosted in data centers

### Clients
- Contact servers
- May have dynamic IP addresses
- Do not typically communicate directly with other clients

Examples:
- HTTP
- FTP

---

## Peer-to-Peer (P2P) Architecture

- No always-on server
- End systems communicate directly with each other
- Peers request services from other peers
- Highly scalable since new peers also provide capacity

---

## Process Communication

A **process** is a program running on a host's operating system.

Processes on different hosts communicate by exchanging messages.

### Types of Processes

1. **Client Process**
   - Initiates communication

2. **Server Process**
   - Waits to be contacted

In a P2P architecture, a process can act as both a client and a server simultaneously.

---

## Sockets

Processes send and receive messages through a **socket**.

A socket is identified by:
- IP address
- Port number

<img width="611" height="238" alt="Socket Communication Diagram" src="https://github.com/user-attachments/assets/19f03a56-dab2-45ee-bca9-ff60c769c5c9" />

---

## Addressing Processes

To receive messages, a process must have an identifier.

### Host Identification
- Each host has a unique 32-bit IP address (IPv4)

### Process Identification
A process identifier consists of:
- IP address
- Port number

### Common Port Numbers

| Service | Port |
|----------|--------|
| HTTP Server | 80 |
| Mail Server | 25 |

### Example

To send an HTTP request to `gaia.cs.umass.edu`:

- IP Address: `128.119.245.12`
- Port Number: `80`

---

## Application-Layer Protocols

An application-layer protocol defines:

- **Types of messages exchanged**
  - Requests
  - Responses

- **Message syntax**
  - Fields in messages
  - How fields are formatted and separated

- **Message semantics**
  - Meaning of information in fields

- **Rules**
  - When and how processes send and respond to messages

---

## What Transport Services Does an Application Need?

Applications may require:

- Data integrity
- Timing
- Throughput
- Security

### Throughput Example

If:

- File size = 600 MB
- Throughput = 10 Mbps

Then:

```text
Transfer Time = File Size / Throughput
```

According to the example:

```text
600 MB / 10 Mbps = 60 seconds
```

> Note: In practice, units should be converted carefully (MB vs Mb).

### Bottleneck Throughput Example

The slowest link determines the overall throughput.

```text
[Source] ----10 Mbps---- [Router] ----2 Mbps---- [Destination]
```

Effective throughput:

```text
2 Mbps
```

---

## Internet Transport Protocol Services

### TCP Services

TCP provides:

- Reliable transport between sender and receiver
- Flow control
- Congestion control
- Connection-oriented communication

TCP does **not** provide:

- Timing guarantees
- Minimum throughput guarantees
- Security

---

### UDP Services

UDP provides:

- Unreliable data transfer
- Minimal overhead

UDP does **not** provide:

- Reliability
- Flow control
- Congestion control
- Timing guarantees
- Throughput guarantees
- Security
- Connection setup

### Why Use UDP?

- Minimal protocol overhead
- Lower latency
- Simpler communication

---

### Class Note

Neither TCP nor UDP provides security.

Security is typically provided by **TLS (Transport Layer Security)**, which operates above TCP.

---

# Web and HTTP

## Web Pages

A web page consists of multiple **objects**, which may be stored on different web servers.

Examples of objects:

- HTML files
- JPEG images
- Videos
- CSS files

A web page contains:

- A base HTML file
- References to additional objects

Each object is addressable through a URL.

### Example URL

```text
www.someschool.edu/someDept/pic.gif
```

```text
www.someschool.edu   -> Host name
/someDept/pic.gif    -> Path name
```

---

## HTTP (Hypertext Transfer Protocol)

HTTP is the application-layer protocol of the Web.

### HTTP Overview

Uses a client-server model.

#### Client
- Requests web objects
- Displays web objects

#### Server
- Sends requested objects

<img width="365" height="403" alt="HTTP Overview" src="https://github.com/user-attachments/assets/2841ff39-dfe1-4737-a5cc-5ff9f533c94a" />

---

## HTTP Uses TCP

1. Client initiates TCP connection
2. Server accepts connection
3. HTTP messages are exchanged
4. TCP connection is closed

### HTTP is Stateless

The server maintains no information about previous client requests.

---

## Round-Trip Time (RTT)

RTT is the time required for:

1. A packet to travel from source to destination
2. The acknowledgment to return

Usually measured in milliseconds (ms).

<img width="661" height="480" alt="RTT Diagram" src="https://github.com/user-attachments/assets/a9c257d3-9e45-45d2-a53a-388b4b72cf5b" />

---

## Non-Persistent HTTP

### Example

<img width="690" height="316" alt="Non-Persistent HTTP Example 1" src="https://github.com/user-attachments/assets/71de5ddb-cb6c-4409-bd8b-88e74bbc0525" />

<img width="691" height="318" alt="Non-Persistent HTTP Example 2" src="https://github.com/user-attachments/assets/5259873d-3ed4-4415-898f-4032c5500ed8" />

### Response Time

<img width="669" height="320" alt="Response Time Diagram" src="https://github.com/user-attachments/assets/48c49859-b5e3-4159-b21b-bc9dd75198f3" />

---

## Persistent vs Non-Persistent HTTP

### Non-Persistent HTTP

- Requires 2 RTTs per object
- Operating system overhead for each TCP connection
- Server closes connection after sending an object

### Persistent HTTP

- Can require as little as 1 RTT for multiple referenced objects
- Reuses the same TCP connection
- Server leaves the connection open after sending objects

---

## HTTP Request Message

<img width="656" height="284" alt="HTTP Request Message" src="https://github.com/user-attachments/assets/a5c7329b-4866-448f-a3ec-58ade4ced1b3" />

---

## HTTP Response Message

<img width="628" height="240" alt="HTTP Response Message" src="https://github.com/user-attachments/assets/182b9523-0c00-469e-a7be-43087cf7cb8e" />

---

## Common HTTP Status Codes

| Code | Meaning |
|--------|---------|
| 200 | OK |
| 301 | Moved Permanently |
| 400 | Bad Request |
| 404 | Not Found |

---

## Web Caches

### Goal

Satisfy client requests without contacting the origin server.

### Process

1. Browser sends request to cache
2. Cache checks whether object exists locally
3. If found, cache returns object
4. Otherwise:
   - Cache requests object from origin server
   - Receives object
   - Stores a copy
   - Returns object to client

<img width="332" height="218" alt="Web Cache Diagram" src="https://github.com/user-attachments/assets/21d16531-d5c6-4271-9652-681fd25b850d" />

---

## Web Caches (Proxy Servers)

### Benefits

- Reduced response time
- Reduced network traffic
- Reduced load on origin servers

### Cache Behavior

A web cache acts as:

#### Client
- When communicating with the origin server

#### Server
- When communicating with the requesting client

---

# DNS (Domain Name System)

## What is DNS?

DNS is an application-layer protocol.

### Why DNS Exists

Machines need unique identifiers.

Computers use IP addresses:

```text
128.119.245.12
```

Humans prefer names:

```text
cs.ucdavis.edu
```

DNS maps human-readable names to IP addresses.

---

## DNS Services and Structure

DNS is distributed because the Internet is distributed.

### DNS Services

#### Hostname-to-IP Mapping

```text
hostname -> IP address
```

#### Load Distribution

Multiple replicated servers can share the same hostname.

This allows traffic to be distributed among servers.

---

## Why Not Use a Centralized DNS?

Problems with centralization:

- Single point of failure
- Maintenance challenges
- Increased delay
- Poor scalability

---

## DNS: A Distributed Hierarchical Database

<img width="746" height="377" alt="DNS Hierarchy" src="https://github.com/user-attachments/assets/70081fad-be7d-4155-b61b-7f119c9058c4" />

---

## DNS Root Name Servers

DNS is a cached, distributed database that maps names to IP addresses.

<img width="689" height="252" alt="Root Name Servers" src="https://github.com/user-attachments/assets/9d4d79ad-db87-458c-9a61-5f1bbbdc7145" />

### Intuition

DNS is like asking for directions.

A server may not know the final answer, but it can tell you where to ask next.

---

## Top-Level Domain (TLD) and Authoritative Servers

<img width="655" height="296" alt="TLD and Authoritative DNS" src="https://github.com/user-attachments/assets/b8a84966-08e9-4158-8285-24c10f58891f" />

Resolution path:

```text
Root Server
    ↓
TLD Server
    ↓
Authoritative DNS Server
    ↓
IP Address
```

- Root server knows TLD servers
- TLD server knows authoritative servers
- Authoritative server knows the actual IP address

---

## DNS Name Resolution: Iterative Query

<img width="713" height="396" alt="Iterative Query" src="https://github.com/user-attachments/assets/08662c45-7579-4314-a449-f19a3aec5fd7" />

---

## DNS Name Resolution: Recursive Query

<img width="722" height="448" alt="Recursive Query" src="https://github.com/user-attachments/assets/099e9795-2af4-4e4f-af5d-6bd66a54321c" />

---

## DNS in Practice

A hybrid approach is typically used:

### Recursive

```text
Client ↔ Local DNS Server
```

### Iterative

```text
Local DNS ↔ Root/TLD/Authoritative Servers
```

---

## Thinking About DNS

DNS is:

- A massive distributed database
- Contains billions of records
- Handles trillions of queries per day
- Read-heavy rather than write-heavy
- Performance-critical

Millions of organizations manage their own DNS records.

---

## DNS Caching

When a DNS server learns a mapping, it caches it.

Benefits:

- Faster future lookups
- Reduced DNS traffic
- Reduced load on upstream servers

### Cache Characteristics

- Cached entries expire after a TTL (Time To Live)
- TLD server information is commonly cached in local DNS servers

```text
DNS Query
     ↓
Cached?
     ↓
Yes → Return immediately
No  → Continue DNS resolution process
```
