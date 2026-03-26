# Architecture Patterns

Reference catalog of distributed system and application architecture patterns.

## Application Architecture Styles

| Style | When to Use | When to Avoid |
|-------|-------------|---------------|
| Monolith | Small team (< 5), MVP, single domain | Multiple teams, independent scaling needs |
| Modular monolith | Medium team, clear domain boundaries | Need independent deployment per module |
| Microservices | Large team, independent scaling, polyglot | Small team, unclear boundaries, early stage |
| Serverless | Event-driven, variable load, low ops capacity | Latency-sensitive, long-running processes |
| Event-driven | Async workflows, audit trails, decoupled systems | Simple CRUD, strong consistency required |

## Distributed System Patterns

### Data Patterns

| Pattern | Purpose | Tradeoff |
|---------|---------|----------|
| CQRS | Separate read/write models | Complexity vs. read/write optimization |
| Event Sourcing | Immutable event log as source of truth | Storage cost vs. audit trail + replay |
| Saga | Distributed transactions across services | Complexity vs. data consistency |
| Outbox | Reliable event publishing with DB writes | Extra table vs. at-least-once delivery |

### Resilience Patterns

| Pattern | Purpose | Implementation |
|---------|---------|----------------|
| Circuit Breaker | Prevent cascade failures | Open after N failures, half-open after timeout |
| Bulkhead | Isolate failure domains | Separate thread pools / connection pools |
| Retry with backoff | Handle transient failures | Exponential backoff with jitter, max retries |
| Timeout | Bound wait time | Per-call timeout, propagate deadline |
| Rate limiter | Protect downstream services | Token bucket or sliding window |

### Communication Patterns

| Pattern | Latency | Coupling | Use When |
|---------|---------|----------|----------|
| Sync REST | Low | High | Simple CRUD, public APIs |
| Sync gRPC | Very low | High | Internal service-to-service, streaming |
| Async message queue | Variable | Low | Decoupled processing, load leveling |
| Async event bus | Variable | Very low | Fan-out, event-driven architectures |
| GraphQL | Low | Medium | Client-driven queries, mobile APIs |

## Caching Strategies

| Strategy | Pattern | Consistency |
|----------|---------|-------------|
| Cache-aside | App reads cache, fills on miss | Eventual (TTL-based) |
| Write-through | Write to cache + DB simultaneously | Strong |
| Write-behind | Write to cache, async flush to DB | Eventual (risk of data loss) |
| Read-through | Cache fetches from DB on miss | Eventual (TTL-based) |

## Scaling Patterns

| Dimension | Approach |
|-----------|----------|
| Vertical | Bigger instance (simple, limited ceiling) |
| Horizontal | More instances behind load balancer |
| Database read | Read replicas |
| Database write | Sharding by tenant/region |
| Compute | Auto-scaling groups, serverless |
| Static assets | CDN edge caching |

## Anti-Patterns to Flag

- Distributed monolith (microservices with synchronous coupling)
- Shared database across services
- God service (one service handling too many domains)
- Chatty interfaces (N+1 service calls)
- Missing circuit breakers on external calls
- No health checks or readiness probes
