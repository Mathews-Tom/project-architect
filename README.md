# project-architect

System architecture agent that conducts phased requirements discovery and produces comprehensive architecture documents with technology stack justification, Mermaid diagrams, data flow design, and implementation roadmaps. Gathers business context before proposing technical solutions.

[![gitagent registry](https://img.shields.io/badge/gitagent-registry-blue)](https://registry.gitagent.sh)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/Mathews-Tom/project-architect
```

---

## What It Can Do

- **Business Discovery** — extracts product understanding, success metrics, constraints, and compliance requirements through structured questioning
- **Technical Requirements** — gathers core functionality, platform needs, performance targets, and security requirements
- **Technology Selection** — evaluates 2-3 options per component with scoring against requirements and tradeoff rationale
- **Architecture Document Production** — generates executive summary, component breakdown, data architecture, security design, API design, and infrastructure topology with Mermaid diagrams
- **ADR Generation** — produces Architecture Decision Records for key decisions with context, alternatives, and consequences
- **Self-Validation** — reviews the produced architecture for missing components, scalability bottlenecks, and security gaps

---

## Structure

```
project-architect/
├── agent.yaml
├── SOUL.md
├── RULES.md
├── README.md
├── assets/
│   ├── icon.png
│   └── banner.png
└── knowledge/
    ├── architecture-patterns.md
    ├── tech-stack-evaluation.md
    ├── mermaid-diagram-guide.md
    └── adr-template.md
```

---

## Built with

Built for the [gitagent](https://gitagent.sh) ecosystem.
