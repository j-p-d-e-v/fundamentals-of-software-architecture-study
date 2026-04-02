# 📘 Chapter 14 – Event-Driven Architecture (EDA)

---

# 🧠 Core Concept

Event-Driven Architecture is based on:

- **Asynchronous communication**
- **Events triggering reactions**
- **Decoupled components**

---

# 🔁 Request-Based vs Event-Based

## Request-Based
- Central control (orchestrator)
- Synchronous
- Deterministic flow
- Immediate response required

## Event-Based
- No central control (broker)
- Asynchronous
- Flow emerges from events
- Fire-and-forget

---

# 🧩 EDA Topologies

---

## 1. Broker Topology

### Definition
- No central coordinator
- Components react independently to events

### Characteristics
- Highly decoupled
- Scalable
- No workflow control
- No global state

### Strengths
- Flexibility
- Easy extensibility
- Broadcast capability

### Weaknesses
- No ordering control
- No workflow visibility
- Difficult error handling
- Eventual consistency

---

## 2. Mediator Topology

### Definition
- Central mediator controls workflow

### Characteristics
- Centralized coordination
- Tracks workflow state
- Controls execution order

### Strengths
- Supports sequencing
- Supports retries and recovery
- Better error handling

### Weaknesses
- Central bottleneck
- Increased complexity
- Reduced flexibility

---

# ⚡ Asynchronous Communication

## Key Insight

> Improves responsiveness, NOT performance

### Why
- Response returned immediately
- Work still happens in background

---

# ❗ Error Handling Problem

## Issue
- Request context no longer exists
- No direct feedback path

## Result
- Errors must be handled out-of-band

---

# 🔁 Workflow Event Pattern

## Purpose
- Handle failures in async systems

## NOT for:
- Normal workflow execution
- Sequencing

## Used for:
- Retry logic
- Repair routing
- Manual intervention

---

# 🔐 Data Reliability in EDA

## Failure Points
1. Producer → Broker
2. Broker → Consumer
3. Consumer → Database

## Solutions
- Persistent queues
- Client acknowledge mode
- ACID + Last Participant Support

---

# 📡 Broadcast Capability

## Broker Strength
- One event → many consumers

## Use cases
- Analytics
- Logging
- Notifications

---

# 🔁 Request-Reply Pattern

## Purpose
- Simulate synchronous behavior over messaging

## Mechanism
- Correlation ID
- Reply queues

## Trade-off
- Adds coupling
- Reduces async benefits

---

# ⚖️ When to Use What

## Request-Based
- Immediate response required
- Strong consistency
- Deterministic flow

## Event-Based
- Scalability needed
- Async processing acceptable
- Loose coupling preferred

---

# 🧠 Architecture Quantum Insight

> If one component waits for another → SAME quantum

Even if messaging is used.

---

# 🔥 Key Rules

1. Transport does NOT define architecture, control does
2. Retry ≠ Mediator
3. Workflow event pattern = error handling only
4. Mediator = workflow control
5. Broker = independent reactions

---

# 🧪 SCENARIOS

---

## Scenario 1: Ride-Hailing System

### Context
- Trip completed triggers:
  - payment
  - driver earnings
  - receipt
  - analytics
- Independent execution
- New consumers may be added

### Expected Answer

- Dominant: **Broker Topology**
- Payment retry handled at **consumer level**
- Delivery:
  - Guaranteed → payment, earnings
  - Best-effort → receipt, analytics

---

## Scenario 2: Stock Trading System

### Context
- Validate → check balance → place trade → return confirmation
- Strict order required
- Immediate response required

### Expected Answer

- Architecture: **Request-Based**
- If messaging used: **Request-Reply pattern**
- Quantum: **Same quantum**

---

## Scenario 3: Workflow Orchestrator

### Context
- DAG execution
- State tracking required
- Ordered execution
- Retry + repair + manual intervention

### Expected Answer

- Dominant: **Mediator Topology (EDA)**
- Broker insufficient:
  - no coordination
  - no state ownership
- Workflow event pattern:
  - used for **failure handling only**
- Risk:
  - central orchestrator bottleneck / SPOF

---

# 🎯 Final Mental Model

## Broker
→ "Things react independently"

## Mediator
→ "System controls execution"

## Workflow Event Pattern
→ "System handles failures separately"

---
