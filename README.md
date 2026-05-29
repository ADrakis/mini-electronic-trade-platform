# Mini Electronic Trading Platform

A simplified electronic trading platform designed to teach the core concepts used in trading firms, investment banks, hedge funds, and financial technology companies.

This project simulates the flow of market data through multiple services, allowing users to submit orders, manage risk, view positions, and monitor trading activity in real time.

The goal is educational rather than financial. The platform is designed to help developers learn distributed systems, messaging, APIs, databases, cloud infrastructure, security, DevOps, and financial market concepts.

---

## Architecture

```text
Market Data Simulator
         │
         ▼
Message Queue
         │
         ▼
Pricing Service
         │
         ▼
Order Management System
         │
         ▼
Risk Engine
         │
         ▼
PostgreSQL Database
         │
         ▼
Web Dashboard
```

---

## Project Goals

This project aims to provide hands-on experience with:

* Distributed systems
* Event-driven architecture
* Financial market concepts
* Real-time data processing
* API development
* Database design
* Security principles
* DevOps practices
* Monitoring and observability

---

## Core Components

### Market Data Simulator

Generates live market prices for financial instruments.

Example symbols:

* EUR/USD
* GBP/USD
* USD/JPY
* BTC/USD

Example market data event:

```json
{
  "symbol": "EURUSD",
  "bid": 1.1250,
  "ask": 1.1252,
  "timestamp": "2026-01-01T12:00:00Z"
}
```

Responsibilities:

* Generate simulated prices
* Publish market events
* Support configurable update intervals
* Stream data to downstream services

---

### Message Queue

Acts as the communication layer between services.

Potential technologies:

* RabbitMQ
* Apache Kafka

Responsibilities:

* Decouple services
* Support event-driven processing
* Improve scalability
* Improve reliability

---

### Pricing Service

Consumes market data and distributes pricing information.

Responsibilities:

* Process incoming market prices
* Store recent price history
* Publish price updates
* Support dashboard subscriptions

---

### Order Management System (OMS)

Allows traders to manage orders.

Supported actions:

* Buy
* Sell
* Modify
* Cancel

Example order:

```json
{
  "symbol": "EURUSD",
  "side": "BUY",
  "quantity": 100000
}
```

Responsibilities:

* Order validation
* Order lifecycle management
* Trade generation
* Audit logging

---

### Risk Engine

Tracks risk across all positions.

Calculations:

* Position
* Exposure
* Profit and Loss (PnL)
* Daily trading limits

Example:

```text
EURUSD +500,000
GBPUSD -250,000
```

Responsibilities:

* Aggregate positions
* Calculate exposure
* Monitor limits
* Generate risk alerts

---

### Web Dashboard

Provides a real-time view of the trading platform.

Features:

* Live prices
* Open orders
* Executed trades
* Risk metrics
* PnL monitoring

Technologies:

* React
* TypeScript
* SignalR or WebSockets
* Charting libraries

---

## Database Design

PostgreSQL will be used as the primary datastore.

Core tables:

```text
Users
Orders
Trades
Positions
MarketData
AuditLogs
```

Topics covered:

* Relational modelling
* Transactions
* Indexing
* Query optimisation
* Data integrity

---

## Security

The platform should implement:

* JWT Authentication
* Role-Based Access Control
* HTTPS
* Secret Management
* Audit Logging
* Input Validation

Roles:

```text
Trader
Support
Admin
```

---

## DevOps

Infrastructure and deployment should be fully automated.

Tools:

* Docker
* GitHub Actions
* Terraform
* Cloud Platform

Deployment pipeline:

```text
Code Push
    │
    ▼
Automated Tests
    │
    ▼
Build
    │
    ▼
Docker Image
    │
    ▼
Deploy
```

---

## Testing Strategy

The platform should include:

### Unit Tests

Validate individual components.

### Integration Tests

Validate service interactions.

### API Tests

Validate endpoints and business workflows.

Example workflow:

```text
Submit Order
      │
      ▼
Trade Executed
      │
      ▼
Position Updated
      │
      ▼
PnL Updated
```

---

## Monitoring & Observability

Every service should produce structured logs.

Example events:

```text
Order Received
Order Validated
Trade Executed
Risk Updated
```

Metrics to monitor:

* Trade count
* Error rate
* Message throughput
* API latency
* Risk alerts

Potential tooling:

* OpenTelemetry
* Prometheus
* Grafana
* Cloud Monitoring

---

## Learning Outcomes

Developers working on this project will gain experience with:

* C#/.NET or Java
* REST APIs
* PostgreSQL
* Docker
* CI/CD
* Terraform
* RabbitMQ or Kafka
* Event-driven architecture
* Distributed systems
* Real-time applications
* Financial market concepts
* Security fundamentals
* Cloud deployments

---

## Stretch Goals

### FIX Protocol Simulator

Implement support for:

* New Order
* Cancel Order
* Execution Report

### Pricing Engine

Calculate:

* Options prices
* Greeks
* Volatility metrics

### Strategy Engine

Example moving average crossover strategy:

```text
If MA20 > MA50
    BUY
Else
    SELL
```

### Market Replay

Replay historical market data to test strategies and platform behaviour.

---

## Disclaimer

This project is intended for educational purposes only.

It is not connected to any financial institution, exchange, broker, or trading venue. No real money, customer data, or proprietary trading systems are involved.
