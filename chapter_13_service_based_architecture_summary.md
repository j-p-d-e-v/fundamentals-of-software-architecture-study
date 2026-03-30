# Chapter 13 Summary — Service-Based Architecture Style

## Core Definition

Service-Based Architecture (SBA) is a distributed architecture style composed of **coarse-grained, domain-scoped services**. It is more modular and deployable than a monolith, but less operationally complex than microservices.

It is a pragmatic middle ground for business systems that want:

- distributed deployment
- domain-based modularity
- stronger transactional consistency
- lower complexity than fine-grained microservices

---

## Core Topology

The default SBA topology is:

- separately deployed **user interface**
- separately deployed **domain services**
- usually a **shared monolithic database**

This means SBA has:

- **stronger deployment boundaries** than a monolith
- but often **weaker data boundaries** than microservices

That trade-off is central to the architecture style.

---

## Service Granularity

Services in SBA are typically **coarse-grained**.

Examples of coarse-grained services:
- OrderService
- CustomerService
- InventoryService
- AccountingService

These are different from fine-grained microservices such as:
- CreateOrderService
- ValidatePaymentService
- ReserveInventoryService

A coarse-grained service can often complete a business request internally through class/component orchestration, instead of requiring many remote service calls.

---

## Why SBA Is Attractive

Because services are coarse-grained, SBA usually has:

- fewer network hops
- fewer remote coordination problems
- lower distributed transaction complexity
- lower operational overhead
- simpler deployment and support model than microservices

This is why the style is often a strong fit for enterprise business applications.

---

## Communication Model

Services are usually called remotely from the UI using:

- REST
- RPC
- messaging
- SOAP

A UI may call services directly, but an API layer or gateway can also be introduced when needed for:

- security
- auditing
- metrics
- service discovery
- external exposure
- centralized cross-cutting concerns

A gateway is optional, not mandatory.

---

## Shared Database and Its Main Trade-Off

A typical SBA system uses a centrally shared database.

### Benefits
- easier SQL joins
- easier reporting
- simpler ACID transactions
- less data duplication
- less synchronization complexity

### Risks
- schema coupling
- hidden dependencies
- weaker service autonomy
- broader coordination when the schema changes
- harder independent evolution of services

This is the biggest structural compromise in SBA:
**service independence at deployment level, but partial coupling at the data level**.

---

## UI Topology Variants

The chapter shows several frontend variants:

### 1. Single Monolithic UI
One UI calls many services.

Good when:
- the frontend is still cohesive
- centralized ownership is acceptable

Risk:
- the frontend can become a bottleneck

### 2. Domain-Based UI
The UI is partitioned by business domain.

Good when:
- the frontend aligns with business areas
- teams want stronger end-to-end domain ownership

### 3. Service-Based UI
The UI is even more distributed and aligned with backend services.

Good when:
- teams need high autonomy

Risks:
- UI consistency problems
- integration complexity
- composition and design-system governance issues

---

## Database Topology Variants

SBA supports a spectrum of database strategies:

### 1. Shared Database
Best for:
- simplicity
- reporting
- strong consistency
- lower duplication

Weakness:
- weakest data autonomy

### 2. Partially Separated Databases
Better domain isolation, but introduces:
- more duplication
- more integration complexity
- more explicit ownership rules

### 3. Database per Domain/Service
Closest to microservices-style ownership.

Strongest autonomy, but also introduces:
- consistency challenges
- duplication risk
- stronger need for clear data boundaries

The important lesson is that database design in SBA is not binary. It exists on a spectrum.

---

## Internal Service Design

A domain service in SBA can be designed internally in multiple ways.

### Technical Partitioning
Traditional layered structure:
- API facade layer
- business logic layer
- persistence layer

### Domain Partitioning
Internal organization by business/domain components instead of only technical layers.

Important takeaway:
a service is not only a deployment unit. It also has its own internal architecture.

---

## Internal Orchestration vs External Orchestration

In SBA, one coarse-grained service often handles a business transaction internally.

Example:
an OrderService might internally:
- create the order
- generate the order ID
- apply payment
- update inventory

In microservices, those responsibilities might be split across multiple remote services.

### SBA advantage
- simpler failure handling
- fewer remote calls
- easier transactions
- less orchestration complexity

### Trade-off
- broader responsibility inside one service
- larger testing scope for service changes

---

## ACID vs BASE

This is one of the biggest distinctions between SBA and microservices.

### In SBA
Business operations often stay within one coarse-grained service, so traditional **ACID transactions** are often possible.

This gives:
- stronger consistency
- easier rollback
- better database integrity

### In Microservices
Operations often span multiple services, so systems rely more on:
- eventual consistency
- BASE
- sagas
- compensation logic

### Important nuance
SBA can still require cross-service orchestration in some cases. When a transaction spans multiple domain services, saga-like coordination may still be needed. SBA reduces distributed transaction pain, but does not eliminate it completely.

---

## Database Partitioning

This is the main warning section of the chapter.

Even if services are domain-partitioned, a shared database can re-couple them.

### Worst practice
Using one shared entity library for all database tables and schema objects.

Why it is bad:
- one schema change can impact every service
- redeployment scope grows
- testing scope grows
- change analysis becomes harder
- service independence is weakened

This creates hidden coupling through shared implementation artifacts.

