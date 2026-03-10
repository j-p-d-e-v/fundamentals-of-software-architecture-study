# Fundamentals of Software Architecture — Chapter 5 Summary
## Identifying Architectural Characteristics

---

# Core Idea of the Chapter

Architects must determine which **architecture characteristics ("-ilities")** matter for a system by analyzing:

- Domain concerns
- Requirements
- Implicit domain knowledge

Not all architectural qualities are written in requirements. Architects must **interpret the problem domain**.

---

# Sources of Architecture Characteristics

Architectural characteristics can come from three places.

## 1. Domain Concerns

Business concerns often imply architectural qualities.

Example:

Domain concern:
System must support millions of users

Architectural implication:
Scalability

Another example:

Domain concern:
Online payment processing

Architectural implication:
Security
Reliability
Auditability

Architects translate **business language → system qualities**.

---

## 2. Explicit Requirements

Some requirements directly state architecture characteristics.

Example:

System must support 1 million concurrent users

Implies:

Scalability
Performance

Explicit requirements are easy to identify because they directly mention system behavior constraints.

---

## 3. Implicit Domain Knowledge

Many architecture characteristics are **not written in requirements** but are assumed based on the domain.

Example:

Requirement:
Accept credit card payments

Implicit architecture characteristic:

Security

Architects must recognize these **unstated expectations**.

---

# Scalability vs Elasticity

The chapter explains an important difference.

## Scalability

Ability of the system to handle **growing load over time**.

Example:

Users increase gradually over months or years

Typical solutions:

- Load balancing
- Horizontal scaling
- Distributed services

---

## Elasticity

Ability of the system to handle **sudden bursts of traffic**.

Example:

Concert ticket sales
Flash sales
Lunch rush in food ordering systems

Elastic systems dynamically increase and decrease resources.

---

# Implicit Characteristics in the Silicon Sandwiches Case

The case study demonstrates how architects derive characteristics from requirements.

Examples:

Requirement:
Integrate with mapping services

Architectural implication:

Interoperability
Reliability
Fault tolerance

---

Requirement:
Mobile device accessibility

Architectural implication:

Usability
Performance

---

Requirement:
Franchised sandwich shops

Architectural implication:

Customizability
Configurability
Multi-tenancy

---

Requirement:
Expand overseas

Architectural implication:

Internationalization
Scalability

---

Requirement:
Accept payment online

Architectural implication:

Security
Auditability
Reliability

---

# Design vs Architecture

Some concerns can be solved either through **architecture** or **design**.

Example: Customization

Architecture approach:

Plugin architecture
Microkernel architecture

Design approach:

Template Method pattern
Configuration files
Feature flags

Architecture affects **system structure**.

Design affects **code implementation**.

---

# Trade-offs in Architecture

A key lesson:

There is no best architecture.
Only the least worst collection of trade-offs.

Architectural decisions always involve compromises.

Example trade-offs:

Microservices → Scalability but more complexity
Monolith → Simplicity but limited scalability
Strong security → Better protection but slower performance

Architects must balance competing qualities.

---

# Prioritizing Architecture Characteristics

Architects should identify many candidate characteristics, then **prioritize the most important ones**.

A useful exercise:

If you had to remove one architecture characteristic, which would it be?

This helps determine which characteristics are **truly critical**.

---

# Key Lessons

1. Architecture characteristics come from **domain concerns, requirements, and implicit knowledge**.
2. Architects must translate **business goals into system qualities**.
3. Not all architecture characteristics appear explicitly in requirements.
4. Over-specifying architecture characteristics leads to **unnecessary complexity**.
5. Architecture always involves **trade-offs**.
6. Architects must **prioritize the most important qualities** for the system.

---

# Core Mental Model

Architectural thinking follows this flow:

Business requirement
↓
Domain concern
↓
Architecture characteristics (-ilities)
↓
Architecture decisions

Example:

Online ordering system
↓
High user traffic
↓
Scalability + Availability
↓
Load balancers + distributed services

---

# Final Insight

Good architects do not try to optimize every characteristic.

Instead they identify:

The smallest set of architectural qualities required for the system to succeed.
