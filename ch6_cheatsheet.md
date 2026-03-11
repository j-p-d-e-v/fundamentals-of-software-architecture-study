# Fundamentals of Software Architecture — Chapter 6 Cheatsheet
## Measuring and Governing Architecture Characteristics

---

## 1. Core Idea

Architecture characteristics must not only be defined, they must also be:

- Measurable
- Continuously verified
- Automatically enforced

This is achieved using **Architecture Fitness Functions**.

Architecture should not rely only on:
- documentation
- diagrams
- code reviews

Instead it should rely on **automated verification**.

---

## 2. Architecture Fitness Function

**Definition**

A mechanism that provides an objective integrity assessment of an architecture characteristic.

Simple idea:

A test that checks whether architecture rules are still respected.

Examples:

| Architecture Rule | Fitness Function |
|---|---|
| No cyclic dependencies | Dependency analysis |
| API latency < 300ms | Performance test |
| System availability | Monitoring |
| Layer isolation | Architecture tests |
| Security configuration | Security scanning |

---

## 3. Types of Measurements

### Operational Measures

Measure runtime behavior.

Examples:
- response time
- throughput
- latency
- error rate

Example metrics:

- Page load < 500ms
- API response < 300ms
- UI interaction < 100ms

Important insight:

Averages can hide real problems.

Example:

Average latency = 200ms
But some requests = 2 seconds

Better metrics include:
- p95 latency
- p99 latency
- maximum response time

---

### Structural Measures

Measure code structure.

Examples:
- modularity
- coupling
- cyclic dependencies
- cyclomatic complexity

#### Cyclomatic Complexity

Measures number of possible execution paths in a function.

Formula:

CC = E − N + 2

Guidelines:

| Complexity | Meaning |
|---|---|
| 1–5 | Good |
| <10 | Acceptable |
| >10 | Needs refactoring |
| >50 | Very complex |

High complexity harms:
- maintainability
- testability
- readability

---

### Process Measures

Measure development process quality.

Examples:
- test coverage
- deployment success rate
- build frequency
- defect rate

Example:

Testability is often measured using code coverage tools.

However:

100% coverage does **not** guarantee correct tests.

---

## 4. Cyclic Dependencies

Example:

A → B → C → A

Problems caused:

- breaks modularity
- increases coupling
- prevents reuse
- leads to “Big Ball of Mud” architecture

Fitness functions can automatically detect cycles and fail the build.

Example tools:

- JDepend
- ArchUnit
- NetArchTest

---

## 5. Layer Governance

Example layered architecture:

Presentation
↓
Controller
↓
Service
↓
Persistence
↓
Database

Rules may include:

- Controller cannot access Persistence directly
- Service may only be accessed by Controller
- Persistence may only be accessed by Service

If violated:

The build fails.

This protects:

- modularity
- maintainability
- testability

---

## 6. Distance from the Main Sequence

Uses two metrics:

- Abstractness (A)
- Instability (I)

Ideal architecture follows:

A + I = 1

Distance from this ideal line indicates design problems.

### Zone of Pain

Low abstraction
Low instability

Meaning:
stable but rigid code.

### Zone of Uselessness

High abstraction
High instability

Meaning:
abstract code nobody uses.

Fitness functions can enforce acceptable distance.

---

## 7. Chaos Engineering

Netflix introduced **Simian Army** tools.

Examples:

### Chaos Monkey
Randomly terminates servers to test resilience.

### Security Monkey
Detects security misconfigurations.

### Conformity Monkey
Ensures services follow governance rules.

### Janitor Monkey
Removes unused cloud resources.

Key philosophy:

Failure **will** happen — systems must be tested for resilience.

---

## 8. Architecture Governance Philosophy

Fitness functions act like **automated checklists**.

Inspired by aviation and medical safety checklists.

They help because:

- complex systems cause mistakes
- humans forget details
- automation prevents architecture drift

---

## 9. Practical Fitness Function Examples

Examples:

- No cyclic dependencies
- Layer access restrictions
- API latency < 300ms
- Service must support REST verbs
- Execution service cannot be publicly exposed

These rules can be enforced via:

- tests
- CI pipelines
- monitoring systems

---

## 10. Big Lesson of Chapter 6

Architecture should be:

- observable
- measurable
- automatically enforced

Not just:

- documentation
- diagrams

Use:

- fitness functions
- metrics
- monitoring
- chaos engineering

---

## One Sentence Summary

Architecture must be **continuously validated through automated checks**.
