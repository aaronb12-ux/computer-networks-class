# Packet Propagation and Transmission Delay Example

## Problem

How long does it take a packet of **1,000 bytes** to propagate over a link with:

- Distance = 2500 km
- Propagation speed = 2.5 × 10⁸ m/s
- Transmission rate = 2 Mbps

More generally:

How long does it take a packet of length **L** to travel over a link of:

- Distance = **d**
- Propagation speed = **s**
- Transmission rate = **R** bps

Does this delay depend on:

- Packet length?
- Transmission rate?

---

# Answer

The total delay is the sum of:

```text
Total Delay = Transmission Delay + Propagation Delay
```

or

```text
dTotal = dTrans + dProp
```

---

## Unit Conversions

```text
2500 km = 2.5 × 10^6 m
1000 bytes = 8000 bits
2 Mbps = 2 × 10^6 bps
```

---

## Propagation Delay

Propagation delay is:

```text
dProp = d / s
```

Substituting the values:

```text
dProp = (2.5 × 10^6 m) / (2.5 × 10^8 m/s)
      = 0.01 s
      = 10 ms
```

---

## Transmission Delay

Transmission delay is:

```text
dTrans = L / R
```

Substituting the values:

```text
dTrans = 8000 bits / (2 × 10^6 bps)
       = 0.004 s
       = 4 ms
```

---

## Total Delay

```text
dTotal = dTrans + dProp
       = 4 ms + 10 ms
       = 14 ms
```

### Final Answer

```text
Total Delay = 14 ms
```

---

# General Formula

For a packet of length **L** bits transmitted over a link with:

- Distance = **d**
- Propagation speed = **s**
- Transmission rate = **R**

The total delay is:

```text
dTotal = (L / R) + (d / s)
```

where:

- `L / R` = Transmission Delay
- `d / s` = Propagation Delay

---

# Does This Delay Depend on Packet Length?

### Yes.

Transmission delay is:

```text
dTrans = L / R
```

As packet length (`L`) increases:

```text
Transmission Delay Increases
```

Therefore:

```text
Total Delay Increases
```

---

# Does This Delay Depend on Transmission Rate?

### Yes.

Transmission delay is:

```text
dTrans = L / R
```

As transmission rate (`R`) increases:

```text
Transmission Delay Decreases
```

Therefore:

```text
Total Delay Decreases
```

---

# Does Propagation Delay Depend on Packet Length or Transmission Rate?

### No.

Propagation delay is:

```text
dProp = d / s
```

It depends only on:

- Distance (`d`)
- Propagation speed (`s`)

It does **not** depend on:

- Packet length (`L`)
- Transmission rate (`R`)

---

# Key Takeaway

| Quantity | Depends On |
|-----------|------------|
| Transmission Delay | Packet Length (L), Transmission Rate (R) |
| Propagation Delay | Distance (d), Propagation Speed (s) |
| Total Delay | L, R, d, and s |

```text
dTotal = (L / R) + (d / s)
```
