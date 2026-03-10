# Software Architecture "-ilities" Cheat Sheet

A quick reference for common **architecture characteristics** used when translating business requirements into architectural qualities.

---

## Scalability
Ability of the system to handle increasing load.

Examples:
- Traffic spikes (Black Friday)
- Growing number of users
- Increasing data volume

Typical solutions:
- Horizontal scaling
- Load balancers
- Distributed systems

---

## Performance
How fast the system responds.

Examples:
- Low latency
- High throughput
- Fast response times

Typical solutions:
- Caching
- CDN
- Query optimization
- Asynchronous processing

---

## Availability
How often the system is operational.

Examples:
- 24/7 uptime
- Minimal downtime

Typical solutions:
- Redundant servers
- Failover mechanisms
- Health monitoring

---

## Reliability
System consistently performs correctly.

Examples:
- Transactions processed correctly
- No data corruption

Typical solutions:
- Transaction management
- Reliable messaging
- Validation

---

## Fault Tolerance
System continues operating even when components fail.

Examples:
- Service crash does not stop the system
- Network failure handled gracefully

Typical solutions:
- Retry logic
- Circuit breakers
- Service redundancy

---

## Recoverability
Ability to recover after failures.

Examples:
- Restart unfinished processes
- Restore system state after crash

Typical solutions:
- Checkpoints
- Event logs
- Transaction recovery

---

## Security
Protection of system and data.

Examples:
- Encryption
- Authentication
- Authorization

Typical solutions:
- TLS
- Identity management
- Secure API gateways

---

## Auditability
Ability to trace system activity.

Examples:
- Transaction logs
- Compliance tracking

Typical solutions:
- Immutable logs
- Monitoring systems
- Event sourcing

---

## Maintainability
Ease of modifying the system.

Examples:
- Fixing bugs
- Updating features

Typical solutions:
- Modular architecture
- Clean code practices
- Documentation

---

## Extensibility
Ease of adding new features.

Examples:
- Adding payment methods
- Supporting new integrations

Typical solutions:
- Plugin architecture
- Modular services
- APIs

---

## Testability
Ease of testing the system.

Examples:
- Automated tests
- Component isolation

Typical solutions:
- Dependency injection
- Modular design

---

## Deployability
Ease of releasing new versions.

Examples:
- Frequent deployments
- Continuous delivery

Typical solutions:
- CI/CD pipelines
- Containers
- Automated deployments

---

## Interoperability
Ability to integrate with other systems.

Examples:
- Third-party APIs
- Partner systems

Typical solutions:
- Standard protocols
- API gateways
- Messaging systems

---

## Usability
Ease of use for users.

Examples:
- Clear UI
- Simple workflows

Typical solutions:
- UX design
- Accessibility support

---

## Portability
Ability to run in different environments.

Examples:
- Cloud providers
- Different operating systems

Typical solutions:
- Containers
- Platform abstraction
