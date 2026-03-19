# Chapter 9 -- Cheatsheet

## Key Concepts

-   Architecture Style = system structure
-   Architecture Pattern = solution within style

## Architecture Types

### Monolithic

-   Single deployable unit
-   Low latency
-   Simple operations

### Distributed

-   Multiple services
-   Network communication
-   Complex operations

## Fallacies (Quick List)

-   Network is reliable ❌
-   Latency is zero ❌
-   Bandwidth is infinite ❌
-   Network is secure ❌
-   Topology never changes ❌
-   One administrator ❌
-   Transport cost is zero ❌
-   Network is homogeneous ❌

## Distributed Challenges

-   Distributed logging
-   Distributed transactions (eventual consistency)
-   API contract versioning

## When to Use Distributed

-   Need independent scaling
-   Need team autonomy
-   Need fault isolation

## When NOT to Use

-   Small team
-   Simple system
-   Low scale requirements

## Rule of Thumb

Start with: Monolith → Modular Monolith → Distributed (if needed)
