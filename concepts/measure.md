# Measure

> **A Measure** is a Proposition expressing a quantitative or qualitative observation of an Entity, Activity, or State, enabling evaluation against Objectives.
## Semantic Identity

```yaml
semantic_id: wsf:Measure
preferred_name: Measure
aliases: [Metric, Indicator, KPI, Observation]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Proposition
defined_by: ADR-WSF-12, ADR-WSF-27
authority: WSF
```

---

## Definition

A **Measure** is an observational Proposition quantifying or qualifying an Entity, Activity, or State.

Measures quantify reality for evaluation. Measures enable Objective progress tracking and Performance assessment.

A Measure is NOT:
- The thing being measured (use Activity, State, etc.);
- An Objective (target, use Objective);
- Raw data without interpretation (use Evidence);

---

## Scope and Application

Measures include KPIs, metrics, indicators, scores. Measure definitions include units, ranges, and collection methods.

---

## Differentia

Measures have units (quantitative) or scales (qualitative); Measures have measurement methods; Measures MAY be aggregated; Measures enable Objective evaluation

---

## Canonical Examples

**OTCHERE Order Fulfillment Latency Measure: average time from order receipt to delivery** : a Measure with units (hours), method (timestamp diff), aggregation (mean), enables Objective evaluation (against 24-hour target).

---

## Cross-References

- ADR-WSF-12
- ADR-WSF-27
- wsf:Proposition : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Measure is a Tier 3 specialisation. Status: Baseline.*
