# System

> **A System** is an Entity composed of interacting Components organised to perform defined Functions and achieve defined Outcomes.
## Semantic Identity

```yaml
semantic_id: wsf:System
preferred_name: System
aliases: [Composite System, Engineered System, Natural System]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Entity
defined_by: ADR-WSF-08, ADR-WSF-27
authority: WSF
```

---

## Definition

A **System** is a composed Entity of interacting Components with defined Functions, Boundaries, and Interfaces.

Systems are the subject of analysis, design, and operation. System Boundaries establish what is inside versus outside. System Interfaces define interactions.

A System is NOT:
- A non-composed Entity (use Entity);
- A Process that the System executes (use Process);
- A Component in isolation (use Component or Entity);

---

## Scope and Application

Systems range from simple (few Components, single Function) to complex (many Components, emergent behaviour). Systems MAY nest (System contains Systems).

---

## Differentia

Systems have internal structure (Components); Systems have Boundaries distinguishing inside from outside; Systems have Interfaces for interaction; Systems MAY be physical, computational, or conceptual

---

## Canonical Examples

**OTCHERE DC-01** : a System (data centre) composed of compute, storage, and networking Components, performing computational Functions within a defined Boundary.

---

## Cross-References

- ADR-WSF-08
- ADR-WSF-27
- wsf:Entity : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*System is a Tier 3 specialisation. Status: Baseline.*
