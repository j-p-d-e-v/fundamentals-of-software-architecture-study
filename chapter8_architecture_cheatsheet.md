# Fundamentals of Software Architecture --- Chapter 8 Cheat Sheet

## Component-Based Thinking & Component Discovery

------------------------------------------------------------------------

# 1. Goal of the Chapter

Chapter 8 explains **how architects discover system components** before
deciding architecture style (monolith vs distributed).

Key idea:

Architecture should be **behavior-driven**, not **database-driven**.

------------------------------------------------------------------------

# 2. Component Discovery Process

Architects iterate through a cycle:

1.  Identify initial components
2.  Assign requirements to components
3.  Analyze roles and responsibilities
4.  Evaluate architecture characteristics
5.  Refine components
6.  Repeat

Architecture discovery is **iterative**, not a one-time design.

------------------------------------------------------------------------

# 3. Component Granularity

Architects must balance between:

### Too Fine-Grained

Example:

UserValidator\
UserFormatter\
UserMapper

Problems:

-   excessive dependencies
-   communication overhead
-   hard to reason about

### Too Coarse-Grained

Example:

ApplicationService

Problems:

-   huge modules
-   high internal coupling
-   difficult testing

Goal: **balanced component boundaries**.

------------------------------------------------------------------------

# 4. The Entity Trap

A common architectural anti-pattern.

Designing components based on **database entities**.

Example:

AuctionManager\
ItemManager\
BidManager

This leads to:

-   CRUD-style systems
-   fragmented business workflows
-   tight coupling between services

Correct approach:

Design components around **behavior and workflows**, not tables.

Example:

Bid Processing\
Payment Handling\
Bid Streaming

------------------------------------------------------------------------

# 5. Three Component Discovery Techniques

### 1. Actor / Actions

Identify system users and what they do.

Example actors:

Bidder\
Auctioneer\
System

Example actions:

View bids\
Place bid\
Process payment

Components emerge from actions.

------------------------------------------------------------------------

### 2. Event Storming

Identify **domain events**.

Example events:

WorkflowPublished\
NodeExecutionCompleted\
ArtifactProduced

Events reveal:

-   system behavior
-   hidden components
-   orchestration logic

------------------------------------------------------------------------

### 3. Workflow-Based Discovery

Analyze **end-to-end workflows**.

Example workflow lifecycle:

Create workflow\
Publish version\
Start execution\
Run nodes\
Produce artifacts

Each stage suggests a component.

------------------------------------------------------------------------

# 6. Architecture Characteristics Influence Components

Architecture characteristics (non-functional requirements) affect
boundaries.

Examples:

Performance\
Scalability\
Security\
Reliability\
Throughput

If two components require **different characteristics**, they should
likely be **separate components**.

Example:

Video streaming → bandwidth optimized\
Payment processing → security optimized

------------------------------------------------------------------------

# 7. Architecture Quantum

Definition:

An **architecture quantum** is a deployable unit with:

-   high functional cohesion
-   synchronous connascence
-   shared architecture characteristics

Inside a quantum:

-   components evolve together

Across quanta:

-   loose coupling
-   asynchronous communication preferred

------------------------------------------------------------------------

# 8. Architecture Style Emerges from Quanta

Architects do **not start with microservices vs monolith**.

Instead:

Requirements → Component Discovery → Architecture Characteristics →
Architecture Quanta → Architecture Style

### One Quantum

Monolithic architecture

### Multiple Quanta

Distributed architecture

------------------------------------------------------------------------

# 9. Key Lessons

1.  Architecture should be **behavior-driven**, not data-driven.
2.  Component discovery is **iterative**.
3.  Avoid the **entity trap**.
4.  Architecture characteristics shape component boundaries.
5.  Architecture quanta determine whether the system becomes monolithic
    or distributed.
6.  Start with **clear component responsibilities**, then decide
    deployment style.

------------------------------------------------------------------------

# 10. Practical Mental Model

When designing a system, ask:

What behaviors exist?\
What events occur?\
What workflows happen?\
What architecture characteristics apply?\
Which parts must evolve together?

Those answers reveal:

**components → architecture quanta → system architecture**.
