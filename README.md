# FloraFlow

Event-driven microservices-based flower ordering platform built with Spring Boot.

FloraFlow is a scalable event-driven flower ordering platform built using a microservices architecture with Spring Boot.

The project focuses on distributed systems concepts such as asynchronous communication, Saga Choreography Pattern, Outbox Pattern, RabbitMQ messaging, and Kubernetes deployment.

---

# Architecture

FloraFlow follows a distributed microservices architecture where each service owns its own database and communicates asynchronously using RabbitMQ Topic Exchange.

## Microservices

- API Gateway
- User Service
- Catalog Service
- Cart Service
- Order Service
- Payment Service
- Wallet Service
- Notification Service

---

# Tech Stack

## Backend
- Java
- Spring Boot
- Spring Security
- Spring Cloud Gateway
- Spring Data JPA

## Database
- PostgreSQL
- Redis

## Messaging
- RabbitMQ
- Topic Exchange
- Dead Letter Queue (DLQ)

## Infrastructure
- Docker
- Kubernetes
- Kubernetes Ingress

---

# Key Features

- JWT Authentication & Authorization
- Refresh Token Mechanism
- Role-Based Access Control
- Event-Driven Architecture
- Saga Choreography Pattern
- Outbox Pattern
- Retry Mechanism
- Dead Letter Queue Handling
- Redis Caching
- Global Exception Handling
- Database per Service
- Kubernetes Deployment

---

# Security

Authentication and authorization are handled by the User Service using Spring Security and JWT.

## Features

- Login & Registration
- Access Token
- Refresh Token
- Password Recovery
- Role-Based Authorization

---

# Cart Management

Cart Service is responsible for:

- Adding products to cart
- Updating cart items
- Removing products from cart
- Checkout preparation before order creation

---

# Messaging Architecture

FloraFlow uses RabbitMQ Topic Exchange for asynchronous communication between services.

## Example Queue Naming

```bash
order.created.queue
payment.status.queue
wallet.status.queue
notification.order.queue
```

All services support:

- Retry Mechanism
- Dead Letter Queue (DLQ)
- Reliable Event Processing

---

# Event Flow

1. User adds products to cart
2. User proceeds to checkout
3. Cart Service creates order request
4. Order Service publishes `OrderCreatedEvent`
5. Payment Service consumes the event
6. Payment Service publishes `PaymentCreatedEvent`
7. Wallet Service validates user balance
8. Wallet Service publishes `WalletStatusEvent`
9. Payment Service updates payment status
10. Payment Service publishes `PaymentStatusEvent`
11. Order Service updates order status
12. Notification Service sends email notification to the user

---

# Order Status Flow

```text
CREATED
PAYMENT_PENDING
PAYMENT_COMPLETED
PAYMENT_FAILED
CANCELLED
READY_FOR_PICKUP
COMPLETED
```

---

# Reliability Patterns

## Saga Choreography Pattern

Services communicate through events without a centralized orchestrator.

## Outbox Pattern

All microservices use the Outbox Pattern to guarantee reliable event publishing.

## Retry & DLQ

Failed messages are retried automatically and redirected to Dead Letter Queues when necessary.

## Global Exception Handling

Every service includes centralized exception handling for consistent API responses.

---

# Redis Usage

Redis is used for:

- Caching
- Catalog data optimization

---

# Kubernetes

The project includes:

- Deployment YAML files
- Service YAML files
- Ingress configuration

---

# Future Improvements

- Distributed Tracing
- Monitoring with Prometheus & Grafana
- CI/CD Pipeline
- Centralized Logging
- API Documentation Gateway
- Service Discovery

---

# Repositories

| Service | Repository |
|---|---|
| API Gateway | https://github.com/AminRamazanov/FloraFlow-ApiGateway |
| User Service | https://github.com/AminRamazanov/FloraFlow-UserService |
| Catalog Service | https://github.com/AminRamazanov/FloraFlow-CatalogService |
| Cart Service | https://github.com/AminRamazanov/FloraFlow-CartService |
| Order Service | https://github.com/AminRamazanov/FloraFlow-OrderService |
| Payment Service | https://github.com/AminRamazanov/FloraFlow-PaymentService |
| Wallet Service | https://github.com/AminRamazanov/FloraFlow-WalletService |
| Notification Service | https://github.com/AminRamazanov/FloraFlow-NotificationService |

---

# Author

Amin Ramazanov  
Java Backend Developer
