# BIAN Service Domain Reference

BIAN (Banking Industry Architecture Network) defines a standard set of Service Domains —
discrete, independently deployable banking capabilities. Use these names when labelling
architecture components, mapping requirements, or checking coverage completeness.

Each Service Domain is responsible for one and only one thing (single responsibility at the banking capability level).

---

## Service Domain Coverage by Banking Area

### Customer & Party Management
| Service Domain | What it does |
|----------------|-------------|
| Party Data Management | Maintains legal entity and person records — the customer master |
| Customer Profile | Customer preferences, relationship data, segmentation |
| Customer Agreement | Manages formal agreements between bank and customer |
| Know Your Customer | KYC workflow — identity verification, risk rating, document collection |
| Customer Relationship Management | Relationship history, interactions, next best action |
| Prospect Management | Pre-customer pipeline, lead management |

### Account Management
| Service Domain | What it does |
|----------------|-------------|
| Current Account | Operating/current account lifecycle — open, maintain, close |
| Savings Account | Savings product lifecycle |
| Term Deposit | Fixed-term deposit lifecycle |
| Loan | Loan account lifecycle — origination through closure |
| Mortgage | Mortgage-specific account management |
| Credit Facility | Revolving credit, overdraft, credit line management |

### Payments
| Service Domain | What it does |
|----------------|-------------|
| Payment Execution | Executes a single payment instruction |
| Payment Initiation | Accepts and validates a payment request from any channel |
| Payment Order | Manages the payment order lifecycle |
| ACH Fulfillment | Batch/ACH payment processing |
| SWIFT Funds Transfer | Correspondent banking / SWIFT message processing |
| Card Transaction | Card payment authorisation and processing |
| Direct Debit | Standing orders and direct debit mandates |

### Lending & Credit
| Service Domain | What it does |
|----------------|-------------|
| Credit Management | Credit policy engine — limits, rules, approval |
| Consumer Loan | Retail lending product lifecycle |
| Corporate Loan | Corporate / commercial lending |
| Mortgage Loan | Mortgage product origination and servicing |
| Collateral Management | Security / collateral registration and valuation |
| Limit Management | Credit and exposure limit tracking |
| Delinquency Management | Collections workflow and early arrears management |

### Cards
| Service Domain | What it does |
|----------------|-------------|
| Card | Card product lifecycle — issue, activate, block |
| Card Collections | Card delinquency and collections |
| Card Financial Settlement | Interchange and settlement with card networks |
| Reward Points Award | Loyalty / rewards point management |

### Trade Finance
| Service Domain | What it does |
|----------------|-------------|
| Letter of Credit | LC issuance, amendment, and settlement |
| Documentary Collection | Collections under UCP/URDG |
| Trade Finance Operations | Trade processing back-office workflow |
| Guarantees | Bank guarantee issuance and management |

### Wealth & Investments
| Service Domain | What it does |
|----------------|-------------|
| Investment Portfolio Management | Portfolio lifecycle and rebalancing |
| Investment Product | Investment product catalogue and pricing |
| Securities Custody | Safekeeping of securities |
| Order Execution | Investment order routing and execution |
| Corporate Actions | Dividend, rights issue, corporate event processing |

### Risk & Compliance
| Service Domain | What it does |
|----------------|-------------|
| Regulatory Compliance | Policy and regulatory obligation tracking |
| Regulatory Reporting | Report generation for regulators (RBI, ECB, etc.) |
| Financial Compliance | Internal financial control compliance |
| AML (Anti-Money Laundering) | Transaction monitoring, alert management |
| Fraud Detection | Real-time fraud scoring and case management |
| Credit Risk Management | Portfolio credit risk measurement |
| Operational Risk Management | Loss event capture, RCSA |

### Channels & Servicing
| Service Domain | What it does |
|----------------|-------------|
| Internet Banking | Self-service online banking |
| Contact Center Operations | Inbound and outbound contact centre workflow |
| Branch Operations | Branch transaction processing and teller workflow |
| ATM Network Management | ATM fleet management and monitoring |
| Servicing Activity Management | Customer service request workflow |

### Product & Pricing
| Service Domain | What it does |
|----------------|-------------|
| Product Directory | Product catalogue — definitions, features, eligibility |
| Product Design | Product development and configuration workflow |
| Pricing | Pricing rules and rate management |
| Fee (and Pricing) | Fee schedule management |
| Promotional Event | Campaign and promotional offer management |

### General Ledger & Finance
| Service Domain | What it does |
|----------------|-------------|
| General Ledger | Core accounting ledger — chart of accounts, journal entries |
| Financial Accounting | Period-end processing, financial statements |
| Financial Reporting | MIS, management reports |
| Nostro Management | Nostro account reconciliation and funding |

### Reference Data & Configuration
| Service Domain | What it does |
|----------------|-------------|
| Currency Exchange | Exchange rate management and conversion |
| Calendar | Business day calendar and holiday management |
| Legal Entity | Bank's own legal entity structure |
| Reference Data Management | Static data — countries, currencies, instruments |

---

## BIAN Coverage Check — How to Use

When designing a solution, run this checklist:
1. List all BIAN Service Domains in scope for the client's requirements
2. Map each requirement to one primary BIAN domain
3. Identify any domain that is required but not addressed by any component — this is a gap
4. Flag domains where two components claim to own the same responsibility — this is a conflict

A well-designed banking architecture should have **no gaps and no conflicts** at the Service Domain level.

---

## BIAN Service Operations

Each Service Domain exposes its capabilities via standard **Service Operations**:

| Operation | Purpose |
|-----------|---------|
| Initiate | Create a new instance of the domain's core object |
| Update | Modify an existing instance |
| Retrieve | Query data from the domain |
| Execute | Trigger a processing action |
| Evaluate | Run an assessment or calculation |
| Notify | Push an event/notification out |
| Grant | Approve an action or request |
| Request | Submit a request for action by another domain |

---

## BIAN and Microservices

Each BIAN Service Domain maps naturally to one or more microservices.
The rule: one microservice should not span two Service Domains.
If a microservice is doing work from two different BIAN domains, it should be split.
