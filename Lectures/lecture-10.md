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

- Buffer management decides which packets to drop or accept
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

---

## Scheduling Policies: Priority

- Traffic classified into priority queues
- High-priority traffic is transmitted first
- FIFO ordering within each queue
- Router continues serving highest priority non-empty queue
- Low priority traffic may starve
- Often used for delay sensitive traffic

<img width="300" height="295" alt="Screenshot 2026-05-12 at 3 03 33 PM" src="https://github.com/user-attachments/assets/4d2ac9de-a141-481e-8bec-95b949051eff" />

---

## Scheduling Policies: Round Robin

- Traffic divided into multiple queues/classes
- Router cyclically serves queues
- One packet transmitted per queue
- All queues receive opportunity to transmit
- Prevents starvation
- Improves fairness compared to strict priority

<img width="281" height="149" alt="Screenshot 2026-05-12 at 3 07 48 PM" src="https://github.com/user-attachments/assets/1b19cb09-97cf-46b8-bb92-7ed057f10752" />

---

## Scheduling Policies: Weighted Fair Queuing (WFQ)

- Generalized form of round-robin
- Each queue is assigned a weight based on priority/class
- Higher weight → higher bandwidth share
- In general, queue 'i' receives (w<sub>i</sub> / Σw<sub>j</sub>) × R of link bandwidth
- Provides minimum bandwidth guarantees
- Balances fairness and prioritization

<img width="798" height="620" alt="Screenshot 2026-05-12 at 3 13 00 PM" src="https://github.com/user-attachments/assets/1ae7a432-e7d3-4f86-a676-2e3066979238" />

<img width="429" height="231" alt="Screenshot 2026-05-12 at 3 12 24 PM" src="https://github.com/user-attachments/assets/5ba189d6-c420-4aff-b518-5e699529157c" />

---

## IP Datagram Format (Header + Payload)

<img width="798" height="620" alt="Screenshot 2026-05-12 at 3 13 00 PM" src="https://github.com/user-attachments/assets/6d5d2169-8aa4-4428-9bd8-0be3f2a72405" />

---

## IP Addressing: Introduction

**Interface:** connection between host/router and physical link

- Routers typically have multiple interfaces
- Each interface has its own IP address
- 32-bit identifier
- Identifies a host/router interface
- A device can have multiple IP addresses
- E.g., wired Ethernet and WiFi

<img width="295" height="281" alt="Screenshot 2026-05-12 at 3 22 12 PM" src="https://github.com/user-attachments/assets/2542b570-86ad-410f-9203-b8506d0a1956" />
