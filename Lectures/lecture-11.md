# Chapter 5: Network Layer - The Control Plane
 
## Network-Layer Functions
 
### Forwarding: Local Router Function
- Moves packets from input port → correct output port
- Uses forwarding table
- Occurs for every arriving packet
- Operates at very fast timescale
### Routing: Network-Wide Function
- Determines best path from source to destination
- Computes forwarding table entries
- Operates at slower timescale
## Control Plane Architectures
 
### Per-Router Control Plane
 
Traditional Internet routing architecture where:
- Each router independently participates in routing
- Routers exchange routing information with each other
- Control logic is distributed across routers
<img width="443" height="264" alt="Screenshot 2026-05-18 at 3 24 03 PM" src="https://github.com/user-attachments/assets/5469702a-e838-4419-941a-db0fadc6fceb" />

Hence, routers compute routes and forward packets.
 
### Software-Defined Networking (SDN) Control Plane
 
SDN separates control plane from data plane:
- Remote controller computes forwarding decisions/routes
- Controller installs forwarding rules/tables in routers
- Simplifies network programmability and management
<img width="436" height="251" alt="Screenshot 2026-05-18 at 3 27 07 PM" src="https://github.com/user-attachments/assets/d5f4fa6b-a837-4811-80be-2f8ffcde40eb" />

## Routing Protocols
 
Protocols determine paths through the network.
 
**Path:** Sequence of routers traversed by packets
 
**Goal:** Find 'good' paths
 
### What Makes a Path 'Good'?
 
'Good' may mean:
- Least cost, lowest delay
- Least congestion, highest reliability
- Path cost may also depend on administrative policy
Routing decisions influence network performance and scalability.
 
<img width="278" height="273" alt="Screenshot 2026-05-18 at 3 29 18 PM" src="https://github.com/user-attachments/assets/fb85a89c-3c89-463d-91c9-e559bb2490aa" />

### Graph Abstraction: Link Costs
 
<img width="736" height="375" alt="Screenshot 2026-05-18 at 3 31 30 PM" src="https://github.com/user-attachments/assets/511554ff-40d9-4984-aab6-37ffee0fdda9" />

## Routing Algorithm Classification
 
### By Update Frequency
 
**Static:**
- Routes change slowly
- Usually manually configured
- Suitable for stable networks
**Dynamic:**
- Routes adapt to network changes
- Routers periodically exchange routing updates
- More responsive but may introduce instability
### By Information Distribution
 
**Centralized (Link-State):**
- Routers have complete topology and link-cost information
- Link-state routing belongs here
- Routers independently compute shortest paths
**Decentralized (Distance Vector):**
- Routers initially know only immediate neighbors and link costs
- Routing knowledge improves iteratively over time
- Distance vector routing belongs here
## Dijkstra's Link-State Routing Algorithm
 
### How It Works
 
1. Each router advertises its own directly connected links
2. Routers forward received advertisements to neighbors (flooding)
3. Every router eventually learns complete topology
4. Each router independently runs Dijkstra locally
5. Dijkstra computes least-cost paths from source to destination
6. Output is used to construct forwarding tables
<img width="743" height="464" alt="Screenshot 2026-05-18 at 3 43 26 PM" src="https://github.com/user-attachments/assets/8ee8eafd-d998-424e-b3dc-a5176b48dea3" />
---
 
## Summary Comparison
 
| Architecture | Control Location | Complexity | Flexibility |
|--------------|-----------------|------------|-------------|
| Per-Router | Distributed | Higher | Lower |
| SDN | Centralized | Lower | Higher |
 
| Algorithm Type | Information | Computation | Example |
|----------------|-------------|-------------|---------|
| Link-State | Complete topology | Independent | Dijkstra |
| Distance Vector | Local neighbors | Iterative | Bellman-Ford |
  
