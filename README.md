# Banking Architecture Kit

A practical toolkit for banking solution architecture work — built around TOGAF ADM and the BIAN Service Domain model.

## What's in Here

```
banking-architecture-kit/
├── skill/                          # Claude architecture skill
│   ├── SKILL.md                    # Skill definition — install in Claude Code / Cowork
│   └── references/
│       ├── togaf-adm.md            # TOGAF ADM phases, views, artifacts quick reference
│       ├── bian-service-domains.md # Full BIAN service domain catalog by banking area
│       └── architecture-patterns.md# Integration, deployment, security patterns
│
├── assessment-tool/
│   └── architecture-assessment.html# Interactive maturity assessment (open in browser)
│
└── evals/
    └── evals.json                  # Test cases for the architecture skill
```

## The Architecture Skill

The skill (`skill/SKILL.md`) teaches Claude to act as a senior banking solution architect.

**It handles four output types:**
- Architecture diagrams (HTML, layered, BIAN-labelled)
- Solution design documents (TOGAF-structured Word docs)
- Client proposals (deck-ready narrative arc)
- RFP/RFI technical responses (compliance matrix format)

**Frameworks applied:**
- TOGAF ADM for method and artifact structure
- BIAN Service Domain model for banking capability naming and completeness checking
- Vendor-neutral by default

**To install:** Copy the `skill/` folder into your Claude Code skills directory, or import via Cowork.

## The Assessment Tool

`assessment-tool/architecture-assessment.html` — open directly in any browser, no server needed.

A client workshop tool that walks through 8 architecture domains (24 scored questions), produces a radar chart of actual vs industry benchmark, and generates a prioritised gap analysis table.

**Domains covered:**
1. Core Banking (BIAN Coverage)
2. Payments (Rail Modernisation & Open Banking)
3. Lending & Credit (Origination & Scoring)
4. Integration & APIs (Architecture Patterns)
5. Data & Analytics (Platform Maturity)
6. Cloud & Infrastructure (DevOps & DR)
7. Security & Compliance (Zero Trust & AML)
8. Observability & Operations (Monitoring & Audit)

## Frameworks Reference

| Framework | What it provides | Reference file |
|-----------|-----------------|----------------|
| TOGAF ADM | Method, phases, artifact types | `skill/references/togaf-adm.md` |
| BIAN v12 | Banking capability names, service domain boundaries | `skill/references/bian-service-domains.md` |
| Architecture Patterns | Integration, deployment, security patterns | `skill/references/architecture-patterns.md` |
