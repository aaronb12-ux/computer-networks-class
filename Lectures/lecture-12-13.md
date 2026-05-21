# Chapter 5: Network Layer: Control Plane

## Distance-Vector Routing:

**Key characteristics:**
- Neighbor-based routing
- No complete topology knowledge
- Iterative asynchronous local updates
- Uses neighbor advertised distances

**Each neighbor (router) knows:**
- Direct neighbor costs
- Neighbor advertised distances

**Algorithm properties:**
- Uses Bellman-Ford style computation
- Self-stopping

---

### Example:

<img width="533" height="213" alt="Screenshot 2026-05-21 at 12 39 56 PM" src="https://github.com/user-attachments/assets/a0c1aede-821b-48ef-9018-1805d16d487f" />

**'B' only knows:**
- Direct costs to 'A' and 'C'
- Advertised distances from 'A' and 'C'

**'A' will advertise to 'B' about 'Z', 'X', and 'C'**

---

## Distance Vector Algorithm

Based on **Bellman-Ford (BF) equation** (dynamic programming)

### Bellman-Ford Equation

Let D<sub>x</sub>(y): cost of least-cost path from x to y

**Then: D<sub>x</sub>(y) = min<sub>v</sub> {c(x,v) + D<sub>v</sub>(y)}**

Where:
- **min** = minimum taken over all neighbors v of x
- **c(x,v)** = direct cost of link from x to v
- **D<sub>v</sub>(y)** = v's estimated least-cost-path cost to y

---

### Bellman-Ford Example:

<img width="307" height="273" alt="Screenshot 2026-05-21 at 12 59 55 PM" src="https://github.com/user-attachments/assets/c0759357-4389-4377-9891-fb20cec0b39e" />

---

### Distance Vector: Example

<img width="610" height="354" alt="Screenshot 2026-05-21 at 1 02 50 PM" src="https://github.com/user-attachments/assets/aa1b6ed3-ff54-4e2a-b297-117b88e6f5e6" />

---

## Comparison of LS and DV Algorithms

| Link State | Distance Vector |
|------------|-----------------|
| Global topology view | Neighborhood/local view |
| Floods link-state advertisements | Exchanges distance vectors with neighbors |
| Flooding overhead | Low overhead |
| Faster convergence | Convergence can be slow |
| Loops less likely | Routing loops/count-to-infinity possible |
| Bad info affects local computation | Incorrect advertisements can propagate recursively |

---

## Making Routing Scalable:

The structure of the internet is hierarchical.

There exist **Autonomous Systems (AS)** which are administrated by the ISP.

**Note:** Each AS contains a set of interconnected routers. E.g., An AS in Davis could be operated by AT&T.

---

## Internet Approach to Scalable Routing:

**Intra-AS:** Communication within the network

**Inter-AS:** Communication between ASes

**Gateway routers** connect different ASes.

Routers within an AS communicate with each other using the same protocol (i.e., same intra-domain protocol).
