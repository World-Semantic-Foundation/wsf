# Service

> **A Service** is a Function exposed by an Entity for consumption by other Entities, with defined Interfaces, Service Levels, and Operational characteristics.
## Semantic Identity

```yaml
semantic_id: wsf:Service
preferred_name: Service
aliases: [API, External Function, Offered Function]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Function
defined_by: ADR-WSF-08, ADR-WSF-25
authority: WSF
```

---

## Definition

A **Service** is an exposed Function with contractual Interfaces and operational characteristics.

Services expose Capabilities to other Entities. Service definitions include Interface contracts, SLAs, and Operational metrics.

A Service is NOT:
- An internal-only Function (use Function);
- A Capability to perform work (use Capability);
- A Product delivered to a customer (use Product);

---

## Scope and Application

Services are the externally-visible manifestation of Capabilities. Service quality is measured against SLAs.

---

## Differentia

Services have external consumers; Services have defined Interfaces (inputs, outputs, behaviour); Services MAY have Service Level Agreements (SLAs); Services are typically billable

---

## Canonical Examples

**OTCHERE Order Fulfillment Service** : an exposed Function with Interface (order submission API),), SLA (24-hour fulfillment), and operational characteristics (capacity, availability).

---

## Cross-References

- ADR-WSF-08
- ADR-WSF-25
- wsf:Function : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Service is a Tier 3 specialisation. Status: Baseline.*
