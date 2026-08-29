# Activity

> **An Activity** is an actual occurrence of a Function by an Entity at a specific time, producing Events that may be recorded as evidence.
## Semantic Identity

```yaml
semantic_id: wsf:Activity
preferred_name: Activity
aliases: [Performance, Operation, Execution]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Event
defined_by: ADR-WSF-12, ADR-WSF-27
authority: WSF
```

---

## Definition

A **Activity** is an actual occurrence of a Function by an Entity, observed at a specific time and place.

Activities bridge Functions (potential) and Outcomes (results). Each Activity has a timestamp, executor, inputs, outputs, and MAY carry Measurements.

A Activity is NOT:
- The potential to perform work (use Function or Capability);
- An abstract Process template (use Process);
- A mere State observation (use State);

---

## Scope and Application

Activities are the realisation of Functions. Activity records MAY carry quantitative or qualitative data.

---

## Differentia

Activities are actual (occurred), not potential; they are time-bounded; they produce observable Events; Activities MAY be measured

---

## Canonical Examples

**Order #12345 fulfilled on 2026-08-29 by OTCHERE Inc** : an Activity (occurrence of Order Fulfillment Function) with start time, completion time, executor, and Outcome.

---

## Cross-References

- ADR-WSF-12
- ADR-WSF-27
- wsf:Event : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Activity is a Tier 3 specialisation. Status: Baseline.*
