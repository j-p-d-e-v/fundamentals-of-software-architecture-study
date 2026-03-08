# Fundamentals of Software Architecture --- Chapter 3 Summary

## Modularity

## 1. What is Modularity

Modularity refers to organizing a system into logical units (modules)
that group related functionality together.

A module can be: - a package - a namespace - a class group - a service -
a component

Goal of modularity: - make systems easier to understand - isolate
responsibilities - reduce unintended dependencies

Key principle:

High cohesion inside modules\
Low coupling between modules

------------------------------------------------------------------------

## 2. Cohesion

Cohesion measures how strongly related the responsibilities inside a
module are.

A highly cohesive module contains functions that all contribute to a
single purpose.

Example (High Cohesion):

OrderService - createOrder() - cancelOrder() - getOrder()

Example (Low Cohesion):

UtilityService - sendEmail() - calculateTax() - parseCSV()

Low cohesion leads to: - "God classes" - utility dumping grounds -
difficult maintenance

------------------------------------------------------------------------

## 3. Types of Cohesion (Best → Worst)

Functional Cohesion\
All functions contribute to one responsibility.

Sequential Cohesion\
Output of one function becomes input of another.

Communicational Cohesion\
Operations work on the same data.

Procedural Cohesion\
Functions must run in a specific sequence.

Temporal Cohesion\
Grouped because they run at the same time (e.g., startup tasks).

Logical Cohesion\
Grouped by type of activity but not strongly related.

Coincidental Cohesion (Worst)\
Unrelated functionality placed together.

------------------------------------------------------------------------

## 4. LCOM (Lack of Cohesion of Methods)

LCOM is a metric used to evaluate cohesion inside classes.

Idea: Methods should operate on shared data fields.

Low LCOM = good cohesion\
High LCOM = class likely has multiple responsibilities

LCOM helps detect: - God classes - misplaced responsibilities

However, metrics should be interpreted with architectural judgment.

------------------------------------------------------------------------

## 5. Coupling

Coupling measures how strongly modules depend on each other.

Two common metrics:

### Afferent Coupling (Ca)

Number of modules that depend on a module.

High Ca → module is important and stable.

### Efferent Coupling (Ce)

Number of modules a module depends on.

High Ce → module is fragile and easily affected by changes.

Goal: Minimize unnecessary coupling between modules.

------------------------------------------------------------------------

## 6. Instability

Instability measures how likely a module is to change.

Formula:

I = Ce / (Ce + Ca)

Range: 0 → stable module\
1 → unstable module

Stable modules should change rarely.\
Unstable modules are allowed to evolve more frequently.

------------------------------------------------------------------------

## 7. Abstractness

Abstractness measures how many abstractions exist in a module.

Formula:

A = number of abstract classes / total classes

Range: 0 → completely concrete\
1 → completely abstract

Stable modules should tend toward higher abstraction.

------------------------------------------------------------------------

## 8. The Main Sequence

Architectural balance occurs when abstractness and instability align.

Healthy modules fall near the **main sequence line**.

Two problematic zones exist:

Zone of Pain: - low abstractness - low instability - stable but hard to
modify

Zone of Uselessness: - high abstractness - high instability -
abstractions that nobody depends on

------------------------------------------------------------------------

## 9. Connascence

Connascence describes how components must change together.

Definition:

Two components are connascent if changing one requires changing the
other to maintain correctness.

Connascence explains the **nature of coupling**.

------------------------------------------------------------------------

## 10. Types of Connascence

### Static Connascence (compile-time)

Connascence of Name\
Modules must agree on a name.

Connascence of Type\
Modules must agree on types.

Connascence of Meaning\
Modules must agree on value interpretation.

Connascence of Position\
Order of parameters matters.

Connascence of Algorithm\
Multiple modules implement the same algorithm.

------------------------------------------------------------------------

### Dynamic Connascence (runtime)

Connascence of Execution\
Operations must execute in a specific order.

Connascence of Timing\
Timing relationships must hold.

Connascence of Value\
Shared values must change together.

Connascence of Identity\
Components reference the same entity.

Dynamic connascence is stronger and more dangerous.

------------------------------------------------------------------------

## 11. Connascence Design Rules

1.  Minimize overall connascence.

2.  Minimize connascence across module boundaries.

3.  Maximize connascence inside modules.

Architectural guideline:

Use strong connascence inside modules.\
Use weak connascence between modules.

------------------------------------------------------------------------

## 12. Architectural Implication

Good modular architecture results in:

-   cohesive modules
-   weak inter-module dependencies
-   stable system evolution

Architectural boundaries should expose only weak dependencies such as:

-   API contracts
-   message schemas
-   shared type definitions

Avoid strong cross-boundary dependencies such as:

-   shared database tables
-   shared algorithms
-   strict execution ordering

------------------------------------------------------------------------

## Key Takeaways

-   Modularity organizes systems into logical units.
-   High cohesion improves clarity and maintainability.
-   Low coupling reduces ripple effects when systems change.
-   Connascence explains how components must change together.
-   Strong dependencies should remain inside modules, while boundaries
    should expose only weak dependencies.
