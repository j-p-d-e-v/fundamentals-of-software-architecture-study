# Chapter 11 – Pipeline Architecture (Summary)

Pipeline architecture, also known as pipes and filters, is a design pattern where data flows through a sequence of independent processing units called filters. Each filter performs a specific operation and passes the result to the next filter via pipes.

This architecture is inherently unidirectional and emphasizes simplicity, composability, and separation of concerns. Filters are typically stateless and designed to perform a single task, making them easy to reuse and replace.

There are four main types of filters:
- Producers: generate initial data
- Transformers: modify data
- Testers: apply conditions and control flow
- Consumers: finalize output (e.g., storing data)

Pipeline architecture is widely used in systems like Unix shell commands, ETL processes, and stream processing platforms.

Despite its strengths in simplicity and modularity, pipeline architecture has notable limitations. It is typically implemented as a monolith, meaning it lacks independent scalability and fault isolation. If one component fails, it can affect the entire system.

Overall, pipeline architecture is best suited for linear, data-processing workflows where each step is clearly defined and independent.
