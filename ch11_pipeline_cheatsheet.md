# Chapter 11 – Pipeline Architecture (Cheat Sheet)

## Core Concept
Pipeline Architecture = Pipes + Filters

- Filters: processing units
- Pipes: data flow between filters
- Flow: unidirectional, sequential

## Key Properties
- Stateless (per filter)
- Data-driven flow
- Point-to-point communication
- Small payloads preferred

## Filter Types
1. Producer
   - Entry point
   - Outputs only

2. Transformer
   - Transforms data
   - Similar to map()

3. Tester
   - Conditional logic / branching
   - Similar to filter()

4. Consumer
   - End of pipeline
   - Persists or outputs data

## Strengths
- Simplicity ⭐⭐⭐⭐⭐
- Low Cost ⭐⭐⭐⭐⭐
- Modularity ⭐⭐⭐⭐

## Weaknesses
- Scalability ⭐
- Elasticity ⭐
- Fault Tolerance ⭐

## Architecture Notes
- Monolithic (1 quantum)
- No independent scaling
- Failure affects entire pipeline

## When to Use
- ETL pipelines
- Data processing flows
- Stream processing (simple transformations)

## When NOT to Use
- Complex workflows
- Distributed systems orchestration
- Stateful processes
