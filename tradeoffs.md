# Common Architecture Trade-offs

Architecture requires balancing competing system qualities.

Architects aim for the **least worst architecture**, not a perfect one.

---

## Security vs Performance

Security mechanisms add overhead.

Examples:
- Encryption
- Authentication
- Authorization checks

Trade-off:
More security → slower performance.

---

## Consistency vs Scalability

Highly scalable distributed systems may sacrifice strict consistency.

Example:
- Eventual consistency in distributed databases

Trade-off:
Strong consistency → reduced scalability.

---

## Availability vs Consistency

Related to the CAP theorem.

Trade-off:
Systems may sacrifice consistency to remain available during failures.

---

## Flexibility vs Simplicity

Highly flexible architectures are often more complex.

Trade-off:
Generic architecture → harder to build and maintain.

---

## Performance vs Maintainability

Highly optimized systems can become difficult to maintain.

Trade-off:
Optimization vs readability and maintainability.

---

## Key Principle

Architecture is about balancing competing constraints.

The goal is the **least worst architecture**.
