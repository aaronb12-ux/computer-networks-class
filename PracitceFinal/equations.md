# Networking Conversions & Key Formulas

---

## 📌 Unit Conversions

```
1 Gbps = 1 × 10^9 bps
1 Mbps = 1 × 10^6 bps
1 Kbps = 1 × 10^3 bps
```

```
1 ms = 0.001 s
```

---

## 📌 Transmission Delay

```
dtrans = L / R
```

Where:
- L = packet/frame length (bits)
- R = transmission rate (bps)

---

## 📌 Propagation Delay

```
dprop = D / S
```

Where:
- D = distance (meters)
- S = propagation speed (m/s)

---

## 📌 Total Link Delay

```
Total delay = transmission delay
            + propagation delay
            + queueing delay
            + processing delay
```

---

## 📌 Stop-and-Wait Utilization

```
U = dtrans / (RTT + dtrans)
```

Where:
- RTT = round-trip time
- dtrans = transmission time

---

## 📌 CSMA/CD Efficiency

### Step 1: Compute ratio

```
a = dprop / dtrans
```

Example:

```
a = 10 µs / 120 µs
  = 0.0833
```

---

### Step 2: Efficiency formula

```
Efficiency ≈ 1 / (1 + 5a)
```

---

## 📌 Key Intuition

- Higher propagation delay → worse efficiency
- Higher transmission time (larger frames) → better efficiency
- Efficiency depends heavily on:

```
a = dprop / dtrans
```
```



