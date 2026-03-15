# Fundamentals of Software Architecture --- Chapter 8 Summary

## Component-Based Thinking

Chapter 8 focuses on **how architects discover system components**
before deciding the architecture style of a system.

The key message of the chapter:

> Architecture should be **behavior-driven**, not **data-driven**.

Architects must understand system responsibilities and behaviors before
deciding whether the system becomes a monolith or distributed
architecture.

------------------------------------------------------------------------

# 1. Component Discovery Process

Architects usually follow an **iterative discovery process**:

1.  Identify initial components
2.  Assign requirements to those components
3.  Analyze roles and responsibilities
4.  Evaluate architecture characteristics
5.  Refine component boundaries
6.  Repeat the process

Architecture discovery is **not linear**. It evolves through refinement.

------------------------------------------------------------------------

# 2. Component Granularity

Architects must avoid two extremes.

### Too Fine-Grained

Example:

UserValidator\
UserFormatter\
UserMapper

Problems:

-   excessive communication
-   too many dependencies
-   difficult reasoning

### Too Coarse-Grained

Example:

ApplicationService

Problems:

-   huge modules
-   high coupling
-   difficult testing and maintenance

Goal: **balanced component boundaries**.

------------------------------------------------------------------------

# 3. The Entity Trap

A common mistake when designing architecture is the **entity trap**.

This happens when architects design components around **database tables
or ORM entities**.

Example:

AuctionManager\
ItemManager\
BidManager

This leads to:

-   CRUD-oriented services
-   scattered business logic
-   tightly coupled components

Correct approach:

Components should represent **system behavior and responsibilities**,
not storage structures.

Example:

Bid Processing\
Payment Handling\
Bid Streaming

------------------------------------------------------------------------

# 4. Three Component Discovery Techniques

The chapter introduces three ways to discover components.

## 1. Actor / Actions

Identify:

-   who interacts with the system
-   what actions they perform

Actors in the auction example:

Bidder\
Auctioneer\
System

Actions:

View bids\
Place bid\
Process payment

Components are derived from these behaviors.

------------------------------------------------------------------------

## 2. Event Storming

Focus on **events that occur in the system**.

Examples:

BidPlaced\
AuctionStarted\
PaymentCompleted

Events help reveal:

-   system behavior
-   orchestration patterns
-   hidden components

------------------------------------------------------------------------

## 3. Workflow-Based Discovery

Analyze **end-to-end workflows**.

Example workflow:

Start auction\
Receive bids\
Process payments\
Close auction

Each step in the workflow suggests possible components.

------------------------------------------------------------------------

# 5. Architecture Characteristics Influence Components

Architecture characteristics are **non-functional requirements** that
shape system boundaries.

Examples:

Performance\
Scalability\
Security\
Reliability\
Latency

If two parts of the system require **different architecture
characteristics**, they may need separate components.

Example:

Video streaming → optimized for bandwidth\
Payment processing → optimized for security

------------------------------------------------------------------------

# 6. Architecture Quantum

An **architecture quantum** is defined as:

A deployable unit with:

-   high functional cohesion
-   synchronous connascence
-   shared architecture characteristics

Inside a quantum:

Components evolve together.

Across quanta:

Communication should be loosely coupled and often asynchronous.

------------------------------------------------------------------------

# 7. Architecture Style Emerges from Quanta

Architects do **not start by choosing microservices or monoliths**.

Instead:

Requirements\
→ Component Discovery\
→ Architecture Characteristics\
→ Architecture Quanta\
→ Architecture Style

If the architecture results in:

One quantum → Monolithic architecture

Multiple quanta → Distributed architecture

------------------------------------------------------------------------

# 8. Key Lessons

1.  Architecture should be **behavior-driven**, not data-driven.
2.  Component discovery is **iterative**.
3.  Avoid the **entity trap**.
4.  Architecture characteristics influence component boundaries.
5.  Architecture quanta determine the final architecture style.
6.  Discover components first before deciding deployment structure.

------------------------------------------------------------------------

# 9. Mental Model for Architects

When designing a system, ask:

What actors interact with the system?\
What actions do they perform?\
What events occur in the system?\
What workflows exist?\
Which architecture characteristics apply?\
Which components must evolve together?

Answering these questions reveals:

**components → architecture quanta → architecture style**
