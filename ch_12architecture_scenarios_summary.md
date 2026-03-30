# Fundamentals of Software Architecture --- Scenario Exam Summary (with Challenges)

------------------------------------------------------------------------

## Scenario 1 --- Image Processing System

### Problem

Design a system to process uploaded images: - validation - virus scan -
resize - watermark - metadata extraction

Constraints: - high throughput - ordered steps - no branching - fault
isolation

### Architecture

-   Pipeline (Pipes and Filters) as core
-   Event-driven for ingestion and decoupling

### Key Insight

-   Sequential, ordered processing → pipeline fit
-   Event-driven is supporting, not dominant

### Trade-offs

-   Operational complexity
-   Data coupling between stages
-   Backpressure handling
-   Observability challenges

### Challenge / Critique

-   Misidentifying event-driven as primary architecture
-   Incorrect assumption that pipeline = synchronous
-   Missing pipes and filters terminology
-   Weak trade-off depth (no backpressure, schema coupling)

------------------------------------------------------------------------

## Scenario 2 --- Desktop IDE

### Problem

Design an extensible IDE: - lightweight core - plugins (languages,
linters, themes) - third-party extensions - optional hot-reload

### Architecture

-   Microkernel

### Key Insight

-   Core = stable editor system
-   Plugins = extensible features
-   Requires contracts + registry

### Trade-offs

-   Plugin quality control
-   Security risks (in-process vs out-of-process)
-   Performance overhead
-   Versioning and compatibility issues
-   Plugin dependency conflicts

### Challenge / Critique

-   Justification too shallow (missing contracts, registry)
-   Misuse of "scalability" in desktop context
-   Missing plugin lifecycle and dependency issues

------------------------------------------------------------------------

## Scenario 3 --- Real-time Log Processing Platform

### Problem

Design a log processing system: - parsing - enrichment - filtering -
routing - supports user-defined logic

Constraints: - high throughput - low latency - extensibility

### Architecture

-   Event-driven (ingestion & transport)
-   Pipeline (processing flow)
-   Microkernel (extensibility within stages)

### Key Insight

-   Event-driven = data movement
-   Pipeline = processing structure
-   Microkernel = extensibility inside stages

### Trade-offs

-   High operational complexity
-   Data contract coupling
-   Versioning challenges
-   Backpressure management
-   Observability complexity
-   Plugin isolation vs performance trade-offs

### Challenge / Critique

-   Lack of clear architectural boundaries
-   Microkernel incorrectly applied at system level (should be per
    stage)
-   Missing:
    -   backpressure strategy
    -   schema evolution issues
    -   observability depth
    -   plugin isolation decisions

------------------------------------------------------------------------

## Scenario 4 --- Workflow Orchestration System (Your System)

### Problem

Design a DAG-based workflow engine: - user-defined nodes - dynamic
workflows - retries and recovery - partial re-execution - high
concurrency

### Architecture

-   Workflow Orchestration (DAG engine) → core
-   Event-driven → communication layer
-   Microkernel → node execution (plugins)
-   Pipeline → optional, internal only (inside nodes)

### Key Insight

-   Pipeline is NOT suitable for DAG systems
-   DAG orchestrator controls execution and state
-   Microkernel applies at node level, not system-wide

### Trade-offs

-   Orchestrator bottleneck
-   Complex state management
-   Idempotency requirements
-   Observability challenges
-   Backpressure across workers
-   Plugin security risks
-   Data coupling between nodes
-   Dynamic workflow mutation complexity

### Challenge / Critique

-   Incorrect use of Pipeline as top-level architecture
-   Weak boundary definition
-   Missing:
    -   orchestrator scaling risks
    -   state consistency issues
    -   retry/idempotency implications
    -   execution ordering guarantees

------------------------------------------------------------------------

# Key Lessons

-   Do not force known architectures into problems
-   Always identify the **dominant architecture**
-   Clearly define **boundaries and responsibilities**
-   Trade-offs must be **system-specific and deep**
