# Product

> **A coherent, governable bundle of Functions and Services offered by an Entity for exchange, consumption, or value realization by other Entities.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Product
preferred_name: Product
status: Baseline
version: 1.0.0
defined_by: ADR-WSF-36 (Product Semantic Grounding)
classification: Tier 3 (Specialisation)
parent: wsf:Function
authority: WSF
```

---

## Definition

A **Product** is a coherent, governable bundle of Functions and Services offered by an Entity for exchange, consumption, or value realization by other Entities.

A Product is NOT:
- A physical artifact only (a Product may be intangible);
- A System (a System operates; a Product is offered);
- A Service alone (a Service is a single Function exposed; a Product composes);
- A Capability (a Capability is potential; a Product is a packaged offering).

A Product IS:
- A governance unit: identity, provenance, version, and lifecycle attach to it;
- A composition: it bundles one or more Functions and/or Services;
- An exchangeable: it is offered by an Entity to other Entities;
- A value carrier: consumption realizes value for the consuming Entity.

---

## Why Product Is a Specialisation Concept

Product completes the vocabulary chain:

```
Capability -> Disposition -> Function -> Service -> Product
```

WSF grounds Service as a Function exposed by an Entity for consumption by other Entities (Tier 3, parent wsf:Function). Product composes Functions and Services into an exchangeable, governable unit. This keeps the inheritance chain intact and gives downstream programs (e.g., Enterprise-Semantics Agentic Product, Autonomous Product) an authoritative base record to specialize.

---

## Key Distinctions

| Concept | Relationship to Product |
|---|---|
| **Function** | The parent: an intended-purpose disposition; Product packages Functions |
| **Service** | A single Function exposed for consumption; a Product may bundle many Services |
| **Capability** | Potential; a Product is a packaged offering, not a potential |
| **Resource** | A thing consumed or used; a Product is offered and exchanged |
| **System** | An operating construct; a System may realize a Product's Functions |
| **Outcome** | The value realized on consumption; a Product enables Outcomes |

---

## Canonical Example

### OTCHERE Inc (Enterprise)

```yaml
- product:
    semantic_id: wsf-ex:OTCHERE-DataPlatform
    preferred_name: OTCHERE Data Platform
    type: Digital Product
    offered_by: wsf-ex:OTCHERE-Inc
    bundles:
      functions:
        - wsf-ex:DataIngestionFunction
        - wsf-ex:DataStorageFunction
        - wsf-ex:DataAnalysisFunction
      services:
        - wsf-ex:ManagedIngestionService
        - wsf-ex:ManagedHostingService
    lifecycle_state: Generally Available
    context:
      domain: Enterprise
      market: Commercial
    provenance:
      source: OTCHERE Inc Product Catalogue
      asserted_by: Product Management
      asserted_at: 2026-09-26
```

---

## Relationships

### Product participates in

- `offered_by` → Entity (the offering Entity)
- `bundles` → Function (composition)
- `bundles` → Service (composition)
- `consumed_by` → Entity (the consuming Entity)
- `enables` → Outcome (value realization)
- `governed_by` → Authority (product governance)

---

## Constraints

- A Product MUST be offered by an Entity (offering is constitutive of Product)
- A Product MUST bundle at least one Function or Service
- A Product MUST have identity and provenance (per Principle 4: Identity Separation)
- A Product's assertions MUST have provenance
- Specializations of Product SHALL NOT redefine the foundation locally (per ADR-WSF-36 §2.3; WSF is the semantic authority)

---

## Specialization Patterns

```
wsf:Product
    │
    ├── Agentic Product       (material agentic behavior at product level)
    ├── Autonomous Product    (material autonomous behavior at product level)
    ├── Physical Product      (tangible carrier)
    ├── Digital Product        (software, data, platform offerings)
    └── Service Product       (pure-service bundle)
```

Boundary assertions per ADR-WSF-36 §2.4: specialization requires material agentic/autonomous behavior at the product level; AI is not required.

---

## Related Concepts

- [Function](./function.md) : parent concept
- [Service](./service.md) : bundled exposure of a Function
- [Capability](./capability.md) : ultimate disposition root
- [Outcome](./outcome.md) : value realized on consumption
- [Entity](./entity.md) : offering and consuming parties

---

## Cross-References

- ADR-WSF-36: Product Semantic Grounding (defining decision)
- CR-WSF-36: companion change request
- wsf-spec PR #1: vocabulary landing (additive-only, 2026-09-27)
- Recon-ES-006: gap finding resolved by this concept

---

*Product is a Tier 3 specialisation concept. Status: Baseline.*
