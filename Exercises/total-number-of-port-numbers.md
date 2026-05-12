## Total Number of Ports Available

**Question:** What is the total number of ports that can be used by a process?

---

### Solution:

**Port field = 16 bits → 2¹⁶ = 65,536 total ports**

**Numbered 0 to 65,535 (that's 65,536 distinct values)**

---

### Port Ranges:

**0 - 1,023:** Well-known ports
- Examples: HTTP (80), DNS (53), SSH (22)

**1,024 - 49,151:** Registered ports

**49,152 - 65,535:** Ephemeral/dynamic ports

---

### Key Points:

- Total number of ports: **65,536** (2¹⁶)
- Port numbering: **0 to 65,535** (inclusive)
- Port 0 is reserved and typically not used in practice
