
# Chapter 7 – Architecture Quantum Case Study Cheat Sheet
_Fundamentals of Software Architecture_

This cheat sheet summarizes how an architect would design the **online auction system** from the case study using **architecture characteristics** and **architecture quanta**.

---

# Step 1 — Identify the Driving Requirements

From the case study we extract the most important requirements.

1. Nationwide scale
2. Hundreds or thousands of bidders
3. Many simultaneous auctions
4. Real-time bidding
5. Live video stream
6. Correct ordering of bids
7. Credit card payments
8. Reputation tracking
9. Company expanding through mergers

Architects ask:

> Which requirements will strongly influence the architecture?

These are the **Driving Architecture Characteristics**.

---

# Step 2 — Extract Architecture Characteristics

| Requirement | Architecture Characteristic |
|---|---|
| Nationwide scale | Scalability |
| Bursty auction traffic | Elasticity |
| Real-time bidding | Performance |
| Ordered bids | Reliability / Consistency |
| Credit card payment | Security |
| Fraud history | Auditability |
| Live video | Scalability + Performance |
| Company mergers | Interoperability |

Not all characteristics affect every subsystem.

This is where **Architecture Quantum** becomes important.

---

# Step 3 — Identify Architecture Quanta

Different parts of the system have **different priorities**.

| Quantum | Description |
|---|---|
| Bid Processing | Real-time bid submission |
| Bid Streaming | Broadcasting bids to bidders |
| Video Streaming | Live video delivery |
| Payments | Credit card processing |
| Reputation | Bidder reputation tracking |

Each quantum optimizes for **different architecture characteristics**.

---

# Step 4 — Assign Characteristics to Each Quantum

## Bid Processing Quantum

This is the **core auction logic**.

| Characteristic | Reason |
|---|---|
| Reliability | Bids must not be lost |
| Ordering | Correct auction results |
| Performance | Real-time bidding |
| Availability | Auctions cannot stop |

This subsystem requires **strict correctness and low latency**.

---

## Bid Streaming Quantum

Broadcasts bid updates to participants.

| Characteristic | Reason |
|---|---|
| Scalability | Many viewers |
| Performance | Real-time updates |
| Availability | Continuous bidder feedback |

Typically implemented with **event streaming / pub-sub systems**.

---

## Video Streaming Quantum

Handles live video for auctions.

| Characteristic | Reason |
|---|---|
| Throughput | Large video data |
| Scalability | Many viewers |
| Performance | Low latency delivery |

Usually implemented using **CDNs or media streaming infrastructure**.

---

## Payment Quantum

Handles credit card transactions.

| Characteristic | Reason |
|---|---|
| Security | Sensitive financial data |
| Reliability | Correct charging |
| Auditability | Financial traceability |

Often isolated as a **secure subsystem**.

---

## Reputation Quantum

Tracks bidder behavior and reputation.

| Characteristic | Reason |
|---|---|
| Integrity | Correct reputation scores |
| Auditability | Track reputation changes |
| Consistency | Prevent manipulation |

This subsystem can tolerate **higher latency** than bidding.

---

# Step 5 — Derive the Architecture Structure

Based on the quanta, a possible architecture emerges:

```
Bidders
   │
   ▼
Bid Gateway
   │
   ▼
Bid Processing Service
   │
   ▼
Event Stream
   │
   ├── Bid Streaming Service
   ├── Auctioneer Dashboard
   └── Analytics
```

Other supporting services:

- Video Service
- Payment Service
- Reputation Service

Each subsystem is optimized for its **own architecture characteristics**.

---

# Step 6 — Hybrid Architecture

The system likely uses **multiple architectural styles**.

| Subsystem | Likely Architecture Style |
|---|---|
| Bid processing | Event-driven |
| Bid streaming | Pub/Sub streaming |
| Video | CDN / media pipeline |
| Payments | Secure service boundary |
| Reputation | Data service |

Modern distributed systems are typically **hybrid architectures**.

---

# Step 7 — Why Architecture Quanta Matter

Architecture quanta help architects determine:

- System boundaries
- Service granularity
- Scaling strategies
- Technology choices

Example:

| Subsystem | Key Characteristics |
|---|---|
| Bid processing | Reliability + Ordering |
| Video streaming | Throughput |
| Payments | Security |

If all these responsibilities lived in a **single monolith**, it would be difficult to optimize each requirement.

Splitting them into **architecture quanta** allows specialized designs.

---

# Key Lesson

Architecture should be driven by **architecture characteristics**, not just by code structure.

Architecture Quanta help answer:

> Which parts of the system must evolve and operate together?
