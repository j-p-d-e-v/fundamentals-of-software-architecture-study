# Chapter 10 – Layered Architecture Cheatsheet

## Structure
Presentation → Business → Persistence → Database

---

## Core Rules
- Each layer has a single responsibility
- No direct access across multiple layers (in closed layers)
- Keep dependencies one-directional (top → down)

---

## Closed vs Open Layers

### Closed Layers
- Must go through each layer
- Strong isolation
- More maintainable

### Open Layers
- Can skip layers
- Better performance
- Higher coupling

---

## Anti-Pattern: Sinkhole
- Layer adds no logic
- Just passes data
- Adds latency and complexity

---

## Strengths
- Easy to understand
- Low cost
- Clear structure

---

## Weaknesses
- Poor scalability
- Hard to evolve
- Performance overhead
- Deployment risk (monolith)

---

## When to Use
- Small systems
- Simple apps
- Early-stage development

---

## When to Avoid
- High scalability needs
- Complex domains
- Distributed systems

---

## Key Architect Questions
1. Does this layer add value?
2. Are layers properly isolated?
3. Should this be closed or open?
4. Are we creating sinkholes?
5. Is this still the right architecture as we grow?

---

## One-Line Summary
Layered architecture optimizes for simplicity and cost, but sacrifices scalability and flexibility.
