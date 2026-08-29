# Objective

> **An Objective** is a Goal with explicit success criteria and time-bound target, enabling measurable evaluation against Outcomes.
## Semantic Identity

```yaml
semantic_id: wsf:Objective
preferred_name: Objective
aliases: [SMART Goal, Target Objective, KPI Target]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Goal
defined_by: ADR-WSF-12, ADR-WSF-27
authority: WSF
```

---

## Definition

A **Objective** is a Goal with measurable success criteria and time-bound target.

Objectives enable Goal evaluation through measurable criteria. Objectives drive Activity prioritisation and Performance measurement.

A Objective is NOT:
- An open-ended aspiration (use Goal);
- A Measurement (use Measure);
- An Outcome (already achieved, use Outcome);

---

## Scope and Application

Objectives bridge Goals (aspirational) and Measurements (concrete). Objectives enable Performance management.

---

## Differentia

Objectives have quantifiable success criteria (SMART); Objectives have deadlines; Objectives MAY be aggregated into strategic Goals

---

## Canonical Examples

**OTCHERE Q3 2026 Objective: ship 95% of orders within 24 hours** : an Objective with success criteria (95%), time bound (Q3 2026), and evaluability against Order Fulfillment Outcomes.

---

## Cross-References

- ADR-WSF-12
- ADR-WSF-27
- wsf:Goal : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Objective is a Tier 3 specialisation. Status: Baseline.*
