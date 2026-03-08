# Fundamentals of Software Architecture --- Chapter 2 Summary

## Architectural Thinking

## 1. What is Architectural Thinking

Architectural thinking is the ability to view a system from a high‑level
perspective and understand how different parts interact.\
Architects focus on system structure, trade‑offs, and alignment with
business goals rather than only implementation details.

Key ideas: - Think about **systems as a whole** - Evaluate **trade‑offs
between solutions** - Understand **technical breadth across many
domains** - Align technical decisions with **business drivers**

------------------------------------------------------------------------

## 2. Architecture vs Design

### Architecture Decisions

Architecture decisions define the **structure of the system**.

Examples: - System architecture style (monolith vs microservices) -
Communication patterns (REST, messaging, event‑driven) - Service
boundaries - Deployment topology

Architecture operates at a **higher level of abstraction** and affects
the entire system.

### Design Decisions

Design decisions define **how components are implemented internally**.

Examples: - Class structures - Algorithms - Data structures - Internal
service logic

Architecture focuses on **system structure**, while design focuses on
**implementation details**.

------------------------------------------------------------------------

## 3. Technical Breadth vs Technical Depth

Developers typically focus on **technical depth**: - deep expertise in
specific technologies

Architects require **technical breadth**: - knowledge across many
technology domains

Examples of domains architects should understand: - databases -
messaging systems - networking - caching - infrastructure - distributed
systems

Technical breadth allows architects to: - evaluate multiple solutions -
understand system interactions - make informed trade‑off decisions

------------------------------------------------------------------------

## 4. The Knowledge Pyramid

Knowledge can be categorized into three areas:

1.  **Things you know**
2.  **Things you know you don't know**
3.  **Things you don't know you don't know**

Architects must continually expand awareness of technologies to reduce
the unknown areas.

------------------------------------------------------------------------

## 5. Frozen Caveman Anti‑Pattern

The Frozen Caveman Anti‑Pattern occurs when architects make decisions
based on **past negative experiences** rather than analyzing current
trade‑offs.

Example behavior: "We can't use that technology because it failed once
before."

Why it is dangerous: - blocks innovation - creates biased decisions -
prevents objective trade‑off analysis

Architects must evaluate solutions based on **current context**, not
past fear.

------------------------------------------------------------------------

## 6. Trade‑Off Analysis

A core principle of architecture:

**There is no perfect architecture. Every decision involves
trade‑offs.**

Examples:

Monolith: - simpler - easier debugging - fewer operational challenges

But: - harder to scale parts independently

Microservices: - better scalability - team autonomy

But: - distributed complexity - harder debugging - operational overhead

Architects must analyze: - what is gained - what is sacrificed

------------------------------------------------------------------------

## 7. Understanding Business Drivers

Architecture decisions must align with **business goals**.

Examples of business drivers: - faster feature delivery - scalability
requirements - regulatory compliance - cost constraints

Architects translate business needs into **architecture
characteristics**, such as: - scalability - availability - performance -
security

------------------------------------------------------------------------

## 8. Architects Should Stay Hands‑On

Architects should continue working with code but avoid becoming
development bottlenecks.

Recommended activities:

### Proofs of Concept (POCs)

Test technologies and validate architecture decisions.

### Fixing Bugs

Understand system weaknesses and stay close to the codebase.

### Working on Technical Debt

Improve structural quality of the system.

### Building Developer Tools

Create automation or utilities that help development teams.

------------------------------------------------------------------------

## 9. Avoiding the Bottleneck Trap

Architects should avoid owning critical production code that blocks team
progress.

Instead: - guide the architecture - mentor developers - review
implementations - distribute knowledge across the team

------------------------------------------------------------------------

## Key Takeaways

-   Architecture focuses on **system structure and trade‑offs**
-   Architects require **technical breadth**
-   Architecture decisions must align with **business drivers**
-   Architects must remain **hands‑on but avoid bottlenecks**
-   **No architecture is perfect --- every decision involves
    trade‑offs**
