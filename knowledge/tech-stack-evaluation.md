# Tech Stack Evaluation

Scoring framework for technology selection decisions.

## Evaluation Dimensions

| Dimension | Weight | What to Assess |
|-----------|--------|----------------|
| Requirements fit | 25% | Does it solve the specific technical requirements? |
| Team expertise | 20% | Current team skill level, hiring market depth |
| Ecosystem maturity | 15% | Library availability, community size, documentation quality |
| Scalability | 15% | Vertical/horizontal scaling ceiling, cost curve |
| Time to market | 15% | Development speed, boilerplate reduction, tooling |
| Operational cost | 10% | Hosting, licensing, maintenance burden |

## Backend Framework Selection

| Framework | Language | Strengths | Watch Out |
|-----------|----------|-----------|-----------|
| FastAPI | Python | Async, auto-docs, type hints | GIL for CPU-bound, ecosystem fragmentation |
| Django | Python | Batteries included, admin, ORM | Monolithic, async still maturing |
| Express | Node.js | Minimal, huge ecosystem | No structure opinions, callback patterns |
| NestJS | TypeScript | Structured, DI, decorators | Learning curve, over-engineered for small projects |
| Gin | Go | Performance, simplicity | Smaller ecosystem, verbose error handling |
| Axum | Rust | Performance, safety | Steep learning curve, longer dev time |

## Database Selection

| Type | Products | Best For | Avoid When |
|------|----------|----------|------------|
| Relational | PostgreSQL, MySQL | Structured data, ACID, complex queries | Unstructured data, extreme write scale |
| Document | MongoDB, DynamoDB | Flexible schema, nested data | Complex joins, strong consistency |
| Key-value | Redis, Memcached | Caching, sessions, rate limiting | Primary data store, complex queries |
| Graph | Neo4j, Neptune | Relationship-heavy data | Simple CRUD, tabular data |
| Time-series | TimescaleDB, InfluxDB | Metrics, logs, IoT | General application data |
| Vector | Pgvector, Pinecone | Similarity search, embeddings | Exact match queries |
| Search | Elasticsearch, Meilisearch | Full-text search, faceting | Primary data store |

## Cloud Provider Comparison

| Service | AWS | GCP | Azure |
|---------|-----|-----|-------|
| Compute | EC2, ECS, Lambda | Compute Engine, Cloud Run, Cloud Functions | VMs, Container Apps, Functions |
| Database | RDS, DynamoDB | Cloud SQL, Firestore | Azure SQL, Cosmos DB |
| Queue | SQS, SNS | Pub/Sub, Cloud Tasks | Service Bus |
| Storage | S3 | Cloud Storage | Blob Storage |
| Auth | Cognito | Firebase Auth | Azure AD B2C |
| CDN | CloudFront | Cloud CDN | Azure CDN |

## Decision Template

For each major component decision, document:

1. **Context** — what requirement drives this decision
2. **Options considered** — minimum 2, with pros/cons
3. **Decision** — which option and why
4. **Consequences** — what this enables and what it constrains
5. **Risk** — vendor lock-in level, migration difficulty

## Red Flags in Stack Proposals

- Choosing technology because it is trendy, not because it fits requirements
- No consideration of team expertise or hiring availability
- Ignoring operational complexity (Kubernetes for a 2-person team)
- Selecting multiple databases without justification per data type
- No cost projection for expected scale
