# Chapter 5: Network Layer — Control Plane

# Distance-Vector Routing

## Key Characteristics
- Neighbor-based routing
- No complete topology knowledge
- Iterative, asynchronous local updates
- Uses neighbor advertised distances

## Each Router Knows
- Direct neighbor costs
- Neighbor advertised distances

## Algorithm Properties
- Uses Bellman-Ford style computation
- Self-stopping

---

## Example

![Distance Vector Example](https://github.com/user-attachments/assets/a0c1aede-821b-48ef-9018-1805d16d487f)

### `B` Only Knows:
- Direct costs to `A` and `C`
- Advertised distances from `A` and `C`

### `A` Advertises to `B` About:
- `Z`
- `X`
- `C`

---

# Distance Vector Algorithm

Based on the **Bellman-Ford (BF) equation** (dynamic programming).

## Bellman-Ford Equation

Let:

- `D_x(y)` = cost of the least-cost path from `x` to `y`

```math
D_x(y) = min_v { c(x,v) + D_v(y) }
```

Where:
- `min` = minimum over all neighbors `v` of `x`
- `c(x,v)` = direct link cost from `x` to `v`
- `D_v(y)` = `v`'s estimated least-cost path cost to `y`

---

## Bellman-Ford Example

![Bellman-Ford Example](https://github.com/user-attachments/assets/c0759357-4389-4377-9891-fb20cec0b39e)

---

# Distance Vector Example

![Distance Vector Routing Example](https://github.com/user-attachments/assets/aa1b6ed3-ff54-4e2a-b297-117b88e6f5e6)

---

# Comparison of LS and DV Algorithms

| Link State (LS) | Distance Vector (DV) |
|-----------------|----------------------|
| Global topology view | Local/neighborhood view |
| Floods link-state advertisements | Exchanges distance vectors with neighbors |
| Flooding overhead | Lower overhead |
| Faster convergence | Can converge slowly |
| Routing loops less likely | Routing loops/count-to-infinity possible |
| Bad info affects local computation | Incorrect advertisements can propagate recursively |

---

# Making Routing Scalable

The Internet uses a hierarchical structure.

## Autonomous Systems (AS)

- An **AS** is a set of interconnected routers
- Each AS is administered by an ISP or organization
- Example: An AS in Davis could be operated by AT&T

Routers inside the same AS communicate using the same intra-domain routing protocol.

---

# Internet Approach to Scalable Routing

## Intra-AS
Communication within the same AS.

## Inter-AS
Communication between different ASes.

## Gateway Routers
- Connect different ASes
- Handle traffic entering and leaving an AS
