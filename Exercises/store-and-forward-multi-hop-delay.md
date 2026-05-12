## Network Transfer Time Problem

In the network below, the source wants to transfer a huge file of size 8 × 10⁶ bits to the destination. How much time will it take for the file to reach the destination, assuming no other traffic?

<img width="292" height="94" alt="Screenshot 2026-05-12 at 4 07 00 PM" src="https://github.com/user-attachments/assets/fb4fcc8f-575a-49d4-8987-bc95e2a474e1" />

### Solution:

When it comes to link delays, the bottleneck dominates → when one link is orders of magnitude slower than the rest, it sets the pace for the whole transfer.

**Time = File Size / Bottleneck rate**

**Note:** All computations should be done with bits (bps)

### Converting to bps:

- 200 Mbps = 200 × 10⁶ bps = 2 × 10⁸ bps
- 2 Mbps = 2 × 10⁶ bps
- 8000 Kbps = 8000 × 10³ bps = 8 × 10⁶ bps

**Bottleneck = min(2 × 10⁸, 2 × 10⁶, 8 × 10⁶) = 2 × 10⁶ bps**

### Calculation:

**T = (8 × 10⁶ bits) / (2 × 10⁶ bps) = 4 seconds**

---

### Shortcut: Unit Prefixes

- **k (kilo)** = thousand = 10³
- **M (mega)** = million = 10⁶
- **G (giga)** = billion = 10⁹
