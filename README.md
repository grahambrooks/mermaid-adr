# mermaid-adr

Example Architecture Decision Records (ADRs) that include Mermaid.js diagrams

## Overview

This repository provides a collection of example ADRs demonstrating how to document architectural decisions using Mermaid.js diagrams. The examples cover a hypothetical e-commerce platform built with microservices architecture.

## What's Included

The [decisions](decisions/) directory contains 7 example ADRs showcasing different types of Mermaid.js diagrams:

- **C4 Diagrams**: Context, Container, and Component diagrams for visualizing architecture at different levels
- **Behavioral Diagrams**: Sequence diagrams, state diagrams, and flowcharts
- **Structural Diagrams**: Entity relationship diagrams

## Quick Start

Browse the [decisions](decisions/) directory to see examples:

1. [ADR-0001: Adopt Microservices Architecture](decisions/0001-adopt-microservices-architecture.md) - C4 Context diagram
2. [ADR-0002: API Gateway Pattern](decisions/0002-api-gateway-pattern.md) - C4 Container diagram
3. [ADR-0003: Event-Driven Order Processing](decisions/0003-event-driven-order-processing.md) - Sequence diagram
4. [ADR-0004: Circuit Breaker Pattern](decisions/0004-circuit-breaker-pattern.md) - Flowchart
5. [ADR-0005: Database per Service](decisions/0005-database-per-service.md) - Entity Relationship diagram
6. [ADR-0006: CQRS Pattern](decisions/0006-cqrs-pattern-product-catalog.md) - C4 Component diagram
7. [ADR-0007: Order State Machine](decisions/0007-order-state-machine.md) - State diagram

## Why ADRs with Mermaid?

**ADRs** (Architecture Decision Records) help teams:
- Document important architectural decisions
- Understand the context and rationale behind decisions
- Track the evolution of architecture over time
- Onboard new team members more effectively

**Mermaid.js** provides:
- Text-based diagrams that live in your repository
- Version control for your diagrams
- Easy updates without specialized tools
- Automatic rendering on GitHub, GitLab, and documentation platforms

## Resources

- [Architecture Decision Records](https://adr.github.io/)
- [Mermaid.js Documentation](https://mermaid.js.org/)
- [C4 Model for Software Architecture](https://c4model.com/)

## License

These examples are provided as-is for educational and reference purposes.
