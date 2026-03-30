# Chapter 13 Review Scenarios - Service-Based Architecture

Use these scenarios to practice identifying the dominant architecture, boundaries, and trade-offs.

---

## Scenario 1 - Order Management Platform

A retail company wants separate domain teams for Orders, Billing, Inventory, and Customer Support. Each domain should be deployable independently, but the company still wants strong transactional consistency for most workflows and centralized reporting using SQL joins across domains. Leadership explicitly wants to avoid the operational overhead of microservices.

### Practice prompts
1. What is the dominant architecture?
2. Why is it a better fit than microservices?
3. What database approach best matches this scenario?
4. What is the main trade-off?

---

## Scenario 2 - Shared Entity Library Debate

A team designs a service-based system with separate domain services. To avoid duplication, they create one shared entities library that contains every database table mapping, common SQL queries, and all shared persistence models. Every service depends on this library.

### Practice prompts
1. What architectural problem does this introduce?
2. Why does this weaken service boundaries?
3. What better approach would you recommend?

---

## Scenario 3 - ACID or Eventual Consistency

A business workflow includes creating an order, reserving stock, charging payment, and producing an invoice. The architects want the system to remain distributed but also want most of this flow to either fully succeed or fully roll back together.

### Practice prompts
1. Which style fits better: SBA or microservices?
2. Why does the transaction requirement matter?
3. Where should orchestration ideally happen?

---

## Scenario 4 - Scaling Hotspots

An electronics recycling platform has services for Quoting, Receiving, Assessment, Recycling, Accounting, and Reporting. Only Quoting and Item Status receive heavy public traffic. The internal operational services have low traffic and stable load.

### Practice prompts
1. Why is SBA a strong fit here?
2. Which services would you scale first?
3. Why is this still different from microservices?

---

## Scenario 5 - Common Domain Risk

A distributed business platform uses logical data partitions for customer, orders, tracking, and billing, but all services also depend on a large `common` schema that contains shared reference data, shared identity structures, and utility entities used almost everywhere.

### Practice prompts
1. What risk is forming here?
2. Why can `common` become a hidden monolith?
3. How would you control this risk?

---

## Scenario 6 - UI Partitioning

A company currently has a single web UI calling several backend domain services. Over time, teams want the customer-facing portal, internal finance tools, and warehouse tools to evolve separately because they have different release cadence, security requirements, and users.

### Practice prompts
1. What UI evolution path makes sense?
2. Does this still fit SBA?
3. How can frontend partitioning affect architectural quanta?

---

## Scenario 7 - One Quantum vs Many

A system has separate domain services but all of them still use one frontend and one database. Later, the company separates customer-facing capabilities into their own frontend, own services, and own database, while keeping internal operations in a different stack.

### Practice prompts
1. Why is the first version effectively one quantum?
2. Why does the second version create multiple quanta?
3. What architectural isolation improves?

---

## Scenario 8 - When SBA Is the Wrong Answer

A digital platform wants every small capability released independently by separate teams. Each service must own its own database. Very fine-grained scaling is required because traffic patterns differ significantly across capabilities. The company accepts eventual consistency and is prepared for high operational complexity.

### Practice prompts
1. Should you choose SBA?
2. Which architecture fits better?
3. Which exact requirements disqualify SBA?

---

## Scenario 9 - Boundary Drift

An architect says: “We will use Service-Based Architecture because each business domain is a separate service.” However, the services call each other frequently for small operations, most workflows cross multiple services, and the database is also being split aggressively per service.

### Practice prompts
1. Why is this reasoning incomplete?
2. Is the system still behaving like classic SBA?
3. What signs show it is drifting toward microservices?

---

## Scenario 10 - Reporting Pressure

A business wants strong centralized reporting across customer, billing, and order domains. They also want domain-based deployment separation, but they do not want to build complex event pipelines just to keep reporting views synchronized across many isolated databases.

### Practice prompts
1. Why does this point toward SBA?
2. What data model choice becomes attractive?
3. What trade-off must still be governed carefully?

---

## Scenario 11 - Hidden Coupling Through Change

A team claims their architecture is modular because services are separately deployed. However, every schema change requires three or four service teams to coordinate because they all depend on shared tables and shared persistence objects.

### Practice prompts
1. What does this reveal about the real architecture?
2. Why is deployment independence not the full story?
3. What Chapter 13 lesson does this scenario illustrate?

---

## Scenario 12 - Exam-Style Mixed Choice

A company wants:
- domain-based decomposition
- separate deployment per large business capability
- strong transactional integrity for order-related flows
- moderate scalability
- lower cost than microservices
- simpler operational support model
- some shared data/reporting convenience

### Practice prompts
1. What is the dominant architecture?
2. What are the two strongest reasons for your answer?
3. What is the biggest architectural risk?
4. What wrong alternative might look attractive, and why is it less appropriate?

---

## Fast Self-Check Template

For every scenario, answer using this structure:

1. **Dominant architecture**
2. **Why it fits**
3. **Main boundary**
4. **Main trade-off**
5. **Closest wrong alternative and why it is wrong**

---

## Quick Answer Key Themes

You should repeatedly recognize these Chapter 13 patterns:

### SBA indicators
- coarse-grained domain services
- independent deployment
- strong transactional needs
- shared or partially shared database
- lower complexity than microservices
- centralized reporting still matters

### Microservices indicators
- fine-grained services
- strict database ownership
- independent release of tiny capabilities
- very fine-grained scaling
- eventual consistency is acceptable
- high operational maturity is expected

### Main SBA danger
- hidden coupling through shared database structures and shared libraries

### Main SBA mitigation
- logical database partitioning aligned to domains
- small and stable common area
- controlled blast radius of change
