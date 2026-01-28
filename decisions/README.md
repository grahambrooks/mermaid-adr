# Architecture Decision Records

This directory contains Architecture Decision Records (ADRs) that document important architectural decisions made for our e-commerce platform.

## What is an ADR?

An Architecture Decision Record (ADR) is a document that captures an important architectural decision made along with its context and consequences. Each ADR describes:

- **Status**: The current state of the decision (Accepted, Proposed, Deprecated, Superseded)
- **Context**: The issue or problem motivating the decision
- **Decision**: The architectural decision and its rationale
- **Consequences**: The resulting context after applying the decision, including positive and negative impacts

## ADR List

| ADR | Title | Diagrams |
|-----|-------|----------|
| [0001](0001-adopt-microservices-architecture.md) | Adopt Microservices Architecture | C4 Context |
| [0002](0002-api-gateway-pattern.md) | API Gateway Pattern for Microservices | C4 Container |
| [0003](0003-event-driven-order-processing.md) | Event-Driven Order Processing | Sequence Diagram |
| [0004](0004-circuit-breaker-pattern.md) | Circuit Breaker Pattern for Service Resilience | Flowchart |
| [0005](0005-database-per-service.md) | Database per Service Pattern | Entity Relationship Diagram |
| [0006](0006-cqrs-pattern-product-catalog.md) | CQRS Pattern for Product Catalog | C4 Component |
| [0007](0007-order-state-machine.md) | Order State Machine for Order Lifecycle Management | State Diagram |

## Mermaid.js Diagrams

All ADRs in this directory include [Mermaid.js](https://mermaid.js.org/) diagrams to visualize the architectural decisions. The diagrams include:

### C4 Diagrams

C4 (Context, Containers, Components, and Code) is a set of hierarchical diagrams for visualizing software architecture:

- **C4 Context** (ADR-0001): Shows the system in its environment with users and external systems
- **C4 Container** (ADR-0002): Shows the high-level technology choices and how containers communicate
- **C4 Component** (ADR-0006): Shows the components within a container and their interactions

### Behavioral Diagrams

- **Sequence Diagram** (ADR-0003): Shows how processes operate with one another and in what order
- **State Diagram** (ADR-0007): Shows the different states an entity can be in and the transitions between them
- **Flowchart** (ADR-0004): Shows the step-by-step flow of a process or algorithm

### Structural Diagrams

- **Entity Relationship Diagram** (ADR-0005): Shows the data model and relationships between entities

## Viewing the Diagrams

The Mermaid diagrams can be rendered in several ways:

1. **GitHub**: GitHub automatically renders Mermaid diagrams in markdown files
2. **Mermaid Live Editor**: Copy the diagram code to [https://mermaid.live](https://mermaid.live)
3. **VS Code**: Use extensions like "Markdown Preview Mermaid Support"
4. **Documentation Sites**: Tools like MkDocs, Docusaurus, and GitBook support Mermaid

## ADR Template

When creating new ADRs, follow this structure:

```markdown
# ADR-XXXX: [Title]

## Status

[Proposed | Accepted | Deprecated | Superseded]

## Context

[Describe the issue or problem motivating this decision]

## Decision

[Describe the architectural decision]

[Include Mermaid diagram(s) to visualize the decision]

## Consequences

### Positive
- [List positive impacts]

### Negative
- [List negative impacts]

### Mitigation Strategies
- [How to address negative consequences]
```

## References

- [Architecture Decision Records](https://adr.github.io/)
- [Mermaid.js Documentation](https://mermaid.js.org/)
- [C4 Model](https://c4model.com/)
- [Michael Nygard's ADR Template](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions)
