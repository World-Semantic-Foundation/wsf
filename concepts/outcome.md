# Outcome

> **An Outcome** is the result produced by an Activity or Process, representing a change in State relative to the initial conditions.
## Semantic Identity

```yaml
semantic_id: wsf:Outcome
preferred_name: Outcome
aliases: [Result, Achievement, Output]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:State
defined_by: ADR-WSF-12, ADR-WSF-27
authority: WSF
```

---

## Definition

A **Outcome** is the State-change result produced by an Activity or Process.

Outcomes anchor Process and Activity evaluation. Outcomes enable Goal satisfaction assessment and Performance measurement.

A Outcome is NOT:
- The activity that produced the result (use Activity);
- The capability that enabled it (use Capability);
- The goal that motivated it (use Goal);

---

## Scope and Application

Outcomes are recorded as State assertions with provenance. Outcomes MAY be desired (Goals) or actual (Results).

---

## Differentia

Outcomes are results; they MAY be measured, evaluated against Goals, or compared to expected results

---

## Canonical Examples

**Order #12345 delivered on 2026-08-30 to customer** : an Outcome of the Order Fulfillment Process; measurable against Goals (on-time delivery, accuracy).

---

## Cross-References

- ADR-WSF-12
- ADR-WSF-27
- wsf:State : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Outcome is a Tier 3 specialisation. Status: Baseline.*
