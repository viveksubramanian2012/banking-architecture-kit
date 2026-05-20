# TOGAF ADM Reference

## Architecture Development Method (ADM) — Phase Summary

The ADM is a cycle. For banking engagements, you rarely run the full cycle end-to-end in one shot.
Know which phase the client is actually in and produce artifacts for that phase.

### Preliminary Phase
**Purpose:** Set up the architecture capability and governance.
**Key artifacts:** Architecture Principles, Architecture Repository setup, Stakeholder map.
**Banking relevance:** Establishing architecture governance before a core banking transformation.

### Phase A — Architecture Vision
**Purpose:** Define scope, stakeholders, and high-level solution concept. Get buy-in.
**Key artifacts:** Architecture Vision document, Statement of Architecture Work, Stakeholder map, Business scenarios.
**Banking relevance:** The opening slide in any client proposal. Answer: what are we building and why?

### Phase B — Business Architecture
**Purpose:** Define the target business capability model, processes, and value streams.
**Key artifacts:** Business capability map, Process flows, Organisation map, Business interaction matrix.
**Banking relevance:** Map to BIAN Service Domains at this phase. The capability map IS the BIAN domain coverage table.

### Phase C — Information Systems Architecture
Two sub-phases:

**C1 — Data Architecture**
Define key data entities, ownership, flows, and master data strategy.
Key artifacts: Data entity diagram, Data flow diagram, Data migration strategy.
Banking relevance: Customer master data, account data, transaction data lineage.

**C2 — Application Architecture**
Define the system components, their responsibilities, and interactions.
Key artifacts: Application portfolio, Component diagram, Interface catalogue, API inventory.
Banking relevance: This is where microservices, core banking modules, and channel applications are mapped.

### Phase D — Technology Architecture
**Purpose:** Define the infrastructure, deployment model, and platform.
**Key artifacts:** Platform diagram, Network diagram, Deployment diagram, Cloud architecture.
**Banking relevance:** Cloud vs on-premise decision, containerisation, HA/DR requirements.

### Phase E — Opportunities & Solutions
**Purpose:** Define the roadmap — what to build when, dependencies, and quick wins.
**Key artifacts:** Project portfolio, Implementation roadmap, Work packages, Migration plan.
**Banking relevance:** Phased delivery plan for a core banking replacement or digital transformation.

### Phase F — Migration Planning
**Purpose:** Finalise sequence and dependencies for implementation.
**Key artifacts:** Transition architectures, Migration plan, Risk register.
**Banking relevance:** Data migration strategy, parallel run periods, cutover planning.

### Phase G — Implementation Governance
**Purpose:** Oversee implementation to ensure architecture compliance.
**Key artifacts:** Architecture contract, Compliance assessment, Change requests.
**Banking relevance:** Architecture review board during delivery. Preventing drift from the approved design.

### Phase H — Architecture Change Management
**Purpose:** Manage changes to the architecture post-implementation.
**Key artifacts:** Change request log, Impact assessment, Updated architecture.
**Banking relevance:** Handling new regulatory requirements or product additions post-go-live.

---

## TOGAF Architecture Views — Quick Reference

| View | Audience | Key question answered |
|------|----------|----------------------|
| Business | CxO, Business | What capabilities do we have / need? |
| Application | Solution Architect, BA | What systems deliver those capabilities? |
| Data | Data Architect, Compliance | What data exists, where, and who owns it? |
| Technology | Infrastructure, DevOps | How is it deployed and on what platform? |
| Security | CISO, Risk | How is access controlled and data protected? |

---

## Architecture Principles — Banking Defaults

1. **API-First** — All integration via APIs; no direct database-to-database calls.
2. **Business Capability Alignment** — Every system maps to one or more BIAN Service Domains.
3. **Data Ownership is Single-Source** — Each data entity has one authoritative system of record.
4. **Security by Design** — Security controls defined in architecture, not bolted on in delivery.
5. **Cloud-Ready** — Architecture should not assume on-premise-only deployment.
6. **Vendor Portability** — Avoid proprietary lock-in at the integration layer.
7. **Observability Built In** — Logging, tracing, and monitoring designed from day one.
8. **Regulatory Compliance is Non-Negotiable** — Compliance requirements are architecture constraints, not afterthoughts.

---

## Architecture Artifacts Quick Selector

| What the client asks for | TOGAF artifact to produce |
|--------------------------|--------------------------|
| "Show me the overall solution" | Architecture Vision (Phase A) |
| "What capabilities are covered?" | Business Capability Map (Phase B) |
| "How do the systems connect?" | Application Interaction Diagram (Phase C2) |
| "Where does the data live?" | Data Entity / Data Flow Diagram (Phase C1) |
| "How is it deployed?" | Deployment / Technology Diagram (Phase D) |
| "What do we build first?" | Implementation Roadmap (Phase E) |
| "Why did we make that decision?" | Architecture Decision Record |
| "How do we migrate?" | Migration Plan (Phase F) |
