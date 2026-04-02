# ⚡ Chapter 14 – Event-Driven Architecture (Ultra-Condensed Cheatsheet)

---

# 🧠 CORE IDEA

EDA = **asynchronous, event-based communication**

> Components react to events, not direct calls

---

# 🔁 REQUEST vs EVENT

| | Request-Based | Event-Based |
|--|--|--|
| Control | Centralized | Distributed |
| Flow | Deterministic | Emergent |
| Timing | Synchronous | Asynchronous |
| Response | Immediate | Deferred |

---

# 🧩 TOPOLOGIES

## 🟢 Broker

- No central control
- Components react independently
- Broadcast model

### ✅ Use when:
- independent processing
- extensibility
- analytics / notifications

### ❌ Weakness:
- no ordering
- no state ownership
- hard error handling

---

## 🔵 Mediator

- Central workflow controller
- Tracks state
- Controls execution order

### ✅ Use when:
- sequencing required
- retries / recovery needed
- workflow orchestration

### ❌ Weakness:
- bottleneck
- complexity
- reduced flexibility

---

# ⚡ ASYNC INSIGHT

> Improves **responsiveness**, NOT **performance**

- response returns fast
- work still happens later

---

# ❗ ERROR HANDLING PROBLEM

- request context is gone
- no direct feedback
- must handle **out-of-band**

---

# 🔁 WORKFLOW EVENT PATTERN

### Purpose:
→ Handle **failures in async systems**

### NOT for:
→ normal workflow execution

### Used for:
- retry
- repair
- escalation

---

# 🔐 RELIABILITY (CRITICAL)

## Failure Points:
1. Producer → Broker
2. Broker → Consumer
3. Consumer → DB

## Solutions:
- persistent queue
- client acknowledge
- transactional commit (LPS)

---

# 📡 BROADCAST

- 1 event → many consumers
- max decoupling

Use for:
- logging
- analytics
- notifications

---

# 🔁 REQUEST-REPLY (Pseudo Sync)

- simulate sync over messaging
- uses correlation ID

### Trade-off:
- adds coupling
- reduces async benefit

---

# ⚖️ WHEN TO USE

## Request-Based
- immediate response
- strong consistency
- strict ordering

## Event-Based
- scalability
- async processing
- loose coupling

---

# 🧠 QUANTUM RULE

> If A waits for B → SAME quantum

(even with messaging)

---

# 🔥 KEY RULES

1. Control defines architecture, not transport
2. Retry ≠ Mediator
3. Mediator = workflow control
4. Workflow pattern = failure handling
5. Broker = independent reactions

---

# 🎯 QUICK DECISION GUIDE

| Requirement | Use |
|--|--|
| independent consumers | Broker |
| ordered workflow | Mediator |
| retry / repair only | Workflow Event Pattern |
| immediate response | Request-Based |
| async + scalable | Event-Based |

---

# 🧠 FINAL MODEL

Broker → "React"
Mediator → "Control"
Workflow Pattern → "Fix failures"

---
