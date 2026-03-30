# Chapter 13 Cheatsheet - Service-Based Architecture

## One-Line Definition
Service-Based Architecture is a **distributed architecture of coarse-grained domain services**, usually with a **shared or partially shared database**, positioned between a monolith and microservices.

---

## Fast Identification Signals

Choose **Service-Based Architecture** when the scenario includes:

- clear business domains
- separate deployment per domain
- strong transactional consistency still matters
- lower complexity than microservices is desired
- shared reporting or SQL joins still matter
- coarse-grained services are acceptable

---

## Core Shape

- Distributed system
- Coarse-grained domain services
- UI can be monolithic, domain-based, or service-based
- Database can be shared, partially partitioned, or more separated
- API gateway/proxy is optional

---

## Main Strengths

- better deployability than a monolith
- good modularity
- good testability
- better ACID support than microservices
- lower operational complexity than microservices
- fewer remote calls than fine-grained architectures
- good reliability and fault tolerance

---

## Main Weaknesses

- weaker elasticity
- less precise scaling
- broader service scope than microservices
- shared database can create schema coupling
- hidden coupling can appear through shared libraries
- autonomy is weaker than microservices

---

## Key Trade-Off

### What SBA gains
- simpler transactions
- stronger local consistency
- simpler coordination
- lower ops complexity

### What SBA loses
- less fine-grained autonomy
- less precise scaling
- broader test/change scope
- possible database coupling

---

## ACID vs BASE

### SBA
- business transaction often stays inside one coarse-grained service
- local transaction boundary is easier
- ACID is more feasible

### Microservices
- workflow often spans many services
- eventual consistency is more common
- sagas/compensation are more common

---

## Shared Database Rule

Shared database is useful for:
- joins
- reporting
- consistency
- lower duplication

Shared database is dangerous because of:
- schema coupling
- hidden dependencies
- change blast radius
- weaker service autonomy

---

## Worst Practice

### One giant shared entities library
Why it is bad:
- couples all services to one implementation artifact
- increases change blast radius
- increases retesting/redeployment scope
- weakens independence

---

## Better Practice

### Logical database partitioning by domain
Examples:
- customer
- order
- invoicing
- tracking
- common

Goal:
- contain the blast radius of schema change
- keep domains meaningful
- keep common small and stable

---

## "Common" Domain Warning

A common domain is necessary sometimes, but dangerous if it grows too large.

Rule:
- keep common small
- keep common stable
- govern changes carefully

If everything depends on common, common becomes the hidden monolith.

---

## Internal Service Design

A service can be internally organized using:
- layered design
- domain partitioning

Important:
A service is both:
- a deployment unit
- an internal architecture unit

---

## Quanta

### One quantum
All services share the same UI and database.

### Multiple quanta
Services are partitioned together with:
- separate UI
- separate database
- separate operational/security zones

---

## Ratings to Remember

### Strong
- Deployability
- Fault tolerance
- Modularity
- Reliability
- Testability
- Cost

### Medium
- Performance
- Scalability
- Simplicity
- Evolutionary support

### Lower
- Elasticity

---

## SBA vs Monolith vs Microservices

### Monolith
- simplest deployment
- simpler data model
- weaker independent deployability

### Service-Based Architecture
- distributed
- coarse-grained services
- shared or partially shared data
- stronger ACID support
- pragmatic middle ground

### Microservices
- distributed
- fine-grained services
- database ownership per service
- more eventual consistency
- higher autonomy and higher complexity

---

## Use SBA When

- domains are clear
- you want distributed deployment
- ACID still matters
- shared reporting matters
- you want less complexity than microservices
- moderate scalability is enough

---

## Do Not Use SBA When

- strict database ownership per service is required
- very fine-grained scaling is required
- very small independently released services are required
- eventual consistency is acceptable and autonomy matters more
- the organization is aiming fully for microservices

---

## Exam Trigger Phrases

If you see:
- “clear business domains”
- “independent deployment”
- “strong consistency”
- “shared reporting”
- “avoid microservices complexity”

Think: **Service-Based Architecture**

If you see:
- “strict per-service data ownership”
- “independent release of tiny capabilities”
- “fine-grained scaling”
- “eventual consistency is okay”

Think: **Microservices**
