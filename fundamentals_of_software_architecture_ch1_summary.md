# Fundamentals of Software Architecture --- Chapter 1 Summary

## 1. What Software Architecture Is

Software architecture is composed of four key elements:

-   **Structure** --- How the system is organized (modules, layers,
    services, components).
-   **Architecture Characteristics** --- The quality attributes of the
    system such as scalability, performance, security, reliability, and
    deployability.
-   **Architecture Decisions** --- The important rules and constraints
    that guide how the system must be built.
-   **Design Principles** --- Guidelines developers follow when
    implementing the system (e.g., SOLID, loose coupling, separation of
    concerns).

In simple form:

    Architecture = Structure + Characteristics + Decisions + Principles

------------------------------------------------------------------------

## 2. The Role of a Software Architect

Architects are responsible for:

-   Making architectural decisions
-   Guiding technology choices
-   Ensuring architecture compliance
-   Continually analyzing system health
-   Understanding both technology and business needs

Architecture is not only technical; it also involves:

-   leadership
-   communication
-   negotiation
-   organizational awareness

------------------------------------------------------------------------

## 3. Architecture Is Influenced by People and Organizations

Architectural decisions often affect multiple teams. Because of this,
architects must:

-   communicate clearly
-   justify decisions
-   align stakeholders
-   balance business needs and technical constraints

Good architecture succeeds when teams **understand and support it**.

------------------------------------------------------------------------

## 4. Architecture Must Evolve

Software systems contain:

-   **Known knowns** -- things we understand
-   **Known unknowns** -- things we know we must investigate
-   **Unknown unknowns** -- surprises that appear later

Because of this uncertainty, architecture must be **iterative and
adaptable**, not designed perfectly upfront.

This is why modern systems evolve gradually rather than relying on **Big
Design Up Front (BDUF)**.

------------------------------------------------------------------------

## 5. Architecture Erosion

Over time, architecture can degrade if rules are not enforced.

Example violation:

    Presentation → Database

Instead of the intended flow:

    Presentation → Business → Persistence → Database

This gradual breakdown is called **architecture erosion** or
**structural decay**.

To prevent this, teams use **architecture fitness functions**.

------------------------------------------------------------------------

## 6. Architecture Fitness Functions

A fitness function is an automated check that ensures architecture rules
are respected.

Example:

-   Preventing the presentation layer from accessing the database
-   Verifying service dependencies
-   Enforcing architectural boundaries

These checks usually run automatically in **CI pipelines**.

Architecture therefore becomes **continuously validated**, not just
documented.

------------------------------------------------------------------------

## 7. Engineering Practices vs Development Process

The book distinguishes two ideas:

### Development Process

How work is organized.

Examples:

-   Scrum
-   Kanban
-   Waterfall

### Engineering Practices

Technical techniques that improve software quality.

Examples:

-   automated testing
-   continuous integration
-   refactoring
-   deployment automation

Architecture depends more on **engineering practices** than on process
frameworks.

------------------------------------------------------------------------

## 8. Data Is an Architectural Concern

Architecture is not only about services and code.

Data also plays a major role:

-   data ownership
-   data access patterns
-   database scaling
-   consistency models

Code and data have a **symbiotic relationship** --- both must be
designed together.

------------------------------------------------------------------------

# The Two Laws of Software Architecture

## First Law

> Everything in software architecture is a trade-off.

Every architectural decision improves some qualities while making others
worse.

Example:

Microservices improve: - scalability - independent deployments

But introduce: - distributed complexity - operational overhead - network
failures

Good architects constantly evaluate **trade-offs**.

------------------------------------------------------------------------

## Second Law

> Why is more important than how.

Understanding *why* an architecture exists is critical.

Before changing a system, architects must understand:

-   the business context
-   historical decisions
-   system constraints
-   team structure
-   operational requirements

Without understanding the **reason behind decisions**, it is impossible
to evaluate architecture correctly.

------------------------------------------------------------------------

# Key Mental Model for Architecture

Good architects always think in terms of:

-   **tradeoffs**
-   **constraints**
-   **system evolution**
-   **organizational impact**
-   **business outcomes**

Architecture is not just about designing systems.

It is about **making informed decisions under uncertainty**.
