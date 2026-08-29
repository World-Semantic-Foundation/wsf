# Constraint

> **A Constraint** is a limiting condition on an Entity, Activity, or State, restricting the set of valid possibilities or behaviours.
## Semantic Identity

```yaml
semantic_id: wsf:Constraint
preferred_name: Constraint
aliases: [Limitation, Restriction, Bound]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Proposition
defined_by: ADR-WSF-13
authority: WSF
```

---

## Definition

A **Constraint** is a limiting condition restricting valid States or behaviours.

Constraints define the space of valid States and behaviours. Constraints MAY be checked, violated, or enforced.

A Constraint is NOT:
- An enabling condition (use Capability or Disposition);
- A goal to be achieved (use Goal);
- A rule expressed with formal logic (use Rule);

---

## Scope and Application

Constraints include physical constraints (gravity, conservation), logical constraints (consistency), business constraints (budget), regulatory constraints (compliance).

---

## Differentia

Constraints restrict possibilities; Constraints MAY be intrinsic (natural laws) or extrinsic (governance); Constraints MAY be soft (preferences) or hard (inviolable)

---

## Canonical Examples

**OTCHERE warehouse capacity constraint: max 50,000 SKUs** : a Constraint limiting inventory storage; constrains inventory Activities; violation triggers overflow handling.

---

## Cross-References

- ADR-WSF-13
- wsf:Proposition : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Constraint is a Tier 3 specialisation. Status: Baseline.*
