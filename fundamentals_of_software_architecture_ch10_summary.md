# Chapter 10 – Layered Architecture Summary

## Core Idea
Layered architecture organizes systems into horizontal layers:
- Presentation
- Business
- Persistence
- Database

It is one of the most common and simplest architecture styles.

---

## Key Characteristics

### Strengths
- Simple and easy to understand
- Low cost to build and maintain (initially)
- Familiar to most developers
- Clear separation of concerns

### Weaknesses
- Poor scalability (single deployment unit)
- Limited flexibility
- Hard to evolve for complex systems
- Performance overhead due to multiple layers

---

## Important Concepts

### 1. Separation of Concerns
Each layer has a specific responsibility and should not mix concerns.

### 2. Technical Partitioning
Layers are grouped by technical role, not business domain.

### 3. Layers of Isolation
- Closed layers: strict flow, no skipping
- Open layers: allow skipping for performance

Trade-off:
- Closed = better maintainability
- Open = better performance

---

## Architecture Sinkhole Anti-Pattern
Occurs when layers only pass data without adding value.

Rule:
- <=20% sinkholes: acceptable
- ~80% sinkholes: wrong architecture choice

---

## When to Use
- Small applications
- Simple domains
- Tight deadlines
- Starting point before evolving architecture

---

## Key Trade-offs

| Characteristic | Rating |
|--------------|--------|
| Simplicity   | High   |
| Cost         | High   |
| Modularity   | Medium |
| Reliability  | Medium |
| Performance  | Low    |
| Scalability  | Low    |
| Deployability| Low    |

---

## Key Insight
Layered architecture is a **starting point**, not an end state for complex systems.
