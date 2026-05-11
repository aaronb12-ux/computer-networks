## Principles of Congestion Control:

<img width="253" height="148" alt="Screenshot 2026-05-07 at 11 24 43 AM" src="https://github.com/user-attachments/assets/9ab3c49b-1f91-4813-ba9d-ca821a909e8e" />

Congestion happens when too many senders transmit more data than the network can handle.

**Manifests as:**
- Long delays (due to queuing)
- Packet loss (buffer full)
- Packets get dropped

Congestion control is about the network being overloaded.

**Note:** This is different from flow control → Flow control is about the receiver being overwhelmed.

---

## Causes/Costs of Congestion: Insights

Sending rate increases → Packets spend more time in queue (if the buffer is full, packets are dropped) → Causes delay

Dropped packets trigger retransmission, which adds more load onto the network.

Therefore, congestion is a serious problem.

---

## Approaches Towards Congestion Control

TCP does not get any direct feedback from routers. Instead, it infers congestion based on observation. e.g., Packet loss or increasing delay indicates congestion.

Therefore, sender must adjust its sending rate based on what is inferred (i.e., signals received).

---

## TCP Congestion Control: Details

TCP controls its sending rate using **congestion window (cwnd)**.

cwnd limits how much data can be 'in-flight' at any given time.

<img width="296" height="191" alt="Screenshot 2026-05-07 at 11 29 34 AM" src="https://github.com/user-attachments/assets/42df2f8e-6f60-4ce7-94c2-f45a0c4d0d63" />

**Typically:** lastByteSent - lastByteACKed (in-flight data) ≤ min{cwnd, rwnd}

If there is infinite receiver buffer (i.e., rwnd = ∞), then cwnd effectively controls the sending rate.

**Throughput = cwnd / RTT** (assuming no loss and full utilization)

ACK arrival reflects network delivery rate, so TCP naturally adapts its sending rate to the network. Hence TCP is said to be **self-clocking**.

---

## TCP Slow Start

When a connection begins, TCP starts with a small cwnd.

Initially, **cwnd = 1 MSS** (max segment size)

<img width="213" height="308" alt="Screenshot 2026-05-07 at 11 33 56 AM" src="https://github.com/user-attachments/assets/7f429db2-89bd-415b-b3e2-a0b91475b905" />

Each time an ACK is received, cwnd increases by 1 MSS.

This causes cwnd to **double every RTT**.

→ Therefore, even though it starts slowly, growth is exponential.

---

## TCP: From Slow Start to Congestion Avoidance

Exponential growth cannot continue indefinitely, as it would quickly overload the network.

Hence TCP switches to a more cautious phase called **congestion avoidance**.

This transition happens when cwnd reaches a threshold called **ssthresh** (slow start threshold), which is typically set after a packet loss.

After this point, cwnd increases linearly to avoid congestion.

**Fast Recovery:** In this phase, after receiving 3-duplicate ACKs, the cwnd is reduced by half and 3 is added.

---

## TCP Congestion Control: AIMD

TCP increases its rate slowly over time. But when it detects congestion, it reduces the rate significantly.

<img width="476" height="154" alt="Screenshot 2026-05-07 at 11 42 20 AM" src="https://github.com/user-attachments/assets/6c7b53c6-4281-4df2-b814-66f0c59c51f9" />

The graph shows steady state AIMD behavior (after slow start) and ignores fast recovery details.

**Note:** During fast recovery, and after 3-duplicate ACKs, cwnd continues to increase by 1 MSS for every additional duplicate ACK.

Once ACK for missing segment is received, cwnd goes back to ssthresh.

---

## TCP AIMD: More

**Two congestion control variants:**
- **TCP Tahoe:** Early TCP version (baseline)
- **TCP Reno:** Improved revision of Tahoe with fast retransmit + fast recovery

Both implement AIMD, but differ in how they handle packet loss.

**During congestion avoidance:** cwnd += 1 MSS per RTT

**During fast recovery:** cwnd += 1 MSS per ACK

**Takeaway:** Tahoe resets, Reno recovers

| Event | TCP Tahoe | TCP Reno |
|-------|-----------|----------|
| 3 Duplicate ACKs | cwnd = 1 MSS | ssthresh = cwnd/2 and cwnd = ssthresh + 3 |
| Timeout | cwnd = 1 MSS | cwnd = 1 MSS |

**Key:** Duplicate ACKs indicate that packets are still flowing, suggesting mild congestion.

<img width="489" height="286" alt="Screenshot 2026-05-07 at 11 51 23 AM" src="https://github.com/user-attachments/assets/39e2bcac-058f-44c9-9082-299e8bf2e1dd" />

<img width="483" height="282" alt="Screenshot 2026-05-07 at 11 52 44 AM" src="https://github.com/user-attachments/assets/a6c02a3b-5ffe-4cd5-9bea-780b8d693bf5" />

<img width="493" height="382" alt="Screenshot 2026-05-07 at 11 55 41 AM" src="https://github.com/user-attachments/assets/ba33d567-2f35-424d-8a4d-0baff33a820c" />

<img width="494" height="388" alt="Screenshot 2026-05-07 at 11 56 16 AM" src="https://github.com/user-attachments/assets/b23d5169-a3dc-4d36-b867-9fc8f8b50b53" />

---

## Average TCP Reno Throughput:

**Loss event (3-duplicate ACKs):**
- cwnd = w/2; w is the value when loss occurred

**Congestion Avoidance:**
- cwnd increases by 1 MSS per RTT

**Result:** cwnd oscillates between w/2 and w

**Average window = (w + w/2) / 2 = 3w/4**

**Throughput = 3w / (4 × RTT)**
