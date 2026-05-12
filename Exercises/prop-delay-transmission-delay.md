## Propagation vs Transmission Delay Problem

A sender is transmitting a packet of length L = 1,250 bytes over a link with a transmission rate R = 10 Mbps. If the propagation speed of the medium is s = 2.5 × 10⁸ m/s, at what distance (d) would the propagation delay be exactly equal to the transmission delay?

---

### Solution:

**Step 1: Calculate Transmission Delay**

**d<sub>transmission</sub> = L / R**

**Conversions needed:**
- **Bytes to bits:** 1 byte = 8 bits, so 1,250 bytes = 1,250 × 8 = 10,000 bits
- **Mbps to bps:** 10 Mbps = 10 × 10⁶ bps = 10,000,000 bps

**Calculation:**

d<sub>transmission</sub> = 10,000 bits / 10,000,000 bps = 0.001 s

**Converting seconds to milliseconds:**
- **s to ms:** 1 s = 1,000 ms, so 0.001 s = 1 ms

**d<sub>transmission</sub> = 1 ms**

---

**Step 2: Set Propagation Delay Equal to Transmission Delay**

**Propagation Delay = d / s**

Since we want propagation delay = transmission delay:

d / s = d<sub>transmission</sub>

d / s = 0.001 s

d = s × 0.001 s

d = 2.5 × 10⁸ m/s × 0.001 s = 250,000 m

**Converting meters to kilometers:**
- **m to km:** 1 km = 1,000 m, so 250,000 m = 250 km

**d = 250 km**

---

### All Conversions Used:

1. **Bytes to bits:** multiply by 8
   - 1,250 bytes = 10,000 bits

2. **Mbps to bps:** multiply by 10⁶
   - 10 Mbps = 10,000,000 bps

3. **Seconds to milliseconds:** multiply by 1,000
   - 0.001 s = 1 ms

4. **Meters to kilometers:** divide by 1,000
   - 250,000 m = 250 km

---

### Summary:

At a distance of **250 km**, the propagation delay equals the transmission delay of **1 ms**.
