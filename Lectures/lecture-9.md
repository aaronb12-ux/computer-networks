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

---

## The Network Core

- Internet core: Mesh of interconnected routers
- Hosts break application messages into packets
  - Routers forward packets hop-by-hop
  - Uses store-and-forward transmission
- Transmission delay at a router = L (packet length) / R (link transmission rate)

<img width="271" height="289" alt="Screenshot 2026-05-11 at 3 25 50 PM" src="https://github.com/user-attachments/assets/4d0e1943-3096-459e-9b68-e45572ea51e1" />

---

## Packet-Switching: Store-and-Forward

<img width="624" height="148" alt="Screenshot 2026-05-11 at 3 28 11 PM" src="https://github.com/user-attachments/assets/8c28ced7-8551-40b5-839c-191937fc185d" />

**Time required to reach destination:**

**Example: 3 packets and 2 links**
- 1st packet → L/R (to get to router) + L/R (to get to destination) = 2L/R
- 2nd packet → Time for 1st packet + L/R = 3L/R
- 3rd packet → 4L/R

**General formula:** If there are N links and P packets, total time = **(N + P - 1) × L / R**

---

## Packet-Switching: Queuing

<img width="451" height="155" alt="Screenshot 2026-05-11 at 3 30 56 PM" src="https://github.com/user-attachments/assets/28032894-9a2e-4d95-9f55-6b8b92920507" />

Queuing occurs when arrival rate > service rate.

- Packets wait in output buffer
- Queue buildup increases delay
- Full buffer leads to packet loss
- Packet switching enables resource sharing

---

## Alternative to Packet Switching: Circuit Switching

<img width="240" height="231" alt="Screenshot 2026-05-11 at 3 33 25 PM" src="https://github.com/user-attachments/assets/a039e0b2-1a5f-4296-87e8-a3d26a46c5a6" />

- Dedicated bandwidth allocated per connection
- No resource sharing
- Used traditionally in telephone networks
- Idle reserved resources cannot be used by someone else
- Circuit setup required before transmission

---

## Circuit Switching: FDM and TDM

### Frequency Division Multiplexing (FDM):
- Frequency divided into bands
- Each user gets dedicated band
- Simultaneous transmission possible

<img width="281" height="114" alt="Screenshot 2026-05-11 at 3 36 06 PM" src="https://github.com/user-attachments/assets/8c244b19-cf26-4877-89d6-36a5648e711e" />

### Time Division Multiplexing (TDM):
- Time divided into slots
- Each user gets periodic timeslot
- User transmits sequentially in time

<img width="297" height="104" alt="Screenshot 2026-05-11 at 3 36 42 PM" src="https://github.com/user-attachments/assets/284fdd97-3a5c-4397-a8ef-776dd079ea24" />

---

## Packet Switching versus Circuit Switching

### Packet Switching:
- Efficient for bursty traffic
- Resources shared dynamically
- No dedicated bandwidth
- Packets may be queued
- Congestion may cause delay or loss
- Better resource utilization
- Packets routed independently

### Circuit Switching:
- Inefficient if user is idle
- Resources reserved
- Dedicated bandwidth per connection
- Predictable transmission
- Guaranteed resource availability
- Possible bandwidth wastage
- Fixed path/circuit
