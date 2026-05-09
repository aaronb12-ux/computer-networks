# Network Layer: Data Plane

## Network-Layer Services and Protocols

Network layer exists in both hosts and routers.

Routers examine destination IP addresses.

Routers move datagrams hop-by-hop toward destination.

<img width="271" height="255" alt="Screenshot 2026-05-09 at 3 52 38 PM" src="https://github.com/user-attachments/assets/4905371e-2d6e-4609-b6d9-11bfb248b209" />

---

## Two Key Network-Layer Functions

### Forwarding:
- Local function performed at each router
- Moves packet from input port to correct output port
- Uses forwarding table
- Operates at a fast timescale (hardware/data plane)

### Routing:
- Network-wide function
- Determines complete path from source to destination
- Uses routing algorithms
- Operates at a slower timescale (software/control plane)

---

## Per-Router Control Plane

**Traditional Networking Approach:**

Routers exchange routing information.

Control logic distributed across routers.

---

## Software-Defined Networking (SDN) Control Plane

Remote controller computes, installs forwarding tables in routers.

<img width="377" height="232" alt="Screenshot 2026-05-09 at 3 58 43 PM" src="https://github.com/user-attachments/assets/2b53dba8-20ad-494a-98c6-9bedf0d96b7b" />

Centralized controller computes routes.

Control logic separated from forwarding hardware.

---

## Network Service Model

Defines services provided by network layer.

Internet uses **best-effort service**.

**No guarantee on:**
- Delivery
- Delay
- Bandwidth
- Packet order

### Why Best-Effort Works Well:
- Simpler/scalable design
- Efficient resource sharing
- TCP provides reliability


slide 11