### Better approach
Use **logical database partitioning** aligned with business domains.

Example partitions:
- common
- customer
- invoicing
- order
- tracking

Then match these with corresponding shared libraries instead of one giant shared library.

### Goal
Do not eliminate all coupling. Instead, **control the blast radius of change**.

---

## The “Common” Domain Warning

A common domain or shared common library is often necessary, but it is risky.

If everything depends on `common`, then common becomes a hidden monolith.

Best practice:
- keep common small
- keep common stable
- govern common changes carefully

The chapter’s key rule is:

> Make the logical partitioning in the database as fine-grained as possible while still maintaining well-defined data domains.

---

## Example Architecture: Electronics Recycling System

The example system uses the following domain services:

- Quoting
- Receiving
- Assessment
- Accounting
- Item Status
- Recycling
- Reporting

This is a good SBA example because each service is a **coarse-grained business capability**, not a tiny technical function.

### Key lessons from the example
- only some services need scaling, such as Quoting and Item Status
- internal operational services may remain single-instance
- the UI can be federated by domain
- customer-facing and internal operations can be separated
- data can also be separated by operational/security zone

This demonstrates how SBA can support:
- scalability
- security zoning
- fault tolerance
- modular deployment
- focused change isolation

---

## Architecture Characteristics Ratings

### Strong areas
- Deployability: 4 stars
- Fault tolerance: 4 stars
- Modularity: 4 stars
- Overall cost: 4 stars
- Reliability: 4 stars
- Testability: 4 stars

### Medium areas
- Evolutionary: 3 stars
- Performance: 3 stars
- Scalability: 3 stars
- Simplicity: 3 stars

### Lower area
- Elasticity: 2 stars

### Interpretation
SBA is not the absolute best at any one quality attribute, but it performs well across many important business concerns. That balance is what makes it pragmatic.

---

## Why Elasticity Is Lower Than Scalability

SBA can scale, but coarse-grained services make scaling less precise.

When you scale one service, you also replicate functionality that may not be under pressure.

That makes SBA:

- reasonably scalable
- but less resource-efficient than finer-grained microservices

So:
- **Scalability** is moderate
- **Elasticity** is weaker

---

## Why Reliability and Fault Tolerance Are Strong

Because services are generally self-contained and use less interservice communication than microservices, SBA tends to have:

- fewer remote calls
- fewer distributed transactions
- less network chatter
- fewer service coordination failures

That usually improves reliability and fault tolerance compared with more fine-grained distributed architectures.

Important nuance:
the shared database can still remain a critical dependency.

---

## Architectural Quanta

SBA can have **one or many quanta** depending on how the UI and database are partitioned.

### Single quantum
If services share the same UI and database, the overall system may effectively be one quantum.

### Multiple quanta
If UI and database are federated into separate domains or security zones, multiple quanta can exist.

Example from the chapter:
- one quantum for customer-facing operations
- one quantum for internal operations

This shows that SBA can become more isolated and modular when partitioning includes not only services, but also UI and data.

---

## When to Use Service-Based Architecture

Use SBA when you want:

- a distributed architecture
- domain-based modularity
- better deployability than a monolith
- stronger transactional integrity than microservices usually provide
- lower cost and lower complexity than more advanced distributed styles
- less need for orchestration/choreography across many tiny services

### Strong fit conditions
SBA is a good choice when:
- business domains are clear
- services should be domain-scoped and independently deployed
- ACID still matters
- full microservices complexity is unnecessary
- shared data is acceptable if governed well
- moderate scalability is enough

---

## DDD Fit

SBA is a natural fit for **domain-driven design** because services are:

- domain-scoped
- coarse-grained
- aligned with business capability boundaries

It is not always as strict as microservices bounded contexts, but it is still strongly domain-oriented.

---

## When NOT to Use SBA

SBA is not the best choice when you need:

- strict database ownership per service
- very fine-grained scaling
- extreme service autonomy
- independent release cadence for many tiny capabilities
- strong isolation from shared schema coupling
- organization-wide readiness for microservice-level governance and operations

In those cases, microservices may be a better fit.

---

## Main Strengths

- pragmatic distributed architecture
- coarse-grained domain modularity
- good deployability
- good testability
- better ACID support than most distributed styles
- good fault tolerance and reliability
- lower cost and complexity than microservices

---

## Main Weaknesses

- weaker elasticity
- less precise scaling
- broader change and testing scope than microservices
- shared database can become a coupling hotspot
- shared/common data can undermine service independence
- hidden coupling can reappear through shared entity libraries

---

## Most Important Exam Distinction

Choose **Service-Based Architecture** when a scenario says:

- we want distributed services
- domains are clear
- services should be coarse-grained
- strong transactions still matter
- shared database is acceptable
- we want less complexity than microservices

Choose **Microservices** instead when a scenario says:

- every capability must be independently owned and deployed
- data ownership must be isolated per service
- fine-grained scaling matters a lot
- release independence matters a lot
- eventual consistency is acceptable
- the organization can handle high operational complexity

---

## Final Mental Model

Service-Based Architecture is:

- **distributed**
- **domain-partitioned**
- **coarse-grained**
- **transaction-friendly**
- **less complex than microservices**
- **more modular than a monolith**
- **pragmatic for business systems**

It is the middle ground between the simplicity of a monolith and the autonomy of microservices.
