# Lecture 1

## Chapter 1:
- What is the internet? What is a protocol?
- Internet structure
- Protocol layers, service models

The internet is the tree trunk. It branches out, and has branches that reach leaves. The leaves are the access points. The tree trunk allows this flow of data to be seamless.

## "Nuts and Bolts" View

**Billions of connected computing devices:**
- Hosts = end systems
- Running network apps at internet's 'edge'

**Packet switches:** forward packets (chunks of data)
- Routers and switches

**Communication links:**
- Fiber, copper, radio, satellite
- Transmission rate: bandwidth

**Networks:**
- Collection of devices, routers, links: managed by organization

**Internet:** 'network of networks'
- Interconnected ISPs

**Protocols are Everywhere:**
- Control sending, receiving of messages
- HTTP (web), streaming video, Zoom, TCP, IP, WiFi, 4G/5G, Ethernet

**Internet Standards:**
- RFC: Request for Comments
- IETF: Internet Engineering Task Force

## Services View of the Internet

<img width="589" height="548" alt="Screenshot 2026-04-01 at 3 32 52 PM" src="https://github.com/user-attachments/assets/c25aa146-cdcf-49c0-86b1-4c345a597a27" />

The services view is more of understanding which service application is being used in what case.

**Infrastructure** that provides services to applications:
- Web, streaming video, multimedia, teleconferencing, email, social media, etc.

Provides programming interface to distributed applications:
- Hooks allowing sending/receiving apps to 'connect' to, use internet transport service
- Provides service options, analogous to postal service

## What is a Protocol?

Protocols define the format, order, and messages sent and received among network entities, and actions taken on message transmission and receipt.

<img width="409" height="169" alt="Screenshot 2026-04-01 at 3 35 25 PM" src="https://github.com/user-attachments/assets/04a07fd9-3a98-4936-bd09-818f065f6b1d" />

## A Closer Look at Internet Structure

**Network edge:**
- Hosts: clients and servers
- Servers often in data centers

**Access Networks, physical media:**
- Wired, wireless communication links

<img width="240" height="270" alt="Screenshot 2026-04-01 at 3 37 24 PM" src="https://github.com/user-attachments/assets/48697e67-f36f-4fd9-9c79-5f19f2cc6886" />

### What happens when you initialize a request?

You initialize a ping, it goes through UC Davis network that is your local ISP. This local ISP is now connected.

All of the devices are connected to routers:

**Network Core:**
- Interconnected routers
- Network of routers

<img width="263" height="298" alt="Screenshot 2026-04-01 at 3 41 12 PM" src="https://github.com/user-attachments/assets/1357aac6-b4e9-4ab1-922c-07af601cd01a" />

## Wireless Access Networks

Shared wireless access network connects end system to router via base station aka 'access point'

<img width="1311" height="479" alt="Screenshot 2026-04-01 at 3 44 29 PM" src="https://github.com/user-attachments/assets/5a85797a-102e-4da3-b795-1cf751564d2f" />

## Access Networks: Data Center Networks

High-bandwidth links (10s to 100s Gbps) connect hundreds to thousands of servers together and to internet.

### Question: Given millions of access ISPs, how do you connect them together?

Connecting each access ISP directly does not scale → O(N²) connections.

ISPs are the physical locations that data traffic is exchanged (it's a physical entity).

If we suggested one global ISP, and it's a viable business, there will be competitors. Who will want to be connected? There will soon be content provider networks (e.g. Google, Microsoft, Akamai) who may run their own network, bring services, content close to end users.

<img width="634" height="358" alt="Screenshot 2026-04-01 at 4 05 57 PM" src="https://github.com/user-attachments/assets/b775f9c5-b29c-49aa-b95b-05907a9d2db4" />

## Protocol "Layers" and Reference Models

Networks are complex with many "pieces":
- Hosts
- Routers
- Links of various media
- Applications
- Protocols
- Hardware, software

### Why Layering?

Each layer is designed to carry out tasks and is responsible for a specific role, helping the layer below it. Layering breaks down complexity, keeping it modular.

### Layered Internet Protocol Stack

**Application:** supporting network applications
- HTTP, IMAP, SMTP, DNS

**Transport:** process-process data transfer
- TCP, UDP

**Network:** routing of datagrams from source to destination
- IP, routing protocols

**Link:** data transfer between neighboring network elements
- Ethernet

**Physical:** bits "on the wire"



