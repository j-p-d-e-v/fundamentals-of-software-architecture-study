
# Fundamentals of Software Architecture — Chapter 4 Summary
## Architecture Characteristics Defined

## 1. What Are Architecture Characteristics?
Architecture characteristics describe the **operational and quality attributes of a system**, rather than the features it provides.

They answer:

- **What does the system do?** → Domain requirements
- **How well must the system do it?** → Architecture characteristics

### Examples

Domain Requirement:
- User can send messages
- User can create an account

Architecture Characteristics:
- System must support 10 million users
- System must be available 24/7
- All data must be encrypted
- System response time must be < 200 ms

Architecture characteristics influence **architectural structure and design decisions**.

---

# 2. Three Criteria of Architecture Characteristics

A requirement becomes an architecture characteristic if it:

1. **Is not directly related to domain functionality**
2. **Influences structural aspects of the system**
3. **Is critical to the system's success**

Example:

Requirement:
System must support 10 million users.

Why architectural?
Because it forces architectural decisions such as:

- Load balancing
- Distributed systems
- Horizontal scaling
- Database sharding

---

# 3. Explicit vs Implicit Architecture Characteristics

### Explicit Characteristics
Clearly written in requirements.

Examples:

- System must support 100k concurrent users
- System uptime must be 99.99%
- Data must be encrypted

### Implicit Characteristics
Not written but **assumed necessary**.

Examples:

- Security
- Reliability
- Availability

Architects must **identify implicit characteristics** during system analysis.

---

# 4. Categories of Architecture Characteristics

The chapter organizes characteristics into three broad groups.

## Operational Characteristics
Concern how the system behaves in production.

Examples:

- Availability
- Reliability
- Performance
- Recoverability
- Robustness
- Scalability

These affect infrastructure and operations.

Example decisions:

- Redundant servers
- Load balancers
- Failover systems
- Distributed deployment

---

## Structural Characteristics
Concern the **internal structure of the system and codebase**.

Examples:

- Configurability
- Extensibility
- Maintainability
- Portability
- Installability
- Reusability
- Supportability
- Upgradeability

These influence **how easily the system evolves over time**.

---

## Cross-Cutting Characteristics
These affect **multiple parts of the system simultaneously**.

Examples:

- Security
- Privacy
- Authentication
- Authorization
- Accessibility
- Legal compliance
- Data archiving

Security is a classic cross-cutting concern because it affects:

- APIs
- Databases
- Network communication
- Logging
- Infrastructure

---

# 5. Custom Architecture Characteristics

Sometimes organizations create **unique characteristics specific to their business**.

Example from the book: **“Italy-ility”**

This represented a requirement that the system must continue operating if the company lost communication with its Italian branch.

It combined multiple characteristics:

- Availability
- Recoverability
- Resilience

Lesson:

Architecture characteristics can be **business-specific**.

---

# 6. Architecture Terminology Is Ambiguous

Many architecture terms overlap or have unclear definitions.

Examples:

| Term | Meaning |
|-----|------|
Interoperability | Ease of integrating with other systems |
Compatibility | Ability to operate within standards or environments |
Availability | System is operational |
Reliability | System functions correctly over time |

Example in networking:

UDP:
- Available
- Not reliable

TCP:
- Reliable delivery

Architects must establish **shared vocabulary within teams**.

---

# 7. ISO Software Quality Model

The ISO model lists several software quality characteristics.

Examples:

- Performance efficiency
- Compatibility
- Usability
- Reliability
- Security
- Maintainability
- Portability

These provide a **reference framework**, but no universal standard exists.

---

# 8. Functional Suitability Is NOT an Architecture Characteristic

Functional suitability describes **whether the system performs the intended functions**.

Examples:

- Functional completeness
- Functional correctness
- Functional appropriateness

These are **domain requirements**, not architectural qualities.

Architecture characteristics focus on **system behavior and qualities**, not functionality.

---

# 9. Trade-offs in Architecture

Architecture characteristics often **conflict with each other**.

Examples:

Security vs Performance
- Encryption adds CPU overhead and latency

Scalability vs Consistency
- Distributed systems often sacrifice strict consistency

Flexibility vs Simplicity
- Highly flexible systems introduce complexity

Architects must balance these competing forces.

---

# 10. The "Least Worst Architecture"

Architects cannot optimize every characteristic simultaneously.

Therefore the goal is:

> **Do not aim for the best architecture, aim for the least worst architecture.**

Meaning:

Find the best balance among competing constraints.

---

# 11. Avoid Too Many Architecture Characteristics

Supporting too many characteristics leads to:

- Overengineering
- Complex designs
- Generic architectures that solve nothing well

Architects must identify **the few most critical characteristics**.

---

# 12. Architecture Is Iterative

Architecture is rarely correct on the first attempt.

Instead it evolves through:

1. Design
2. Implementation
3. Learning
4. Adjustment

This aligns with **Agile principles**.

Architecture should therefore be **iterative and adaptable**.

---

# Key Takeaways

1. Architecture characteristics describe **system qualities**, not features.
2. They drive **architectural decisions and system structure**.
3. Characteristics often **conflict**, creating trade-offs.
4. Architects aim for the **least worst architecture**, not perfection.
5. The most important skill is identifying **the few critical characteristics**.
6. Architecture evolves through **iteration and refinement**.
