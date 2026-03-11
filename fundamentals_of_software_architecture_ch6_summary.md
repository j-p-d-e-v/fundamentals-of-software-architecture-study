 Chapter 6 Summary — Measuring and Governing Architecture Characteristics
(Fundamentals of Software Architecture)

---

## 1. Main Idea of the Chapter

Architecture characteristics must not only be **defined**, they must also be:

- Measurable
- Continuously verified
- Automatically enforced

Architectural rules should not rely only on documentation or diagrams.

Instead, they should be **verified automatically using fitness functions**.

---

## 2. Architecture Fitness Functions

**Definition**

A fitness function is a mechanism that provides an objective integrity assessment
of an architecture characteristic.

In simple terms:

A test that verifies whether architectural rules are still respected.

Examples:

| Architecture Characteristic | Fitness Function |
|---|---|
| Performance | latency tests |
| Security | vulnerability scanning |
| Modularity | dependency analysis |
| Availability | monitoring |
| Scalability | load tests |

---

## 3. Types of Architecture Measurements

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

Average metrics can hide problems.

Example:

Average latency = 200ms
Some requests = 2 seconds

Better metrics include:

- p95 latency
- p99 latency
- maximum latency

---

### Structural Measures

Measure code structure.

Examples:

- modularity
- coupling
- cyclic dependencies
- cyclomatic complexity

#### Cyclomatic Complexity

Measures number of execution paths in code.

Formula:

CC = E − N + 2

General guideline:

| Complexity | Interpretation |
|---|---|
| 1–5 | Good |
| <10 | Acceptable |
| >10 | Needs refactoring |
| >50 | Extremely complex |

High complexity harms:

- maintainability
- testability
- readability

---

### Process Measures

Measure development process quality.

Examples:

- code coverage
- deployment success rate
- build frequency
- defect rate

Important note:

100% test coverage does **not guarantee correct tests**.

---

## 4. Cyclic Dependencies

Example:

A → B → C → A

Problems:

- destroys modularity
- increases coupling
- prevents reuse
- leads to "Big Ball of Mud"

Fitness functions can detect cycles automatically and fail the build.

Example tools:

- JDepend
- ArchUnit
- NetArchTest

---

## 5. Enforcing Layered Architecture

Example layered system:

Presentation
↓
Controller
↓
Service
↓
Persistence
↓
Database

Example rules:

- Controllers cannot access persistence directly
- Services are accessed only by controllers
- Persistence is accessed only by services

If violated:

The build fails.

This protects:

- Modularity
- Maintainability
- Testability

---

## 6. Distance from the Main Sequence

Uses two metrics:

- Abstractness (A)
- Instability (I)

Ideal architecture follows:

A + I = 1

Distance from this ideal line reveals structural design problems.

### Zone of Pain

Low abstraction + low instability

Meaning: rigid but stable code.

### Zone of Uselessness

High abstraction + high instability

Meaning: abstract code nobody depends on.

Fitness functions can enforce acceptable distance.

---

## 7. Chaos Engineering

Netflix created the **Simian Army** to test system resilience.

Examples:

### Chaos Monkey
Randomly shuts down servers to test system resilience.

### Security Monkey
Detects security misconfigurations.

### Conformity Monkey
Ensures services follow governance rules.

### Janitor Monkey
Removes unused infrastructure.

Key philosophy:

Failure is inevitable. Systems must be designed and tested to survive it.

---

## 8. Architecture Governance

Fitness functions act like automated **checklists**.

Inspired by aviation and surgical safety checklists.

They help because:

- complex systems cause mistakes
- developers are busy
- automation prevents architecture drift

---

## 9. Practical Fitness Function Examples

Examples:

- No cyclic dependencies
- Layer access restrictions
- API latency < 300ms
- Services must support standard REST verbs
- Internal services must not be publicly accessible

These checks can run in:

- CI pipelines
- automated tests
- monitoring systems

---

## 10. Key Lesson

Architecture should be:

- observable
- measurable
- automatically enforced

Not just documented.

Architecture becomes part of the system through:

- tests
- metrics
- monitoring
- chaos engineering

---

## One Sentence Summary

Architecture is not just design — it must be **continuously verified through automated checks.**
