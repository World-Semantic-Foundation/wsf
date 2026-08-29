# Resource

> **A Resource** is an Entity that is consumed, used, or produced by an Activity or Process, contributing to its execution or Outcomes.
## Semantic Identity

```yaml
semantic_id: wsf:Resource
preferred_name: Resource
aliases: [Asset, Input, Material]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Entity
defined_by: ADR-WSF-08, ADR-WSF-09
authority: WSF
```

---

## Definition

A **Resource** is an Entity that Activities or Processes consume, use, or produce.

Resources are the inputs and outputs of Processes. Resource availability MAY constrain Activity scheduling.

A Resource is NOT:
- An Entity that is not consumed/used/produced (use Entity directly);
- A capability to perform work (use Capability);
- A goal the work aims to achieve (use Goal);

---

## Scope and Application

Resources include consumables (used once), durables (reused), and producers (created by the Process). Resources MAY be renewable or non-renewable.

---

## Differentia

Resources are Entities in a specific role (consumed/used/produced); Resources MAY be physical (raw materials, equipment) or non-physical (information, time); Resources have availability constraints

---

## Canonical Examples

**OTCHERE DC-01** is a Resource (computational infrastructure) consumed by digital Processes. **Order #12345** is a Resource (output) produced by the Order Fulfillment Process.

---

## Cross-References

- ADR-WSF-08
- ADR-WSF-09
- wsf:Entity : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Resource is a Tier 3 specialisation. Status: Baseline.*
