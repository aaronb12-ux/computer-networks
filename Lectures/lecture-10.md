## Router Architecture Overview

High-level view of generic router architecture:

<img width="524" height="269" alt="Screenshot 2026-05-11 at 4 09 15 PM" src="https://github.com/user-attachments/assets/f173de78-5ba0-4c57-903d-995ac0fa1e8a" />

**Components:**
- Input ports perform forwarding lookup
- Switching fabric transfers packets internally
- Output ports contain queues/scheduling
- Router processor computes routing information

---

## Buffer Management

Packets are dropped if buffer is full.

<img width="391" height="251" alt="Screenshot 2026-05-11 at 4 11 15 PM" src="https://github.com/user-attachments/assets/599ac850-8173-4b0d-9100-5efc6aced944" />

- Link acts as a server transmitting packets
- Transmission rate is limited by link bandwidth 'R'

---

## Packet Scheduling: FCFS (First Come First Served)

- Single queue
- Also called FIFO (First In First Out)
- Packets served in order of arrival
- No traffic differentiation
- Simple scheduling policy

<img width="601" height="114" alt="Screenshot 2026-05-11 at 4 13 56 PM" src="https://github.com/user-attachments/assets/43290472-55b2-46cf-882c-97e09b3d1df2" />
