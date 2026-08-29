# Capability

> **A grounded potential of an Entity to accomplish a defined kind of effect — a specialized form of Disposition.**

---

## Semantic Identity

```yaml
semantic_id: wsf:Capability
preferred_name: Capability
status: Baseline
version: 0.1.0
defined_by: ADR-WSF-07 (Capacity–Ability–Capability)
classification: Derived (Tier 3)
parent_class: wsf:Disposition
domain: Disposition
```

---

## Definition

A **Capability** represents an attributable, contextualized potential of an Entity to accomplish a defined kind of effect or outcome, grounded in relevant Capacity and Ability within a defined context.

**Capability** is NOT:
- An abstract label
- A current performance indicator
- Equivalent to Process, Function, Service, or Outcome
- A free-floating primitive (it is grounded in Disposition)

---

## The Disposition Realization Chain

```
DISPOSITION (foundational)
    │
    ├── Capacity      (potential/extent available)
    ├── Ability       (competence/disposition to perform)
    └── Capability    (attributable, contextualized potential)
                        │
                        │ enables
                        ▼
                     FUNCTION    (purposeful kind of activity)
                        │
                        │ realized as
                        ▼
                      ACTIVITY    (what can be performed)
                        │
                        │ occurs as
                        ▼
                       EVENT      (actual occurrence)
                        │
                        │ produces/causes
                        ▼
                      CHANGE
                        │
                        ▼
                      STATE
```

This is a semantic **REALIZATION** chain, not inheritance. Capability is grounded in Disposition; Activity realizes Capability as Event; Event produces Change to State.

---

## Key Distinctions

| Concept | Distinction from Capability |
|---|---|
| **Capacity** | Capacity is potential/extent. Capability is the realized/attributable potential. |
| **Ability** | Ability is competence/disposition. Capability grounds in Ability. |
| **Function** | Function is the kind of activity. Capability enables Function. |
| **Activity** | Activity is what can be performed. Capability may enable it. |
| **Process** | Process is structured activity. Process ≠ Capability. |
| **Service** | Service exposes Capability. Service ≠ Capability. |
| **Outcome** | Outcome is achieved result. Capability enables Outcome. |
| **Resource** | Resource may enable Capability. Resource ≠ Capability. |

---

## Canonical Example: WSF Capability

```yaml
- capability:
    semantic_id: wsf-cap:OrderFulfillment
    preferred_name: Order Fulfillment
    classification: Foundational Capability
    parent: wsf:Capability
    bearer:
      - entity: wsf-ex:OTCHERE-Inc
        role: Enterprise
    grounding:
      capacity:
        - type: Processing Capacity
          extent: 100,000 orders/day
      ability:
        - type: Operational Competence
          evidence: 10 years operational history
    context:
      domain: Enterprise Operations
      period: 2024-01-01 to present
    enables:
      function: wsf-fn:ManageCustomerOrders
    produces:
      outcome: wsf-out:FulfilledOrder
    evidence:
      - source: Operational metrics
      - source: Architecture assessment
    provenance:
      asserted_by: OTCHERE Inc Architecture Team
      asserted_at: 2026-08-29
```

### OpenDEA Specialization

```yaml
- capability:
    semantic_id: odea:BusinessCapability
    preferred_name: Business Capability
    parent: wsf:Capability
    specialization_context:
      context: Enterprise Architecture
      organization_type: Business
    additional_constraints:
      - must contribute to Business Outcome
      - must be traceable to Business Function
    examples:
      - Order Management Business Capability
      - Customer Service Business Capability
      - Financial Planning Business Capability
```

### Capability vs Actual Event

```
"OTCHERE Inc has Order Fulfillment Capability"     (Disposition — capability)
   ↓
"OTCHERE Inc fulfilled Order #12345 on 2026-08-29"  (Occurrence — event)

The capability persists.
The event occurred (or did not).
These are different statements.
```

---

## Semantic Validation Test

A proposed capability should answer:

1. **What Entity** does it concern?
2. **What Role/context** is relevant?
3. **What Capacity** supports it?
4. **What Ability** supports it?
5. **What Function** does it enable?
6. **What Outcome** does it support?
7. **What Evidence** supports the assertion?

If these questions cannot be answered, the label may not be a semantically grounded capability.

---

## Constraints

- A Capability MUST be attributable to an Entity (in a Role)
- A Capability MUST be grounded in Capacity + Ability (directly or by context)
- A Capability is NOT equivalent to current performance
- A Capability does NOT require a Process (it may exist without being exercised)
- A Capability is NOT equivalent to Function (it enables Function)

---

## Specialization Pattern

```
WSF Capability
    │
    ├── Business Capability       (OpenDEA)
    ├── Operational Capability    (OpenDEA)
    ├── Technical Capability      (OpenDEA)
    ├── Organizational Capability (organizational context)
    ├── Digital Capability        (technology context)
    └── ...
```

Specialization must preserve Capability semantics (per ADR-WSF-04 — Semantic Inheritance).

---

## Related Concepts

- **Disposition** (wsf:Disposition) — Parent category
- **Capacity** (wsf:Capacity) — One grounding dimension
- **Ability** (wsf:Ability) — Other grounding dimension
- **Function** (wsf:Function) — What capability enables
- **Entity** (wsf:Entity) — Bearer of capability
- **Role** (wsf:Role) — Contextual attribution

---

## Cross-References

- ADR-WSF-07: Capacity–Ability–Capability (parent)
- Investigation 1: Capability–Ability–Capacity (foundation)
- Investigation 4: Ontological Classification (Capability is not free-floating primitive)
- Investigation 7: Existence-Occurrence (Disposition grounding)
- ADR-WSF-04: Semantic Inheritance (specialization rules)
- ADR-WSF-09: Foundational Concept Taxonomy

---

*Capability is a Tier 3 derived concept grounded in Disposition (Tier 1). Status: Baseline.*
