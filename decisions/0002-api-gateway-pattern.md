# ADR-0002: API Gateway Pattern for Microservices

## Status

Accepted

## Context

With our microservices architecture (as decided in ADR-0001), we face challenges:
- Clients need to know about multiple service endpoints
- Different services may use different protocols
- Cross-cutting concerns (authentication, rate limiting, logging) are duplicated
- Making changes to service endpoints impacts all clients

We need a solution that provides a single entry point for clients while managing the complexity of the backend microservices.

## Decision

We will implement an API Gateway pattern that serves as a single entry point for all client requests. The gateway will route requests to appropriate backend services and handle cross-cutting concerns.

### Container Architecture

```mermaid
C4Container
    title Container diagram for E-Commerce Platform

    Person(customer, "Customer", "Platform user")
    
    Container_Boundary(platform, "E-Commerce Platform") {
        Container(web, "Web Application", "React", "Provides UI to customers")
        Container(mobile, "Mobile App", "React Native", "Provides mobile experience")
        Container(gateway, "API Gateway", "Kong/AWS API Gateway", "Routes requests, handles auth, rate limiting")
        
        Container(product, "Product Service", "Node.js", "Manages product catalog")
        Container(order, "Order Service", "Java Spring Boot", "Handles order processing")
        Container(user, "User Service", "Python FastAPI", "Manages user accounts")
        Container(cart, "Cart Service", "Go", "Manages shopping carts")
        
        ContainerDb(productDb, "Product Database", "PostgreSQL", "Stores product data")
        ContainerDb(orderDb, "Order Database", "PostgreSQL", "Stores order data")
        ContainerDb(userDb, "User Database", "PostgreSQL", "Stores user data")
        ContainerDb(cache, "Cache", "Redis", "Caches frequently accessed data")
    }
    
    System_Ext(payment, "Payment Gateway", "External payment processor")
    
    Rel(customer, web, "Uses", "HTTPS")
    Rel(customer, mobile, "Uses", "HTTPS")
    Rel(web, gateway, "Makes API calls", "HTTPS/JSON")
    Rel(mobile, gateway, "Makes API calls", "HTTPS/JSON")
    
    Rel(gateway, product, "Routes to", "HTTP/REST")
    Rel(gateway, order, "Routes to", "HTTP/REST")
    Rel(gateway, user, "Routes to", "HTTP/REST")
    Rel(gateway, cart, "Routes to", "HTTP/REST")
    
    Rel(product, productDb, "Reads/Writes", "TCP/SQL")
    Rel(order, orderDb, "Reads/Writes", "TCP/SQL")
    Rel(user, userDb, "Reads/Writes", "TCP/SQL")
    
    Rel(product, cache, "Caches", "TCP/Redis Protocol")
    Rel(cart, cache, "Stores", "TCP/Redis Protocol")
    
    Rel(order, payment, "Processes payment", "HTTPS/API")
```

## Consequences

### Positive

- **Single Entry Point**: Clients interact with one endpoint instead of multiple services
- **Simplified Client Code**: Clients don't need to know about service locations or handle service discovery
- **Centralized Cross-Cutting Concerns**: Authentication, logging, rate limiting handled in one place
- **Protocol Translation**: Gateway can translate between client-friendly protocols and internal protocols
- **Flexibility**: Can modify backend services without impacting clients
- **Security**: Provides an additional security layer

### Negative

- **Single Point of Failure**: Gateway becomes a critical component that needs high availability
- **Performance Bottleneck**: All traffic goes through the gateway
- **Complexity**: Adds another component to maintain and monitor
- **Configuration Management**: Gateway routing rules need to be kept in sync with services

### Mitigation Strategies

- Deploy gateway in a highly available configuration (multiple instances, load balanced)
- Implement comprehensive monitoring and alerting
- Use a proven, production-ready gateway solution (Kong, AWS API Gateway, etc.)
- Implement proper caching strategies to reduce load
- Set up automated configuration management and testing
