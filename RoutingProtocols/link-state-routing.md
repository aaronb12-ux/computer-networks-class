## Link-State Routing, CIDR, and Distance Vector

---

## Link-State Routing

### Concept:

Consider a network with each link labeled by its bandwidth. The **width of a path** is defined as the bandwidth of the bottleneck link (the link with the smallest bandwidth along the path).

<img width="286" height="129" alt="Screenshot 2026-05-28 at 1 29 51 PM" src="https://github.com/user-attachments/assets/759ef075-70a0-49ef-98bb-c81d803f3474" />

---

### Problem:

**a)** Find the widest paths from C to all other network nodes assuming link-state routing. Show the steps in the computation.

**b)** What is the corresponding spanning tree?

---

### Solution (Part A):

**Key Variables:**
- **W(v):** Width of path from source node C to destination v
- **P(v):** Previous node (neighbor of v) along the current widest path from C to destination v
- **N:** Set of nodes whose widest-cost path from source is definitely known

**Two Important Modifications from Shortest Path Problems:**

1. **W(v) calculation:** Consider all paths from C to V. For each path, W(v) is given by the **minimum bandwidth link** along the path.
   - Example: Path C → A → B → V, then W(v) = min(bandwidth C→A, A→B, B→V)
   - We take the minimum bandwidth because the bottleneck link limits throughput

2. **Objective:** Instead of minimizing W(v) (as in shortest path), the objective here is to **maximize** W(v)

---

### Step 1: Initialize

Starting from source node C, determine widest paths to all neighbors (A, D, E).

Nodes B and F are not reachable directly from C. So W(x) is filled as 0.

<img width="555" height="295" alt="Screenshot 2026-05-28 at 1 41 28 PM" src="https://github.com/user-attachments/assets/fda8cf7e-dbc7-44fb-8c8a-e30de61e85cb" />

**N = {C}** (source node always has zero distance/width to itself)

| Node | W(v) | P(v) |
|------|------|------|
| A | 1 | C |
| B | 0 | - |
| D | 3 | C |
| E | 2 | C |
| F | 0 | - |

---

### Step 2: Add D (W(D) = 3, highest width)

Node D has the widest path from C, so it's added to N.

Recompute paths to B, E, and F through D.

<img width="651" height="373" alt="Screenshot 2026-05-28 at 1 50 20 PM" src="https://github.com/user-attachments/assets/9814b097-6784-49cc-ad88-79bc8d8b6d94" />

**Calculations:**
- **W(A):** Path C → D → A: min(W(D), bandwidth D→A) = min(3, 3) = **3** (better than 1)
  - P(A) = D

- **W(B):** Path C → D → B: min(bandwidth C→D, bandwidth D→B) = min(3, 2) = **2**
  - P(B) = D

- **W(E):** Path C → D → E: min(C→D, D→E) = min(3, 3) = **3** (better than 2)
  - P(E) = D

- **W(F):** Path C → D → F: min(C→D, D→F) = min(3, 2) = **2**
  - P(F) = D

**Updated Table:**

| Node | W(v) | P(v) |
|------|------|------|
| A | 3 | D |
| B | 2 | D |
| D | 3 | C |
| E | 3 | D |
| F | 2 | D |

---

### Step 3: Add A (W(A) = 3)

With node A added to the set of known nodes N, the paths to B, E, and F are recomputed.

We need to find any new path via A that could increase the bottleneck bandwidth to reach B, E, F.

<img width="624" height="329" alt="Screenshot 2026-05-28 at 2 08 43 PM" src="https://github.com/user-attachments/assets/604eb44b-01c7-41ec-9433-79a45df0902d" />

In this case, there is no such path with A, so the table entries are unaffected.

**N = {C, D, A}**

---

### Step 4: Add E (W(E) = 3)

With node E added to the set of known nodes, the paths to B and F are recomputed.

We need to find any path via E that could increase the bottleneck bandwidth to reach B and F.

