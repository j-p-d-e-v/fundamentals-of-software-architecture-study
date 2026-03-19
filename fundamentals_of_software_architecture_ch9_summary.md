# Chapter 9 -- Foundations (Summary)

## Architecture Styles

Architecture styles define the overall structure of a system, including
how components interact and are deployed.

## Style vs Pattern

-   Style: high-level structure
-   Pattern: lower-level solution within a style

## Historical Evolution

Unitary → Client/Server → Three-tier → Modern architectures

## Big Ball of Mud

An anti-pattern characterized by: - high coupling - low cohesion - lack
of structure

## Monolithic vs Distributed

### Monolithic

-   Single deployment unit
-   Fast communication
-   Easier debugging

### Distributed

-   Multiple deployment units
-   Network-based communication
-   Higher complexity

## Fallacies of Distributed Computing

1.  Network is reliable
2.  Latency is zero
3.  Bandwidth is infinite
4.  Network is secure
5.  Topology never changes
6.  Only one administrator
7.  Transport cost is zero
8.  Network is homogeneous

## Key Trade-offs

Distributed systems improve: - scalability - deployability - fault
isolation

But introduce: - latency - complexity - observability challenges

## Key Insight

Do not distribute systems unless required by architecture
characteristics.
