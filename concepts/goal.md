# Goal

> **A Goal** is a desired Outcome expressed as a Proposition, defining a target State that an Entity intends to reach through Activities and Resource allocation.
## Semantic Identity

```yaml
semantic_id: wsf:Goal
preferred_name: Goal
aliases: [Objective, Target, Aim]
status: Baseline
version: 0.1.0
classification: Tier 3 (Specialisation)
parent: wsf:Proposition
defined_by: ADR-WSF-12, ADR-WSF-27
authority: WSF
```

---

## Definition

A **Goal** is a desired-State Proposition that motivates Activity and Resource allocation.

Goals drive Activity selection and Resource allocation. Goals enable Outcome evaluation and Performance assessment.

A Goal is NOT:
- An achieved Outcome (use Outcome);
- A Capability that might achieve it (use Capability);
- A general aspiration without evaluation criteria (use Term or Statement);

---

## Scope and Application

Goals guide planning, decision-making, and Activity prioritisation. Goal satisfaction is evaluated against actual Outcomes.

---

## Differentia

Goals are future-directed; Goals are evaluable against Outcomes; Goals MAY be decomposed into sub-goals; Goals MAY conflict (requiring trade-offs)

---

## Canonical Examples

**OTCHERE Inc Goal: 99% on-time order delivery** : a Goal evaluated against actual Outcomes (delivery timestamps); decomposable into sub-goals (warehouse efficiency, shipping reliability).

---

## Cross-References

- ADR-WSF-12
- ADR-WSF-27
- wsf:Proposition : the parent foundational concept
- `/wsf-examples/` : worked examples

---

*Goal is a Tier 3 specialisation. Status: Baseline.*
