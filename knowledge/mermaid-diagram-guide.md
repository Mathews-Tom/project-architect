# Mermaid Diagram Guide

Reference for generating architecture diagrams using Mermaid syntax.

## Diagram Types for Architecture

| Diagram Type | Use For | Mermaid Keyword |
|-------------|---------|-----------------|
| System topology | Component relationships, data flow | `graph` or `flowchart` |
| Sequence | API call flows, auth handshakes | `sequenceDiagram` |
| Entity relationship | Database schema design | `erDiagram` |
| State machine | Workflow states, order lifecycle | `stateDiagram-v2` |
| Class diagram | Domain model, service interfaces | `classDiagram` |
| C4 Context | System context boundaries | `C4Context` |

## System Topology Template

```mermaid
graph TB
    subgraph "Client Layer"
        WEB[Web App]
        MOB[Mobile App]
    end

    subgraph "API Layer"
        GW[API Gateway]
        AUTH[Auth Service]
    end

    subgraph "Service Layer"
        SVC1[Service A]
        SVC2[Service B]
    end

    subgraph "Data Layer"
        DB[(PostgreSQL)]
        CACHE[(Redis)]
        QUEUE[Message Queue]
    end

    WEB --> GW
    MOB --> GW
    GW --> AUTH
    GW --> SVC1
    GW --> SVC2
    SVC1 --> DB
    SVC1 --> CACHE
    SVC2 --> DB
    SVC1 -- async --> QUEUE
    QUEUE -- async --> SVC2
```

## Sequence Diagram Template

```mermaid
sequenceDiagram
    participant C as Client
    participant G as Gateway
    participant A as Auth
    participant S as Service
    participant D as Database

    C->>G: POST /api/resource
    G->>A: Validate token
    A-->>G: 200 OK
    G->>S: Forward request
    S->>D: INSERT
    D-->>S: Success
    S-->>G: 201 Created
    G-->>C: 201 Created
```

## ER Diagram Template

```mermaid
erDiagram
    USER ||--o{ ORDER : places
    ORDER ||--|{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : "ordered in"

    USER {
        uuid id PK
        string email UK
        string name
        timestamp created_at
    }
```

## Style Conventions

| Element | Shape | Example |
|---------|-------|---------|
| Service/API | Rectangle | `[Service Name]` |
| Database | Cylinder | `[(Database)]` |
| Queue/Topic | Parallelogram | `[/Queue/]` |
| External system | Rounded rect | `(External API)` |
| User/Client | Stadium | `([User])` |

## Arrow Conventions

| Arrow | Meaning |
|-------|---------|
| `-->` | Synchronous call |
| `-- async -->` | Asynchronous message |
| `-.->` | Optional/conditional |
| `==>` | Data flow (heavy) |

## Subgraph Usage

Group components by:
- Deployment boundary (VPC, cluster, region)
- Domain boundary (user service, payment service)
- Layer (client, API, service, data)

## Checklist Before Delivery

| Check | Requirement |
|-------|-------------|
| All components from spec present | Yes |
| Data flow direction arrows correct | Yes |
| Async vs sync communication distinguished | Yes |
| External system boundaries marked | Yes |
| Database types indicated | Yes |
| Subgraphs match deployment topology | Yes |
