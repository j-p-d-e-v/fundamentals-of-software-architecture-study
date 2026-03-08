# Fundamentals of Software Architecture --- Chapter 3 Cheat Sheet

## Modularity (Architect's Practical Guide)

This cheat sheet focuses on the most practical ideas architects use from
Chapter 3.

------------------------------------------------------------------------

# 1. Core Principle

Good architecture follows this rule:

High cohesion inside modules\
Low coupling between modules

Meaning: - Modules should contain related responsibilities - Modules
should have minimal dependencies on other modules

------------------------------------------------------------------------

# 2. Cohesion

Cohesion answers:

Do the responsibilities inside this module belong together?

High Cohesion Example

OrderService - createOrder() - cancelOrder() - getOrder()

Low Cohesion Example

UtilityService - sendEmail() - calculateTax() - parseCSV()

Rule: Modules should represent clear business responsibilities.

------------------------------------------------------------------------

# 3. Coupling

Coupling measures how much modules depend on each other.

Ask:

If I change this module, how many other modules break?

Lower coupling means: - easier refactoring - easier testing - safer
deployments

------------------------------------------------------------------------

# 4. Types of Dependencies (Connascence)

Connascence explains how modules depend on each other.

From weakest (good) to strongest (bad):

Name Type Meaning Position Algorithm Execution Timing Value Identity

Rule:

Move dependencies toward the top of the list.

------------------------------------------------------------------------

# 5. Good Dependencies Across Modules

Architectural boundaries should prefer: - API contracts - event
schemas - shared type definitions - message formats

These create: Connascence of name or type (weak dependencies)

------------------------------------------------------------------------

# 6. Dangerous Dependencies Across Modules

Avoid strong cross-module dependencies such as: - shared algorithms -
strict execution ordering - shared database tables - timing assumptions

These create fragile systems.

------------------------------------------------------------------------

# 7. Three Design Rules

1.  Minimize overall connascence.
2.  Minimize connascence across module boundaries.
3.  Maximize connascence inside modules.

Meaning: - tightly related logic stays together - modules communicate
through simple contracts

------------------------------------------------------------------------

# 8. Healthy Modular Architecture

Inside module: - strong cohesion - strong internal relationships

Across modules: - weak dependencies - clear interfaces

------------------------------------------------------------------------

# 9. Practical Architect Questions

When designing systems ask:

1.  Does this responsibility belong in this module?
2.  How many modules will break if this changes?
3.  What type of dependency exists between them?

------------------------------------------------------------------------

# 10. One-Sentence Summary

A well-designed system has focused modules with minimal and weak
dependencies between them.
