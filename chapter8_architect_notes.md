# Fundamentals of Software Architecture --- Chapter 8

## Architect Thinking Reference & Applied Notes

This document expands the Chapter 8 concepts and applies them to a
**workflow orchestration platform** example.\
The goal is to capture **architectural reasoning**, not just
definitions.

------------------------------------------------------------------------

# 1. Core Idea of Chapter 8

Architecture design should **not begin with microservices or deployment
decisions**.

Instead the flow should be:

Requirements\
→ Component Discovery\
→ Architecture Characteristics\
→ Architecture Quanta\
→ Architecture Style

Architecture style **emerges from decomposition**.

------------------------------------------------------------------------

# 2. Component Discovery Methods

Chapter 8 introduces three main techniques.

  -----------------------------------------------------------------------
  Method                  Focus                   When Useful
  ----------------------- ----------------------- -----------------------
  Actor / Actions         Who interacts with the  General systems
                          system and what they do 

  Event Storming          What events occur in    Event‑driven
                          the system              architectures

  Workflow Discovery      End‑to‑end system       Process orchestration
                          processes               systems
  -----------------------------------------------------------------------

Good architects often **apply all three**.

------------------------------------------------------------------------

# 3. Actor / Actions Example (Workflow Platform)

Actors:

User\
System Scheduler\
Execution Engine\
Skill Runtime\
External Systems

Actions:

User - Create workflow - Edit workflow - Publish workflow version -
Start workflow execution - View execution results

Scheduler - Detect queued sessions - Claim execution session - Dispatch
execution

Execution Engine - Load workflow snapshot - Evaluate dependencies -
Execute nodes - Track session state

Skill Runtime - Execute skills - Produce outputs - Return artifacts

From this we discover components:

Workflow Definition Manager\
Workflow Execution Engine\
Workflow Scheduler\
Skill Runtime\
Artifact Manager\
Execution Monitoring

------------------------------------------------------------------------

# 4. Event Storming Example

Events represent things that **already happened**.

Examples:

WorkflowPublished\
WorkflowExecutionQueued\
WorkflowExecutionStarted\
NodeExecutionStarted\
NodeExecutionCompleted\
ArtifactProduced\
WorkflowExecutionCompleted

Event flow example:

WorkflowExecutionStarted\
→ NodeExecutionScheduled\
→ NodeExecutionStarted\
→ SkillExecutionCompleted\
→ ArtifactProduced\
→ NodeExecutionCompleted

Key architectural insight:

**NodeExecutionCompleted becomes the central event**.

It triggers:

-   dependency evaluation
-   scheduling of next nodes
-   artifact propagation

This reveals the importance of the **execution engine's dependency
resolver**.

------------------------------------------------------------------------

# 5. Workflow Discovery Example

Analyzing the lifecycle of workflow execution:

Design Phase - Create workflow - Edit workflow - Publish version

Execution Request - Start workflow run - Create execution session

Scheduling - Queue execution - Claim session - Dispatch execution

Runtime Execution - Execute nodes - Produce artifacts - Resolve
dependencies

Observability - View node states - View artifacts - Monitor execution

Components discovered:

Workflow Definition Manager\
Execution Session Manager\
Workflow Scheduler\
Workflow Execution Engine\
Skill Runtime\
Artifact Manager\
Execution Monitoring

------------------------------------------------------------------------

# 6. Avoiding the Entity Trap

Bad design example:

UserService\
WorkflowService\
ArtifactService

These mirror **database tables**.

Problems:

-   CRUD‑driven architecture
-   fragmented behavior
-   heavy service coupling

Correct approach:

Design around **behavior**.

Example:

Workflow Execution Engine\
Scheduler\
Skill Runtime\
Artifact System

Architecture should follow **system behavior**, not storage models.

------------------------------------------------------------------------

# 7. Architecture Characteristics

Non‑functional requirements influence boundaries.

Examples:

Performance\
Scalability\
Security\
Reliability\
Latency

Example separation:

Video Streaming → bandwidth optimized\
Payment Processing → security optimized

Different characteristics often require **separate components**.

------------------------------------------------------------------------

# 8. Architecture Quantum

Definition:

A deployable unit with:

-   high functional cohesion
-   synchronous connascence
-   shared architecture characteristics

Inside a quantum:

-   components evolve together

Across quanta:

-   asynchronous communication preferred

------------------------------------------------------------------------

# 9. Applying Architecture Quanta to Workflow Platform

Possible decomposition:

Quantum 1 -- Execution Platform

Scheduler\
Workflow Execution Engine\
Session State\
Node State

These share:

execution semantics\
state transitions\
ordering guarantees

------------------------------------------------------------------------

Quantum 2 -- Skill Runtime

Worker execution environment

Characteristics:

parallelism\
resource isolation

------------------------------------------------------------------------

Quantum 3 -- Artifact Storage

Handles:

logs\
large outputs\
file artifacts

Characteristics:

storage scalability\
retention policies

------------------------------------------------------------------------

Quantum 4 -- Workflow Design System

Workflow editor\
Workflow versioning\
Execution monitoring

Characteristics:

interactive UI\
configuration management

------------------------------------------------------------------------

# 10. Control Plane vs Execution Plane

Workflow platforms often separate responsibilities.

Control Plane:

workflow definitions\
session management\
scheduling

Execution Plane:

node execution\
skill runtime\
artifact production

This pattern appears in:

Temporal\
Airflow\
Argo\
Prefect

------------------------------------------------------------------------

# 11. Modular Monolith Strategy

Multiple architecture quanta **do not require microservices**.

A system may still be deployed as a single binary while maintaining
clear component boundaries.

Benefits:

simpler deployment\
faster iteration\
clean internal architecture

Later, components can be extracted into services if necessary.

------------------------------------------------------------------------

# 12. Mental Checklist for Architects

When designing a system ask:

What actors interact with the system?\
What actions do they perform?\
What events occur?\
What workflows exist?\
Which components share architecture characteristics?\
Which components must evolve together?

These answers reveal:

components → architecture quanta → architecture style.
