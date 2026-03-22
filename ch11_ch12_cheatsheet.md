# 📦 Fundamentals of Software Architecture — Cheatsheet (Ch 11 + Ch 12)

---

# 🧠 Chapter 11 — Pipeline Architecture

## Core Idea
Pipeline = Pipes + Filters  
Data flows sequentially and unidirectionally.

## Structure
Producer → Transformer → Tester → Consumer

## Characteristics

### Strengths
- Simplicity ⭐⭐⭐⭐⭐
- Low cost ⭐⭐⭐⭐⭐
- Modularity ⭐⭐⭐⭐

### Weaknesses
- Scalability ⭐
- Elasticity ⭐
- Fault tolerance ⭐

## When to Use
- ETL processing
- Log processing
- Stream transformations
- Linear workflows

## Key Insight
Pipeline = **fixed, linear flow**

---

# 🧠 Chapter 12 — Microkernel Architecture

## Core Idea
Microkernel = Core System + Plug-ins

- Core = minimal, stable logic
- Plugins = extensible, variable logic

## Components

### Core System
- Orchestration
- Routing
- Plugin resolution
- Minimal “happy path”

### Plug-ins
- Independent
- Self-contained
- Volatile (change frequently)

## Communication Models

### 1. In-process (Default)
Core → Plugin (direct call)

### 2. Remote (Advanced)
Core → Plugin (REST / Messaging)

⚠️ Still logically monolithic

## Registry
- Maps plugin → implementation
- Can be:
  - simple (map)
  - advanced (service discovery)

## Contracts
Defines:
- Input
- Output
- Behavior

Rule:
Core must NOT know plugin internals

## Data Ownership

❌ Bad: Plugin → Shared DB  
✅ Good: Plugin → Core → DB  
✅ Advanced: Plugin owns its own DB

---

# ⚔️ Pipeline vs Microkernel

| Aspect | Pipeline | Microkernel |
|--------|--------|------------|
| Flow | Linear | Dynamic |
| Control | Fixed | Context-based |
| Extensibility | Low | High |
| Use case | Data processing | Product platforms |

---

# 🧠 Combined Mental Model

Pipeline = **flow control**  
Microkernel = **extensibility mechanism**

---

# 🧩 Applying to Workflow Systems

## Correct Architecture

- Top-level → Workflow (DAG)
- Execution → Microkernel
- Node logic → Pipeline (optional)

## Structure

API → Orchestrator → Execution Engine → Plugins

---

# ⚠️ Key Risks

1. Core bottleneck
2. Fault propagation
3. Plugin isolation issues
4. Contract/versioning drift

---

# 🔥 Key Takeaways

- Do NOT use pipeline for DAG systems
- Microkernel is NOT for scalability
- Combine architectures based on responsibility
- Separate:
  - Control plane (orchestrator)
  - Execution plane (plugins/workers)

---

# 🚀 Final Insight

Most real systems are:

Workflow (DAG) + Microkernel + Event-driven

NOT a single architecture.