<img width="341" height="190" alt="Screenshot 2026-05-28 at 3 05 07 PM" src="https://github.com/user-attachments/assets/c1097d3f-efbe-4769-8a15-8e3adeabfc18" />

In this case, there is no such new path with E.

**Note:** If the weight of E→B were 4 instead of 2, then W(B) would have been updated to 3:
- Path C → D → E → B: min(3, 7, 4) = 3 (better than 2)

**N = {C, D, A, E}**

---

### Step 5: Add B (W(B) = 2)

With node B added to the set of known nodes N, the paths to F are recomputed.

We need to find any new path via B that could increase the bottleneck bandwidth to reach F.

<img width="623" height="351" alt="Screenshot 2026-05-28 at 3 23 43 PM" src="https://github.com/user-attachments/assets/47671846-1b7f-4a4d-afc6-4ab4a8a333bf" />

In this case, there is no such new path with B.

**N = {C, D, A, E, B}**

---

### Final Step: Add F (W(F) = 2)

All nodes are now in N. The computation is complete.

**Final Table:**

<img width="616" height="314" alt="Screenshot 2026-05-28 at 3 25 41 PM" src="https://github.com/user-attachments/assets/00781ad5-3fe9-4868-a38f-5cab0d60ff6d" />

| Node | W(v) | P(v) |
|------|------|------|
| A | 3 | D |
| B | 2 | D |
| C | ∞ | - |
| D | 3 | C |
| E | 3 | D |
| F | 2 | D |

---

### Solution (Part B): Spanning Tree

<img width="376" height="211" alt="Screenshot 2026-05-28 at 3 26 35 PM" src="https://github.com/user-attachments/assets/a5508263-403d-490a-9c4f-6895eedac35d" />

**To construct the spanning tree:**

1. Draw all nodes A to F
2. Using the table constructed previously, for each node X in {A to F}, draw an edge between node X and P(X)
3. Set the link weights on these edges to be equal to the original graph's link weights given in the problem

**Result:** A tree rooted at C with edges:
- C → D (width 3)
- D → A (width 3)
- D → B (width 2)
- D → E (width 3)
- D → F (width 2)

---

## CIDR: Classless Inter-Domain Routing

### Problem:

For each of the following CIDR formatted addresses, what is the **address range** and **how many hosts** can you accommodate?

- 199.200.4.0/22
- 225.1.80.0/20
- 210.24.0.0/14

---

### General Formula:

If the prefix is **/n:**

- **Host bits:** 32 − n
- **Total addresses in the block:** 2^(32 − n)
- **Usable hosts (excluding network + broadcast):** 2^(32 − n) − 2

---

### Solution:

### Example 1: 199.200.4.0/22

**Host bits:** 32 − 22 = **10 bits**

**Total addresses:** 2¹⁰ = **1,024 addresses**

**Address range:** 199.200.4.0 − 199.200.7.255

---

### Example 2: 225.1.80.0/20

**Host bits:** 32 − 20 = **12 bits**

**Total addresses:** 2¹² = **4,096 addresses**

**Address range:** 225.1.80.0 − 225.1.95.255

---

### Example 3: 210.24.0.0/14

**Host bits:** 32 − 14 = **18 bits**

**Total addresses:** 2¹⁸ = **262,144 addresses**

**Address range:** 210.24.0.0 − 210.27.255.255

---

## Key Formulas

### Link-State Routing:
**W(v) = max over all paths of (min bandwidth along each path)**

Objective: **Maximize** W(v)

### CIDR:
**Total addresses = 2^(32 − prefix_length)**

**Usable hosts = 2^(32 − prefix_length) − 2**

---

## Summary

**Link-State Routing:**
- Uses bandwidth (width) as metric
- **Maximizes** bottleneck bandwidth
- Greedy algorithm selects widest-path node at each step
- Final result is spanning tree with maximum widths

**CIDR:**
- Host bits = 32 − prefix length
- Calculate 2^(host bits) for total addresses
- Subtract 2 if excluding network and broadcast addresses


 

  

    
