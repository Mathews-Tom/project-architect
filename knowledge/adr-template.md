# ADR Template

Architecture Decision Record format and guidelines.

## Standard ADR Structure

```markdown
# ADR-NNN: <Decision Title>

**Status:** Proposed | Accepted | Deprecated | Superseded by ADR-XXX
**Date:** YYYY-MM-DD
**Deciders:** <list of people involved>

## Context

<What is the technical or business situation that requires a decision?
Include constraints, requirements, and forces at play. State facts, not opinions.>

## Decision

<What is the decision and why was it chosen? Be specific — name technologies,
patterns, and approaches. State the decision in active voice: "We will use X.">

## Options Considered

### Option 1: <Name>
- **Pros:** ...
- **Cons:** ...

### Option 2: <Name>
- **Pros:** ...
- **Cons:** ...

### Option 3: <Name>
- **Pros:** ...
- **Cons:** ...

## Consequences

### Positive
- <What becomes easier or possible>

### Negative
- <What becomes harder or impossible>
- <New constraints introduced>

### Risks
- <Identified risks and mitigations>

## References
- <Links to research, benchmarks, or related ADRs>
```

## When to Write an ADR

| Decision Type | Write ADR? |
|---------------|-----------|
| Database selection | Yes |
| Monolith vs. microservices | Yes |
| Auth strategy (OAuth, JWT, sessions) | Yes |
| API style (REST, GraphQL, gRPC) | Yes |
| Cloud provider selection | Yes |
| Framework selection | Yes |
| Caching strategy | Yes |
| Message queue selection | Yes |
| Naming convention change | No |
| Library version bump | No |
| Code formatting rules | No |
| Test framework selection | Depends on scope |

## ADR Quality Criteria

| Criterion | Requirement |
|-----------|-------------|
| Context states the problem | No solution leakage in context section |
| Options minimum | At least 2 options considered |
| Pros/cons balanced | Every option has both pros and cons |
| Decision justified | Clear link from context to decision |
| Consequences honest | Negative consequences stated explicitly |
| Risks identified | At least one risk with mitigation |
| Status current | Status reflects actual state |

## ADR Numbering

- Sequential: `ADR-001`, `ADR-002`, ...
- Store in: `docs/adr/` or `architecture/decisions/`
- Index file: `docs/adr/README.md` listing all ADRs with status

## ADR Lifecycle

```
Proposed → Accepted → [Active]
                    → Deprecated (no longer relevant)
                    → Superseded by ADR-XXX (replaced)
```

## Common Pitfalls

- Writing ADRs after the decision is implemented (write before or during)
- Omitting rejected options (the reasoning for rejection is the most valuable part)
- No negative consequences (every decision has downsides)
- Too long (target 1-2 pages, not a whitepaper)
- Missing context (future readers need to understand why, not just what)
