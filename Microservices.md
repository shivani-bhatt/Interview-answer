
# Microservices Architecture – Key Components & How They Work Together

Microservices architecture is a design approach where an application is built as a collection of small, independent services that communicate with each other.

---

## Main Parts of Microservices Architecture

### 1. **Client / Frontend**
- This is the user-facing application (Web, Mobile, UI).
- Sends requests to backend services via APIs.
- Does not directly communicate with individual services in most cases.

---

### 2. **API Gateway**
- Acts as a single entry point for all client requests.
- Routes requests to appropriate microservices.
- Handles:
  - Authentication & Authorization
  - Rate limiting
  - Logging
  - Request aggregation

Example:
```

Client → API Gateway → Microservice

```

---

### 3. **Microservices (Core Services)**
- Independent services responsible for specific business functionalities.
- Each service:
  - Has its own logic
  - Is independently deployable
  - Communicates via APIs (REST, gRPC, messaging)

Example Services:
- User Service
- Order Service
- Payment Service

---

### 4. **Service Registry & Discovery**
- Keeps track of all running services and their locations.
- Enables services to find each other dynamically.

Flow:
```

Service registers itself → Registry
Other services query registry → Get service location

```

---

### 5. **Database per Service**
- Each microservice has its own database.
- Ensures loose coupling and independent scaling.

Types:
- SQL (PostgreSQL, MySQL)
- NoSQL (MongoDB)

---

### 6. **Inter-Service Communication**
Two main approaches:

#### a) Synchronous (Request/Response)
- REST APIs / gRPC
- Immediate response required

#### b) Asynchronous (Event-driven)
- Message brokers (Kafka, RabbitMQ)
- Services communicate via events

Example:
```

Order Service → emits "Order Created" event → Payment Service listens

```

---

### 7. **Message Broker (Event Bus)**
- Handles asynchronous communication between services.
- Ensures decoupling and reliability.

---

### 8. **Configuration Server**
- Centralized configuration management.
- Stores environment-specific configs.

---

### 9. **Security Layer**
- Handles:
  - Authentication (JWT, OAuth2)
  - Authorization
- Often integrated at API Gateway level.

---

### 10. **Monitoring & Logging**
- Tracks system health and performance.
- Tools used:
  - Logging: ELK Stack
  - Monitoring: Prometheus, Grafana

---

### 11. **Containerization & Orchestration**
- Services are packaged into containers (Docker).
- Managed using orchestration tools (Kubernetes).

---

## How Everything Works Together

### Step-by-Step Flow

1. **Client sends request**
```

Client → API Gateway

```

2. **API Gateway routes request**
```

API Gateway → Relevant Microservice

```

3. **Service discovery happens**
```

Gateway → Service Registry → Finds service instance

```

4. **Microservice processes request**
- May call other services (sync or async)
- May publish events to message broker

5. **Database interaction**
```

Microservice → Its own database

```

6. **Response sent back**
```

Microservice → API Gateway → Client

```

---

## Key Benefits

- Independent deployment
- Scalability
- Fault isolation
- Technology flexibility

---

## Challenges

- Distributed system complexity
- Data consistency
- Network latency
- Monitoring difficulty

---

## Simple Architecture Diagram (Conceptual)

```

```
      Client (Web/Mobile)
              │
       API Gateway
              │
```

┌──────────────┼──────────────┐
│              │              │
User Service   Order Service   Payment Service
│              │              │
DB_User        DB_Order       DB_Payment
│
Message Broker

```

---

## Summary

Microservices architecture works by dividing a large system into smaller, independent services that communicate through APIs or events. Components like API Gateway, Service Registry, Message Broker, and individual databases ensure scalability, flexibility, and maintainability.

---
