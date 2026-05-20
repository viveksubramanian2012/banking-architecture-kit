# Banking Architecture Patterns

Proven patterns for banking solution design. Each entry covers: what it is, when to use it, and the trade-offs.

---

## Integration Patterns

### API-Led Connectivity
**Structure:** System APIs (expose raw capabilities) → Process APIs (orchestrate) → Experience APIs (channel-specific).
**Use when:** You need to serve multiple channels from the same backend services without duplicating logic.
**Trade-off:** Three-layer adds latency; requires disciplined API governance or the layers collapse.
**Banking example:** Core banking system API → Loan origination process API → Mobile banking experience API.

### Event-Driven Architecture (EDA)
**Structure:** Producers emit domain events; consumers subscribe independently. No direct coupling.
**Use when:** Real-time processing across domains (e.g., payment completed → update account balance → trigger notification → update reporting).
**Trade-off:** Eventual consistency. Not suitable where you need synchronous confirmation (e.g., payment authorisation).
**Banking example:** Kafka topics per BIAN domain. Account Management publishes `account.balance.updated`; Regulatory Reporting and Notification both consume it independently.

### Synchronous Request-Response (REST / gRPC)
**Use when:** The caller needs an immediate answer — authorisation, balance enquiry, rate quote.
**Trade-off:** Tight temporal coupling. If the downstream is slow, the upstream waits.
**Banking example:** Card authorisation — the terminal cannot move on until it receives approve/decline.

### Orchestration via BPM / Workflow Engine
**Use when:** Multi-step processes with human tasks, SLA tracking, and conditional branching — loan origination, account opening, KYC.
**Trade-off:** BPM engines become a bottleneck if used for high-volume, low-complexity flows.
**Banking example:** BPMN workflow for KYC — document collection → verification → risk scoring → approval → account activation.

### Canonical Data Model (CDM)
**Structure:** Define a bank-wide data model for key entities (Customer, Account, Transaction). All integrations translate to/from CDM.
**Use when:** Multiple source systems publish the same entity in different formats.
**Trade-off:** CDM governance overhead. CDMs rot if not actively maintained.

### Strangler Fig (Legacy Modernisation)
**Structure:** New capabilities built in the modern architecture; old system calls routed through a facade that gradually shifts traffic.
**Use when:** Replacing a monolithic core banking system without a big-bang cutover.
**Trade-off:** Long transition period means running two systems simultaneously.
**Banking example:** New payments microservice deployed; facade intercepts payment calls and routes to new service while legacy handles others.

---

## Core Banking Architecture Patterns

### Modular Core Banking
**Structure:** Core banking broken into independently deployable modules (each mapping to a BIAN domain) that share a common database.
**Use when:** Bank needs flexibility to upgrade one module without touching others.
**Trade-off:** Shared database creates coupling at the data layer even if application layer is separated.

### Composable Banking / Headless Core
**Structure:** Core banking exposes everything via APIs. Channels and processes are built outside the core.
**Use when:** Bank wants to move fast on channel innovation without waiting for core banking release cycles.
**Trade-off:** Core banking becomes a "dumb" ledger; business logic lives in the integration layer.

### Two-Speed Architecture
**Structure:** Legacy core handles settlements and accounting (slow, stable). Digital layer handles engagement and UX (fast, experimental).
**Use when:** Bank cannot replace the core quickly but must deliver digital experiences now.

---

## Deployment Patterns

### Active-Active Multi-Region
**Use when:** Bank requires zero-downtime and cross-region failover (typically for payments or trading systems).
**Requirements:** Distributed transaction management, data replication, global load balancing.

### Active-Passive DR
**Use when:** Bank requires recovery from a full site failure but can tolerate a defined RTO/RPO (e.g., 4 hours RTO, 1 hour RPO).

### Cloud-Native (Kubernetes / Containerised)
**Use when:** Bank is building new capabilities and wants horizontal scalability, CI/CD, and infrastructure portability.
**Pattern:** Microservices in containers → Kubernetes orchestration → Service mesh → API Gateway for external exposure.

### Hybrid Cloud
**Use when:** Sensitive data must remain on-premise; non-sensitive workloads can run in the cloud.
**Pattern:** On-premise core banking + cloud-hosted digital layer, connected via private link.

---

## Security Architecture Patterns

### Zero Trust Network Architecture
**Principle:** Never trust, always verify. No implicit trust based on network location.
**Components:** Identity-based access, micro-segmentation, continuous verification, least-privilege.

### API Security Layers
1. Edge: WAF, DDoS protection, rate limiting
2. Gateway: OAuth 2.0 / OpenID Connect, JWT validation, API key management
3. Service-to-service: mTLS, service mesh policies
4. Data: Field-level encryption for PII, tokenisation for card data

---

## Non-Functional Requirement Benchmarks (Banking Defaults)

| NFR | Typical banking requirement |
|-----|---------------------------|
| Availability | 99.99% for payments, 99.9% for non-critical |
| Payment throughput | 1,000–10,000 TPS for real-time payments |
| API response time | < 200ms P95 for synchronous APIs |
| Batch processing | EOD batch must complete within 4–6 hour window |
| RTO (recovery time) | 4 hours for tier-1 systems |
| RPO (recovery point) | 1 hour for tier-1 systems |
| Data retention | 7–10 years for transaction data (varies by jurisdiction) |
| Audit trail | Immutable, tamper-evident log for all financial transactions |
