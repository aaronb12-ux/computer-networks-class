# File Transfer Through Multi-Link Path

Suppose Host A wants to send a large file to Host B. The path from Host A to Host B has three links with rates:

```text
R1 = 500 Kbps
R2 = 2 Mbps
R3 = 1 Mbps
```

---

## Network Diagram

```text
[A] <----> [Router] <----> [Router] <----> [B]
      500 Kbps        2 Mbps        1 Mbps
```

---

## Conversions

```text
500 Kbps = 500 × 10^3 bps = 500,000 bps
2 Mbps   = 2 × 10^6 bps   = 2,000,000 bps
1 Mbps   = 1 × 10^6 bps   = 1,000,000 bps
```

---

# 1. Throughput of the File Transfer

The end-to-end throughput is determined by the **bottleneck link** (slowest link):

```text
Throughput = min(R1, R2, R3)
```

```text
Throughput = 500 Kbps
```

### Final Answer:

```text
Throughput = 500 × 10^3 bps = 500,000 bps
```

---

# 2. File Transfer Time

## Given:

```text
File size = 4 × 10^6 bytes
```

Convert to bits:

```text
L = 4 × 10^6 × 8 = 32 × 10^6 bits
```

---

## Throughput:

```text
R = 500 × 10^3 bps = 5 × 10^5 bps
```

---

## Transfer Time

We use:

```text
dTotal = L / R
```

Substitute values:

```text
dTotal = (32 × 10^6) / (5 × 10^5)
       = (32 / 5) × 10^(6 - 5)
       = (32 / 5) × 10
       = 64 seconds
```

---

## Final Answer:

```text
Total time = 64 seconds
```

---

# Key Insight

- End-to-end throughput is limited by the **slowest link**
- Even if other links are faster, they do not increase throughput
- File transfer time depends only on:
  - File size (bits)
  - Bottleneck rate
